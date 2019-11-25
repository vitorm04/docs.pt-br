---
title: Algoritmo de carregamento de assembly gerenciado-.NET Core
description: Descrição dos detalhes do algoritmo de carregamento de assembly gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973510"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmo de carregamento de assembly gerenciado

Os assemblies gerenciados são localizados e carregados com um algoritmo que envolve vários estágios.

Todos os assemblies gerenciados, exceto assemblies satélite e `WinRT` assemblies, usam o mesmo algoritmo.

## <a name="when-are-managed-assemblies-loaded"></a>Quando os assemblies gerenciados são carregados?

O mecanismo mais comum para disparar uma carga de assembly gerenciada é uma referência de assembly estática. Essas referências são inseridas pelo compilador sempre que o código usa um tipo definido em outro assembly. Esses assemblies são carregados (`load-by-name`) conforme necessário pelo tempo de execução.

O uso direto de APIs específicas também irá disparar cargas:

|API  |Descrição  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Carregar do caminho.|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Carregar do objeto.|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Carregar do caminho em uma nova instância de <xref:System.Runtime.Loader.AssemblyLoadContext>|A nova instância <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Carregar do caminho na instância de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.<p>Adiciona um manipulador de <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> a <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. O manipulador carregará as dependências do assembly de seu diretório.|A instância <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`|Inferido do chamador.<p>Prefira <xref:System.Runtime.Loader.AssemblyLoadContext> métodos.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Carregar do objeto em uma nova instância de <xref:System.Runtime.Loader.AssemblyLoadContext>.|A nova instância <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`|Inferido do chamador.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> métodos com um argumento `assemblyResolver`.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Se o tipo `name` descreve um tipo genérico de assembly qualificado, dispare um `Load-by-name`.|Inferido do chamador.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> ao usar nomes de tipo qualificado de assembly.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`|Inferido do chamador.<p>Prefira <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> métodos usando um argumento <xref:System.Type>.|

## <a name="algorithm"></a>Algoritmo

O algoritmo a seguir descreve como o tempo de execução carrega um assembly gerenciado.

1. Determinar o <xref:System.Runtime.Loader.AssemblyLoadContext>de `active`.

    - Para uma referência de assembly estático, o `active` <xref:System.Runtime.Loader.AssemblyLoadContext> é a instância que carregou o assembly de referência.
    - As APIs preferenciais tornam a `active` <xref:System.Runtime.Loader.AssemblyLoadContext> explícita.
    - Outras APIs inferem o <xref:System.Runtime.Loader.AssemblyLoadContext>`active`. Para essas APIs, a propriedade <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> é usada. Se seu valor for `null`, a instância <xref:System.Runtime.Loader.AssemblyLoadContext> inferida será usada.
    - Consulte a tabela acima.

2. Para os métodos de `Load-by-name`, o <xref:System.Runtime.Loader.AssemblyLoadContext> ativo carrega o assembly. Em ordem de prioridade por:
    - Verificando sua `cache-by-name`.

    - Chamar a função <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.

    - Verificando o cache das instâncias de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> e executando a lógica de [investigação padrão do assembly gerenciado](default-probing.md#managed-assembly-default-probing) .

    - Gerando o evento <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> para o AssemblyLoadContext ativo.

    - Gerando o evento <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

3. Para os outros tipos de cargas, o `active` <xref:System.Runtime.Loader.AssemblyLoadContext> carrega o assembly. Em ordem de prioridade por:
    - Verificando sua `cache-by-name`.

    - Carregando a partir do caminho especificado ou do objeto de assembly bruto.

4. Em ambos os casos, se um assembly for carregado recentemente, então:
   - O evento <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> é gerado.
   - Uma referência é adicionada à `cache-by-name`da instância de <xref:System.Runtime.Loader.AssemblyLoadContext> do assembly.

5. Se o assembly for encontrado, uma referência será adicionada conforme necessário para o `cache-by-name`de <xref:System.Runtime.Loader.AssemblyLoadContext> da instância do `active`.

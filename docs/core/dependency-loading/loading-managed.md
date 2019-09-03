---
title: Algoritmo de carregamento de assembly gerenciado-.NET Core
description: Descrição dos detalhes do algoritmo de carregamento de assembly gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bf95cbd0eebed064f0198ae9b0f7a4288a938f8a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70234617"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmo de carregamento de assembly gerenciado

Os assemblies gerenciados são localizados e carregados com um algoritmo que envolve vários estágios.

Todos os assemblies gerenciados, exceto `WinRT` assemblies satélite e assemblies, usam o mesmo algoritmo.

## <a name="when-are-managed-assemblies-loaded"></a>Quando os assemblies gerenciados são carregados?

O mecanismo mais comum para disparar uma carga de assembly gerenciada é uma referência de assembly estática. Essas referências são inseridas pelo compilador sempre que o código usa um tipo definido em outro assembly. Esses assemblies são carregados (`load-by-name`) conforme necessário pelo tempo de execução.

O uso direto de APIs específicas também irá disparar cargas:

|API  |Descrição  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Carregar do caminho.|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Carregar do objeto.|A instância [deste](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Carregar do caminho em uma nova <xref:System.Runtime.Loader.AssemblyLoadContext> instância|A nova instância <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Carregar do caminho na <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instância.<p>Adiciona um <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> manipulador a <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. O manipulador carregará as dependências do assembly de seu diretório.|A instância <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Inferido do chamador.<p>Prefira <xref:System.Runtime.Loader.AssemblyLoadContext> métodos.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Carregar do objeto.|Inferido do chamador.<p>Prefira <xref:System.Runtime.Loader.AssemblyLoadContext> métodos.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Inferido do chamador.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> métodos com um `assemblyResolver` argumento.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Se Type `name` descrever um tipo genérico de assembly qualificado, dispare um `Load-by-name`.|Inferido do chamador.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> ao usar nomes de tipo qualificado de assembly.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Inferido do chamador.<p>Prefira <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> métodos que tomam <xref:System.Type> um argumento.|

## <a name="algorithm"></a>Algoritmo

O algoritmo a seguir descreve como o tempo de execução carrega um assembly gerenciado.

1. Determine o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.

    - Para uma referência de assembly estática, `active` a <xref:System.Runtime.Loader.AssemblyLoadContext> é a instância que carregou o assembly de referência.
    - As APIs preferenciais `active` tornam o <xref:System.Runtime.Loader.AssemblyLoadContext> explícito.
    - Outras APIs inferem o `active`. <xref:System.Runtime.Loader.AssemblyLoadContext> Para essas APIs, a <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> propriedade é usada. Se seu valor for `null`, a instância inferida <xref:System.Runtime.Loader.AssemblyLoadContext> será usada.
    - Consulte a tabela acima.

2. Para os `Load-by-name` métodos, o ativo <xref:System.Runtime.Loader.AssemblyLoadContext> carrega o assembly. Em ordem de prioridade por:
    - Verificando `cache-by-name`seu.

    - Chamando a <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> função.

    - Verificando <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> o cache de instâncias e executando a lógica de [investigação padrão do assembly gerenciado](default-probing.md#managed-assembly-default-probing) .

    - Gerando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento para o AssemblyLoadContext ativo.

    - Gerando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.

3. Para os outros tipos de cargas, o `active` <xref:System.Runtime.Loader.AssemblyLoadContext> carrega o assembly. Em ordem de prioridade por:
    - Verificando `cache-by-name`seu.

    - Carregando a partir do caminho especificado ou do objeto de assembly bruto.

4. Em ambos os casos, se um assembly for carregado recentemente, então:
   - O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento é gerado.
   - Uma referência é adicionada à <xref:System.Runtime.Loader.AssemblyLoadContext> `cache-by-name`instância do assembly.

5. Se o assembly for encontrado, uma referência será adicionada conforme necessário para a `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instância do `cache-by-name`.

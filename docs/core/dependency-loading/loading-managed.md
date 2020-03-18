---
title: Algoritmo de carregamento de montagem gerenciado - .NET Core
description: Descrição dos detalhes do algoritmo de carregamento de montagem gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973510"
---
# <a name="managed-assembly-loading-algorithm"></a>Algoritmo de carregamento de montagem gerenciado

Os conjuntos gerenciados são localizados e carregados com um algoritmo que envolve vários estágios.

Todos os conjuntos gerenciados, `WinRT` exceto conjuntos de satélites e conjuntos, usam o mesmo algoritmo.

## <a name="when-are-managed-assemblies-loaded"></a>Quando os conjuntos gerenciados são carregados?

O mecanismo mais comum para ativar uma carga de montagem gerenciada é uma referência de montagem estática. Essas referências são inseridas pelo compilador sempre que o código usa um tipo definido em outro conjunto. Estas montagens são`load-by-name`carregadas ( ) conforme necessário pelo tempo de execução.

O uso direto de APIs específicas também acionará cargas:

|API  |Descrição  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|O [caso deste.](../../csharp/language-reference/keywords/this.md)|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Carga do caminho.|O [caso deste.](../../csharp/language-reference/keywords/this.md)|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Carregar do objeto.|O [caso deste.](../../csharp/language-reference/keywords/this.md)|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Carregar do caminho <xref:System.Runtime.Loader.AssemblyLoadContext> em uma nova instância|A nova instância <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Carregar do caminho <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> na instância.<p>Adiciona <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> um <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>manipulador a . O manipulador carregará as dependências da montagem de seu diretório.|A instância <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Inferido de ouvinte.<p>Prefiro <xref:System.Runtime.Loader.AssemblyLoadContext> métodos.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Carregar do objeto <xref:System.Runtime.Loader.AssemblyLoadContext> em uma nova instância.|A nova instância <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Inferido de ouvinte.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> métodos com argumentos. `assemblyResolver`|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Se `name` o tipo descrever um tipo `Load-by-name`genérico qualificado de montagem, acione um .|Inferido de ouvinte.<p>Prefira <xref:System.Type.GetType%2A?displayProperty=nameWithType> ao usar nomes de tipo qualificados para montagem.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Inferido de ouvinte.<p>Prefira <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> métodos para <xref:System.Type> argumentar.|

## <a name="algorithm"></a>Algoritmo

O algoritmo a seguir descreve como o tempo de execução carrega um conjunto gerenciado.

1. Determine `active` <xref:System.Runtime.Loader.AssemblyLoadContext>o .

    - Para uma referência de `active` <xref:System.Runtime.Loader.AssemblyLoadContext> montagem estática, é a instância que carregou o conjunto de referência.
    - As APIs `active` <xref:System.Runtime.Loader.AssemblyLoadContext> preferidas deixam explícito.
    - Outras APIs `active` <xref:System.Runtime.Loader.AssemblyLoadContext>inferem o . Para essas APIs, a <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> propriedade é usada. Se o `null`seu valor for, então a instância inferida <xref:System.Runtime.Loader.AssemblyLoadContext> é usada.
    - Veja a tabela acima.

2. Para `Load-by-name` os métodos, <xref:System.Runtime.Loader.AssemblyLoadContext> o ativo carrega a montagem. Em ordem prioritária por:
    - Verificando `cache-by-name`seu .

    - Chamando <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> a função.

    - Verificando <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> o cache das instâncias e executando a lógica [de sondagem padrão do conjunto gerenciado.](default-probing.md#managed-assembly-default-probing)

    - Elevando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento para o AssemblyLoadContext ativo.

    - Levantando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.

3. Para os outros tipos de `active` <xref:System.Runtime.Loader.AssemblyLoadContext> cargas, as cargas do conjunto. Em ordem prioritária por:
    - Verificando `cache-by-name`seu .

    - Carregando a partir do caminho especificado ou do objeto de montagem bruto.

4. Em ambos os casos, se uma montagem estiver recém-carregada, então:
   - O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento foi levantado.
   - Uma referência é adicionada à <xref:System.Runtime.Loader.AssemblyLoadContext> instância `cache-by-name`da assembléia.

5. Se a montagem for encontrada, uma referência `active` <xref:System.Runtime.Loader.AssemblyLoadContext> será `cache-by-name`adicionada conforme necessário à da instância.

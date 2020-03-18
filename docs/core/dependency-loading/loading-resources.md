---
title: Algoritmo de carregamento de montagem por satélite - .NET Core
description: Descrição dos detalhes do algoritmo de carregamento de montagem do satélite no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70234605"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algoritmo de carregamento de montagem por satélite

Os conjuntos de satélites são usados para armazenar recursos localizados personalizados para linguagem e cultura.

Os conjuntos de satélites usam um algoritmo de carregamento diferente dos conjuntos gerais gerenciados.

## <a name="when-are-satellite-assemblies-loaded"></a>Quando os conjuntos de satélites são carregados?

Os conjuntos de satélites são carregados ao carregar um recurso localizado.

A API básica para carregar <xref:System.Resources.ResourceManager?displayProperty=fullName> recursos localizados é a classe. Em última <xref:System.Resources.ResourceManager> análise, <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> a classe <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>chamará o método para cada um .

As APIs de nível superior podem abstrair a API de baixo nível.

## <a name="algorithm"></a>Algoritmo

O processo de fallback de recurso do .NET CORE envolve as seguintes etapas:

1. Determine `active` <xref:System.Runtime.Loader.AssemblyLoadContext> a instância. Em todos os `active` casos, a instância <xref:System.Runtime.Loader.AssemblyLoadContext>é a da assembléia executora.

2. A `active` instância tenta carregar uma montagem via satélite para a cultura solicitada em ordem prioritária por:
    - Verificando seu cache.
    - Verificando o diretório da montagem em execução atual para um <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> subdiretório `es-MX`que corresponda ao solicitado (por exemplo ).

        > [!NOTE]
        > Esse recurso não foi implementado no .NET Core antes do 3.0.
        >
        > [!NOTE]
        > No Linux e macOS, o subdiretório é sensível a maiúsculas e minúsculas e deve:
        > - Exatamente caso compatível.
        > - Seja em minúsculas.

    - Se `active` for <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> a instância, executando a lógica de sondagem padrão de [montagem de satélite (recurso).](default-probing.md#satellite-resource-assembly-probing)

    - Chamando <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> a função.

    - Levantando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento.

    - Levantando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.

3. Se um conjunto de satélite estiver carregado:
   - O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento foi levantado.
   - A assembléia é procurada pelo recurso solicitado. Se o tempo de execução encontrar o recurso na montagem, ele o usará. Se não encontrar o recurso, ele continua a pesquisa.

    > [!NOTE]
    > Para localizar um recurso dentro do assembly satélite, o runtime procura o arquivo de recurso solicitado pelo <xref:System.Resources.ResourceManager> para o <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> atual. Dentro do arquivo de recursos, ele procura o nome do recurso solicitado. Se nenhum for encontrado, o recurso será tratado como não encontrado.

4. O tempo de execução a seguir pesquisa os conjuntos de cultura dos pais através de muitos níveis potenciais, cada vez repetindo as etapas 2 & 3.

    Cada cultura tem apenas um pai, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> que é definido pela propriedade.

    A busca por culturas parentais <xref:System.Globalization.CultureInfo.Parent%2A> pára <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>quando a propriedade de uma cultura é .

    Para <xref:System.Globalization.CultureInfo.InvariantCulture>o , não voltamos aos passos 2 & 3, mas sim continuar com o passo 5.

5. Se o recurso ainda não for encontrado, o recurso para a cultura padrão (recuo) será usado.

   Normalmente, os recursos para a cultura padrão são incluídos no assembly do aplicativo principal. No entanto, <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> você <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> pode especificar para a propriedade. Este valor indica que o local final de recuo para os recursos é uma montagem de satélite em vez da montagem principal.

    > [!NOTE]
    > A cultura padrão é o retrocesso final. Portanto, recomendamos que você sempre inclua um conjunto exaustivo de recursos no arquivo de recursos padrão. Isso ajuda a evitar que exceções sejam lançadas. Ao ter um conjunto exaustivo, você fornece um recuo para todos os recursos e garante que pelo menos um recurso esteja sempre presente para o usuário, mesmo que não seja culturalmente específico.

6. Enfim,
   - Se o tempo de execução não encontrar um arquivo de <xref:System.Resources.MissingManifestResourceException> recurso <xref:System.Resources.MissingSatelliteAssemblyException> para uma cultura padrão (recuo), uma ou exceção será lançada.
   - Se o arquivo de recurso for encontrado, mas o `null`recurso solicitado não estiver presente, a solicitação retorna .

---
title: Algoritmo de carregamento de assembly satélite-.NET Core
description: Descrição dos detalhes do algoritmo de carregamento do assembly satélite no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bfdc1d8179d46a13b3d137a87397fa3e573da33c
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70234605"
---
# <a name="satellite-assembly-loading-algorithm"></a>Algoritmo de carregamento de assembly satélite

Os assemblies satélite são usados para armazenar recursos localizados personalizados para linguagem e cultura.

Os assemblies satélite usam um algoritmo de carregamento diferente dos assemblies gerenciados gerais.

## <a name="when-are-satellite-assemblies-loaded"></a>Quando os assemblies satélite são carregados?

Os assemblies satélite são carregados durante o carregamento de um recurso localizado.

A API básica para carregar recursos localizados é a <xref:System.Resources.ResourceManager?displayProperty=fullName> classe. Por fim <xref:System.Resources.ResourceManager> , a classe chamará o <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> método <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>para cada.

APIs de nível superior podem abstrair a API de nível baixo.

## <a name="algorithm"></a>Algoritmo

O processo de fallback de recurso do .NET CORE envolve as seguintes etapas:

1. Determine a `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instância. Em todos os casos, `active` a instância é o <xref:System.Runtime.Loader.AssemblyLoadContext>assembly em execução.

2. A `active` instância tenta carregar um assembly satélite para a cultura solicitada em ordem de prioridade:
    - Verificando seu cache.
    - Verificando o diretório do assembly atualmente em execução para um subdiretório que corresponda ao solicitado <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (por exemplo `es-MX`).

        > [!NOTE]
        > Este recurso não foi implementado no .NET Core antes de 3,0.
        >
        > [!NOTE]
        > No Linux e no macOS, o subdiretório diferencia maiúsculas de minúsculas e deve ser:
        > - Correspondência de maiúsculas e minúsculas.
        > - Estar em letras minúsculas.

    - Se `active` for a <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instância, executando a lógica de [investigação de assembly (recurso) satélite padrão](default-probing.md#satellite-resource-assembly-probing) .

    - Chamando a <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> função.

    - Gerando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento.

    - Gerando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.

3. Se um assembly satélite for carregado:
   - O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento é gerado.
   - O assembly é pesquisado para o recurso solicitado. Se o tempo de execução localizar o recurso no assembly, ele o usará. Se não encontrar o recurso, ele continua a pesquisa.

    > [!NOTE]
    > Para localizar um recurso dentro do assembly satélite, o tempo de execução procura o arquivo de recurso solicitado pelo <xref:System.Resources.ResourceManager> para o <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> atual. Dentro do arquivo de recurso, ele procura o nome do recurso solicitado. Se nenhum for encontrado, o recurso será tratado como não encontrado.

4. Em seguida, o tempo de execução pesquisa os assemblies de cultura pai por meio de vários níveis potenciais, cada vez que as etapas 2 & 3 são repetidas.

    Cada cultura tem apenas um pai, que é definido pela <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> propriedade.

    A pesquisa de culturas pai é interrompida quando a <xref:System.Globalization.CultureInfo.Parent%2A> propriedade de <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>uma cultura é.

    Para o <xref:System.Globalization.CultureInfo.InvariantCulture>, não retornamos às etapas 2 & 3, mas, em vez disso, continue com a etapa 5.

5. Se o recurso ainda não for encontrado, o recurso para a cultura padrão (fallback) será usado.

   Normalmente, os recursos para a cultura padrão são incluídos no assembly do aplicativo principal. No entanto, você <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pode especificar <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> para a propriedade. Esse valor indica que o local de fallback final para recursos é um assembly satélite em vez do assembly principal.

    > [!NOTE]
    > A cultura padrão é o fallback final. Portanto, é recomendável que você sempre inclua um conjunto completo de recursos no arquivo de recurso padrão. Isso ajuda a evitar que exceções sejam lançadas. Tendo um conjunto completo, você fornece um fallback para todos os recursos e garante que pelo menos um recurso esteja sempre presente para o usuário, mesmo que ele não seja culturalmente específico.

6. Disso
   - Se o tempo de execução não encontrar um arquivo de recurso para uma cultura padrão (fallback <xref:System.Resources.MissingManifestResourceException> ) <xref:System.Resources.MissingSatelliteAssemblyException> , uma exceção ou será lançada.
   - Se o arquivo de recurso for encontrado, mas o recurso solicitado não estiver presente, `null`a solicitação retornará.

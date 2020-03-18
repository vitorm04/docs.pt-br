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
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="d6e51-103">Algoritmo de carregamento de montagem por satélite</span><span class="sxs-lookup"><span data-stu-id="d6e51-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="d6e51-104">Os conjuntos de satélites são usados para armazenar recursos localizados personalizados para linguagem e cultura.</span><span class="sxs-lookup"><span data-stu-id="d6e51-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="d6e51-105">Os conjuntos de satélites usam um algoritmo de carregamento diferente dos conjuntos gerais gerenciados.</span><span class="sxs-lookup"><span data-stu-id="d6e51-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="d6e51-106">Quando os conjuntos de satélites são carregados?</span><span class="sxs-lookup"><span data-stu-id="d6e51-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="d6e51-107">Os conjuntos de satélites são carregados ao carregar um recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="d6e51-108">A API básica para carregar <xref:System.Resources.ResourceManager?displayProperty=fullName> recursos localizados é a classe.</span><span class="sxs-lookup"><span data-stu-id="d6e51-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="d6e51-109">Em última <xref:System.Resources.ResourceManager> análise, <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> a classe <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>chamará o método para cada um .</span><span class="sxs-lookup"><span data-stu-id="d6e51-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d6e51-110">As APIs de nível superior podem abstrair a API de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="d6e51-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="d6e51-111">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="d6e51-111">Algorithm</span></span>

<span data-ttu-id="d6e51-112">O processo de fallback de recurso do .NET CORE envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="d6e51-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="d6e51-113">Determine `active` <xref:System.Runtime.Loader.AssemblyLoadContext> a instância.</span><span class="sxs-lookup"><span data-stu-id="d6e51-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="d6e51-114">Em todos os `active` casos, a instância <xref:System.Runtime.Loader.AssemblyLoadContext>é a da assembléia executora.</span><span class="sxs-lookup"><span data-stu-id="d6e51-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="d6e51-115">A `active` instância tenta carregar uma montagem via satélite para a cultura solicitada em ordem prioritária por:</span><span class="sxs-lookup"><span data-stu-id="d6e51-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="d6e51-116">Verificando seu cache.</span><span class="sxs-lookup"><span data-stu-id="d6e51-116">Checking its cache.</span></span>
    - <span data-ttu-id="d6e51-117">Verificando o diretório da montagem em execução atual para um <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> subdiretório `es-MX`que corresponda ao solicitado (por exemplo ).</span><span class="sxs-lookup"><span data-stu-id="d6e51-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="d6e51-118">Esse recurso não foi implementado no .NET Core antes do 3.0.</span><span class="sxs-lookup"><span data-stu-id="d6e51-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="d6e51-119">No Linux e macOS, o subdiretório é sensível a maiúsculas e minúsculas e deve:</span><span class="sxs-lookup"><span data-stu-id="d6e51-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="d6e51-120">Exatamente caso compatível.</span><span class="sxs-lookup"><span data-stu-id="d6e51-120">Exactly match case.</span></span>
        > - <span data-ttu-id="d6e51-121">Seja em minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d6e51-121">Be in lower case.</span></span>

    - <span data-ttu-id="d6e51-122">Se `active` for <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> a instância, executando a lógica de sondagem padrão de [montagem de satélite (recurso).](default-probing.md#satellite-resource-assembly-probing)</span><span class="sxs-lookup"><span data-stu-id="d6e51-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="d6e51-123">Chamando <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> a função.</span><span class="sxs-lookup"><span data-stu-id="d6e51-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="d6e51-124">Levantando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="d6e51-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="d6e51-125">Levantando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="d6e51-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="d6e51-126">Se um conjunto de satélite estiver carregado:</span><span class="sxs-lookup"><span data-stu-id="d6e51-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="d6e51-127">O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento foi levantado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="d6e51-128">A assembléia é procurada pelo recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="d6e51-129">Se o tempo de execução encontrar o recurso na montagem, ele o usará.</span><span class="sxs-lookup"><span data-stu-id="d6e51-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="d6e51-130">Se não encontrar o recurso, ele continua a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d6e51-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d6e51-131">Para localizar um recurso dentro do assembly satélite, o runtime procura o arquivo de recurso solicitado pelo <xref:System.Resources.ResourceManager> para o <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> atual.</span><span class="sxs-lookup"><span data-stu-id="d6e51-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d6e51-132">Dentro do arquivo de recursos, ele procura o nome do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="d6e51-133">Se nenhum for encontrado, o recurso será tratado como não encontrado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="d6e51-134">O tempo de execução a seguir pesquisa os conjuntos de cultura dos pais através de muitos níveis potenciais, cada vez repetindo as etapas 2 & 3.</span><span class="sxs-lookup"><span data-stu-id="d6e51-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="d6e51-135">Cada cultura tem apenas um pai, <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> que é definido pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="d6e51-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="d6e51-136">A busca por culturas parentais <xref:System.Globalization.CultureInfo.Parent%2A> pára <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>quando a propriedade de uma cultura é .</span><span class="sxs-lookup"><span data-stu-id="d6e51-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="d6e51-137">Para <xref:System.Globalization.CultureInfo.InvariantCulture>o , não voltamos aos passos 2 & 3, mas sim continuar com o passo 5.</span><span class="sxs-lookup"><span data-stu-id="d6e51-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="d6e51-138">Se o recurso ainda não for encontrado, o recurso para a cultura padrão (recuo) será usado.</span><span class="sxs-lookup"><span data-stu-id="d6e51-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="d6e51-139">Normalmente, os recursos para a cultura padrão são incluídos no assembly do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="d6e51-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="d6e51-140">No entanto, <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> você <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> pode especificar para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d6e51-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d6e51-141">Este valor indica que o local final de recuo para os recursos é uma montagem de satélite em vez da montagem principal.</span><span class="sxs-lookup"><span data-stu-id="d6e51-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d6e51-142">A cultura padrão é o retrocesso final.</span><span class="sxs-lookup"><span data-stu-id="d6e51-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="d6e51-143">Portanto, recomendamos que você sempre inclua um conjunto exaustivo de recursos no arquivo de recursos padrão.</span><span class="sxs-lookup"><span data-stu-id="d6e51-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="d6e51-144">Isso ajuda a evitar que exceções sejam lançadas.</span><span class="sxs-lookup"><span data-stu-id="d6e51-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="d6e51-145">Ao ter um conjunto exaustivo, você fornece um recuo para todos os recursos e garante que pelo menos um recurso esteja sempre presente para o usuário, mesmo que não seja culturalmente específico.</span><span class="sxs-lookup"><span data-stu-id="d6e51-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="d6e51-146">Enfim,</span><span class="sxs-lookup"><span data-stu-id="d6e51-146">Finally,</span></span>
   - <span data-ttu-id="d6e51-147">Se o tempo de execução não encontrar um arquivo de <xref:System.Resources.MissingManifestResourceException> recurso <xref:System.Resources.MissingSatelliteAssemblyException> para uma cultura padrão (recuo), uma ou exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="d6e51-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="d6e51-148">Se o arquivo de recurso for encontrado, mas o `null`recurso solicitado não estiver presente, a solicitação retorna .</span><span class="sxs-lookup"><span data-stu-id="d6e51-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>

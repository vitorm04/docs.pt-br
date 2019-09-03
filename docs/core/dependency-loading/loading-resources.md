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
# <a name="satellite-assembly-loading-algorithm"></a><span data-ttu-id="120ef-103">Algoritmo de carregamento de assembly satélite</span><span class="sxs-lookup"><span data-stu-id="120ef-103">Satellite assembly loading algorithm</span></span>

<span data-ttu-id="120ef-104">Os assemblies satélite são usados para armazenar recursos localizados personalizados para linguagem e cultura.</span><span class="sxs-lookup"><span data-stu-id="120ef-104">Satellite assemblies are used to store localized resources customized for language and culture.</span></span>

<span data-ttu-id="120ef-105">Os assemblies satélite usam um algoritmo de carregamento diferente dos assemblies gerenciados gerais.</span><span class="sxs-lookup"><span data-stu-id="120ef-105">Satellite assemblies use a different loading algorithm than general managed assemblies.</span></span>

## <a name="when-are-satellite-assemblies-loaded"></a><span data-ttu-id="120ef-106">Quando os assemblies satélite são carregados?</span><span class="sxs-lookup"><span data-stu-id="120ef-106">When are satellite assemblies loaded?</span></span>

<span data-ttu-id="120ef-107">Os assemblies satélite são carregados durante o carregamento de um recurso localizado.</span><span class="sxs-lookup"><span data-stu-id="120ef-107">Satellite assemblies are loaded when loading a localized resource.</span></span>

<span data-ttu-id="120ef-108">A API básica para carregar recursos localizados é a <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.</span><span class="sxs-lookup"><span data-stu-id="120ef-108">The basic API to load localized resources is the <xref:System.Resources.ResourceManager?displayProperty=fullName> class.</span></span> <span data-ttu-id="120ef-109">Por fim <xref:System.Resources.ResourceManager> , a classe chamará o <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> método <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>para cada.</span><span class="sxs-lookup"><span data-stu-id="120ef-109">Ultimately the <xref:System.Resources.ResourceManager> class will call the <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A> method for each <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="120ef-110">APIs de nível superior podem abstrair a API de nível baixo.</span><span class="sxs-lookup"><span data-stu-id="120ef-110">Higher-level APIs may abstract the low-level API.</span></span>

## <a name="algorithm"></a><span data-ttu-id="120ef-111">Algoritmo</span><span class="sxs-lookup"><span data-stu-id="120ef-111">Algorithm</span></span>

<span data-ttu-id="120ef-112">O processo de fallback de recurso do .NET CORE envolve as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="120ef-112">The .NET Core resource fallback process involves the following steps:</span></span>

1. <span data-ttu-id="120ef-113">Determine a `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instância.</span><span class="sxs-lookup"><span data-stu-id="120ef-113">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext> instance.</span></span> <span data-ttu-id="120ef-114">Em todos os casos, `active` a instância é o <xref:System.Runtime.Loader.AssemblyLoadContext>assembly em execução.</span><span class="sxs-lookup"><span data-stu-id="120ef-114">In all cases, the `active` instance is the executing assembly's <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span>

2. <span data-ttu-id="120ef-115">A `active` instância tenta carregar um assembly satélite para a cultura solicitada em ordem de prioridade:</span><span class="sxs-lookup"><span data-stu-id="120ef-115">The `active` instance attempts to load a satellite assembly for the requested culture in priority order by:</span></span>
    - <span data-ttu-id="120ef-116">Verificando seu cache.</span><span class="sxs-lookup"><span data-stu-id="120ef-116">Checking its cache.</span></span>
    - <span data-ttu-id="120ef-117">Verificando o diretório do assembly atualmente em execução para um subdiretório que corresponda ao solicitado <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (por exemplo `es-MX`).</span><span class="sxs-lookup"><span data-stu-id="120ef-117">Checking the directory of the currently executing assembly for a subdirectory that matches the requested <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> (for example `es-MX`).</span></span>

        > [!NOTE]
        > <span data-ttu-id="120ef-118">Este recurso não foi implementado no .NET Core antes de 3,0.</span><span class="sxs-lookup"><span data-stu-id="120ef-118">This feature was not implemented in .NET Core before 3.0.</span></span>
        >
        > [!NOTE]
        > <span data-ttu-id="120ef-119">No Linux e no macOS, o subdiretório diferencia maiúsculas de minúsculas e deve ser:</span><span class="sxs-lookup"><span data-stu-id="120ef-119">On Linux and macOS, the subdirectory is case-sensitive and must either:</span></span>
        > - <span data-ttu-id="120ef-120">Correspondência de maiúsculas e minúsculas.</span><span class="sxs-lookup"><span data-stu-id="120ef-120">Exactly match case.</span></span>
        > - <span data-ttu-id="120ef-121">Estar em letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="120ef-121">Be in lower case.</span></span>

    - <span data-ttu-id="120ef-122">Se `active` for a <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instância, executando a lógica de [investigação de assembly (recurso) satélite padrão](default-probing.md#satellite-resource-assembly-probing) .</span><span class="sxs-lookup"><span data-stu-id="120ef-122">If `active` is the <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instance, by running the [default satellite (resource) assembly probing](default-probing.md#satellite-resource-assembly-probing) logic.</span></span>

    - <span data-ttu-id="120ef-123">Chamando a <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> função.</span><span class="sxs-lookup"><span data-stu-id="120ef-123">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> function.</span></span>

    - <span data-ttu-id="120ef-124">Gerando <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="120ef-124">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event.</span></span>

    - <span data-ttu-id="120ef-125">Gerando <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="120ef-125">Raising the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

3. <span data-ttu-id="120ef-126">Se um assembly satélite for carregado:</span><span class="sxs-lookup"><span data-stu-id="120ef-126">If a satellite assembly is loaded:</span></span>
   - <span data-ttu-id="120ef-127">O <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="120ef-127">The <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
   - <span data-ttu-id="120ef-128">O assembly é pesquisado para o recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="120ef-128">The assembly is searched it for the requested resource.</span></span> <span data-ttu-id="120ef-129">Se o tempo de execução localizar o recurso no assembly, ele o usará.</span><span class="sxs-lookup"><span data-stu-id="120ef-129">If the runtime finds the resource in the assembly, it uses it.</span></span> <span data-ttu-id="120ef-130">Se não encontrar o recurso, ele continua a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="120ef-130">If it doesn't find the resource, it continues the search.</span></span>

    > [!NOTE]
    > <span data-ttu-id="120ef-131">Para localizar um recurso dentro do assembly satélite, o tempo de execução procura o arquivo de recurso solicitado pelo <xref:System.Resources.ResourceManager> para o <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> atual.</span><span class="sxs-lookup"><span data-stu-id="120ef-131">To find a resource within the satellite assembly, the runtime searches for the resource file requested by the <xref:System.Resources.ResourceManager> for the current <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>.</span></span> <span data-ttu-id="120ef-132">Dentro do arquivo de recurso, ele procura o nome do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="120ef-132">Within the resource file, it searches for the requested resource name.</span></span> <span data-ttu-id="120ef-133">Se nenhum for encontrado, o recurso será tratado como não encontrado.</span><span class="sxs-lookup"><span data-stu-id="120ef-133">If either is not found, the resource is treated as not found.</span></span>

4. <span data-ttu-id="120ef-134">Em seguida, o tempo de execução pesquisa os assemblies de cultura pai por meio de vários níveis potenciais, cada vez que as etapas 2 & 3 são repetidas.</span><span class="sxs-lookup"><span data-stu-id="120ef-134">The runtime next searches the parent culture assemblies through many potential levels, each time repeating steps 2 & 3.</span></span>

    <span data-ttu-id="120ef-135">Cada cultura tem apenas um pai, que é definido pela <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="120ef-135">Each culture has only one parent, which is defined by the <xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="120ef-136">A pesquisa de culturas pai é interrompida quando a <xref:System.Globalization.CultureInfo.Parent%2A> propriedade de <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>uma cultura é.</span><span class="sxs-lookup"><span data-stu-id="120ef-136">The search for parent cultures stops when a culture's <xref:System.Globalization.CultureInfo.Parent%2A> property is <xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType>.</span></span>

    <span data-ttu-id="120ef-137">Para o <xref:System.Globalization.CultureInfo.InvariantCulture>, não retornamos às etapas 2 & 3, mas, em vez disso, continue com a etapa 5.</span><span class="sxs-lookup"><span data-stu-id="120ef-137">For the <xref:System.Globalization.CultureInfo.InvariantCulture>, we don't return to steps 2 & 3, but rather continue with step 5.</span></span>

5. <span data-ttu-id="120ef-138">Se o recurso ainda não for encontrado, o recurso para a cultura padrão (fallback) será usado.</span><span class="sxs-lookup"><span data-stu-id="120ef-138">If the resource is still not found, the resource for the default (fallback) culture is used.</span></span>

   <span data-ttu-id="120ef-139">Normalmente, os recursos para a cultura padrão são incluídos no assembly do aplicativo principal.</span><span class="sxs-lookup"><span data-stu-id="120ef-139">Typically, the resources for the default culture are included in the main application assembly.</span></span> <span data-ttu-id="120ef-140">No entanto, você <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> pode especificar <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="120ef-140">However, you can specify <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> for the <xref:System.Resources.NeutralResourcesLanguageAttribute.Location?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="120ef-141">Esse valor indica que o local de fallback final para recursos é um assembly satélite em vez do assembly principal.</span><span class="sxs-lookup"><span data-stu-id="120ef-141">This value indicates that the ultimate fallback location for resources is a satellite assembly rather than the main assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="120ef-142">A cultura padrão é o fallback final.</span><span class="sxs-lookup"><span data-stu-id="120ef-142">The default culture is the ultimate fallback.</span></span> <span data-ttu-id="120ef-143">Portanto, é recomendável que você sempre inclua um conjunto completo de recursos no arquivo de recurso padrão.</span><span class="sxs-lookup"><span data-stu-id="120ef-143">Therefore, we recommend that you always include an exhaustive set of resources in the default resource file.</span></span> <span data-ttu-id="120ef-144">Isso ajuda a evitar que exceções sejam lançadas.</span><span class="sxs-lookup"><span data-stu-id="120ef-144">This helps prevent exceptions from being thrown.</span></span> <span data-ttu-id="120ef-145">Tendo um conjunto completo, você fornece um fallback para todos os recursos e garante que pelo menos um recurso esteja sempre presente para o usuário, mesmo que ele não seja culturalmente específico.</span><span class="sxs-lookup"><span data-stu-id="120ef-145">By having an exhaustive set, you provide a fallback for all resources and ensure that at least one resource is always present for the user, even if it is not culturally specific.</span></span>

6. <span data-ttu-id="120ef-146">Disso</span><span class="sxs-lookup"><span data-stu-id="120ef-146">Finally,</span></span>
   - <span data-ttu-id="120ef-147">Se o tempo de execução não encontrar um arquivo de recurso para uma cultura padrão (fallback <xref:System.Resources.MissingManifestResourceException> ) <xref:System.Resources.MissingSatelliteAssemblyException> , uma exceção ou será lançada.</span><span class="sxs-lookup"><span data-stu-id="120ef-147">If the runtime doesn't find a resource file for a default (fallback) culture, a <xref:System.Resources.MissingManifestResourceException> or <xref:System.Resources.MissingSatelliteAssemblyException> exception is thrown.</span></span>
   - <span data-ttu-id="120ef-148">Se o arquivo de recurso for encontrado, mas o recurso solicitado não estiver presente, `null`a solicitação retornará.</span><span class="sxs-lookup"><span data-stu-id="120ef-148">If the resource file is found but the requested resource isn't present, the request returns `null`.</span></span>

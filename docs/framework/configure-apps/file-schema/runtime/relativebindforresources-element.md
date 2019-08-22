---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 859e8a12421ea92aa48c54317e052683eb8e83f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663491"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="53f27-102">\<Elemento de > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="53f27-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="53f27-103">Otimiza o teste para assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="53f27-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="53f27-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="53f27-104">\<configuration> Element</span></span>  
<span data-ttu-id="53f27-105">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="53f27-105">\<runtime> Element</span></span>  
<span data-ttu-id="53f27-106">\<Elemento de > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="53f27-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f27-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53f27-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53f27-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="53f27-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53f27-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="53f27-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53f27-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="53f27-110">Attributes</span></span>  
  
|<span data-ttu-id="53f27-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="53f27-111">Attribute</span></span>|<span data-ttu-id="53f27-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="53f27-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="53f27-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="53f27-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="53f27-114">Especifica se o Common Language Runtime otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="53f27-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="53f27-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="53f27-116">Valor</span><span class="sxs-lookup"><span data-stu-id="53f27-116">Value</span></span>|<span data-ttu-id="53f27-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="53f27-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="53f27-118">O tempo de execução não otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="53f27-119">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="53f27-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="53f27-120">O tempo de execução otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53f27-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="53f27-121">Child Elements</span></span>  
 <span data-ttu-id="53f27-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="53f27-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53f27-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="53f27-123">Parent Elements</span></span>  
  
|<span data-ttu-id="53f27-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="53f27-124">Element</span></span>|<span data-ttu-id="53f27-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="53f27-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="53f27-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53f27-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="53f27-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="53f27-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53f27-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="53f27-128">Remarks</span></span>  
 <span data-ttu-id="53f27-129">Em geral, as investigações do Resource Manager para recursos, conforme documentado no tópico [empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="53f27-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="53f27-130">Isso significa que quando o Gerenciador de recursos investiga uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, examinar uma pasta específica de cultura na base de código do aplicativo, consultar Windows Installer para assemblies satélites e gerar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="53f27-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="53f27-131">O `<relativeBindForResources>` elemento otimiza a maneira como as investigações do Gerenciador de recursos para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="53f27-132">Ele pode melhorar o desempenho ao investigar os recursos sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="53f27-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="53f27-133">Quando o assembly satélite é implantado no mesmo local que o assembly de código.</span><span class="sxs-lookup"><span data-stu-id="53f27-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="53f27-134">Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélite também deverão ser instalados lá.</span><span class="sxs-lookup"><span data-stu-id="53f27-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="53f27-135">Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélite também deverão ser instalados em uma pasta específica de cultura na base de código.</span><span class="sxs-lookup"><span data-stu-id="53f27-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="53f27-136">Quando Windows Installer não é usado ou é usado apenas raramente para a instalação sob demanda de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="53f27-137">Quando o código do aplicativo não manipula <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="53f27-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="53f27-138">Definir o `enabled` atributo `<relativeBindForResources>` do elemento para `true` otimizar a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="53f27-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="53f27-139">Ele usa o local do assembly de código pai para investigar o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="53f27-140">Ele não consulta Windows Installer para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="53f27-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="53f27-141">Ele não gera o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="53f27-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f27-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53f27-142">See also</span></span>

- [<span data-ttu-id="53f27-143">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="53f27-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="53f27-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="53f27-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53f27-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="53f27-145">Configuration File Schema</span></span>](../index.md)

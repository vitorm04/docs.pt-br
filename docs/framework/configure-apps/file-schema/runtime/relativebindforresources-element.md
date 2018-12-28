---
title: '&lt;relativeBindForResources&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1933fad8ea87351a56fcc7dd4a4fd67e890b58f5
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613889"
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="6fa23-102">&lt;relativeBindForResources&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="6fa23-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="6fa23-103">Otimiza o teste para assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="6fa23-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="6fa23-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="6fa23-104">\<configuration> Element</span></span>  
<span data-ttu-id="6fa23-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="6fa23-105">\<runtime> Element</span></span>  
<span data-ttu-id="6fa23-106">\<relativeBindForResources > elemento</span><span class="sxs-lookup"><span data-stu-id="6fa23-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa23-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fa23-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fa23-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6fa23-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6fa23-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6fa23-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fa23-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6fa23-110">Attributes</span></span>  
  
|<span data-ttu-id="6fa23-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="6fa23-111">Attribute</span></span>|<span data-ttu-id="6fa23-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa23-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6fa23-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6fa23-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6fa23-114">Especifica se o common language runtime otimiza a investigação de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6fa23-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="6fa23-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6fa23-116">Valor</span><span class="sxs-lookup"><span data-stu-id="6fa23-116">Value</span></span>|<span data-ttu-id="6fa23-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa23-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6fa23-118">O tempo de execução não otimiza a investigação de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="6fa23-119">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="6fa23-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="6fa23-120">O tempo de execução otimiza a investigação de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fa23-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6fa23-121">Child Elements</span></span>  
 <span data-ttu-id="6fa23-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6fa23-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fa23-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6fa23-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6fa23-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fa23-124">Element</span></span>|<span data-ttu-id="6fa23-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fa23-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6fa23-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6fa23-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6fa23-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6fa23-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa23-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fa23-128">Remarks</span></span>  
 <span data-ttu-id="6fa23-129">Em geral, o Gerenciador de recursos de investigações para recursos, conforme documentado na [Empacotando e implantando recursos](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="6fa23-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="6fa23-130">Isso significa que quando investigações do Gerenciador de recursos para uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, procurar em uma pasta específicas da cultura na consulta do aplicativo de base, de código do Windows Installer para assemblies satélite e acionar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="6fa23-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="6fa23-131">O `<relativeBindForResources>` elemento otimiza a maneira na qual o Gerenciador de recursos investigações para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="6fa23-132">Ele pode melhorar o desempenho quando a investigação para recursos nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="6fa23-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="6fa23-133">Quando o assembly satélite é implantado no mesmo local que o assembly de código.</span><span class="sxs-lookup"><span data-stu-id="6fa23-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="6fa23-134">Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélites também devem ser instalados lá.</span><span class="sxs-lookup"><span data-stu-id="6fa23-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="6fa23-135">Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélites também devem ser instalados em uma pasta específica de cultura na base de código.</span><span class="sxs-lookup"><span data-stu-id="6fa23-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="6fa23-136">Quando o Windows Installer não é usado ou apenas raramente é usado para instalação sob demanda dos assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="6fa23-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="6fa23-137">Quando o código do aplicativo não processa o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="6fa23-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="6fa23-138">Definindo o `enabled` atributo o `<relativeBindForResources>` elemento a ser `true` otimiza a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6fa23-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="6fa23-139">Ele usa o local do assembly de código pai para investigar o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="6fa23-140">Ele não consulta do Windows Installer para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="6fa23-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="6fa23-141">Ele não gere a <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> eventos.</span><span class="sxs-lookup"><span data-stu-id="6fa23-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa23-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fa23-142">See Also</span></span>  
- [<span data-ttu-id="6fa23-143">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="6fa23-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
- [<span data-ttu-id="6fa23-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6fa23-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="6fa23-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6fa23-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

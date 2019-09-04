---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1ac2900707ddb39c62b34b0ebfbc4547cdd2653
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252355"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="2982a-102">\<Elemento de > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="2982a-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="2982a-103">Otimiza o teste para assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="2982a-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="2982a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2982a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2982a-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2982a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2982a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources>**</span><span class="sxs-lookup"><span data-stu-id="2982a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2982a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2982a-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2982a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2982a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2982a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2982a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2982a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2982a-110">Attributes</span></span>  
  
|<span data-ttu-id="2982a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="2982a-111">Attribute</span></span>|<span data-ttu-id="2982a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="2982a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2982a-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2982a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2982a-114">Especifica se o Common Language Runtime otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2982a-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="2982a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2982a-116">Valor</span><span class="sxs-lookup"><span data-stu-id="2982a-116">Value</span></span>|<span data-ttu-id="2982a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2982a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2982a-118">O tempo de execução não otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="2982a-119">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="2982a-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="2982a-120">O tempo de execução otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2982a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2982a-121">Child Elements</span></span>  
 <span data-ttu-id="2982a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2982a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2982a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2982a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2982a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="2982a-124">Element</span></span>|<span data-ttu-id="2982a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="2982a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2982a-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2982a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2982a-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2982a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2982a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="2982a-128">Remarks</span></span>  
 <span data-ttu-id="2982a-129">Em geral, as investigações do Resource Manager para recursos, conforme documentado no tópico [empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="2982a-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="2982a-130">Isso significa que quando o Gerenciador de recursos investiga uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, examinar uma pasta específica de cultura na base de código do aplicativo, consultar Windows Installer para assemblies satélites e gerar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="2982a-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="2982a-131">O `<relativeBindForResources>` elemento otimiza a maneira como as investigações do Gerenciador de recursos para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="2982a-132">Ele pode melhorar o desempenho ao investigar os recursos sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="2982a-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="2982a-133">Quando o assembly satélite é implantado no mesmo local que o assembly de código.</span><span class="sxs-lookup"><span data-stu-id="2982a-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="2982a-134">Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélite também deverão ser instalados lá.</span><span class="sxs-lookup"><span data-stu-id="2982a-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="2982a-135">Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélite também deverão ser instalados em uma pasta específica de cultura na base de código.</span><span class="sxs-lookup"><span data-stu-id="2982a-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="2982a-136">Quando Windows Installer não é usado ou é usado apenas raramente para a instalação sob demanda de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="2982a-137">Quando o código do aplicativo não manipula <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="2982a-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="2982a-138">Definir o `enabled` atributo `<relativeBindForResources>` do elemento para `true` otimizar a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2982a-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="2982a-139">Ele usa o local do assembly de código pai para investigar o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="2982a-140">Ele não consulta Windows Installer para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="2982a-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="2982a-141">Ele não gera o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="2982a-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2982a-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2982a-142">See also</span></span>

- [<span data-ttu-id="2982a-143">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="2982a-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="2982a-144">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2982a-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2982a-145">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="2982a-145">Configuration File Schema</span></span>](../index.md)

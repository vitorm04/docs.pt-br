---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153900"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="ac795-102">Elemento \<relativeBindForResources></span><span class="sxs-lookup"><span data-stu-id="ac795-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="ac795-103">Otimiza o teste para assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="ac795-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="ac795-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac795-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac795-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac795-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ac795-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac795-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac795-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac795-107">Attributes</span></span>  
  
|<span data-ttu-id="ac795-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac795-108">Attribute</span></span>|<span data-ttu-id="ac795-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac795-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ac795-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ac795-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac795-111">Especifica se o Common Language Runtime otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ac795-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ac795-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="ac795-113">Valor</span><span class="sxs-lookup"><span data-stu-id="ac795-113">Value</span></span>|<span data-ttu-id="ac795-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac795-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ac795-115">O tempo de execução não otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="ac795-116">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ac795-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="ac795-117">O tempo de execução otimiza a investigação para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac795-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac795-118">Child Elements</span></span>  
 <span data-ttu-id="ac795-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="ac795-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac795-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac795-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ac795-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac795-121">Element</span></span>|<span data-ttu-id="ac795-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac795-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac795-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac795-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ac795-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="ac795-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac795-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac795-125">Remarks</span></span>  
 <span data-ttu-id="ac795-126">Em geral, as investigações do Resource Manager para recursos, conforme documentado no tópico [empacotando e implantando recursos](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="ac795-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="ac795-127">Isso significa que quando o Gerenciador de recursos investiga uma versão localizada específica de um recurso, ele pode procurar no cache de assembly global, examinar uma pasta específica de cultura na base de código do aplicativo, consultar Windows Installer para assemblies satélites e gerar o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="ac795-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="ac795-128">O `<relativeBindForResources>` elemento otimiza a maneira como as investigações do Gerenciador de recursos para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="ac795-129">Ele pode melhorar o desempenho ao investigar os recursos sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="ac795-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="ac795-130">Quando o assembly satélite é implantado no mesmo local que o assembly de código.</span><span class="sxs-lookup"><span data-stu-id="ac795-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="ac795-131">Em outras palavras, se o assembly de código estiver instalado no cache de assembly global, os assemblies satélite também deverão ser instalados lá.</span><span class="sxs-lookup"><span data-stu-id="ac795-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="ac795-132">Se o assembly de código estiver instalado na base de código do aplicativo, os assemblies satélite também deverão ser instalados em uma pasta específica de cultura na base de código.</span><span class="sxs-lookup"><span data-stu-id="ac795-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="ac795-133">Quando Windows Installer não é usado ou é usado apenas raramente para a instalação sob demanda de assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="ac795-134">Quando o código do aplicativo não manipula o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="ac795-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="ac795-135">Definir o `enabled` atributo do `<relativeBindForResources>` elemento para `true` otimizar a investigação do Gerenciador de recursos para assemblies satélite da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ac795-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="ac795-136">Ele usa o local do assembly de código pai para investigar o assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="ac795-137">Ele não consulta Windows Installer para assemblies satélite.</span><span class="sxs-lookup"><span data-stu-id="ac795-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="ac795-138">Ele não gera o <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> evento.</span><span class="sxs-lookup"><span data-stu-id="ac795-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac795-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="ac795-139">See also</span></span>

- [<span data-ttu-id="ac795-140">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="ac795-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="ac795-141">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="ac795-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac795-142">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="ac795-142">Configuration File Schema</span></span>](../index.md)

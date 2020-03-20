---
title: Elemento <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153900"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="a098e-102">\<elemento> relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="a098e-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="a098e-103">Otimiza o teste para assemblies satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="a098e-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a098e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a098e-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a098e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a098e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bindForResources>**</span><span class="sxs-lookup"><span data-stu-id="a098e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a098e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a098e-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a098e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a098e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a098e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a098e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a098e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a098e-110">Attributes</span></span>  
  
|<span data-ttu-id="a098e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="a098e-111">Attribute</span></span>|<span data-ttu-id="a098e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a098e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a098e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a098e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a098e-114">Especifica se o tempo de execução do idioma comum otimiza a sonda para conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a098e-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="a098e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a098e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="a098e-116">Value</span></span>|<span data-ttu-id="a098e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a098e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a098e-118">O tempo de execução não otimiza a sonda para conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="a098e-119">Esse é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="a098e-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="a098e-120">O tempo de execução otimiza a sonda para conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a098e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a098e-121">Child Elements</span></span>  
 <span data-ttu-id="a098e-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a098e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a098e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a098e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a098e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="a098e-124">Element</span></span>|<span data-ttu-id="a098e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="a098e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a098e-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a098e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a098e-127">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="a098e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a098e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a098e-128">Remarks</span></span>  
 <span data-ttu-id="a098e-129">Em geral, o Gerenciador de Recursos testa recursos, conforme documentado no tópico [Embalagem e Distribuição de Recursos.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a098e-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="a098e-130">Isso significa que, quando o Resource Manager testa uma versão localizada específica de um recurso, ele pode olhar no cache de montagem global, procurar uma pasta <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> específica de cultura na base de código do aplicativo, consultar o Windows Installer para conjuntos de satélites e aumentar o evento.</span><span class="sxs-lookup"><span data-stu-id="a098e-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="a098e-131">O `<relativeBindForResources>` elemento otimiza a forma como o Resource Manager sonda para conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="a098e-132">Pode melhorar o desempenho ao sondar recursos nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="a098e-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="a098e-133">Quando o conjunto de satélites é implantado no mesmo local que o conjunto de códigos.</span><span class="sxs-lookup"><span data-stu-id="a098e-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="a098e-134">Em outras palavras, se o conjunto de códigos for instalado no cache de montagem global, os conjuntos de satélites também devem ser instalados lá.</span><span class="sxs-lookup"><span data-stu-id="a098e-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="a098e-135">Se o conjunto de códigos estiver instalado na base de código do aplicativo, os conjuntos de satélites também devem ser instalados em uma pasta específica de cultura na base de código.</span><span class="sxs-lookup"><span data-stu-id="a098e-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="a098e-136">Quando o Windows Installer não é usado ou é usado apenas raramente para instalação demanda de conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="a098e-137">Quando o código do <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> aplicativo não lida com o evento.</span><span class="sxs-lookup"><span data-stu-id="a098e-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="a098e-138">Definir `enabled` o atributo `true` do elemento para otimizar a `<relativeBindForResources>` sonda do Resource Manager para conjuntos de satélites da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a098e-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="a098e-139">Ele usa a localização do conjunto de código sondar para a montagem do satélite.</span><span class="sxs-lookup"><span data-stu-id="a098e-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="a098e-140">Ele não consulta o Windows Installer para conjuntos de satélites.</span><span class="sxs-lookup"><span data-stu-id="a098e-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="a098e-141">Isso não levanta <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> o evento.</span><span class="sxs-lookup"><span data-stu-id="a098e-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a098e-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="a098e-142">See also</span></span>

- [<span data-ttu-id="a098e-143">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="a098e-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="a098e-144">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="a098e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a098e-145">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a098e-145">Configuration File Schema</span></span>](../index.md)

---
title: '&lt;adicionar&gt; &lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 8b7a4730af6690616058a91cf23bb39734d81abc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541710"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="27fa4-102">&lt;adicionar&gt; &lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="27fa4-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="27fa4-103">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="27fa4-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="27fa4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="27fa4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27fa4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="27fa4-105">\<behaviors></span></span>  
<span data-ttu-id="27fa4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="27fa4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="27fa4-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="27fa4-107">\<behavior></span></span>  
<span data-ttu-id="27fa4-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="27fa4-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="27fa4-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="27fa4-109">\<defaultPorts></span></span>  
<span data-ttu-id="27fa4-110">\<add></span><span class="sxs-lookup"><span data-stu-id="27fa4-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fa4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27fa4-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27fa4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27fa4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="27fa4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27fa4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27fa4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="27fa4-114">Attributes</span></span>  
  
|<span data-ttu-id="27fa4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="27fa4-115">Attribute</span></span>|<span data-ttu-id="27fa4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="27fa4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27fa4-117">porta</span><span class="sxs-lookup"><span data-stu-id="27fa4-117">port</span></span>|<span data-ttu-id="27fa4-118">Um inteiro que especifica o número de porta de comunicação padrão</span><span class="sxs-lookup"><span data-stu-id="27fa4-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="27fa4-119">esquema</span><span class="sxs-lookup"><span data-stu-id="27fa4-119">scheme</span></span>|<span data-ttu-id="27fa4-120">Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.</span><span class="sxs-lookup"><span data-stu-id="27fa4-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27fa4-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27fa4-121">Child Elements</span></span>  
 <span data-ttu-id="27fa4-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="27fa4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27fa4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27fa4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="27fa4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="27fa4-124">Element</span></span>|<span data-ttu-id="27fa4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="27fa4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27fa4-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="27fa4-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="27fa4-127">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="27fa4-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27fa4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27fa4-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>

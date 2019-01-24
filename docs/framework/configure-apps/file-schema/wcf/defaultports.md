---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2c742f98315c0e497ac4117953424bae913cb5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614491"
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="5eda8-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="5eda8-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="5eda8-103">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="5eda8-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="5eda8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5eda8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5eda8-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5eda8-105">\<behaviors></span></span>  
<span data-ttu-id="5eda8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5eda8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5eda8-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5eda8-107">\<behavior></span></span>  
<span data-ttu-id="5eda8-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5eda8-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="5eda8-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5eda8-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eda8-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5eda8-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5eda8-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5eda8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5eda8-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5eda8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5eda8-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="5eda8-113">Attributes</span></span>  
 <span data-ttu-id="5eda8-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5eda8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5eda8-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5eda8-115">Child Elements</span></span>  
  
|<span data-ttu-id="5eda8-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="5eda8-116">Element</span></span>|<span data-ttu-id="5eda8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5eda8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5eda8-118">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="5eda8-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="5eda8-119">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="5eda8-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5eda8-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5eda8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5eda8-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5eda8-121">Element</span></span>|<span data-ttu-id="5eda8-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5eda8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5eda8-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="5eda8-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="5eda8-124">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="5eda8-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eda8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5eda8-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

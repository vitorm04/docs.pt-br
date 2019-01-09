---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 7ddfddaa13778ce98bd93b6d8029438377fc7e94
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145179"
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="80d50-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="80d50-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="80d50-103">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="80d50-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="80d50-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80d50-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80d50-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="80d50-105">\<behaviors></span></span>  
<span data-ttu-id="80d50-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="80d50-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="80d50-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="80d50-107">\<behavior></span></span>  
<span data-ttu-id="80d50-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="80d50-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="80d50-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="80d50-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d50-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80d50-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80d50-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="80d50-111">Attributes and Elements</span></span>  
 <span data-ttu-id="80d50-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="80d50-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80d50-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="80d50-113">Attributes</span></span>  
 <span data-ttu-id="80d50-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="80d50-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80d50-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="80d50-115">Child Elements</span></span>  
  
|<span data-ttu-id="80d50-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="80d50-116">Element</span></span>|<span data-ttu-id="80d50-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="80d50-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80d50-118">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="80d50-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="80d50-119">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="80d50-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80d50-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="80d50-120">Parent Elements</span></span>  
  
|<span data-ttu-id="80d50-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="80d50-121">Element</span></span>|<span data-ttu-id="80d50-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="80d50-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80d50-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="80d50-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="80d50-124">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="80d50-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80d50-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d50-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

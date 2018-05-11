---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2f7de066a1b91e9fa22fbe0213e221c6f4bbe617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="3e60e-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="3e60e-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="3e60e-103">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3e60e-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="3e60e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e60e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e60e-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3e60e-105">\<behaviors></span></span>  
<span data-ttu-id="3e60e-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3e60e-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3e60e-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="3e60e-107">\<behavior></span></span>  
<span data-ttu-id="3e60e-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="3e60e-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="3e60e-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="3e60e-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e60e-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e60e-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e60e-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e60e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3e60e-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e60e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e60e-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e60e-113">Attributes</span></span>  
 <span data-ttu-id="3e60e-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3e60e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3e60e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e60e-115">Child Elements</span></span>  
  
|<span data-ttu-id="3e60e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e60e-116">Element</span></span>|<span data-ttu-id="3e60e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e60e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e60e-118">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="3e60e-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="3e60e-119">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3e60e-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e60e-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e60e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3e60e-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e60e-121">Element</span></span>|<span data-ttu-id="3e60e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e60e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e60e-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="3e60e-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="3e60e-124">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="3e60e-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e60e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e60e-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 7e661570f8b94b979595a615b3f6819d41ed5e35
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766693"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="7b932-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="7b932-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="7b932-103">Permite a recuperação de informações de endereço de metadados de cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="7b932-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="7b932-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b932-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b932-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7b932-105">\<behaviors></span></span>  
<span data-ttu-id="7b932-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7b932-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b932-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7b932-107">\<behavior></span></span>  
<span data-ttu-id="7b932-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="7b932-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b932-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b932-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b932-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7b932-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b932-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7b932-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b932-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7b932-112">Attributes</span></span>  
 <span data-ttu-id="7b932-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7b932-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b932-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7b932-114">Child Elements</span></span>  
  
|<span data-ttu-id="7b932-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b932-115">Element</span></span>|<span data-ttu-id="7b932-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b932-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b932-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="7b932-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="7b932-118">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="7b932-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b932-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7b932-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b932-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7b932-120">Element</span></span>|<span data-ttu-id="7b932-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b932-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b932-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="7b932-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7b932-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="7b932-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b932-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b932-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

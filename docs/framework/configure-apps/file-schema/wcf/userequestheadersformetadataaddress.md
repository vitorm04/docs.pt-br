---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 6c03057fca23b037702c702b9a574045ebb302b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656616"
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="584ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="584ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="584ce-103">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="584ce-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="584ce-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="584ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="584ce-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="584ce-105">\<behaviors></span></span>  
<span data-ttu-id="584ce-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="584ce-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="584ce-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="584ce-107">\<behavior></span></span>  
<span data-ttu-id="584ce-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="584ce-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="584ce-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="584ce-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="584ce-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="584ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="584ce-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="584ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="584ce-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="584ce-112">Attributes</span></span>  
 <span data-ttu-id="584ce-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="584ce-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="584ce-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="584ce-114">Child Elements</span></span>  
  
|<span data-ttu-id="584ce-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="584ce-115">Element</span></span>|<span data-ttu-id="584ce-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="584ce-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="584ce-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="584ce-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="584ce-118">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="584ce-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="584ce-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="584ce-119">Parent Elements</span></span>  
  
|<span data-ttu-id="584ce-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="584ce-120">Element</span></span>|<span data-ttu-id="584ce-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="584ce-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="584ce-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="584ce-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="584ce-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="584ce-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="584ce-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="584ce-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

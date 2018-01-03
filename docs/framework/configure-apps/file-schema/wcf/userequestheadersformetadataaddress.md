---
title: '&lt;useRequestHeadersForMetadataAddress&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94dafcfa68463a0e82696cf16a96abe45632e72a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="562ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="562ce-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="562ce-103">Permite a recuperação de informações de endereço de metadados de cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="562ce-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="562ce-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="562ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="562ce-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="562ce-105">\<behaviors></span></span>  
<span data-ttu-id="562ce-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="562ce-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="562ce-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="562ce-107">\<behavior></span></span>  
<span data-ttu-id="562ce-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="562ce-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562ce-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="562ce-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="562ce-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="562ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="562ce-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="562ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="562ce-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="562ce-112">Attributes</span></span>  
 <span data-ttu-id="562ce-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="562ce-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="562ce-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="562ce-114">Child Elements</span></span>  
  
|<span data-ttu-id="562ce-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="562ce-115">Element</span></span>|<span data-ttu-id="562ce-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="562ce-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="562ce-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="562ce-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="562ce-118">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="562ce-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="562ce-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="562ce-119">Parent Elements</span></span>  
  
|<span data-ttu-id="562ce-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="562ce-120">Element</span></span>|<span data-ttu-id="562ce-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="562ce-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="562ce-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="562ce-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="562ce-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="562ce-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="562ce-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="562ce-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

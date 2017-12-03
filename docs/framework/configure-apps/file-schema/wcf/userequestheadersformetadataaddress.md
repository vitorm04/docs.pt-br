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
ms.openlocfilehash: 1e7f69da871376f83422fb330f8babd56bb1fdcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="969c0-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="969c0-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="969c0-103">Permite a recuperação de informações de endereço de metadados de cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="969c0-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="969c0-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="969c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="969c0-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="969c0-105">\<behaviors></span></span>  
<span data-ttu-id="969c0-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="969c0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="969c0-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="969c0-107">\<behavior></span></span>  
<span data-ttu-id="969c0-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="969c0-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="969c0-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="969c0-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="969c0-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="969c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="969c0-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="969c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="969c0-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="969c0-112">Attributes</span></span>  
 <span data-ttu-id="969c0-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="969c0-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="969c0-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="969c0-114">Child Elements</span></span>  
  
|<span data-ttu-id="969c0-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="969c0-115">Element</span></span>|<span data-ttu-id="969c0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="969c0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="969c0-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="969c0-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="969c0-118">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="969c0-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="969c0-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="969c0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="969c0-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="969c0-120">Element</span></span>|<span data-ttu-id="969c0-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="969c0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="969c0-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="969c0-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="969c0-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="969c0-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="969c0-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="969c0-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

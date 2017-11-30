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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c538939a97e43239048853b5d6c32251d557d7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltuserequestheadersformetadataaddressgt"></a><span data-ttu-id="b1fc7-102">&lt;useRequestHeadersForMetadataAddress&gt;</span><span class="sxs-lookup"><span data-stu-id="b1fc7-102">&lt;useRequestHeadersForMetadataAddress&gt;</span></span>
<span data-ttu-id="b1fc7-103">Permite a recuperação de informações de endereço de metadados de cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b1fc7-103">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b1fc7-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1fc7-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-105">\<behaviors></span></span>  
<span data-ttu-id="b1fc7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b1fc7-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-107">\<behavior></span></span>  
<span data-ttu-id="b1fc7-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-108">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1fc7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1fc7-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1fc7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1fc7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1fc7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1fc7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1fc7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1fc7-112">Attributes</span></span>  
 <span data-ttu-id="b1fc7-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b1fc7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b1fc7-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1fc7-114">Child Elements</span></span>  
  
|<span data-ttu-id="b1fc7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1fc7-115">Element</span></span>|<span data-ttu-id="b1fc7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1fc7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1fc7-117">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-117">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="b1fc7-118">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="b1fc7-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1fc7-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1fc7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b1fc7-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1fc7-120">Element</span></span>|<span data-ttu-id="b1fc7-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1fc7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1fc7-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="b1fc7-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b1fc7-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b1fc7-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1fc7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1fc7-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

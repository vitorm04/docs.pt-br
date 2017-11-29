---
title: '&lt;defaultPorts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e127935977795181411dfa6b03d8b09fe88e0f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltdefaultportsgt"></a><span data-ttu-id="78f30-102">&lt;defaultPorts&gt;</span><span class="sxs-lookup"><span data-stu-id="78f30-102">&lt;defaultPorts&gt;</span></span>
<span data-ttu-id="78f30-103">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="78f30-103">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="78f30-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="78f30-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="78f30-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="78f30-105">\<behaviors></span></span>  
<span data-ttu-id="78f30-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="78f30-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="78f30-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="78f30-107">\<behavior></span></span>  
<span data-ttu-id="78f30-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="78f30-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="78f30-109">\<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="78f30-109">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f30-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78f30-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78f30-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="78f30-111">Attributes and Elements</span></span>  
 <span data-ttu-id="78f30-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="78f30-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78f30-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="78f30-113">Attributes</span></span>  
 <span data-ttu-id="78f30-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="78f30-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78f30-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="78f30-115">Child Elements</span></span>  
  
|<span data-ttu-id="78f30-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="78f30-116">Element</span></span>|<span data-ttu-id="78f30-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="78f30-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78f30-118">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="78f30-118">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="78f30-119">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="78f30-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78f30-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="78f30-120">Parent Elements</span></span>  
  
|<span data-ttu-id="78f30-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="78f30-121">Element</span></span>|<span data-ttu-id="78f30-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="78f30-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78f30-123">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="78f30-123">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="78f30-124">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="78f30-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78f30-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78f30-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

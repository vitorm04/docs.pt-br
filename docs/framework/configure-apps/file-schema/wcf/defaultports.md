---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130618"
---
# <a name="defaultports"></a><span data-ttu-id="ceea2-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ceea2-101">\<defaultPorts></span></span>
<span data-ttu-id="ceea2-102">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="ceea2-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="ceea2-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ceea2-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ceea2-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ceea2-104">\<behaviors></span></span>  
<span data-ttu-id="ceea2-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ceea2-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ceea2-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ceea2-106">\<behavior></span></span>  
<span data-ttu-id="ceea2-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="ceea2-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="ceea2-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="ceea2-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceea2-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ceea2-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceea2-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ceea2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ceea2-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ceea2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceea2-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ceea2-112">Attributes</span></span>  
 <span data-ttu-id="ceea2-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ceea2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ceea2-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ceea2-114">Child Elements</span></span>  
  
|<span data-ttu-id="ceea2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="ceea2-115">Element</span></span>|<span data-ttu-id="ceea2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ceea2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceea2-117">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="ceea2-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="ceea2-118">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="ceea2-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceea2-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ceea2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ceea2-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ceea2-120">Element</span></span>|<span data-ttu-id="ceea2-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ceea2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceea2-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="ceea2-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="ceea2-123">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="ceea2-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceea2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ceea2-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

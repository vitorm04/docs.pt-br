---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130618"
---
# <a name="defaultports"></a><span data-ttu-id="d87bb-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="d87bb-101">\<defaultPorts></span></span>
<span data-ttu-id="d87bb-102">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="d87bb-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="d87bb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d87bb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d87bb-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d87bb-104">\<behaviors></span></span>  
<span data-ttu-id="d87bb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d87bb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d87bb-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d87bb-106">\<behavior></span></span>  
<span data-ttu-id="d87bb-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="d87bb-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="d87bb-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="d87bb-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87bb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d87bb-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d87bb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d87bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d87bb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d87bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d87bb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d87bb-112">Attributes</span></span>  
 <span data-ttu-id="d87bb-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d87bb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d87bb-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d87bb-114">Child Elements</span></span>  
  
|<span data-ttu-id="d87bb-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="d87bb-115">Element</span></span>|<span data-ttu-id="d87bb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d87bb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d87bb-117">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="d87bb-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="d87bb-118">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="d87bb-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d87bb-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d87bb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d87bb-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="d87bb-120">Element</span></span>|<span data-ttu-id="d87bb-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d87bb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d87bb-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="d87bb-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="d87bb-123">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="d87bb-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d87bb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d87bb-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

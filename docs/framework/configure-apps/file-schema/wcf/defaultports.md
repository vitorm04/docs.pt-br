---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 4d7fdfb1cccb14f03d11864f1939cb578c79880a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704109"
---
# <a name="defaultports"></a><span data-ttu-id="3db10-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="3db10-101">\<defaultPorts></span></span>
<span data-ttu-id="3db10-102">Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3db10-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="3db10-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3db10-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3db10-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3db10-104">\<behaviors></span></span>  
<span data-ttu-id="3db10-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3db10-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3db10-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="3db10-106">\<behavior></span></span>  
<span data-ttu-id="3db10-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="3db10-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="3db10-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="3db10-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db10-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3db10-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3db10-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3db10-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3db10-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3db10-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3db10-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3db10-112">Attributes</span></span>  
 <span data-ttu-id="3db10-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3db10-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3db10-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3db10-114">Child Elements</span></span>  
  
|<span data-ttu-id="3db10-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="3db10-115">Element</span></span>|<span data-ttu-id="3db10-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3db10-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3db10-117">\<Adicionar > de \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="3db10-117">\<add> of \<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|<span data-ttu-id="3db10-118">Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="3db10-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3db10-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3db10-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3db10-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3db10-120">Element</span></span>|<span data-ttu-id="3db10-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3db10-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3db10-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="3db10-122">\<useRequestHeadersForMetadataAddress></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|<span data-ttu-id="3db10-123">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="3db10-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3db10-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3db10-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

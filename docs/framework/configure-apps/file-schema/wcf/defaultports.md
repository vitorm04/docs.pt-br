---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925882"
---
# <a name="defaultports"></a><span data-ttu-id="48faa-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="48faa-101">\<defaultPorts></span></span>
<span data-ttu-id="48faa-102">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="48faa-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="48faa-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="48faa-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="48faa-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="48faa-104">\<behaviors></span></span>  
<span data-ttu-id="48faa-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="48faa-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="48faa-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="48faa-106">\<behavior></span></span>  
<span data-ttu-id="48faa-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="48faa-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="48faa-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="48faa-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48faa-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48faa-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48faa-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48faa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48faa-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="48faa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48faa-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="48faa-112">Attributes</span></span>  
 <span data-ttu-id="48faa-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="48faa-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="48faa-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48faa-114">Child Elements</span></span>  
  
|<span data-ttu-id="48faa-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="48faa-115">Element</span></span>|<span data-ttu-id="48faa-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="48faa-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48faa-117">\<Adicionar > de \<DefaultPorts ></span><span class="sxs-lookup"><span data-stu-id="48faa-117">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="48faa-118">Um ponto de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="48faa-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48faa-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48faa-119">Parent Elements</span></span>  
  
|<span data-ttu-id="48faa-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="48faa-120">Element</span></span>|<span data-ttu-id="48faa-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="48faa-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48faa-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="48faa-122">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="48faa-123">Uma lista de portas padrão.</span><span class="sxs-lookup"><span data-stu-id="48faa-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48faa-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48faa-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

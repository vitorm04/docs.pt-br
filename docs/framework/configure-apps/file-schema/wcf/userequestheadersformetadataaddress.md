---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940545"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="b930f-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b930f-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="b930f-102">Habilita a recuperação de informações de endereço de metadados dos cabeçalhos de mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b930f-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="b930f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b930f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b930f-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b930f-104">\<behaviors></span></span>  
<span data-ttu-id="b930f-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="b930f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b930f-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b930f-106">\<behavior></span></span>  
<span data-ttu-id="b930f-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="b930f-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b930f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b930f-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b930f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b930f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b930f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b930f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b930f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b930f-111">Attributes</span></span>  
 <span data-ttu-id="b930f-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b930f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b930f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b930f-113">Child Elements</span></span>  
  
|<span data-ttu-id="b930f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b930f-114">Element</span></span>|<span data-ttu-id="b930f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b930f-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b930f-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b930f-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="b930f-117">Uma coleção de portas padrão que listam os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.</span><span class="sxs-lookup"><span data-stu-id="b930f-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b930f-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b930f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b930f-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="b930f-119">Element</span></span>|<span data-ttu-id="b930f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="b930f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b930f-121">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="b930f-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b930f-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b930f-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b930f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b930f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7469f06567ec8dab98592118ed392a680d4fb81a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="f1129-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="f1129-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="f1129-103">Especifica a descoberta de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="f1129-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="f1129-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f1129-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1129-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="f1129-105">\<behaviors></span></span>  
<span data-ttu-id="f1129-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f1129-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f1129-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="f1129-107">\<behavior></span></span>  
<span data-ttu-id="f1129-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="f1129-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1129-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1129-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1129-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1129-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f1129-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1129-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1129-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1129-112">Attributes</span></span>  
 <span data-ttu-id="f1129-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f1129-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f1129-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1129-114">Child Elements</span></span>  
  
|<span data-ttu-id="f1129-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1129-115">Element</span></span>|<span data-ttu-id="f1129-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1129-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1129-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="f1129-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="f1129-118">Uma coleção de pontos de extremidade de anúncio.</span><span class="sxs-lookup"><span data-stu-id="f1129-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="f1129-119">Use esta seção para especificar os pontos de extremidade a ser usado para enviar mensagens de aviso.</span><span class="sxs-lookup"><span data-stu-id="f1129-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="f1129-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="f1129-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="f1129-121">Uma coleção de pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f1129-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="f1129-122">Use esta seção para especificar pontos de extremidade para escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f1129-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1129-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1129-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f1129-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1129-124">Element</span></span>|<span data-ttu-id="f1129-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1129-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1129-126">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="f1129-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f1129-127">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="f1129-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1129-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1129-128">Remarks</span></span>  
 <span data-ttu-id="f1129-129">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração faz com que todos os pontos de extremidade de serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="f1129-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="f1129-130">Você pode configurar os recursos de descoberta de tais pontos de extremidade usando o [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) ou [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementos filho.</span><span class="sxs-lookup"><span data-stu-id="f1129-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="f1129-131">Use o [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) seção para configurar os anúncios especificando a configuração de ponto de extremidade a ser usada para enviar anúncios de serviço (online/Hello e offline/Bye).</span><span class="sxs-lookup"><span data-stu-id="f1129-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="f1129-132">Use o [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) seção para especificar manualmente o ponto de extremidade para escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="f1129-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1129-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1129-133">Example</span></span>  
 <span data-ttu-id="f1129-134">O exemplo de configuração a seguir especifica que o CalculatorService seja detectável e, opcionalmente, especifica o ponto de extremidade do anúncio a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f1129-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
  ...  
  </service>  
</services>  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="udpEndpoint"  
                        kind="udpAnnouncementEndpoint" />  
        </announcementEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1129-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1129-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

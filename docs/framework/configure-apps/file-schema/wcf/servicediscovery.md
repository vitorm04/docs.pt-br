---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936268"
---
# <a name="servicediscovery"></a><span data-ttu-id="6f69f-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="6f69f-101">\<serviceDiscovery></span></span>
<span data-ttu-id="6f69f-102">Especifica a descoberta de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="6f69f-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="6f69f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6f69f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f69f-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="6f69f-104">\<behaviors></span></span>  
<span data-ttu-id="6f69f-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="6f69f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6f69f-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="6f69f-106">\<behavior></span></span>  
<span data-ttu-id="6f69f-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="6f69f-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f69f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f69f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f69f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f69f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6f69f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6f69f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f69f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f69f-111">Attributes</span></span>  
 <span data-ttu-id="6f69f-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f69f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f69f-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f69f-113">Child Elements</span></span>  
  
|<span data-ttu-id="6f69f-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f69f-114">Element</span></span>|<span data-ttu-id="6f69f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f69f-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f69f-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="6f69f-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="6f69f-117">Uma coleção de pontos de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="6f69f-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="6f69f-118">Use esta seção para especificar os pontos de extremidade a serem usados para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="6f69f-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="6f69f-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="6f69f-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="6f69f-120">Uma coleção de pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6f69f-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="6f69f-121">Use esta seção para especificar os pontos de extremidade nos quais as mensagens de descoberta são escutadas.</span><span class="sxs-lookup"><span data-stu-id="6f69f-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f69f-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f69f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6f69f-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f69f-123">Element</span></span>|<span data-ttu-id="6f69f-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f69f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f69f-125">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="6f69f-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6f69f-126">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="6f69f-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f69f-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f69f-127">Remarks</span></span>  
 <span data-ttu-id="6f69f-128">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração torna todos os pontos de extremidade desse serviço detectáveis.</span><span class="sxs-lookup"><span data-stu-id="6f69f-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="6f69f-129">Você pode configurar ainda mais os recursos de descoberta desses pontos de extremidade usando os [ \<elementos filho DiscoveryEndpoint >](discoveryendpoint.md) ou [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="6f69f-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="6f69f-130">Use a [ \<seção > de announcementEndpoint](announcementendpoint.md) para configurar os anúncios especificando a configuração do ponto de extremidade a ser usada para enviar comunicados de serviço (online/Olá e offline/até).</span><span class="sxs-lookup"><span data-stu-id="6f69f-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="6f69f-131">Use a [ \<seção > de DiscoveryEndpoint](discoveryendpoint.md) para especificar manualmente o ponto de extremidade no qual escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="6f69f-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f69f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f69f-132">Example</span></span>  
 <span data-ttu-id="6f69f-133">O exemplo de configuração a seguir especifica que o CalculatorService a ser descoberto e, opcionalmente, especifica o ponto de extremidade de anúncio a ser usado.</span><span class="sxs-lookup"><span data-stu-id="6f69f-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f69f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f69f-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

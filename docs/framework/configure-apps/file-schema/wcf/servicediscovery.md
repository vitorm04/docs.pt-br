---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 54a9833f56927568af711a103bd3831b767711e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209990"
---
# <a name="servicediscovery"></a><span data-ttu-id="23658-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="23658-101">\<serviceDiscovery></span></span>
<span data-ttu-id="23658-102">Especifica a detectabilidade de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="23658-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="23658-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23658-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="23658-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="23658-104">\<behaviors></span></span>  
<span data-ttu-id="23658-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="23658-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="23658-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="23658-106">\<behavior></span></span>  
<span data-ttu-id="23658-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="23658-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23658-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23658-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23658-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23658-109">Attributes and Elements</span></span>  
 <span data-ttu-id="23658-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23658-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23658-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="23658-111">Attributes</span></span>  
 <span data-ttu-id="23658-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="23658-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23658-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23658-113">Child Elements</span></span>  
  
|<span data-ttu-id="23658-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="23658-114">Element</span></span>|<span data-ttu-id="23658-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="23658-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23658-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="23658-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="23658-117">Uma coleção de pontos de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="23658-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="23658-118">Use esta seção para especificar os pontos de extremidade a ser usado para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="23658-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="23658-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="23658-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="23658-120">Uma coleção de pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="23658-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="23658-121">Use esta seção para especificar os pontos de extremidade no qual escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="23658-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23658-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23658-122">Parent Elements</span></span>  
  
|<span data-ttu-id="23658-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="23658-123">Element</span></span>|<span data-ttu-id="23658-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="23658-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23658-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="23658-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="23658-126">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="23658-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23658-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="23658-127">Remarks</span></span>  
 <span data-ttu-id="23658-128">Quando adicionado à configuração de comportamento do serviço, este elemento de configuração faz com que todos os pontos de extremidade de serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="23658-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="23658-129">Você pode configurar os recursos de descoberta de tais pontos de extremidade usando o [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) ou [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) elementos filho.</span><span class="sxs-lookup"><span data-stu-id="23658-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="23658-130">Use o [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) seção para configurar os anúncios, especificando a configuração de ponto de extremidade a ser usado para enviar comunicados de serviço (online/Hello e offline/até logo).</span><span class="sxs-lookup"><span data-stu-id="23658-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="23658-131">Use o [ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) seção para especificar manualmente o ponto de extremidade para escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="23658-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23658-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23658-132">Example</span></span>  
 <span data-ttu-id="23658-133">O exemplo de configuração a seguir especifica que o CalculatorService seja detectável e, opcionalmente, especifica o ponto de extremidade de comunicado a ser usado.</span><span class="sxs-lookup"><span data-stu-id="23658-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23658-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23658-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

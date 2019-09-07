---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399629"
---
# <a name="servicediscovery"></a><span data-ttu-id="84cde-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="84cde-101">\<serviceDiscovery></span></span>
<span data-ttu-id="84cde-102">Especifica a descoberta de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="84cde-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="84cde-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="84cde-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="84cde-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="84cde-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="84cde-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84cde-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="84cde-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84cde-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="84cde-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="84cde-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="84cde-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de indescoberta**</span><span class="sxs-lookup"><span data-stu-id="84cde-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84cde-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84cde-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84cde-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="84cde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84cde-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="84cde-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84cde-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="84cde-112">Attributes</span></span>  
 <span data-ttu-id="84cde-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="84cde-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84cde-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="84cde-114">Child Elements</span></span>  
  
|<span data-ttu-id="84cde-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="84cde-115">Element</span></span>|<span data-ttu-id="84cde-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="84cde-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84cde-117">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="84cde-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="84cde-118">Uma coleção de pontos de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="84cde-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="84cde-119">Use esta seção para especificar os pontos de extremidade a serem usados para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="84cde-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="84cde-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="84cde-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="84cde-121">Uma coleção de pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="84cde-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="84cde-122">Use esta seção para especificar os pontos de extremidade nos quais as mensagens de descoberta são escutadas.</span><span class="sxs-lookup"><span data-stu-id="84cde-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84cde-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="84cde-123">Parent Elements</span></span>  
  
|<span data-ttu-id="84cde-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="84cde-124">Element</span></span>|<span data-ttu-id="84cde-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="84cde-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84cde-126">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="84cde-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="84cde-127">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="84cde-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84cde-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="84cde-128">Remarks</span></span>  
 <span data-ttu-id="84cde-129">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração torna todos os pontos de extremidade desse serviço detectáveis.</span><span class="sxs-lookup"><span data-stu-id="84cde-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="84cde-130">Você pode configurar ainda mais os recursos de descoberta desses pontos de extremidade usando os [ \<elementos filho DiscoveryEndpoint >](discoveryendpoint.md) ou [ \<announcementEndpoint >](announcementendpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="84cde-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="84cde-131">Use a [ \<seção > de announcementEndpoint](announcementendpoint.md) para configurar os anúncios especificando a configuração do ponto de extremidade a ser usada para enviar comunicados de serviço (online/Olá e offline/até).</span><span class="sxs-lookup"><span data-stu-id="84cde-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="84cde-132">Use a [ \<seção > de DiscoveryEndpoint](discoveryendpoint.md) para especificar manualmente o ponto de extremidade no qual escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="84cde-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84cde-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84cde-133">Example</span></span>  
 <span data-ttu-id="84cde-134">O exemplo de configuração a seguir especifica que o CalculatorService a ser descoberto e, opcionalmente, especifica o ponto de extremidade de anúncio a ser usado.</span><span class="sxs-lookup"><span data-stu-id="84cde-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84cde-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84cde-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

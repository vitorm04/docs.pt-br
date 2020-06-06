---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399629"
---
# \<serviceDiscovery>
<span data-ttu-id="71637-101">Especifica a descoberta de pontos de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="71637-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="71637-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71637-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71637-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="71637-103">Attributes and Elements</span></span>  
 <span data-ttu-id="71637-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="71637-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71637-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="71637-105">Attributes</span></span>  
 <span data-ttu-id="71637-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="71637-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71637-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="71637-107">Child Elements</span></span>  
  
|<span data-ttu-id="71637-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="71637-108">Element</span></span>|<span data-ttu-id="71637-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="71637-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="71637-110">Uma coleção de pontos de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="71637-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="71637-111">Use esta seção para especificar os pontos de extremidade a serem usados para enviar mensagens de comunicado.</span><span class="sxs-lookup"><span data-stu-id="71637-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="71637-112">Uma coleção de pontos de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="71637-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="71637-113">Use esta seção para especificar os pontos de extremidade nos quais as mensagens de descoberta são escutadas.</span><span class="sxs-lookup"><span data-stu-id="71637-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71637-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="71637-114">Parent Elements</span></span>  
  
|<span data-ttu-id="71637-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="71637-115">Element</span></span>|<span data-ttu-id="71637-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="71637-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="71637-117">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="71637-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71637-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="71637-118">Remarks</span></span>  
 <span data-ttu-id="71637-119">Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração torna todos os pontos de extremidade desse serviço detectáveis.</span><span class="sxs-lookup"><span data-stu-id="71637-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="71637-120">Você pode configurar ainda mais os recursos de descoberta desses pontos de extremidade usando os [\<discoveryEndpoint>](discoveryendpoint.md) [\<announcementEndpoint>](announcementendpoint.md) elementos filho ou.</span><span class="sxs-lookup"><span data-stu-id="71637-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="71637-121">Use a [\<announcementEndpoint>](announcementendpoint.md) seção para configurar os comunicados especificando a configuração do ponto de extremidade a ser usada para enviar comunicados de serviço (online/Olá e offline/adeus).</span><span class="sxs-lookup"><span data-stu-id="71637-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="71637-122">Use a [\<discoveryEndpoint>](discoveryendpoint.md) seção para especificar manualmente o ponto de extremidade no qual escutar as mensagens de descoberta.</span><span class="sxs-lookup"><span data-stu-id="71637-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71637-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71637-123">Example</span></span>  
 <span data-ttu-id="71637-124">O exemplo de configuração a seguir especifica que o CalculatorService a ser descoberto e, opcionalmente, especifica o ponto de extremidade de anúncio a ser usado.</span><span class="sxs-lookup"><span data-stu-id="71637-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71637-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="71637-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

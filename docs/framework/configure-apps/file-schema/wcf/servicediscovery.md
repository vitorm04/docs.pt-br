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
# <a name="servicediscovery"></a>\<serviceDiscovery>
Especifica a descoberta de pontos de extremidade de serviço.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de portais  
\<> de comportamento  
\<serviceDiscovery>  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|Uma coleção de pontos de extremidade de comunicado. Use esta seção para especificar os pontos de extremidade a serem usados para enviar mensagens de comunicado.|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|Uma coleção de pontos de extremidade de descoberta. Use esta seção para especificar os pontos de extremidade nos quais as mensagens de descoberta são escutadas.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração torna todos os pontos de extremidade desse serviço detectáveis. Você pode configurar ainda mais os recursos de descoberta desses pontos de extremidade usando os [ \<elementos filho DiscoveryEndpoint >](discoveryendpoint.md) ou [ \<announcementEndpoint >](announcementendpoint.md) . Use a [ \<seção > de announcementEndpoint](announcementendpoint.md) para configurar os anúncios especificando a configuração do ponto de extremidade a ser usada para enviar comunicados de serviço (online/Olá e offline/até). Use a [ \<seção > de DiscoveryEndpoint](discoveryendpoint.md) para especificar manualmente o ponto de extremidade no qual escutar as mensagens de descoberta.  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir especifica que o CalculatorService a ser descoberto e, opcionalmente, especifica o ponto de extremidade de anúncio a ser usado.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>

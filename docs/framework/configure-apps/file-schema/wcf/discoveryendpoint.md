---
title: '&lt;discoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be4dc40327f7d1bfa713cefe80908cdba5bc7101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryendpointgt"></a>&lt;discoveryEndpoint&gt;

Este elemento de configuração define um ponto de extremidade padrão com um contrato de correção da descoberta. Quando adicionado à configuração de serviço, ele especifica onde ouvir as mensagens de descoberta. Quando adicionado à configuração de cliente especifica para onde enviar as consultas de descoberta.  
  
\<System. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sintaxe

```xml
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed" 
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxResponseDelay="Timespan" 
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos

| Atributo        | Descrição |  
| ---------------- | ----------- |  
| discoveryMode    | Uma cadeia de caracteres que especifica o modo de protocolo de descoberta. Os valores válidos são "Ad hoc" e "Gerenciado". No modo gerenciado o protocolo depende de um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos. Modo ad hoc requer o protocolo a usar UDP multicast mecanismo para localizar serviços disponíveis. Para obter mais informações sobre a propriedade, consulte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery. Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005. Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Um valor Timespan que especifica o valor máximo para o protocolo de descoberta de atraso aguardará antes de enviar determinadas mensagens, como teste de correspondência ou resolva.<br /><br /> Se todas as ProbeMatches forem enviados ao mesmo tempo, pode resultar uma profusão de rede. Para evitar que isso ocorra, ProbeMatches são enviadas com um atraso aleatório entre cada ProbeMatch. É o atraso aleatório no intervalo de 0 até o valor definido por este atributo. Se esse atributo é definido como 0, as mensagens de ProbeMatches são enviadas em um loop estreito sem atraso. Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total gasto para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay. Esse valor só é relevante para serviços, ele não é usado por clientes. |  
| `name`           | Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão. O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração. |  
  
### <a name="child-elements"></a>Elementos filho

nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |  
| ------- | ----------- |  
| [\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo. |  
  
## <a name="example"></a>Exemplo

O exemplo a seguir demonstra um serviço que escuta as mensagens de descoberta por um transporte de multicast de rede ponto a ponto. O exemplo especifica explicitamente o WS-Discovery versão de abril de 2005.  
  
A configuração de ponto de extremidade padrão é definida por serviço e não pode ser compartilhada entre o serviço. Se desejar outro serviço que têm o mesmo ponto de extremidade de descoberta, a mesma configuração precisa ser adicionada à seção do serviço.  
  
```xml
<services>  
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding" 
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="peerNetDiscovery"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              kind="discoveryEndpoint"  
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />      
  </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"                         
                      version="WSDiscoveryApril2005" />  
  </discoveryEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>Consulte também

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

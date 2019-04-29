---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: d1a3371872f5587a682b8242c29b71808508ca3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704044"
---
# <a name="discoveryendpoint"></a>\<discoveryEndpoint>

Este elemento de configuração define um ponto de extremidade padrão com um contrato de correção da descoberta. Quando adicionado à configuração de serviço, ele especifica onde a escutar as mensagens de descoberta. Quando adicionado à configuração de cliente, ele especifica para onde enviar as consultas de descoberta.  
  
\<system.serviceModel>  
\<standardEndpoints>  
  
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
| discoveryMode    | Uma cadeia de caracteres que especifica o modo do protocolo de descoberta. Os valores válidos são "Adhoc" e "Gerenciado". No modo gerenciado o protocolo se baseia em um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos. Modo ad hoc requer o protocolo a usar o UDP multicast mecanismo para localizar os serviços disponíveis. Para obter mais informações sobre a propriedade, consulte <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>. |  
| discoveryVersion | Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery. Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005. Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Um valor de Timespan que especifica o valor máximo para o atraso, o protocolo de descoberta irá esperar antes de enviar determinadas mensagens, como correspondência de investigação ou resolver.<br /><br /> Se todas as ProbeMatches forem enviadas ao mesmo tempo, pode resultar uma tempestade de rede. Para evitar que isso ocorra, ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch. É o atraso aleatório no intervalo de 0 até o valor definido por este atributo. Se esse atributo é definido como 0, as ProbeMatches de mensagens são enviadas em um loop estreito sem demora. Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total decorrido para enviar mensagens de todas as ProbeMatches não exceda o maxResponseDelay. Esse valor só é relevante para os serviços, ele não é usado pelos clientes. |  
| `name`           | Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão. O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração. |  
  
### <a name="child-elements"></a>Elementos filho

nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai

| Elemento | Descrição |  
| ------- | ----------- |  
| [\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo. |  
  
## <a name="example"></a>Exemplo

O exemplo a seguir demonstra um serviço escutando em mensagens de descoberta em um transporte de multicast rede ponto a ponto. O exemplo especifica explicitamente o WS-Discovery versão de abril de 2005.  
  
A configuração de ponto de extremidade padrão é definida por serviço e não pode ser compartilhada entre o serviço. Se outro serviço gostaria de ter o mesmo ponto de extremidade de descoberta, a mesma configuração precisa ser adicionado à seção do serviço.  
  
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

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

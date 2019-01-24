---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: b46da83a175c2a9cff38abc211d462f3d43c1b9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569213"
---
# <a name="ltudpdiscoveryendpointgt"></a>&lt;udpDiscoveryEndpoint&gt;
Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP multicast de associação. Esse ponto de extremidade tem um contrato fixo e oferece suporte a duas versões do protocolo WS-Discovery. Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|discoveryMode|Uma cadeia de caracteres que especifica o modo do protocolo de descoberta. Os valores válidos são "Adhoc" e "Gerenciado". No modo gerenciado o protocolo se baseia em um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos. Modo ad hoc requer o protocolo a usar o UDP multicast mecanismo para localizar os serviços disponíveis. Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery. Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005. Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Um valor de Timespan que especifica o valor máximo para o atraso, o protocolo de descoberta irá esperar antes de enviar determinadas mensagens, como correspondência de investigação ou resolver.<br /><br /> Se todas as ProbeMatches forem enviadas ao mesmo tempo, pode resultar uma tempestade de rede. Para evitar que isso ocorra, ProbeMatches são enviados com um atraso aleatório entre cada ProbeMatch. É o atraso aleatório no intervalo de 0 até o valor definido por este atributo. Se esse atributo é definido como 0, as ProbeMatches de mensagens são enviadas em um loop estreito sem demora. Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total decorrido para enviar mensagens de todas as ProbeMatches não exceda o maxResponseDelay. Esse valor só é relevante para os serviços, ele não é usado pelos clientes.|  
|multicastAddress|Um Uri que especifica um endereço de multicast a ser usado para enviar e receber as mensagens de descoberta. O valor padrão é o endereço multicast como em conformidade com a especificação do protocolo.|  
|`name`|Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão. O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<udpTransportSettings>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um serviço de escuta para mensagens de descoberta através de um UDP multicast de transporte.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f0165f8cda6701aa11058f2dac1bdde0f9ebbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltudpdiscoveryendpointgt"></a>&lt;udpDiscoveryEndpoint&gt;
Este elemento de configuração define um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP associação multicast. Esse ponto de extremidade tem um contrato fixo e dá suporte a duas versões do protocolo WS-Discovery. Além disso, ele tem uma associação fixa do UDP e um endereço padrão conforme especificado nas especificações do WS-Discovery (WS-Discovery de abril de 2005 ou v 1.1 do WS-Discovery).  
  
 \<sistema. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|discoveryMode|Uma cadeia de caracteres que especifica o modo de protocolo de descoberta. Os valores válidos são "Ad hoc" e "Gerenciado". No modo gerenciado o protocolo depende de um Proxy de descoberta, que atua como um repositório de serviços podem ser descobertos. Modo ad hoc requer o protocolo a usar UDP multicast mecanismo para localizar serviços disponíveis. Esse valor é do tipo <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.|  
|discoveryVersion|Uma cadeia de caracteres que especifica uma das duas versões do protocolo WS-Discovery. Os valores válidos são WSDiscovery11 e WSDiscoveryApril2005. Esse valor é do tipo <xref:System.ServiceModel.Discovery.DiscoveryVersion>.|  
|maxResponseDelay|Um valor Timespan que especifica o valor máximo para o protocolo de descoberta de atraso aguardará antes de enviar determinadas mensagens, como teste de correspondência ou resolva.<br /><br /> Se todas as ProbeMatches forem enviados ao mesmo tempo, pode resultar uma profusão de rede. Para evitar que isso ocorra, ProbeMatches são enviadas com um atraso aleatório entre cada ProbeMatch. É o atraso aleatório no intervalo de 0 até o valor definido por este atributo. Se esse atributo é definido como 0, as mensagens de ProbeMatches são enviadas em um loop estreito sem atraso. Caso contrário, as mensagens de ProbeMatches são enviadas com algum atraso aleatório, de modo que o tempo total gasto para enviar todas as mensagens de ProbeMatches não exceda o maxResponseDelay. Esse valor só é relevante para serviços, ele não é usado por clientes.|  
|multicastAddress|Um Uri que especifica um endereço de multicast para usar para enviar e receber mensagens de descoberta. O valor padrão é o endereço multicast como compatível com a especificação do protocolo.|  
|`name`|Uma cadeia de caracteres que especifica o nome da configuração do ponto de extremidade padrão. O nome é usado no `endpointConfiguration` atributo do ponto de extremidade de serviço para vincular a um ponto de extremidade padrão para sua configuração.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<udpTransportSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|Uma coleção de configurações que permitem que você configure o transporte UDP para o ponto de extremidade UDP.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um serviço de escuta de mensagens de descoberta através de um UDP multicast de transporte.  
  
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
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

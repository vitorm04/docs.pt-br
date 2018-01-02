---
title: '&lt;udpTransportSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88b38fc7c67c404446000ca79d2c6191bfc7eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt"></a>&lt;udpTransportSettings&gt;
Este elemento de configuração expõe configurações de transporte UDP para [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).  
  
\<sistema. ServiceModel >  
\<standardEndpoints >  
\<udpDiscoveryEndpoint >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer" 
                              maxBufferPoolSize="Integer" 
                              maxMulticastRetransmitCount="Integer" 
                              maxPendingMessageCount="Integer" 
                              maxReceivedMessageSize="Integer" 
                              maxUnicastRetransmitCount="Integer" 
                              multicastInterfaceId="String" 
                              socketReceiveBufferSize="Integer" 
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Um inteiro que especifica o número máximo de mensagens de hash usado pelo transporte para identificar mensagens duplicadas.  Detecção de duplicidades será feita no nível de TransportManager. Definir essa propriedade como 0 desabilita a detecção de duplicidades.<br /><br /> Este atributo permite aos administradores de sistema ou desenvolvedores para desativar os algoritmos de detecção de mensagens duplicadas. Isso pode ser desejável para implementar seu próprio algoritmo de detecção de duplicidades.<br /><br /> O padrão é 4112.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho máximo de qualquer pools de buffers usado pelo transporte.|  
|maxMulticastRetransmitCount|Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).<br /><br /> O padrão é 2.|  
|maxPendingMessageCount|Um inteiro que especifica o número máximo de mensagens que foram recebidos, mas ainda não foram removidas do InputQueue para uma instância de canal individual.  Se o InputQueue atingiu seu limite de contagem de mensagens pendentes, a mensagem será descartada.<br /><br /> O padrão é 32.|  
|maxReceivedMessageSize|Um inteiro que especifica o tamanho máximo para uma mensagem que pode ser processada por meio da associação.<br /><br /> O valor padrão é 65507.|  
|maxUnicastRetransmitCount|Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).  Se a mensagem é enviada a um endereço de unicast e uma mensagem de resposta é recebida com um cabeçalho RelatesTo correspondente, retransmissão pode terminar cedo (antes de retransmitir o número configurado de vezes).<br /><br /> O valor padrão é 1.|  
|multicastInterfaceId|Uma cadeia de caracteres que identifica exclusivamente o adaptador de rede que deve ser usado ao enviar e receber tráfego multicast em computadores multihomed. Em tempo de execução, o transporte usará esse valor de atributo para pesquisar o índice de interface, que é usado para definir o `IP_MULTICAST_IF` e `IPV6_MULTICAST_IF` opções de soquete.  O mesmo índice será usado ao ingressar em um grupo de difusão seletiva, se aplicável.<br /><br /> O valor padrão é `null`.|  
|socketReceiveBufferSize|Um inteiro que especifica o tamanho do buffer de recebimento no soquete WinSock subjacente.<br /><br /> Um usuário de um canal de recebimento pode usar esse atributo na ligação para controlar como o sistema se comporta quando ele recebe dados.  Por exemplo, devido a um aplicativo que está consumindo entradas mensagens do WCF no limite máximo, usar um valor mais alto para esse atributo deve permitir que as mensagens empilhar no buffer de WinSock enquanto aguarda o aplicativo possa processá-los.  Usar um valor mais baixo na mesma situação pode resultar em mensagens sendo descartadas. Esse atributo expõe o WinSock subjacente `SO_RCVBUF` opção de soquete. O valor do atributo deve ser pelo menos o tamanho do `maxReceivedMessageSize`.   Configurá-lo como um valor menor do que o `maxReceivedMessageSize` resultará na exceção de tempo de execução.<br /><br /> O valor padrão é 65536.|  
|TimeToLive|Um inteiro que especifica o número de saltos de segmento de rede que um pacote de multicast pode percorrer.  Esse atributo expõe a funcionalidade associada a `IP_MULTICAST_TTL` e `IP_TTL` opções de soquete.<br /><br /> O valor padrão é 1.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Um ponto de extremidade padrão que corrigiu descoberta de associação de transporte do contrato e UDP.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>

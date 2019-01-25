---
title: '&lt;udpTransportSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: 58931cb70f83378740093615adf89a437e32ff2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667187"
---
# <a name="ltudptransportsettingsgt"></a>&lt;udpTransportSettings&gt;
Este elemento de configuração expõe para as configurações de transporte UDP [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).  
  
\<system.ServiceModel>  
\<standardEndpoints>  
\<udpDiscoveryEndpoint>  
  
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
|duplicateMessageHistoryLength|Um inteiro que especifica o número máximo de hashes de mensagem usados pelo transporte para identificar mensagens duplicadas.  Detecção de duplicidades será feita no nível do TransportManager. Definir essa propriedade como 0 desabilita a detecção de duplicidades.<br /><br /> Este atributo permite que os administradores do sistema ou os desenvolvedores a desativar algoritmos de detecção de mensagens duplicadas. Isso pode ser desejável se você quiser implementar seu próprio algoritmo de detecção de duplicidades.<br /><br /> O padrão é 4112.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho máximo de qualquer pool de buffer usado pelo transporte.|  
|maxMulticastRetransmitCount|Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).<br /><br /> O padrão é 2.|  
|maxPendingMessageCount|Um inteiro que especifica o número máximo de mensagens que foram recebidos, mas ainda não foram removidas da InputQueue para uma instância de canal individual.  Se InputQueue atingiu seu limite de contagem de mensagem pendente, a mensagem será descartada.<br /><br /> O padrão é 32.|  
|maxReceivedMessageSize|Um inteiro que especifica o tamanho máximo para uma mensagem que pode ser processada pela associação.<br /><br /> O valor padrão é 65507.|  
|maxUnicastRetransmitCount|Um inteiro que especifica o número máximo de vezes que a mensagem deve ser retransmitida (além do primeiro envio).  Se a mensagem é enviada para um endereço unicast e uma mensagem de resposta for recebida com um cabeçalho RelatesTo correspondente, a retransmissão poderá rescindir no início (antes de retransmitir o número de vezes configurado).<br /><br /> O valor padrão é 1.|  
|multicastInterfaceId|Uma cadeia de caracteres que identifica exclusivamente o adaptador de rede que deve ser usado ao enviar e receber tráfego multicast em computadores com hospedagem múltipla. Em tempo de execução, o transporte usará esse valor de atributo para pesquisar o índice de interface, que é usado para definir a `IP_MULTICAST_IF` e `IPV6_MULTICAST_IF` opções de soquete.  O mesmo índice de interface será usado ao ingressar em um grupo de multicast, se aplicável.<br /><br /> O valor padrão é `null`.|  
|socketReceiveBufferSize|Um inteiro que especifica o tamanho do buffer de recebimento no soquete WinSock subjacente.<br /><br /> Um usuário de um canal de recebimento pode usar esse atributo na ligação para controlar como o sistema se comporta quando ele recebe dados.  Por exemplo, dado um aplicativo que está consumindo entradas mensagens do WCF no limite máximo, usar um valor mais alto para esse atributo seria permitir que as mensagens de pilha para cima no buffer de WinSock enquanto aguarda o aplicativo possa processá-los.  Usar um valor mais baixo na mesma situação resultaria em mensagens sendo interrompidas. Esse atributo expõe o WinSock subjacente `SO_RCVBUF` opção de soquete. Esse valor de atributo deve ser pelo menos o tamanho do `maxReceivedMessageSize`.   Defini-lo como um valor menor do que o `maxReceivedMessageSize` resultará em uma exceção de tempo de execução.<br /><br /> O valor padrão é 65536.|  
|timeToLive|Um inteiro que especifica o número de saltos de segmento de rede que um pacote de multicast pode percorrer.  Esse atributo expõe a funcionalidade associada com o `IP_MULTICAST_TTL` e `IP_TTL` opções de soquete.<br /><br /> O valor padrão é 1.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Um ponto de extremidade padrão que corrigido descoberta, ligação de transporte de contrato e UDP.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Discovery.UdpTransportSettings>

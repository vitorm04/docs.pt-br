---
title: '&lt;tcpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f534bab962e83f76dab7e411cc3c2ca14779df9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
Define um transporte TCP que pode ser usado por um canal transferir mensagens para uma associação personalizada.  
  
 \<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<tcpTransport >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|channelInitializationTimeout|Obtém ou define o limite de tempo de inicialização de um canal para serem aceitos.  O tempo máximo de um canal pode estar no estado de inicialização antes de ser desconectada em segundos. Essa cota inclui o tempo que uma conexão TCP pode tomar para autenticar usando o .net Message Framing protocolo. Um cliente precisa enviar alguns dados iniciais antes que o servidor tenha informações suficientes para executar a autenticação. O padrão é 30 segundos.|  
|connectionBufferSize|Obtém ou define o tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.|  
|hostNameComparisonMode|Obtém ou define um valor que indica se o nome do host é usado para alcançar o serviço ao fazer correspondência no URI.|  
|listenBacklog|O número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web. O `connectionLeaseTimeout` atributo limita a duração em que o cliente aguardará para ser conectado antes de gerar uma exceção de conexão. Esta é uma propriedade de nível de soquete que controla o número máximo de solicitações de conexão em fila que podem estar pendentes para um serviço Web. Quando ListenBacklog é muito baixo, o WCF parar de aceitar solicitações e descartar, portanto, novas conexões até que o servidor confirma a algumas das conexões existentes na fila. O padrão é 16 * número de processadores.|  
|manualAddressing|Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.|  
|maxBufferPoolSize|Obtém ou define o tamanho máximo de qualquer pools de buffers usado pelo transporte.|  
|maxBufferSize|Obtém ou define o tamanho máximo do buffer a ser usado. Para mensagens transmitidas, este valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, lidos em modo em buffer.|  
|maxOutputDelay|Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.|  
|maxPendingAccepts|Obtém ou define o número máximo de pendente assíncrono aceita operações que estão disponíveis para conexões de entrada de processamento para o serviço.|  
|maxPendingConnections|Obtém ou define o número máximo de conexões aguardando a expedição no serviço.|  
|maxReceivedMessageSize|Obtém e define o tamanho máximo de mensagem permitido que pode ser recebido.|  
|portSharingEnabled|Um valor booleano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão. Se isso for `false`, cada associação usará sua própria porta exclusiva. O padrão é `false`.<br /><br /> Essa configuração é relevante apenas para serviços. Os clientes não são afetados.<br /><br /> Usar essa configuração exige a habilitação de serviço de compartilhamento de porta de TCP do Windows Communication Foundation (WCF), alterando o tipo de inicialização para Manual ou automático|  
|teredoEnabled|Um valor booleano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado. O padrão é `false`.<br /><br /> Essa propriedade permite que o Teredo para o soquete TCP subjacente. Para obter mais informações, consulte [visão geral de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Essa propriedade é aplicável apenas em [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] e [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)]tem uma opção de configuração de máquina para o Teredo, portanto ao executar o Vista, essa propriedade será ignorada. Teredo exige que as máquinas cliente e de serviço tem a pilha do IPv6 Microsoft instalado e configurado corretamente para o uso de Teredo. Para obter mais informações sobre como configurar o Teredo, consulte [visão geral de Teredo](http://go.microsoft.com/fwlink/?LinkId=95339). Para obter mais informações, consulte [centros de tecnologia do Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas com o transporte voltado para a conexão.|  
|connectionPoolSettings|Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Esse transporte usa URIs no formato "net.tcp://hostname: porta/caminho". Outros componentes do URI são opcionais.  
  
 O `tcpTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte TCP. Esse transporte é otimizado para comunicação WCF-WCF.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Escolhendo um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

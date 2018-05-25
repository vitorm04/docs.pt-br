---
title: 'Cliente: fábricas de canais e canais'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: a42042eaf9a8bc5461f680e3cf8dc5fcc78cebb5
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="client-channel-factories-and-channels"></a>Cliente: fábricas de canais e canais
Este tópico aborda a criação de canais e fábricas de canais.  
  
## <a name="channel-factories-and-channels"></a>Fábricas de canais e canais  
 Fábricas de canais são responsáveis por criar canais. Canais criados por fábricas de canais são usados para enviar mensagens. Esses canais são responsáveis por recebendo a mensagem da camada acima, executar o processamento que for necessário, em seguida, enviar a mensagem para a camada abaixo. O gráfico a seguir ilustra esse processo.  
  
 ![Canais e fábricas de cliente](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Uma fábrica de canais cria canais.  
  
 Depois de fechada, fábricas de canais são responsáveis por fechar todos os canais criaram que ainda não estão fechados. Observe que o modelo é assimétrico aqui porque quando um ouvinte de canal é fechado, ele apenas para de aceitar novos canais, mas deixa aberta de canais existentes para que eles podem continuar a receber mensagens.  
  
 O WCF fornece auxiliares da classe base para esse processo. (Para um diagrama de classes de auxiliar o canal discutidos neste tópico, consulte [visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.
  
-   O <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida o `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstract.
  
-   O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Cuida do gerenciamento de estado básica. 
  
 A discussão a seguir baseia-se a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
### <a name="creating-a-channel-factory"></a>Criar uma fábrica de canais  
 O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>. O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso para a versão de mensagem do codificador de mensagem. O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para subdividir a instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída de UDP  
 O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>. O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.  
  
 A substituição de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> cria um soquete que é usado para enviar mensagens para esse <xref:System.Net.EndPoint>.  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 O canal pode ser fechado normalmente ou maneira brusca. Se o canal está fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método. Se isso gera uma exceção, a infraestrutura de chamadas `Abort` garantir que o canal é limpa.  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementar `Send()` e `BeginSend()` / `EndSend()`. Isso é dividido em duas seções principais. Primeiro serialize a mensagem em uma matriz de bytes:  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, envie os dados resultantes na conexão:  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvimento de canais](../../../../docs/framework/wcf/extending/developing-channels.md)

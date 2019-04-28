---
title: 'Cliente: fábricas de canais e canais'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: bfa5d2478d5c12f16c2d9531de02e1c868eab560
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858398"
---
# <a name="client-channel-factories-and-channels"></a>Cliente: fábricas de canais e canais
Este tópico aborda a criação de fábricas de canais e canais.  
  
## <a name="channel-factories-and-channels"></a>fábricas de canais e canais  
 Fábricas de canais são responsáveis por criar canais. Canais criados por fábricas de canais são usados para enviar mensagens. Esses canais são responsáveis por recebendo a mensagem da camada acima, executar o processamento que for necessário, em seguida, enviar a mensagem para a camada abaixo. O gráfico a seguir ilustra esse processo.  
  
 ![Canais e fábricas de cliente](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Uma fábrica de canais cria canais.  
  
 Quando fechado, fábricas de canais são responsáveis por quaisquer canais criados por eles que ainda não foram fechados de fechamento. Observe que o modelo é assimétrico aqui porque quando um ouvinte de canais é fechado, ela só para de aceitar novos canais, mas deixa os canais existentes aberto para que eles possam continuar a receber mensagens.  
  
 O WCF fornece auxiliares da classe base para esse processo. (Para um diagrama das classes de auxiliar de canal discutidos neste tópico, consulte [visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
- O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
- O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.
  
- O <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida os `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstrato.
  
- O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Ele cuida do gerenciamento de estado básica. 
  
 A discussão a seguir baseia-se a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
### <a name="creating-a-channel-factory"></a>Criando uma fábrica de canais  
 O `UdpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase>. O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso à versão de mensagem do codificador de mensagem. O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> subdividir nossa instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída UDP  
 O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>. O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.  
  
 A substituição de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> cria um soquete que é usado para enviar mensagens para isso <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 O canal pode ser fechado normalmente ou de maneira brusca. Se o canal seja fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método. Se isso gerar uma exceção, a infraestrutura chame `Abort` garantir que o canal é limpa.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implemente `Send()` e `BeginSend()` / `EndSend()`. Isso se divide em duas seções principais. Primeiro, serialize a mensagem em uma matriz de bytes:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, envie os dados resultantes durante a transmissão:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Consulte também

- [Desenvolvimento de canais](../../../../docs/framework/wcf/extending/developing-channels.md)

---
title: 'Cliente: fábricas de canais e canais'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185687"
---
# <a name="client-channel-factories-and-channels"></a>Cliente: fábricas de canais e canais
Este tema discute a criação de fábricas de canais e canais.  
  
## <a name="channel-factories-and-channels"></a>fábricas de canais e canais  
 As fábricas de canais são responsáveis pela criação de canais. Canais criados por fábricas de canais são usados para enviar mensagens. Esses canais são responsáveis por obter a mensagem da camada acima, realizar qualquer processamento necessário e, em seguida, enviar a mensagem para a camada abaixo. O gráfico a seguir ilustra esse processo.  
  
 ![Fábricas de cliente e canais](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Uma fábrica de canais cria canais.  
  
 Quando fechadas, as fábricas de canais são responsáveis pelo fechamento de todos os canais que criaram que ainda não estão fechados. Note que o modelo é assimétrico aqui porque quando um ouvinte de canal é fechado, ele só deixa de aceitar novos canais, mas deixa os canais existentes abertos para que eles possam continuar recebendo mensagens.  
  
 O WCF fornece ajudantes de classe base para este processo. (Para obter um diagrama das classes de auxiliares de canal discutidas neste tópico, consulte [Visão geral do modelo](channel-model-overview.md)do canal .)  
  
- A <xref:System.ServiceModel.Channels.CommunicationObject> classe <xref:System.ServiceModel.ICommunicationObject> implementa e impõe a máquina estatal descrita na etapa 2 do [Desenvolvimento de Canais](developing-channels.md).  
  
- A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe <xref:System.ServiceModel.Channels.CommunicationObject> implementa e fornece <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> uma <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>classe de base unificada para e . A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe trabalha <xref:System.ServiceModel.Channels.ChannelBase>em conjunto com , que <xref:System.ServiceModel.Channels.IChannel>é uma classe de base que implementa .
  
- A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa e <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` consolida as `OnCreateChannel` sobrecargas em um método abstrato.
  
- A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe <xref:System.ServiceModel.Channels.IChannelListener>implementa. Cuida da gestão básica do Estado.
  
 A seguinte discussão baseia-se na amostra [Transporte: UDP.](../samples/transport-udp.md)  
  
### <a name="creating-a-channel-factory"></a>Criando uma fábrica de canais  
 O `UdpChannelFactory` derivado <xref:System.ServiceModel.Channels.ChannelFactoryBase>de . A amostra <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> substitui-se para fornecer acesso à versão da mensagem do codificador de mensagens. A amostra também <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> se sobrepõe <xref:System.ServiceModel.Channels.BufferManager> para derrubar nossa instância de quando a máquina do estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída do UDP  
 Os `UdpOutputChannel` implementos. <xref:System.ServiceModel.Channels.IOutputChannel> O construtor valida os argumentos e <xref:System.Net.EndPoint> constrói um <xref:System.ServiceModel.EndpointAddress> objeto de destino com base no que é passado.  
  
 A substituição <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> de cria um soquete que <xref:System.Net.EndPoint>é usado para enviar mensagens para isso .  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 O canal pode ser fechado graciosamente ou sem graça. Se o canal estiver fechado graciosamente, o soquete `OnClose` é fechado e uma chamada é feita para o método de classe base. Se isso abrir uma exceção, a infra-estrutura liga `Abort` para garantir que o canal seja limpo.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementar `Send()` `BeginSend()` / `EndSend()`e . Isso se divide em duas seções principais. Primeiro serialize a mensagem em uma matriz de bytes:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, envie os dados resultantes no fio:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Confira também

- [Desenvolvimento de canais](developing-channels.md)

---
title: 'Cliente: fábricas de canais e canais'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795868"
---
# <a name="client-channel-factories-and-channels"></a>Cliente: fábricas de canais e canais
Este tópico discute a criação de fábricas de canais e canais.  
  
## <a name="channel-factories-and-channels"></a>fábricas de canais e canais  
 As fábricas de canal são responsáveis pela criação de canais. Os canais criados por fábricas de canal são usados para enviar mensagens. Esses canais são responsáveis por obter a mensagem da camada acima, executar qualquer processamento necessário e, em seguida, enviar a mensagem para a camada abaixo. O gráfico a seguir ilustra esse processo.  
  
 ![Fábricas e canais de cliente](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Uma fábrica de canais cria canais.  
  
 Quando fechado, as fábricas de canal são responsáveis por fechar todos os canais criados que ainda não estão fechados. Observe que o modelo é assimétrico aqui porque, quando um ouvinte de canal é fechado, ele só para de aceitar novos canais, mas deixa os canais existentes abertos para que possam continuar recebendo mensagens.  
  
 O WCF fornece auxiliares de classe base para esse processo. (Para obter um diagrama das classes auxiliares de canal abordadas neste tópico, consulte [visão geral do modelo de canal](channel-model-overview.md).)  
  
- A <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 de [desenvolvimento de canais](developing-channels.md).  
  
- A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> o e o. A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.
  
- A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> consolida `OnCreateChannel` as `CreateChannel` sobrecargas em um método abstrato.
  
- A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Ele cuida do gerenciamento de estado básico. 
  
 A discussão a seguir se baseia no [transporte: Exemplo](../samples/transport-udp.md) de UDP.  
  
### <a name="creating-a-channel-factory"></a>Criando uma fábrica de canais  
 O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>. As substituições <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> de exemplo para fornecer acesso à versão de mensagem do codificador de mensagem. O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para subdividir nossa instância de <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída UDP  
 O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>. O Construtor valida os argumentos e constrói um objeto de destino <xref:System.Net.EndPoint> com base <xref:System.ServiceModel.EndpointAddress> no que é passado.  
  
 A substituição de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> cria um soquete que é usado para enviar mensagens para isso <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 O canal pode ser fechado de forma normal ou inadequada. Se o canal for fechado normalmente, o Soquete será fechado e uma chamada será feita ao método da `OnClose` classe base. Se isso lançar uma exceção, a infraestrutura chamará `Abort` para garantir que o canal seja limpo.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 `Send()` Implemente `BeginSend()`e ./ `EndSend()` Isso é dividido em duas seções principais. Primeiro, Serialize a mensagem em uma matriz de bytes:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, envie os dados resultantes na conexão:  
  
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

- [Desenvolvimento de canais](developing-channels.md)

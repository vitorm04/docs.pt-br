---
title: 'Serviço: Ouvintes de canal e canais'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 88bfdc879e4f3c7df6b2c4035c7ed7fdc2b4c41d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771444"
---
# <a name="service-channel-listeners-and-channels"></a>Serviço: Ouvintes de canal e canais

Há três categorias de objetos de canal: canais, ouvintes de canais e fábricas de canais. Os canais são a interface entre o aplicativo e a pilha de canais. Ouvintes de canais são responsáveis por criar canais no lado do recebimento (ou escuta), normalmente em resposta a uma nova mensagem de entrada ou a conexão. Fábricas de canais são responsáveis por criar canais no lado do envio para iniciar a comunicação com um ponto de extremidade.

## <a name="channel-listeners-and-channels"></a>Ouvintes de canal e canais

Ouvintes de canais responsáveis pela criação de canais e receber mensagens da camada abaixo ou da rede. As mensagens recebidas são entregues para a camada acima usando um canal que é criado pelo ouvinte de canais.

O diagrama a seguir ilustra o processo de recebimento de mensagens e entregá-los para a camada acima.

![Ouvintes de canais e canais](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Um ouvinte de canais recebendo mensagens e entregar para a camada acima por meio de canais.

O processo pode ser modelado conceitualmente como uma fila dentro de cada canal, embora a implementação, na verdade, não poderá usar uma fila. O ouvinte de canais é responsável por receber mensagens da camada abaixo ou a rede e colocá-las na fila. O canal é responsável por receber mensagens da fila e entregá-las para a camada acima quando essa camada pergunta para uma mensagem, por exemplo, chamando `Receive` no canal.

O WCF fornece auxiliares da classe base para esse processo. (Para um diagrama das classes de auxiliar de canal discutidas neste artigo, consulte [visão geral do modelo de canal](channel-model-overview.md).)

- O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [canais de desenvolvimento](developing-channels.md).

- O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.

- O <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida os `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstrato.

- O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Ele cuida do gerenciamento de estado básica.

A discussão a seguir baseia-se a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.

## <a name="creating-a-channel-listener"></a>Criando um ouvinte de canais

O `UdpChannelListener` que a amostra implementa deriva o <xref:System.ServiceModel.Channels.ChannelListenerBase> classe. Ele usa um único soquete UDP para receber datagramas. O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono. Os dados serem convertidos em mensagens usando a sistema de codificação de mensagem:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Como o mesmo canal de datagrama representa mensagens que chegam de várias fontes, o `UdpChannelListener` é um ouvinte de singleton. Não há no ativo a maioria dos <xref:System.ServiceModel.Channels.IChannel> associado com este ouvinte de cada vez. O exemplo gera outra somente se um canal que é retornado pelo <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> método subsequentemente é descartado. Quando uma mensagem é recebida, ele é enfileirado nesse canal de singleton.

### <a name="udpinputchannel"></a>UdpInputChannel

O `UdpInputChannel` classe implementa <xref:System.ServiceModel.Channels.IInputChannel>. Ele consiste em uma fila de mensagens de entrada que é preenchida pelo `UdpChannelListener`do soquete. Essas mensagens são removidas da fila pelo <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> método.

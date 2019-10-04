---
title: 'Serviço: Ouvintes de canal e canais'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 4367d844867db7fdad013e30d047f9385addbce5
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834795"
---
# <a name="service-channel-listeners-and-channels"></a>Serviço: Ouvintes de canal e canais

Há três categorias de objetos de canal: canais, ouvintes de canal e fábricas de canal. Os canais são a interface entre o aplicativo e a pilha de canais. Os ouvintes de canal são responsáveis por criar canais no lado de recebimento (ou escuta), normalmente em resposta a uma nova mensagem ou conexão de entrada. As fábricas de canal são responsáveis pela criação de canais no lado de envio para iniciar a comunicação com um ponto de extremidade.

## <a name="channel-listeners-and-channels"></a>Ouvintes de canal e canais

Os ouvintes de canal são responsáveis por criar canais e receber mensagens da camada abaixo ou da rede. As mensagens recebidas são entregues à camada acima usando um canal que é criado pelo ouvinte de canal.

O diagrama a seguir ilustra o processo de receber mensagens e fornecê-las à camada acima.

![Ouvintes de canal e canais](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Um ouvinte de canal recebendo mensagens e entregando à camada acima por meio de canais.

O processo pode ser modelado conceitualmente como uma fila dentro de cada canal, embora a implementação possa, na verdade, não usar uma fila. O ouvinte de canal é responsável por receber mensagens da camada abaixo ou da rede e colocá-las na fila. O canal é responsável por obter mensagens da fila e entregá-las à camada acima quando essa camada solicita uma mensagem, por exemplo, chamando `Receive` no canal.

O WCF fornece auxiliares de classe base para esse processo. Para obter um diagrama das classes auxiliares de canal abordadas neste artigo, consulte [visão geral do modelo de canal](channel-model-overview.md).

- A classe <xref:System.ServiceModel.Channels.CommunicationObject> implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [desenvolvimento de canais](developing-channels.md).

- A classe <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>. A classe <xref:System.ServiceModel.Channels.ChannelManagerBase> funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.

- A classe <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida as sobrecargas `CreateChannel` em um método abstrato `OnCreateChannel`.

- A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Ele cuida do gerenciamento de estado básico.

A discussão a seguir se baseia no [Transport: Exemplo](../samples/transport-udp.md) de UDP.

## <a name="creating-a-channel-listener"></a>Criando um ouvinte de canal

O `UdpChannelListener` que o exemplo implementa deriva da classe <xref:System.ServiceModel.Channels.ChannelListenerBase>. Ele usa um único soquete UDP para receber datagramas. O método `OnOpen` recebe dados usando o soquete UDP em um loop assíncrono. Os dados são então convertidos em mensagens usando o sistema de codificação de mensagens:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Como o mesmo canal de datagrama representa mensagens que chegam de um número de fontes, o `UdpChannelListener` é um ouvinte singleton. Há no máximo um <xref:System.ServiceModel.Channels.IChannel> ativo associado a esse ouvinte por vez. O exemplo gera outro somente se um canal retornado pelo método <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> for subsequentemente Descartado. Quando uma mensagem é recebida, ela é enfileirada nesse canal singleton.

### <a name="udpinputchannel"></a>UdpInputChannel

A `UdpInputChannel` classe implementa <xref:System.ServiceModel.Channels.IInputChannel>. Ele consiste em uma fila de mensagens de entrada que é preenchida pelo soquete do `UdpChannelListener`. Essas mensagens são removidas da fila pelo método <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A>.

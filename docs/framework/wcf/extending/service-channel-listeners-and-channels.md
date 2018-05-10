---
title: 'Serviço : ouvintes de canal e canais'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: eca7061243fa7f006079d19c3eaaf86ba906bca2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="service-channel-listeners-and-channels"></a>Serviço : ouvintes de canal e canais
Há três categorias de objetos de canal: canais, ouvintes de canais e fábricas de canais. Canais são a interface entre o aplicativo e a pilha de canais. Ouvintes de canais são responsáveis por criar canais no lado do recebimento (ou escutar), normalmente em resposta a uma nova mensagem de entrada ou a conexão. Fábricas de canais são responsáveis por criar canais no lado de envio para iniciar a comunicação com um ponto de extremidade.  
  
## <a name="channel-listeners-and-channels"></a>Canais e ouvintes de canais  
 Ouvintes de canais são responsáveis por criar canais e recebendo mensagens da camada abaixo ou da rede. As mensagens recebidas são entregues para a camada acima usando um canal que é criado pelo ouvinte de canal.  
  
 O diagrama a seguir ilustra o processo de recebimento de mensagens e entregá-los para a camada acima.  
  
 ![Ouvintes de canal e canais](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")  
Um ouvinte de canal recebendo mensagens e entregue para a camada superior por meio de canais.  
  
 O processo pode ser modelado conceitualmente como uma fila dentro de cada canal, embora a implementação, na verdade, não poderá usar uma fila. O ouvinte do canal é responsável por recebendo mensagens da camada abaixo ou a rede e colocá-los na fila. O canal é responsável por receber mensagens da fila e por entregá-los para a camada acima quando essa camada solicita uma mensagem, por exemplo, chamando `Receive` no canal.  
  
 O WCF fornece auxiliares da classe base para esse processo. (Para um diagrama de classes de auxiliar o canal discutidos neste tópico, consulte [visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.  
  
-   O '<xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida o `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstract.  
  
-   O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Cuida do gerenciamento de estado básica.  
  
 A discussão a seguir baseia-se a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
## <a name="creating-a-channel-listener"></a>Criar um ouvinte de canal  
 O ' UdpChannelListener que implementa o exemplo deriva o <xref:System.ServiceModel.Channels.ChannelListenerBase> classe. Ele usa um único soquete UDP para receber datagramas. O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono. Os dados são convertidos em mensagens usando a codificação de sistema de mensagens:  
  
```  
message = UdpConstants.MessageEncoder.ReadMessage(  
  new ArraySegment<byte>(buffer, 0, count),   
  bufferManager  
);  
```  
  
 Como o mesmo canal de datagrama representa mensagens que chegam de várias fontes, o `UdpChannelListener` um ouvinte de singleton. Há mais de um ativo <xref:System.ServiceModel.Channels.IChannel>' associado a este ouvinte de cada vez. O exemplo gera outra somente se um canal que é retornado pelo <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> método subsequentemente é descartado. Quando uma mensagem é recebida, ele é enfileirado para este canal de singleton.  
  
### <a name="udpinputchannel"></a>UdpInputChannel  
 O `UdpInputChannel` classe implementa <xref:System.ServiceModel.Channels.IInputChannel>. Ele consiste em uma fila de mensagens de entrada que é preenchida pelo `UdpChannelListener`do soquete. Essas mensagens são removidas da fila pelo <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> método.

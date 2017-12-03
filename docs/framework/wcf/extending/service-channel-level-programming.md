---
title: "Programação de nível por canal de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 718f3c8fd2d6ed3434f7231e3ccaf8cf1a663875
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="service-channel-level-programming"></a>Programação de nível por canal de serviço
Este tópico descreve como escrever um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo de serviço sem usar o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> e seu modelo de objeto associado.  
  
## <a name="receiving-messages"></a>Recebendo mensagens  
 Para estar pronto para receber e processar mensagens, são necessárias as seguintes etapas:  
  
1.  Crie uma associação.  
  
2.  Crie um ouvinte de canal.  
  
3.  Abra a escuta de canal.  
  
4.  Ler a solicitação e enviar uma resposta.  
  
5.  Feche todos os objetos de canal.  
  
#### <a name="creating-a-binding"></a>Criar uma associação  
 A primeira etapa na escutando e recebimento de mensagens está criando uma associação. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é fornecido com várias ligações internas ou fornecido pelo sistema que podem ser usados diretamente, criando um deles. Além disso, você também pode criar sua própria associação personalizada criando uma instância de uma classe CustomBinding que é o que faz o código na listagem 1.  
  
 O exemplo de código a seguir cria uma instância de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> e adiciona um <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sua coleção de elementos que é uma coleção de elementos que são usados para criar a pilha de canais de associação. Neste exemplo, porque a coleção de elementos tem apenas o <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, a pilha de canais resultante tem o canal de transporte HTTP.  
  
#### <a name="building-a-channellistener"></a>Criando ChannelListener  
 Depois de criar uma associação, podemos chamar <!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>--> `System.ServiceModel.Channels.Binding.BuildChannelListener` para criar o ouvinte de canal em que o parâmetro de tipo é a forma de canal para criar. Neste exemplo estamos usando <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> como queremos escutar mensagens de entrada em um padrão de troca de mensagem de solicitação/resposta.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel>é usado para receber mensagens e retornando mensagens de resposta de solicitação. Chamando <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> retorna um <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, que pode ser usado para receber a mensagem de solicitação e enviar uma mensagem de resposta de volta.  
  
 Ao criar o ouvinte, passamos o endereço de rede no qual ele escuta, nesse caso `http://localhost:8080/channelapp`. Em geral, cada canal de transporte dá suporte a uma ou possivelmente vários esquemas de endereço, por exemplo, o transporte HTTP dá suporte a esquemas http e https.  
  
 Também passamos vazio <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> ao criar o ouvinte. Um parâmetro de associação é um mecanismo para passar os parâmetros que controlam como o ouvinte deve ser criado. Em nosso exemplo, estamos não usando qualquer esses parâmetros para que podemos passar uma coleção vazia.  
  
#### <a name="listening-for-incoming-messages"></a>Escutar mensagens de entrada  
 Em seguida, chamamos <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> no ouvinte e aceitando os canais de início. O comportamento de <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> depende se o transporte é orientado a conexão ou sem conexão. Para os transportes orientado a conexão, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> bloqueia até que uma nova solicitação de conexão é fornecido no ponto em que ele retorna um novo canal que representa essa nova conexão. Para os transportes de conexão menor, como HTTP, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> retornará imediatamente com um e apenas o canal que cria o ouvinte de transporte.  
  
 Neste exemplo, o ouvinte retorna um canal que implemente <xref:System.ServiceModel.Channels.IReplyChannel>. Para receber de mensagens neste canal, primeira chamada <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> nele para colocá-lo em um estado pronto para comunicação. Em seguida, chamamos <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> quais blocos até que uma mensagem chega.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Ler a solicitação e enviar uma resposta  
 Quando <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> retorna um <xref:System.ServiceModel.Channels.RequestContext>, obtemos a mensagem recebida usando seu <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> propriedade. Podemos gravar o conteúdo da mensagem ação e o corpo, (que vamos supor que é uma cadeia de caracteres).  
  
 Para enviar uma resposta, criamos uma nova mensagem de resposta nesse caso transmitindo de volta os dados de cadeia de caracteres que é recebido na solicitação. Em seguida, chamamos <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> para enviar a mensagem de resposta.  
  
#### <a name="closing-objects"></a>Fechando objetos  
 Para evitar o vazamento de recursos, é muito importante fechar objetos usados nas comunicações quando eles não são mais necessários. Neste exemplo, podemos fechar a mensagem de solicitação, o contexto de solicitação, o canal e o ouvinte.  
  
 O exemplo de código a seguir mostra um serviço básico no qual um ouvinte de canal recebe apenas uma mensagem. Um serviço real mantém aceitando canais e receber mensagens até que o serviço será encerrado.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]

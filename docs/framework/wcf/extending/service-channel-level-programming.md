---
title: Programação de nível por canal de serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: e00b5ae2c72a4d4dcd2140e9c280d5bfda3531c2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197191"
---
# <a name="service-channel-level-programming"></a>Programação de nível por canal de serviço
Este tópico descreve como escrever um aplicativo de serviço do Windows Communication Foundation (WCF) sem usar o <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> e seu modelo de objeto associado.  
  
## <a name="receiving-messages"></a>Recebendo mensagens  
 Para estar pronto para receber e processar mensagens, as etapas a seguir são necessárias:  
  
1.  Crie uma associação.  
  
2.  Crie um ouvinte de canais.  
  
3.  Abra o ouvinte de canais.  
  
4.  Ler a solicitação e enviará uma resposta.  
  
5.  Feche todos os objetos de canal.  
  
#### <a name="creating-a-binding"></a>Criar uma associação  
 A primeira etapa na escutar e receber mensagens é criando uma associação. O WCF é fornecido com diversas ligações internas ou fornecido pelo sistema que podem ser usadas diretamente pela instanciação de um deles. Além disso, você também pode criar sua própria associação personalizado criando uma instância de uma classe CustomBinding que é o que faz o código na listagem 1.  
  
 O exemplo de código a seguir cria uma instância de <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> e adiciona um <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sua coleção de elementos que é uma coleção de elementos de associação que são usados para criar a pilha de canais. Neste exemplo, porque a coleção de elementos tem apenas o <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, a pilha de canais resultante tem o canal de transporte HTTP.  
  
#### <a name="building-a-channellistener"></a>Criando um ChannelListener  
 Depois de criar uma associação, podemos chamar <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> para criar o ouvinte de canais em que o parâmetro de tipo é a forma de canal para criar. Neste exemplo estamos usando <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> porque queremos ouvir mensagens de entrada em um padrão de troca de mensagem de solicitação/resposta.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> é usado para receber mensagens e enviar de volta de mensagens de resposta de solicitação. Chamando <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> retorna um <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, que pode ser usado para receber a mensagem de solicitação e enviar uma mensagem de resposta de volta.  
  
 Ao criar o ouvinte, passamos o endereço de rede na qual ele escuta, nesse caso, `http://localhost:8080/channelapp`. Em geral, cada canal de transporte dá suporte a uma ou, possivelmente, vários esquemas de endereço, por exemplo, o transporte HTTP dá suporte a esquemas http e https.  
  
 Também passamos um vazio <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> ao criar o ouvinte. Um parâmetro de associação é um mecanismo para passar parâmetros que controlam como o ouvinte deve ser criado. Em nosso exemplo, não estamos usando qualquer tais parâmetros. Portanto, podemos passar uma coleção vazia.  
  
#### <a name="listening-for-incoming-messages"></a>Escuta para mensagens de entrada  
 Em seguida, chamamos <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> no ouvinte e aceitar canais de início. O comportamento de <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> depende se o transporte é orientado a conexão ou sem conexão. Para transportes de conexão-oriented <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> bloqueia até que uma nova solicitação de conexão é fornecido no ponto em que ele retorna um novo canal que representa essa nova conexão. Para transportes de conexão menor, como HTTP, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> retornará imediatamente com o e apenas o canal que cria o ouvinte de transporte.  
  
 Neste exemplo, o ouvinte retorna um canal que implementa <xref:System.ServiceModel.Channels.IReplyChannel>. Para receber a mensagens sobre esse canal é primeira chamada <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> -la para colocá-lo em um estado pronto para comunicação. Em seguida, chamamos <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> quais blocos até que uma mensagem chega.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>A leitura da solicitação e enviar uma resposta  
 Quando <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> retorna um <xref:System.ServiceModel.Channels.RequestContext>, podemos obter a mensagem recebida usando seu <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> propriedade. Podemos gravar o conteúdo da mensagem ação e o corpo, (o que vamos supor que é uma cadeia de caracteres).  
  
 Para enviar uma resposta, podemos criar uma nova mensagem de resposta nesse caso, passando de volta os dados de cadeia de caracteres que recebemos na solicitação. Em seguida, chamamos <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> para enviar a mensagem de resposta.  
  
#### <a name="closing-objects"></a>Fechando objetos  
 Para evitar a perda de recursos, é muito importante fechar objetos usados nas comunicações quando eles não são mais necessários. Neste exemplo, vamos fechar a mensagem de solicitação, o contexto da solicitação, o canal e o ouvinte.  
  
 O exemplo de código a seguir mostra um serviço básico no qual um ouvinte de canais recebe apenas uma mensagem. Um serviço real mantém aceitar canais e receber mensagens até que o serviço seja encerrado.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]

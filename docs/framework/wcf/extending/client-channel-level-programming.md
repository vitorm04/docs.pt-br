---
title: Programação de nível de canal cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772577"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="e8373-102">Programação de nível de canal cliente</span><span class="sxs-lookup"><span data-stu-id="e8373-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="e8373-103">Este tópico descreve como escrever um aplicativo de cliente do Windows Communication Foundation (WCF) sem usar o <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> classe e seu modelo de objeto associado.</span><span class="sxs-lookup"><span data-stu-id="e8373-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="e8373-104">Envio de mensagens</span><span class="sxs-lookup"><span data-stu-id="e8373-104">Sending Messages</span></span>  
 <span data-ttu-id="e8373-105">Para estar pronto para enviar mensagens e receber e processar as respostas, são necessárias as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="e8373-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1. <span data-ttu-id="e8373-106">Crie uma associação.</span><span class="sxs-lookup"><span data-stu-id="e8373-106">Create a binding.</span></span>  
  
2. <span data-ttu-id="e8373-107">Crie uma fábrica de canais.</span><span class="sxs-lookup"><span data-stu-id="e8373-107">Build a channel factory.</span></span>  
  
3. <span data-ttu-id="e8373-108">Crie um canal.</span><span class="sxs-lookup"><span data-stu-id="e8373-108">Create a channel.</span></span>  
  
4. <span data-ttu-id="e8373-109">Envie uma solicitação e ler a resposta.</span><span class="sxs-lookup"><span data-stu-id="e8373-109">Send a request and read the reply.</span></span>  
  
5. <span data-ttu-id="e8373-110">Feche todos os objetos de canal.</span><span class="sxs-lookup"><span data-stu-id="e8373-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="e8373-111">Criar uma associação</span><span class="sxs-lookup"><span data-stu-id="e8373-111">Creating a Binding</span></span>  
 <span data-ttu-id="e8373-112">Semelhante ao caso de recebimento (consulte [programação de nível de serviço canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), enviando mensagens começa criando uma associação.</span><span class="sxs-lookup"><span data-stu-id="e8373-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="e8373-113">Este exemplo cria um novo <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> e adiciona um <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sua coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="e8373-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="e8373-114">Criação de uma ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="e8373-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="e8373-115">Em vez de criar uma <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, desta vez, criamos um <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> chamando <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na associação em que o parâmetro de tipo é <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8373-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e8373-116">Embora os ouvintes de canais sejam usados pelo lado que aguarda as mensagens de entrada, fábricas de canais são usadas pelo lado que inicia a comunicação para criar um canal.</span><span class="sxs-lookup"><span data-stu-id="e8373-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="e8373-117">Assim como os ouvintes de canais, fábricas de canais devem ser abertas pela primeira vez antes que possam ser usados.</span><span class="sxs-lookup"><span data-stu-id="e8373-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="e8373-118">Criação de um canal</span><span class="sxs-lookup"><span data-stu-id="e8373-118">Creating a Channel</span></span>  
 <span data-ttu-id="e8373-119">Em seguida, chamamos <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> para criar um <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="e8373-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="e8373-120">Essa chamada usa o endereço do ponto de extremidade com a qual queremos para se comunicar usando o novo canal que está sendo criado.</span><span class="sxs-lookup"><span data-stu-id="e8373-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="e8373-121">Assim que tivermos um canal, chamamos Open-la para colocá-lo em um estado pronto para comunicação.</span><span class="sxs-lookup"><span data-stu-id="e8373-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="e8373-122">Dependendo da natureza do transporte, essa chamada para Open pode iniciar uma conexão com o ponto de extremidade de destino ou pode não fazer nada em todos os na rede.</span><span class="sxs-lookup"><span data-stu-id="e8373-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="e8373-123">Enviar uma solicitação e ler a resposta</span><span class="sxs-lookup"><span data-stu-id="e8373-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="e8373-124">Assim que tivermos um canal aberto, podemos criar uma mensagem e use o método de solicitação do canal para enviar a solicitação e esperar a resposta antes de voltar.</span><span class="sxs-lookup"><span data-stu-id="e8373-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="e8373-125">Quando este método retorna, temos uma mensagem de resposta que podemos ler para descobrir qual foi a resposta do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="e8373-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="e8373-126">Fechando objetos</span><span class="sxs-lookup"><span data-stu-id="e8373-126">Closing Objects</span></span>  
 <span data-ttu-id="e8373-127">Para evitar a perda de recursos, vamos fechar objetos usados nas comunicações quando eles não são mais necessários.</span><span class="sxs-lookup"><span data-stu-id="e8373-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="e8373-128">O exemplo de código a seguir mostra um cliente básico usando a fábrica de canais para enviar uma mensagem e ler a resposta.</span><span class="sxs-lookup"><span data-stu-id="e8373-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]

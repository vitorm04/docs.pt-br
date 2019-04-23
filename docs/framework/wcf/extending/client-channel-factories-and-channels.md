---
title: 'Cliente: fábricas de canais e canais'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: bfa5d2478d5c12f16c2d9531de02e1c868eab560
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166251"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="78f0d-102">Cliente: fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="78f0d-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="78f0d-103">Este tópico aborda a criação de fábricas de canais e canais.</span><span class="sxs-lookup"><span data-stu-id="78f0d-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="78f0d-104">fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="78f0d-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="78f0d-105">Fábricas de canais são responsáveis por criar canais.</span><span class="sxs-lookup"><span data-stu-id="78f0d-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="78f0d-106">Canais criados por fábricas de canais são usados para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="78f0d-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="78f0d-107">Esses canais são responsáveis por recebendo a mensagem da camada acima, executar o processamento que for necessário, em seguida, enviar a mensagem para a camada abaixo.</span><span class="sxs-lookup"><span data-stu-id="78f0d-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="78f0d-108">O gráfico a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="78f0d-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="78f0d-109">![Canais e fábricas de cliente](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="78f0d-109">![Client Factories and Channels](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="78f0d-110">Uma fábrica de canais cria canais.</span><span class="sxs-lookup"><span data-stu-id="78f0d-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="78f0d-111">Quando fechado, fábricas de canais são responsáveis por quaisquer canais criados por eles que ainda não foram fechados de fechamento.</span><span class="sxs-lookup"><span data-stu-id="78f0d-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="78f0d-112">Observe que o modelo é assimétrico aqui porque quando um ouvinte de canais é fechado, ela só para de aceitar novos canais, mas deixa os canais existentes aberto para que eles possam continuar a receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="78f0d-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="78f0d-113">O WCF fornece auxiliares da classe base para esse processo.</span><span class="sxs-lookup"><span data-stu-id="78f0d-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="78f0d-114">(Para um diagrama das classes de auxiliar de canal discutidos neste tópico, consulte [visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="78f0d-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).)</span></span>  
  
-   <span data-ttu-id="78f0d-115">O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 do [canais de desenvolvimento](../../../../docs/framework/wcf/extending/developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="78f0d-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md).</span></span>  
  
-   <span data-ttu-id="78f0d-116">O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> e <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78f0d-117">O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
-   <span data-ttu-id="78f0d-118">O <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida os `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstrato.</span><span class="sxs-lookup"><span data-stu-id="78f0d-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
-   <span data-ttu-id="78f0d-119">O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="78f0d-120">Ele cuida do gerenciamento de estado básica.</span><span class="sxs-lookup"><span data-stu-id="78f0d-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="78f0d-121">A discussão a seguir baseia-se a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="78f0d-121">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="78f0d-122">Criando uma fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="78f0d-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="78f0d-123">O `UdpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="78f0d-124">O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso à versão de mensagem do codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="78f0d-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="78f0d-125">O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> subdividir nossa instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="78f0d-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="78f0d-126">O canal de saída UDP</span><span class="sxs-lookup"><span data-stu-id="78f0d-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="78f0d-127">O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="78f0d-128">O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.</span><span class="sxs-lookup"><span data-stu-id="78f0d-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="78f0d-129">A substituição de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> cria um soquete que é usado para enviar mensagens para isso <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="78f0d-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="78f0d-130">O canal pode ser fechado normalmente ou de maneira brusca.</span><span class="sxs-lookup"><span data-stu-id="78f0d-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="78f0d-131">Se o canal seja fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método.</span><span class="sxs-lookup"><span data-stu-id="78f0d-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="78f0d-132">Se isso gerar uma exceção, a infraestrutura chame `Abort` garantir que o canal é limpa.</span><span class="sxs-lookup"><span data-stu-id="78f0d-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="78f0d-133">Implemente `Send()` e `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="78f0d-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="78f0d-134">Isso se divide em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="78f0d-134">This breaks down into two main sections.</span></span> <span data-ttu-id="78f0d-135">Primeiro, serialize a mensagem em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="78f0d-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="78f0d-136">Em seguida, envie os dados resultantes durante a transmissão:</span><span class="sxs-lookup"><span data-stu-id="78f0d-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="78f0d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78f0d-137">See also</span></span>

- [<span data-ttu-id="78f0d-138">Desenvolvimento de canais</span><span class="sxs-lookup"><span data-stu-id="78f0d-138">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)

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
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="cbfaa-102">Cliente: fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="cbfaa-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="cbfaa-103">Este tema discute a criação de fábricas de canais e canais.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="cbfaa-104">fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="cbfaa-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="cbfaa-105">As fábricas de canais são responsáveis pela criação de canais.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="cbfaa-106">Canais criados por fábricas de canais são usados para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="cbfaa-107">Esses canais são responsáveis por obter a mensagem da camada acima, realizar qualquer processamento necessário e, em seguida, enviar a mensagem para a camada abaixo.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="cbfaa-108">O gráfico a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="cbfaa-109">![Fábricas de cliente e canais](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="cbfaa-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="cbfaa-110">Uma fábrica de canais cria canais.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="cbfaa-111">Quando fechadas, as fábricas de canais são responsáveis pelo fechamento de todos os canais que criaram que ainda não estão fechados.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="cbfaa-112">Note que o modelo é assimétrico aqui porque quando um ouvinte de canal é fechado, ele só deixa de aceitar novos canais, mas deixa os canais existentes abertos para que eles possam continuar recebendo mensagens.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="cbfaa-113">O WCF fornece ajudantes de classe base para este processo.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="cbfaa-114">(Para obter um diagrama das classes de auxiliares de canal discutidas neste tópico, consulte [Visão geral do modelo](channel-model-overview.md)do canal .)</span><span class="sxs-lookup"><span data-stu-id="cbfaa-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="cbfaa-115">A <xref:System.ServiceModel.Channels.CommunicationObject> classe <xref:System.ServiceModel.ICommunicationObject> implementa e impõe a máquina estatal descrita na etapa 2 do [Desenvolvimento de Canais](developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="cbfaa-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="cbfaa-116">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe <xref:System.ServiceModel.Channels.CommunicationObject> implementa e fornece <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> uma <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>classe de base unificada para e .</span><span class="sxs-lookup"><span data-stu-id="cbfaa-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbfaa-117">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe trabalha <xref:System.ServiceModel.Channels.ChannelBase>em conjunto com , que <xref:System.ServiceModel.Channels.IChannel>é uma classe de base que implementa .</span><span class="sxs-lookup"><span data-stu-id="cbfaa-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="cbfaa-118">A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa e <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` consolida as `OnCreateChannel` sobrecargas em um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="cbfaa-119">A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe <xref:System.ServiceModel.Channels.IChannelListener>implementa.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="cbfaa-120">Cuida da gestão básica do Estado.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="cbfaa-121">A seguinte discussão baseia-se na amostra [Transporte: UDP.](../samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="cbfaa-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="cbfaa-122">Criando uma fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="cbfaa-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="cbfaa-123">O `UdpChannelFactory` derivado <xref:System.ServiceModel.Channels.ChannelFactoryBase>de .</span><span class="sxs-lookup"><span data-stu-id="cbfaa-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="cbfaa-124">A amostra <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> substitui-se para fornecer acesso à versão da mensagem do codificador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="cbfaa-125">A amostra também <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> se sobrepõe <xref:System.ServiceModel.Channels.BufferManager> para derrubar nossa instância de quando a máquina do estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="cbfaa-126">O canal de saída do UDP</span><span class="sxs-lookup"><span data-stu-id="cbfaa-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="cbfaa-127">Os `UdpOutputChannel` implementos. <xref:System.ServiceModel.Channels.IOutputChannel></span><span class="sxs-lookup"><span data-stu-id="cbfaa-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="cbfaa-128">O construtor valida os argumentos e <xref:System.Net.EndPoint> constrói um <xref:System.ServiceModel.EndpointAddress> objeto de destino com base no que é passado.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="cbfaa-129">A substituição <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> de cria um soquete que <xref:System.Net.EndPoint>é usado para enviar mensagens para isso .</span><span class="sxs-lookup"><span data-stu-id="cbfaa-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="cbfaa-130">O canal pode ser fechado graciosamente ou sem graça.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="cbfaa-131">Se o canal estiver fechado graciosamente, o soquete `OnClose` é fechado e uma chamada é feita para o método de classe base.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="cbfaa-132">Se isso abrir uma exceção, a infra-estrutura liga `Abort` para garantir que o canal seja limpo.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="cbfaa-133">Implementar `Send()` `BeginSend()` / `EndSend()`e .</span><span class="sxs-lookup"><span data-stu-id="cbfaa-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="cbfaa-134">Isso se divide em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="cbfaa-134">This breaks down into two main sections.</span></span> <span data-ttu-id="cbfaa-135">Primeiro serialize a mensagem em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="cbfaa-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="cbfaa-136">Em seguida, envie os dados resultantes no fio:</span><span class="sxs-lookup"><span data-stu-id="cbfaa-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbfaa-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="cbfaa-137">See also</span></span>

- [<span data-ttu-id="cbfaa-138">Desenvolvimento de canais</span><span class="sxs-lookup"><span data-stu-id="cbfaa-138">Developing Channels</span></span>](developing-channels.md)

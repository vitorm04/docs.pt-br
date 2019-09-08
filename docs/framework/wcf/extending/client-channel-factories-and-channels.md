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
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="1fd4e-102">Cliente: fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="1fd4e-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="1fd4e-103">Este tópico discute a criação de fábricas de canais e canais.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="1fd4e-104">fábricas de canais e canais</span><span class="sxs-lookup"><span data-stu-id="1fd4e-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="1fd4e-105">As fábricas de canal são responsáveis pela criação de canais.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="1fd4e-106">Os canais criados por fábricas de canal são usados para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="1fd4e-107">Esses canais são responsáveis por obter a mensagem da camada acima, executar qualquer processamento necessário e, em seguida, enviar a mensagem para a camada abaixo.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="1fd4e-108">O gráfico a seguir ilustra esse processo.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="1fd4e-109">![Fábricas e canais de cliente](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="1fd4e-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="1fd4e-110">Uma fábrica de canais cria canais.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="1fd4e-111">Quando fechado, as fábricas de canal são responsáveis por fechar todos os canais criados que ainda não estão fechados.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="1fd4e-112">Observe que o modelo é assimétrico aqui porque, quando um ouvinte de canal é fechado, ele só para de aceitar novos canais, mas deixa os canais existentes abertos para que possam continuar recebendo mensagens.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="1fd4e-113">O WCF fornece auxiliares de classe base para esse processo.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="1fd4e-114">(Para obter um diagrama das classes auxiliares de canal abordadas neste tópico, consulte [visão geral do modelo de canal](channel-model-overview.md).)</span><span class="sxs-lookup"><span data-stu-id="1fd4e-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="1fd4e-115">A <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita na etapa 2 de [desenvolvimento de canais](developing-channels.md).</span><span class="sxs-lookup"><span data-stu-id="1fd4e-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="1fd4e-116">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>para <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> o e o.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1fd4e-117">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="1fd4e-118">A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> consolida `OnCreateChannel` as `CreateChannel` sobrecargas em um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="1fd4e-119">A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="1fd4e-120">Ele cuida do gerenciamento de estado básico.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-120">It takes care of basic state management.</span></span> 
  
 <span data-ttu-id="1fd4e-121">A discussão a seguir se baseia no [transporte: Exemplo](../samples/transport-udp.md) de UDP.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="1fd4e-122">Criando uma fábrica de canais</span><span class="sxs-lookup"><span data-stu-id="1fd4e-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="1fd4e-123">O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="1fd4e-124">As substituições <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> de exemplo para fornecer acesso à versão de mensagem do codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="1fd4e-125">O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para subdividir nossa instância de <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="1fd4e-126">O canal de saída UDP</span><span class="sxs-lookup"><span data-stu-id="1fd4e-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="1fd4e-127">O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="1fd4e-128">O Construtor valida os argumentos e constrói um objeto de destino <xref:System.Net.EndPoint> com base <xref:System.ServiceModel.EndpointAddress> no que é passado.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="1fd4e-129">A substituição de <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> cria um soquete que é usado para enviar mensagens para isso <xref:System.Net.EndPoint>.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="1fd4e-130">O canal pode ser fechado de forma normal ou inadequada.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="1fd4e-131">Se o canal for fechado normalmente, o Soquete será fechado e uma chamada será feita ao método da `OnClose` classe base.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="1fd4e-132">Se isso lançar uma exceção, a infraestrutura chamará `Abort` para garantir que o canal seja limpo.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="1fd4e-133">`Send()` Implemente `BeginSend()`e ./ `EndSend()`</span><span class="sxs-lookup"><span data-stu-id="1fd4e-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="1fd4e-134">Isso é dividido em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="1fd4e-134">This breaks down into two main sections.</span></span> <span data-ttu-id="1fd4e-135">Primeiro, Serialize a mensagem em uma matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="1fd4e-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="1fd4e-136">Em seguida, envie os dados resultantes na conexão:</span><span class="sxs-lookup"><span data-stu-id="1fd4e-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fd4e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fd4e-137">See also</span></span>

- [<span data-ttu-id="1fd4e-138">Desenvolvimento de canais</span><span class="sxs-lookup"><span data-stu-id="1fd4e-138">Developing Channels</span></span>](developing-channels.md)

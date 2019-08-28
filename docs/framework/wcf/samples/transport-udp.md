---
title: 'Transporte: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 051b5d6c7a1fc5d110016be9faf9b08653c28a6e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045440"
---
# <a name="transport-udp"></a><span data-ttu-id="15013-102">Transporte: UDP</span><span class="sxs-lookup"><span data-stu-id="15013-102">Transport: UDP</span></span>
<span data-ttu-id="15013-103">O exemplo de transporte UDP demonstra como implementar UDP unicast e multicast como um transporte de Windows Communication Foundation (WCF) personalizado.</span><span class="sxs-lookup"><span data-stu-id="15013-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="15013-104">O exemplo descreve o procedimento recomendado para criar um transporte personalizado no WCF, usando a estrutura de canal e as práticas recomendadas do WCF a seguir.</span><span class="sxs-lookup"><span data-stu-id="15013-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="15013-105">As etapas para criar um transporte personalizado são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="15013-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="15013-106">Decida qual dos padrões de [troca de mensagens](#MessageExchangePatterns) do canal (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) a ChannelFactory e a ChannelListener terão suporte.</span><span class="sxs-lookup"><span data-stu-id="15013-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="15013-107">Em seguida, decida se você dará suporte às variações de sessão dessas interfaces.</span><span class="sxs-lookup"><span data-stu-id="15013-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="15013-108">Crie uma fábrica de canais e um ouvinte que ofereçam suporte ao seu padrão de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="15013-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="15013-109">Certifique-se de que qualquer exceção específica de rede seja normalizada para a classe <xref:System.ServiceModel.CommunicationException>derivada apropriada do.</span><span class="sxs-lookup"><span data-stu-id="15013-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="15013-110">Adicione um [ \<](../../../../docs/framework/misc/binding.md) elemento de > de associação que adiciona o transporte personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="15013-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="15013-111">Para obter mais informações, consulte [adicionando um elemento de associação](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="15013-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="15013-112">Adicione uma seção de extensão de elemento de associação para expor o novo elemento de associação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="15013-113">Adicione extensões de metadados para comunicar recursos a outros pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="15013-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="15013-114">Adicione uma associação que predefine uma pilha de elementos de associação de acordo com um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="15013-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="15013-115">Para obter mais informações, consulte [adicionando uma associação padrão](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="15013-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="15013-116">Adicione uma seção de associação e um elemento de configuração de associação para expor a associação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="15013-117">Para obter mais informações, consulte [adicionando suporte à configuração](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="15013-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="15013-118">Padrões de troca de mensagens</span><span class="sxs-lookup"><span data-stu-id="15013-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="15013-119">A primeira etapa na gravação de um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte.</span><span class="sxs-lookup"><span data-stu-id="15013-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="15013-120">Há três MEPs de escolha:</span><span class="sxs-lookup"><span data-stu-id="15013-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="15013-121">Datagrama (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="15013-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="15013-122">Ao usar um dataMEP de datagrama, um cliente envia uma mensagem usando uma troca "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="15013-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="15013-123">Um incêndio e esquecido o Exchange é um que requer a confirmação fora de banda da entrega bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="15013-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="15013-124">A mensagem pode ser perdida em trânsito e nunca alcançar o serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="15013-125">Se a operação de envio for concluída com êxito na extremidade do cliente, ela não garante que o ponto de extremidade remoto tenha recebido a mensagem.</span><span class="sxs-lookup"><span data-stu-id="15013-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="15013-126">O datagrama é um bloco de construção fundamental para mensagens, pois você pode criar seus próprios protocolos sobre ele, incluindo protocolos confiáveis e protocolos seguros.</span><span class="sxs-lookup"><span data-stu-id="15013-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="15013-127">Canais de datagrama de <xref:System.ServiceModel.Channels.IOutputChannel> cliente implementam a interface e os <xref:System.ServiceModel.Channels.IInputChannel> canais de datagrama de serviço implementam a interface.</span><span class="sxs-lookup"><span data-stu-id="15013-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="15013-128">Solicitação-resposta (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="15013-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="15013-129">Neste MEP, uma mensagem é enviada e uma resposta é recebida.</span><span class="sxs-lookup"><span data-stu-id="15013-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="15013-130">O padrão consiste em pares de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="15013-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="15013-131">Exemplos de chamadas de solicitação-resposta são RPC (chamadas de procedimento remoto) e o navegador obtém.</span><span class="sxs-lookup"><span data-stu-id="15013-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="15013-132">Esse padrão também é conhecido como Half-duplex.</span><span class="sxs-lookup"><span data-stu-id="15013-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="15013-133">Neste MEP, os canais de cliente <xref:System.ServiceModel.Channels.IRequestChannel> implementam o e <xref:System.ServiceModel.Channels.IReplyChannel>os canais de serviço implementam.</span><span class="sxs-lookup"><span data-stu-id="15013-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="15013-134">Duplex (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="15013-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="15013-135">O MEP duplex permite que um número arbitrário de mensagens seja enviado por um cliente e recebido em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="15013-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="15013-136">O duplex MEP é como uma conversa telefônica, onde cada palavra que está sendo falada é uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="15013-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="15013-137">Como ambos os lados podem enviar e receber neste MEP, a interface implementada pelos canais de cliente e de <xref:System.ServiceModel.Channels.IDuplexChannel>serviço é.</span><span class="sxs-lookup"><span data-stu-id="15013-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="15013-138">Cada um desses MEPs também pode dar suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="15013-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="15013-139">A funcionalidade adicionada fornecida por um canal com reconhecimento de sessão é que ela correlaciona todas as mensagens enviadas e recebidas em um canal.</span><span class="sxs-lookup"><span data-stu-id="15013-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="15013-140">O padrão de solicitação-resposta é uma sessão autônoma de duas mensagens, pois a solicitação e a resposta são correlacionadas.</span><span class="sxs-lookup"><span data-stu-id="15013-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="15013-141">Por outro lado, o padrão de solicitação-resposta que dá suporte a sessões implica que todos os pares de solicitação/resposta nesse canal estão correlacionados entre si.</span><span class="sxs-lookup"><span data-stu-id="15013-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="15013-142">Isso oferece um total de seis MEPs – datagrama, solicitação-resposta, duplex, datagrama com sessões, solicitação-resposta com sessões e duplex com sessões – para escolher.</span><span class="sxs-lookup"><span data-stu-id="15013-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15013-143">Para o transporte UDP, o único MEP com suporte é datagrama, porque o UDP é inerentemente a um protocolo "Fire and esqueça".</span><span class="sxs-lookup"><span data-stu-id="15013-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="15013-144">O ICommunicationObject e o ciclo de vida do objeto do WCF</span><span class="sxs-lookup"><span data-stu-id="15013-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="15013-145">O WCF tem um computador de Estado comum que é usado para gerenciar o ciclo de <xref:System.ServiceModel.Channels.IChannel>vida <xref:System.ServiceModel.Channels.IChannelFactory>de objetos <xref:System.ServiceModel.Channels.IChannelListener> como, e que são usados para comunicação.</span><span class="sxs-lookup"><span data-stu-id="15013-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="15013-146">Há cinco Estados em que esses objetos de comunicação podem existir.</span><span class="sxs-lookup"><span data-stu-id="15013-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="15013-147">Esses Estados são representados pela <xref:System.ServiceModel.CommunicationState> enumeração e são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="15013-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="15013-148">Criação Esse é o estado de um <xref:System.ServiceModel.ICommunicationObject> quando ele é instanciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="15013-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="15013-149">Nenhuma e/s (entrada/saída) ocorre nesse estado.</span><span class="sxs-lookup"><span data-stu-id="15013-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="15013-150">Inaugura A transição de objetos para esse <xref:System.ServiceModel.ICommunicationObject.Open%2A> estado quando é chamado.</span><span class="sxs-lookup"><span data-stu-id="15013-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="15013-151">Neste ponto, as propriedades se tornam imutáveis e a entrada/saída pode começar.</span><span class="sxs-lookup"><span data-stu-id="15013-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="15013-152">Essa transição é válida somente a partir do estado criado.</span><span class="sxs-lookup"><span data-stu-id="15013-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="15013-153">Feito Os objetos são transferidos para esse estado quando o processo aberto é concluído.</span><span class="sxs-lookup"><span data-stu-id="15013-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="15013-154">Essa transição é válida somente a partir do estado de abertura.</span><span class="sxs-lookup"><span data-stu-id="15013-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="15013-155">Neste ponto, o objeto é totalmente utilizável para transferência.</span><span class="sxs-lookup"><span data-stu-id="15013-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="15013-156">Incluindo A transição de objetos para esse <xref:System.ServiceModel.ICommunicationObject.Close%2A> estado quando é chamado para um desligamento normal.</span><span class="sxs-lookup"><span data-stu-id="15013-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="15013-157">Essa transição é válida somente a partir do estado aberto.</span><span class="sxs-lookup"><span data-stu-id="15013-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="15013-158">Legenda Os objetos de estado fechado não são mais utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="15013-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="15013-159">Em geral, a maioria das configurações ainda é acessível para inspeção, mas nenhuma comunicação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="15013-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="15013-160">Esse estado é equivalente a ser Descartado.</span><span class="sxs-lookup"><span data-stu-id="15013-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="15013-161">Com falha No estado com falha, os objetos são acessíveis para inspeção, mas não podem mais ser usados.</span><span class="sxs-lookup"><span data-stu-id="15013-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="15013-162">Quando ocorre um erro não recuperável, o objeto faz a transição para esse estado.</span><span class="sxs-lookup"><span data-stu-id="15013-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="15013-163">A única transição válida desse Estado está no `Closed` estado.</span><span class="sxs-lookup"><span data-stu-id="15013-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="15013-164">Há eventos que são acionados para cada transição de estado.</span><span class="sxs-lookup"><span data-stu-id="15013-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="15013-165">O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento e faz com que o objeto faça a transição imediatamente do seu estado atual para o estado fechado.</span><span class="sxs-lookup"><span data-stu-id="15013-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="15013-166">Chamar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> encerra qualquer trabalho não concluído.</span><span class="sxs-lookup"><span data-stu-id="15013-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="15013-167">Fábrica de canais e ouvinte de canal</span><span class="sxs-lookup"><span data-stu-id="15013-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="15013-168">A próxima etapa na gravação de um transporte personalizado é criar uma implementação do <xref:System.ServiceModel.Channels.IChannelFactory> para canais de cliente e <xref:System.ServiceModel.Channels.IChannelListener> do para canais de serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="15013-169">A camada de canal usa um padrão de fábrica para construir canais.</span><span class="sxs-lookup"><span data-stu-id="15013-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="15013-170">O WCF fornece auxiliares de classe base para esse processo.</span><span class="sxs-lookup"><span data-stu-id="15013-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="15013-171">A <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita anteriormente na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="15013-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

- <span data-ttu-id="15013-172">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada <xref:System.ServiceModel.Channels.ChannelListenerBase>para <xref:System.ServiceModel.Channels.ChannelFactoryBase> o e o.</span><span class="sxs-lookup"><span data-stu-id="15013-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="15013-173">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="15013-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="15013-174">A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> consolida `OnCreateChannel` as `CreateChannel` sobrecargas em um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="15013-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="15013-175">A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="15013-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="15013-176">Ele cuida do gerenciamento de estado básico.</span><span class="sxs-lookup"><span data-stu-id="15013-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="15013-177">Neste exemplo, a implementação de fábrica está contida em UdpChannelFactory.cs e a implementação do ouvinte está contida em UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="15013-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="15013-178">As <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="15013-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="15013-179">A fábrica de canais UDP</span><span class="sxs-lookup"><span data-stu-id="15013-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="15013-180">O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="15013-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="15013-181">As substituições <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> de exemplo para fornecer acesso à versão de mensagem do codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="15013-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="15013-182">O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para que possamos subdividir nossa instância de <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="15013-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="15013-183">O canal de saída UDP</span><span class="sxs-lookup"><span data-stu-id="15013-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="15013-184">O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="15013-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="15013-185">O Construtor valida os argumentos e constrói um objeto de destino <xref:System.Net.EndPoint> com base <xref:System.ServiceModel.EndpointAddress> no que é passado.</span><span class="sxs-lookup"><span data-stu-id="15013-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="15013-186">O canal pode ser fechado de forma normal ou inadequada.</span><span class="sxs-lookup"><span data-stu-id="15013-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="15013-187">Se o canal for fechado normalmente, o Soquete será fechado e uma chamada será feita ao método da `OnClose` classe base.</span><span class="sxs-lookup"><span data-stu-id="15013-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="15013-188">Se isso lançar uma exceção, a infraestrutura chamará `Abort` para garantir que o canal seja limpo.</span><span class="sxs-lookup"><span data-stu-id="15013-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="15013-189">Em seguida, `Send()` implementamos e / `BeginSend()`. `EndSend()`</span><span class="sxs-lookup"><span data-stu-id="15013-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="15013-190">Isso é dividido em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="15013-190">This breaks down into two main sections.</span></span> <span data-ttu-id="15013-191">Primeiro, nós serializamos a mensagem em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="15013-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="15013-192">Em seguida, enviamos os dados resultantes na conexão.</span><span class="sxs-lookup"><span data-stu-id="15013-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="15013-193">O UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="15013-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="15013-194">O `UdpChannelListener` que o exemplo implementa deriva <xref:System.ServiceModel.Channels.ChannelListenerBase> da classe.</span><span class="sxs-lookup"><span data-stu-id="15013-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="15013-195">Ele usa um único soquete UDP para receber datagramas.</span><span class="sxs-lookup"><span data-stu-id="15013-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="15013-196">O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono.</span><span class="sxs-lookup"><span data-stu-id="15013-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="15013-197">Os dados são então convertidos em mensagens usando a estrutura de codificação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="15013-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="15013-198">Como o mesmo canal de datagrama representa mensagens que chegam de um número de fontes `UdpChannelListener` , o é um ouvinte singleton.</span><span class="sxs-lookup"><span data-stu-id="15013-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="15013-199">Há, no máximo, um ativo <xref:System.ServiceModel.Channels.IChannel> associado a esse ouvinte por vez.</span><span class="sxs-lookup"><span data-stu-id="15013-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="15013-200">O exemplo gera outro somente se um canal retornado pelo `AcceptChannel` método for descartado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="15013-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="15013-201">Quando uma mensagem é recebida, ela é enfileirada nesse canal singleton.</span><span class="sxs-lookup"><span data-stu-id="15013-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="15013-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="15013-202">UdpInputChannel</span></span>  
 <span data-ttu-id="15013-203">A `UdpInputChannel` classe implementa `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="15013-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="15013-204">Ele consiste em uma fila de mensagens de entrada que é preenchida `UdpChannelListener`pelo soquete do.</span><span class="sxs-lookup"><span data-stu-id="15013-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="15013-205">Essas mensagens são removidas da `IInputChannel.Receive` fila pelo método.</span><span class="sxs-lookup"><span data-stu-id="15013-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="15013-206">Adicionando um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="15013-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="15013-207">Agora que as fábricas e os canais são criados, devemos expô-los ao tempo de execução de ServiceModel por meio de uma associação.</span><span class="sxs-lookup"><span data-stu-id="15013-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="15013-208">Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada a um endereço de serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="15013-209">Cada elemento na pilha é representado por um [ \<](../../../../docs/framework/misc/binding.md) elemento de > de associação.</span><span class="sxs-lookup"><span data-stu-id="15013-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="15013-210">No exemplo, o elemento de associação é `UdpTransportBindingElement`, que deriva de. <xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="15013-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="15013-211">Ele substitui os métodos a seguir para criar as fábricas associadas à nossa associação.</span><span class="sxs-lookup"><span data-stu-id="15013-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="15013-212">Ele também contém membros para clonar `BindingElement` e retornar nosso esquema (SOAP. UDP).</span><span class="sxs-lookup"><span data-stu-id="15013-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="15013-213">Adicionando suporte de metadados para um elemento de associação de transporte</span><span class="sxs-lookup"><span data-stu-id="15013-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="15013-214">Para integrar nosso transporte ao sistema de metadados, devemos dar suporte à importação e à exportação da política.</span><span class="sxs-lookup"><span data-stu-id="15013-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="15013-215">Isso nos permite gerar clientes de nossa ligação por meio da [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15013-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="15013-216">Adicionando suporte a WSDL</span><span class="sxs-lookup"><span data-stu-id="15013-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="15013-217">O elemento de associação de transporte em uma associação é responsável por exportar e importar informações de endereçamento nos metadados.</span><span class="sxs-lookup"><span data-stu-id="15013-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="15013-218">Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados.</span><span class="sxs-lookup"><span data-stu-id="15013-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="15013-219">Exportação de WSDL</span><span class="sxs-lookup"><span data-stu-id="15013-219">WSDL Export</span></span>  
 <span data-ttu-id="15013-220">Para exportar informações de endereçamento, `IWsdlExportExtension` o `UdpTransportBindingElement` implementa a interface.</span><span class="sxs-lookup"><span data-stu-id="15013-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="15013-221">O `ExportEndpoint` método adiciona as informações de endereçamento corretas à porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="15013-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="15013-222">A `UdpTransportBindingElement` implementação`ExportEndpoint` do método também exporta um URI de transporte quando o ponto de extremidade usa uma associação SOAP.</span><span class="sxs-lookup"><span data-stu-id="15013-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="15013-223">Importação de WSDL</span><span class="sxs-lookup"><span data-stu-id="15013-223">WSDL Import</span></span>  
 <span data-ttu-id="15013-224">Para estender o sistema de importação WSDL para lidar com a importação dos endereços, devemos adicionar a configuração a seguir ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="15013-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="15013-225">Ao executar svcutil. exe, há duas opções para obter svcutil. exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="15013-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="15013-226">Aponte para o SvcUtil. exe para nosso arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.</span><span class="sxs-lookup"><span data-stu-id="15013-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="15013-227">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="15013-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="15013-228">O `UdpBindingElementImporter` tipo implementa a `IWsdlImportExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="15013-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="15013-229">O `ImportEndpoint` método importa o endereço da porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="15013-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="15013-230">Adicionando suporte à política</span><span class="sxs-lookup"><span data-stu-id="15013-230">Adding Policy Support</span></span>  
 <span data-ttu-id="15013-231">O elemento de associação personalizado pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="15013-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="15013-232">Exportação de política</span><span class="sxs-lookup"><span data-stu-id="15013-232">Policy Export</span></span>  
 <span data-ttu-id="15013-233">O `UdpTransportBindingElement` tipo implementa `IPolicyExportExtension` para adicionar suporte para exportar a política.</span><span class="sxs-lookup"><span data-stu-id="15013-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="15013-234">Como resultado, `System.ServiceModel.MetadataExporter` o inclui `UdpTransportBindingElement` na geração de política para qualquer associação que a inclua.</span><span class="sxs-lookup"><span data-stu-id="15013-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="15013-235">No `IPolicyExportExtension.ExportPolicy`, adicionamos uma asserção para UDP e outra asserção se estivermos no modo multicast.</span><span class="sxs-lookup"><span data-stu-id="15013-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="15013-236">Isso ocorre porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenado entre ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="15013-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="15013-237">Como os elementos de associação de transporte personalizados são responsáveis pelo tratamento `IPolicyExportExtension` de endereçamento `UdpTransportBindingElement` , a implementação no também deve lidar com a exportação das asserções de política apropriadas do WS-Addressing para indicar a versão do WS-Addressing sendo usado.</span><span class="sxs-lookup"><span data-stu-id="15013-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="15013-238">Importação de política</span><span class="sxs-lookup"><span data-stu-id="15013-238">Policy Import</span></span>  
 <span data-ttu-id="15013-239">Para estender o sistema de importação de política, devemos adicionar a configuração a seguir ao arquivo de configuração para SvcUtil. exe, conforme mostrado no arquivo svcutil. exe. config.</span><span class="sxs-lookup"><span data-stu-id="15013-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="15013-240">Em seguida, `IPolicyImporterExtension` implementamos a partir de`UdpBindingElementImporter`nossa classe registrada ().</span><span class="sxs-lookup"><span data-stu-id="15013-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="15013-241">No `ImportPolicy()`, examinamos as asserções em nosso namespace e processamos aquelas para gerar o transporte e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="15013-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="15013-242">Também devemos remover as asserções que manipulamos da lista de asserções de associação.</span><span class="sxs-lookup"><span data-stu-id="15013-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="15013-243">Novamente, ao executar svcutil. exe, há duas opções de integração:</span><span class="sxs-lookup"><span data-stu-id="15013-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="15013-244">Aponte para o SvcUtil. exe para nosso arquivo de configuração usando\<o arquivo/SvcutilConfig: File >.</span><span class="sxs-lookup"><span data-stu-id="15013-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="15013-245">Adicione a seção de configuração a svcutil. exe. config no mesmo diretório que svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="15013-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="15013-246">Adicionando uma associação padrão</span><span class="sxs-lookup"><span data-stu-id="15013-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="15013-247">Nosso elemento Binding pode ser usado das duas maneiras a seguir:</span><span class="sxs-lookup"><span data-stu-id="15013-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="15013-248">Por meio de uma associação personalizada: Uma associação personalizada permite que o usuário crie sua própria associação com base em um conjunto arbitrário de elementos de ligação.</span><span class="sxs-lookup"><span data-stu-id="15013-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="15013-249">Usando uma associação fornecida pelo sistema que inclui nosso elemento de ligação.</span><span class="sxs-lookup"><span data-stu-id="15013-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="15013-250">O WCF fornece várias dessas associações definidas pelo sistema, `BasicHttpBinding`como, `NetTcpBinding`e `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="15013-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="15013-251">Cada uma dessas associações está associada a um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="15013-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="15013-252">O exemplo implementa a associação de `SampleProfileUdpBinding`perfil no, que deriva <xref:System.ServiceModel.Channels.Binding>de.</span><span class="sxs-lookup"><span data-stu-id="15013-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="15013-253">O `SampleProfileUdpBinding` contém até quatro elementos de ligação dentro dele: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`e `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="15013-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="15013-254">Adicionando um importador de associação padrão personalizado</span><span class="sxs-lookup"><span data-stu-id="15013-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="15013-255">O SvcUtil. exe e `WsdlImporter` o tipo, por padrão, reconhecem e importam associações definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="15013-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="15013-256">Caso contrário, a associação será importada como uma `CustomBinding` instância.</span><span class="sxs-lookup"><span data-stu-id="15013-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="15013-257">Para habilitar svcutil. exe e o `WsdlImporter` para importar `UdpBindingElementImporter` o `SampleProfileUdpBinding` também atua como um importador de associação padrão personalizado.</span><span class="sxs-lookup"><span data-stu-id="15013-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="15013-258">Um importador de associação padrão personalizado implementa `ImportEndpoint` o método `IWsdlImportExtension` na interface para examinar a `CustomBinding` instância importada de metadados para ver se ela pode ter sido gerada por uma associação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="15013-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="15013-259">Em geral, a implementação de um importador de associação padrão personalizado envolve a verificação das propriedades dos elementos de associação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela associação padrão foram alteradas e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="15013-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="15013-260">Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, propagar as propriedades dos elementos de associação para a instância de associação padrão à qual a associação padrão dá suporte e comparar a associação elementos da associação padrão com os elementos de associação importados.</span><span class="sxs-lookup"><span data-stu-id="15013-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="15013-261">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="15013-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="15013-262">Para expor nosso transporte por meio da configuração, devemos implementar duas seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="15013-263">O primeiro é um `BindingElementExtensionElement` para `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="15013-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="15013-264">Isso é para que `CustomBinding` as implementações possam referenciar nosso elemento de ligação.</span><span class="sxs-lookup"><span data-stu-id="15013-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="15013-265">A segunda é uma `Configuration` para nossa `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="15013-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="15013-266">Elemento de extensão do elemento de associação</span><span class="sxs-lookup"><span data-stu-id="15013-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="15013-267">A seção `UdpTransportElement` é um `BindingElementExtensionElement` que expõe `UdpTransportBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="15013-268">Com algumas substituições básicas, definimos nosso nome de seção de configuração, o tipo de nosso elemento de ligação e como criar nosso elemento de ligação.</span><span class="sxs-lookup"><span data-stu-id="15013-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="15013-269">Em seguida, podemos registrar nossa seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="15013-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="15013-270">A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="15013-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="15013-271">Seção de associação</span><span class="sxs-lookup"><span data-stu-id="15013-271">Binding Section</span></span>  
 <span data-ttu-id="15013-272">A seção `SampleProfileUdpBindingCollectionElement` é um `StandardBindingCollectionElement` que expõe `SampleProfileUdpBinding` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="15013-273">A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que deriva de. `StandardBindingElement`</span><span class="sxs-lookup"><span data-stu-id="15013-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="15013-274">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`e às `ConfigurationElement` funções a serem mapeadas da associação.</span><span class="sxs-lookup"><span data-stu-id="15013-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="15013-275">Por fim, substitua `OnApplyConfiguration` o método em `SampleProfileUdpBinding`nosso, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="15013-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="15013-276">Para registrar esse manipulador com o sistema de configuração, adicionamos a seção a seguir ao arquivo de configuração relevante.</span><span class="sxs-lookup"><span data-stu-id="15013-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="15013-277">Em seguida, ele pode ser referenciado na seção de configuração de serviceModel.</span><span class="sxs-lookup"><span data-stu-id="15013-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="15013-278">O cliente e o serviço de teste UDP</span><span class="sxs-lookup"><span data-stu-id="15013-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="15013-279">O código de teste para usar esse transporte de exemplo está disponível nos diretórios UdpTestService e UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="15013-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="15013-280">O código de serviço consiste em dois testes – um teste define associações e pontos de extremidade do código e o outro faz isso por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="15013-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="15013-281">Ambos os testes usam dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="15013-281">Both tests use two endpoints.</span></span> <span data-ttu-id="15013-282">Um ponto de extremidade `SampleUdpProfileBinding` usa o com [ \<ReliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido como. `true`</span><span class="sxs-lookup"><span data-stu-id="15013-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="15013-283">O outro ponto de extremidade usa uma associação `UdpTransportBindingElement`personalizada com.</span><span class="sxs-lookup"><span data-stu-id="15013-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="15013-284">Isso é equivalente a usar `SampleUdpProfileBinding` with [ \<ReliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="15013-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="15013-285">Ambos os testes criam um serviço, adicionam um ponto de extremidade para cada associação, abrem o serviço e aguardam que o usuário pressione ENTER antes de fechar o serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="15013-286">Ao iniciar o aplicativo de teste de serviço, você deverá ver a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="15013-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="15013-287">Em seguida, você pode executar o aplicativo cliente de teste nos pontos de extremidade publicados.</span><span class="sxs-lookup"><span data-stu-id="15013-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="15013-288">O aplicativo de teste do cliente cria um cliente para cada ponto de extremidade e envia cinco mensagens para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="15013-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="15013-289">A saída a seguir está no cliente.</span><span class="sxs-lookup"><span data-stu-id="15013-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="15013-290">A seguir está a saída completa do serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="15013-291">Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione ENTER no serviço e execute o cliente de teste novamente.</span><span class="sxs-lookup"><span data-stu-id="15013-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="15013-292">Você deverá ver a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="15013-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="15013-293">Executar o cliente novamente produz o mesmo resultado dos resultados anteriores.</span><span class="sxs-lookup"><span data-stu-id="15013-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="15013-294">Para regenerar o código do cliente e a configuração usando svcutil. exe, inicie o aplicativo de serviço e execute o SvcUtil. exe a seguir do diretório raiz do exemplo.</span><span class="sxs-lookup"><span data-stu-id="15013-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="15013-295">Observe que svcutil. exe não gera a configuração de extensão de associação para `SampleProfileUdpBinding`o, portanto, você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="15013-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="15013-296">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="15013-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="15013-297">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15013-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="15013-298">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="15013-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="15013-299">Consulte a seção "serviço de teste e cliente de UDP" anterior.</span><span class="sxs-lookup"><span data-stu-id="15013-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="15013-300">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="15013-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="15013-301">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="15013-301">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="15013-302">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="15013-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15013-303">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="15013-303">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

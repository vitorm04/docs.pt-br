---
title: 'Transporte: UDP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc30a755278251ac9e06f2ddd56e2c369b950af4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-udp"></a><span data-ttu-id="8f79e-102">Transporte: UDP</span><span class="sxs-lookup"><span data-stu-id="8f79e-102">Transport: UDP</span></span>
<span data-ttu-id="8f79e-103">O transporte UDP demonstra como implementar UDP unicast e multicast como um personalizado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transporte.</span><span class="sxs-lookup"><span data-stu-id="8f79e-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="8f79e-104">O exemplo descreve o procedimento recomendado para a criação de um transporte personalizado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], usando a estrutura de canal e seguindo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] práticas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="8f79e-104">The sample describes the recommended procedure for creating a custom transport in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="8f79e-105">As etapas para criar um transporte personalizado são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8f79e-105">The steps to create a custom transport are as follows:</span></span>  
  
1.  <span data-ttu-id="8f79e-106">Decidir qual o canal [padrões de troca de mensagem](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) a ChannelFactory e ChannelListener oferecerá suporte.</span><span class="sxs-lookup"><span data-stu-id="8f79e-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="8f79e-107">Em seguida, decida se você oferecer suporte as sessão variações dessas interfaces.</span><span class="sxs-lookup"><span data-stu-id="8f79e-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2.  <span data-ttu-id="8f79e-108">Crie uma fábrica de canal e ouvinte que dão suporte ao padrão de troca de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3.  <span data-ttu-id="8f79e-109">Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4.  <span data-ttu-id="8f79e-110">Adicionar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento que adiciona o transporte personalizado para uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="8f79e-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="8f79e-111">Para obter mais informações, consulte [adicionando um elemento de associação](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="8f79e-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5.  <span data-ttu-id="8f79e-112">Adicione uma seção de extensão do elemento de associação para expor o novo elemento de associação para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6.  <span data-ttu-id="8f79e-113">Adicione extensões de metadados para recursos para outros pontos de extremidade de comunicação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7.  <span data-ttu-id="8f79e-114">Adicione uma associação que pré-configura em uma pilha de elementos de associação de acordo com um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="8f79e-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="8f79e-115">Para obter mais informações, consulte [adicionar uma associação padrão](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="8f79e-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8.  <span data-ttu-id="8f79e-116">Adicione uma seção de associação e o elemento de configuração de associação para expor a associação para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="8f79e-117">Para obter mais informações, consulte [adicionando suporte de configuração](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="8f79e-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="8f79e-118">Padrões de troca de mensagem</span><span class="sxs-lookup"><span data-stu-id="8f79e-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="8f79e-119">A primeira etapa na gravação de um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte.</span><span class="sxs-lookup"><span data-stu-id="8f79e-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="8f79e-120">Há três MEPs à sua escolha:</span><span class="sxs-lookup"><span data-stu-id="8f79e-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="8f79e-121">Datagrama (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="8f79e-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="8f79e-122">Ao usar um datagrama MEPS, um cliente envia uma mensagem usando uma troca de "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="8f79e-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="8f79e-123">Um disparar e esquecer exchange é aquela que requer confirmação fora de banda de entrega bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8f79e-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="8f79e-124">A mensagem pode ser perdido em trânsito e nunca alcançar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="8f79e-125">Se a operação de envio for concluído com êxito no lado do cliente, ele não garante que o ponto de extremidade remoto recebeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="8f79e-126">O datagrama é um componente fundamental para mensagens, como você pode criar seus próprios protocolos sobre ele — incluindo protocolos confiáveis e seguro.</span><span class="sxs-lookup"><span data-stu-id="8f79e-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="8f79e-127">Canais de datagrama do cliente implementam a <xref:System.ServiceModel.Channels.IOutputChannel> canais de datagrama de interface e o serviço implementam o <xref:System.ServiceModel.Channels.IInputChannel> interface.</span><span class="sxs-lookup"><span data-stu-id="8f79e-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="8f79e-128">Solicitação-resposta (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="8f79e-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="8f79e-129">Neste MEPS, uma mensagem é enviada, e uma resposta é recebida.</span><span class="sxs-lookup"><span data-stu-id="8f79e-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="8f79e-130">O padrão consiste em pares de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="8f79e-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="8f79e-131">Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador obtém.</span><span class="sxs-lookup"><span data-stu-id="8f79e-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="8f79e-132">Esse padrão também é conhecido como Half-Duplex.</span><span class="sxs-lookup"><span data-stu-id="8f79e-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="8f79e-133">Este MEPS canais de cliente implementam <xref:System.ServiceModel.Channels.IRequestChannel> e canais de serviço implementam <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="8f79e-134">Duplex (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="8f79e-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="8f79e-135">O MEPS duplex permite que um número arbitrário de mensagens sejam enviadas por um cliente e recebidos em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="8f79e-136">O duplex MEPS é como uma conversa telefônica, onde cada palavra que está sendo falada é uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="8f79e-137">Como ambos os lados podem enviar e receber este MEPS, a interface implementada por canais de cliente e de serviço é <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="8f79e-138">Cada um desses MEPs também pode oferecer suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="8f79e-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="8f79e-139">A funcionalidade adicional fornecida por um canal de reconhecimento de sessão é que ele correlaciona todas as mensagens enviadas e recebidas em um canal.</span><span class="sxs-lookup"><span data-stu-id="8f79e-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="8f79e-140">O padrão de solicitação-resposta é uma sessão de duas mensagens independente, como a solicitação e resposta são correlacionadas.</span><span class="sxs-lookup"><span data-stu-id="8f79e-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="8f79e-141">Em contraste, o padrão de solicitação-resposta que oferece suporte a sessões implica que todos os pares de solicitação/resposta naquele canal são correlacionados com o outro.</span><span class="sxs-lookup"><span data-stu-id="8f79e-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="8f79e-142">Isso lhe dá um total de seis MEPs — datagrama, solicitação-resposta, Duplex, datagrama com sessões de solicitação-resposta com sessões e Duplex com sessões — à sua escolha.</span><span class="sxs-lookup"><span data-stu-id="8f79e-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f79e-143">Para o transporte UDP, a MEPS somente com suporte é datagrama, como UDP inerentemente é um protocolo de "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="8f79e-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="8f79e-144">Ciclo de vida do objeto de ICommunicationObject e o WCF</span><span class="sxs-lookup"><span data-stu-id="8f79e-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8f79e-145">tem uma máquina de estado comum que é usada para gerenciar o ciclo de vida de objetos, como <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, e <xref:System.ServiceModel.Channels.IChannelListener> que são usados para comunicação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-145"> has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="8f79e-146">Há cinco estados em que esses objetos de comunicação podem existir.</span><span class="sxs-lookup"><span data-stu-id="8f79e-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="8f79e-147">Esses estados são representados pelo <xref:System.ServiceModel.CommunicationState> enumeração e são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8f79e-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="8f79e-148">Criado: Esse é o estado de um <xref:System.ServiceModel.ICommunicationObject> quando ele é instanciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="8f79e-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="8f79e-149">Nenhuma entrada/saída (e/s) ocorre nesse estado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="8f79e-150">Abrindo: Transição de objetos para esse estado quando <xref:System.ServiceModel.ICommunicationObject.Open%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="8f79e-151">Neste ponto propriedades são feitas imutáveis e pode começar a entrada/saída.</span><span class="sxs-lookup"><span data-stu-id="8f79e-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="8f79e-152">Esta transição é válida somente do estado criado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="8f79e-153">Aberto: A transição de objetos para esse estado quando o processo de abertura é concluída.</span><span class="sxs-lookup"><span data-stu-id="8f79e-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="8f79e-154">Esta transição é válida somente do estado de abertura.</span><span class="sxs-lookup"><span data-stu-id="8f79e-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="8f79e-155">Neste ponto, o objeto é totalmente pode ser usado para transferência.</span><span class="sxs-lookup"><span data-stu-id="8f79e-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="8f79e-156">Fechamento: Transição de objetos para esse estado quando <xref:System.ServiceModel.ICommunicationObject.Close%2A> é chamado para um desligamento normal.</span><span class="sxs-lookup"><span data-stu-id="8f79e-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="8f79e-157">Esta transição é válida somente do estado aberto.</span><span class="sxs-lookup"><span data-stu-id="8f79e-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="8f79e-158">Fechado: No fechada objetos de estado não são mais utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="8f79e-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="8f79e-159">Em geral, mais alta configuração ainda será acessível para inspeção, mas não há comunicação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="8f79e-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="8f79e-160">Esse estado é equivalente à que está sendo descartado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="8f79e-161">Com falha: No estado com falha, os objetos são acessíveis para inspeção, mas não mais utilizável.</span><span class="sxs-lookup"><span data-stu-id="8f79e-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="8f79e-162">Quando ocorre um erro não recuperável, o objeto faz a transição para esse estado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="8f79e-163">A transição só é válida desse estado é para o `Closed` estado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="8f79e-164">Há eventos que acionam para cada transição de estado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="8f79e-165">O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento e faz com que o objeto transição imediatamente do estado atual para o estado fechado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="8f79e-166">Chamando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> encerra qualquer trabalho não concluído.</span><span class="sxs-lookup"><span data-stu-id="8f79e-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="8f79e-167">Fábrica de canal e ouvinte de canal</span><span class="sxs-lookup"><span data-stu-id="8f79e-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="8f79e-168">A próxima etapa na gravação de um transporte personalizado é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> de canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="8f79e-169">A camada do canal usa um padrão de fábrica para a construção de canais.</span><span class="sxs-lookup"><span data-stu-id="8f79e-169">The channel layer uses a factory pattern for constructing channels.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8f79e-170">Fornece auxiliares da classe base para esse processo.</span><span class="sxs-lookup"><span data-stu-id="8f79e-170"> provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="8f79e-171">O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita anteriormente na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="8f79e-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="8f79e-172">O '<xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-172">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="8f79e-173">O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="8f79e-174">O '<xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida o `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstract.</span><span class="sxs-lookup"><span data-stu-id="8f79e-174">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="8f79e-175">O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="8f79e-176">Cuida do gerenciamento de estado básica.</span><span class="sxs-lookup"><span data-stu-id="8f79e-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="8f79e-177">Neste exemplo, a implementação de fábrica está contida em UdpChannelFactory.cs e a implementação de ouvinte está contida no UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="8f79e-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="8f79e-178">O <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="8f79e-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="8f79e-179">A fábrica de canais de UDP</span><span class="sxs-lookup"><span data-stu-id="8f79e-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="8f79e-180">O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="8f79e-181">O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso para a versão de mensagem do codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="8f79e-182">O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para que podemos pode subdividir a instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="8f79e-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="8f79e-183">O canal de saída de UDP</span><span class="sxs-lookup"><span data-stu-id="8f79e-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="8f79e-184">O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="8f79e-185">O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="8f79e-186">O canal pode ser fechado normalmente ou maneira brusca.</span><span class="sxs-lookup"><span data-stu-id="8f79e-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="8f79e-187">Se o canal está fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método.</span><span class="sxs-lookup"><span data-stu-id="8f79e-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="8f79e-188">Se isso gera uma exceção, a infraestrutura de chamadas `Abort` garantir que o canal é limpa.</span><span class="sxs-lookup"><span data-stu-id="8f79e-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="8f79e-189">Depois de implementar `Send()` e `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="8f79e-190">Isso é dividido em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="8f79e-190">This breaks down into two main sections.</span></span> <span data-ttu-id="8f79e-191">Primeiro, a serialização da mensagem em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="8f79e-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="8f79e-192">Em seguida, podemos enviar os dados resultantes na conexão.</span><span class="sxs-lookup"><span data-stu-id="8f79e-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="8f79e-193">O UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="8f79e-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="8f79e-194">O ' UdpChannelListener que implementa o exemplo deriva o <xref:System.ServiceModel.Channels.ChannelListenerBase> classe.</span><span class="sxs-lookup"><span data-stu-id="8f79e-194">The``UdpChannelListener that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="8f79e-195">Ele usa um único soquete UDP para receber datagramas.</span><span class="sxs-lookup"><span data-stu-id="8f79e-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="8f79e-196">O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono.</span><span class="sxs-lookup"><span data-stu-id="8f79e-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="8f79e-197">Os dados, em seguida, são convertidos em mensagens usando a estrutura de codificação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8f79e-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="8f79e-198">Como o mesmo canal de datagrama representa mensagens que chegam de várias fontes, o `UdpChannelListener` um ouvinte de singleton.</span><span class="sxs-lookup"><span data-stu-id="8f79e-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="8f79e-199">Há, a maioria, um ativo <xref:System.ServiceModel.Channels.IChannel>' associado a este ouvinte de cada vez.</span><span class="sxs-lookup"><span data-stu-id="8f79e-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel>``associated with this listener at a time.</span></span> <span data-ttu-id="8f79e-200">O exemplo gera outra somente se um canal que é retornado pelo `AcceptChannel` método subsequentemente é descartado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="8f79e-201">Quando uma mensagem é recebida, ele é enfileirado para este canal de singleton.</span><span class="sxs-lookup"><span data-stu-id="8f79e-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="8f79e-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="8f79e-202">UdpInputChannel</span></span>  
 <span data-ttu-id="8f79e-203">O `UdpInputChannel` classe implementa `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="8f79e-204">Ele consiste em uma fila de mensagens de entrada que é preenchida pelo `UdpChannelListener`do soquete.</span><span class="sxs-lookup"><span data-stu-id="8f79e-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="8f79e-205">Essas mensagens são removidas da fila pelo `IInputChannel.Receive` método.</span><span class="sxs-lookup"><span data-stu-id="8f79e-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="8f79e-206">Adicionando um elemento de associação</span><span class="sxs-lookup"><span data-stu-id="8f79e-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="8f79e-207">Agora que os canais e fábricas são criados, devemos expor-los no tempo de execução de ServiceModel por meio de uma associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="8f79e-208">Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="8f79e-209">Cada elemento na pilha é representado por um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="8f79e-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="8f79e-210">No exemplo, o elemento de associação é `UdpTransportBindingElement`, que é derivado de <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="8f79e-211">Ela substitui os seguintes métodos para criar as fábricas associadas nossa associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-212">Ele também contém membros para clonagem de `BindingElement` e retornando nosso esquema (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="8f79e-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="8f79e-213">Adicionando suporte a metadados para um elemento de associação de transporte</span><span class="sxs-lookup"><span data-stu-id="8f79e-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="8f79e-214">Para integrar nosso transporte para o sistema de metadados, é deve dar suporte tanto a importação e exportação de política.</span><span class="sxs-lookup"><span data-stu-id="8f79e-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="8f79e-215">Isso permite que clientes da nossa associação por meio de gerar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8f79e-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="8f79e-216">Adicionando suporte a WSDL</span><span class="sxs-lookup"><span data-stu-id="8f79e-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="8f79e-217">O elemento de associação de transporte em uma associação é responsável para exportar e importar informações de endereçamento nos metadados.</span><span class="sxs-lookup"><span data-stu-id="8f79e-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="8f79e-218">Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar uma URI de transporte correta nos metadados.</span><span class="sxs-lookup"><span data-stu-id="8f79e-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="8f79e-219">Exportação WSDL</span><span class="sxs-lookup"><span data-stu-id="8f79e-219">WSDL Export</span></span>  
 <span data-ttu-id="8f79e-220">Para exportar informações de endereçamento de `UdpTransportBindingElement` implementa o `IWsdlExportExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="8f79e-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="8f79e-221">O `ExportEndpoint` método adiciona as informações de endereçamento corretas para a porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="8f79e-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="8f79e-222">O `UdpTransportBindingElement` implementação o `ExportEndpoint` método também exporta um transporte URI quando o ponto de extremidade usa uma associação SOAP.</span><span class="sxs-lookup"><span data-stu-id="8f79e-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="8f79e-223">Importação WSDL</span><span class="sxs-lookup"><span data-stu-id="8f79e-223">WSDL Import</span></span>  
 <span data-ttu-id="8f79e-224">Para estender o sistema de importação WSDL para lidar com a importação de endereços, devemos adicionar a configuração a seguir para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="8f79e-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-225">Ao executar o Svcutil.exe, há duas opções para obter o Svcutil.exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="8f79e-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="8f79e-226">Ponto Svcutil.exe para nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.</span><span class="sxs-lookup"><span data-stu-id="8f79e-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="8f79e-227">Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8f79e-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="8f79e-228">O `UdpBindingElementImporter` tipo implementa o `IWsdlImportExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="8f79e-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="8f79e-229">O `ImportEndpoint` método importa o endereço da porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="8f79e-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="8f79e-230">Adicionando suporte a política</span><span class="sxs-lookup"><span data-stu-id="8f79e-230">Adding Policy Support</span></span>  
 <span data-ttu-id="8f79e-231">O elemento de associação personalizada pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="8f79e-232">Exportação de diretivas</span><span class="sxs-lookup"><span data-stu-id="8f79e-232">Policy Export</span></span>  
 <span data-ttu-id="8f79e-233">O `UdpTransportBindingElement` tipo implementa `IPolicyExportExtension` para adicionar suporte para exportação de política.</span><span class="sxs-lookup"><span data-stu-id="8f79e-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="8f79e-234">Como resultado, `System.ServiceModel.MetadataExporter` inclui `UdpTransportBindingElement` na geração de política para qualquer associação que o inclua.</span><span class="sxs-lookup"><span data-stu-id="8f79e-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="8f79e-235">Em `IPolicyExportExtension.ExportPolicy`, adicionamos uma asserção para UDP e outra asserção se estamos no modo de multicast.</span><span class="sxs-lookup"><span data-stu-id="8f79e-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="8f79e-236">Isso ocorre porque o modo multicast afeta como a pilha de comunicação é construída e, portanto, deve ser coordenada entre os dois lados.</span><span class="sxs-lookup"><span data-stu-id="8f79e-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-237">Como os elementos de associação de transporte personalizado serão responsáveis pela manipulação de endereçamento, o `IPolicyExportExtension` implementação no `UdpTransportBindingElement` também deve tratar exportando as apropriado declarações de política WS-Addressing para indicar a versão do WS-Addressing está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="8f79e-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="8f79e-238">Importação da política</span><span class="sxs-lookup"><span data-stu-id="8f79e-238">Policy Import</span></span>  
 <span data-ttu-id="8f79e-239">Para estender o sistema de importação da política, devemos adicionar a configuração a seguir para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="8f79e-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-240">Em seguida, implementamos `IPolicyImporterExtension` de nossa classe registrada (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="8f79e-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="8f79e-241">Em `ImportPolicy()`, podemos examinar as asserções em nosso namespace e processar os para gerar o transporte e verifique se ela é difundida via multicast.</span><span class="sxs-lookup"><span data-stu-id="8f79e-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="8f79e-242">Nós também deve remover as asserções que tratamos da lista de declarações de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="8f79e-243">Novamente, ao executar o Svcutil.exe, há duas opções para integração:</span><span class="sxs-lookup"><span data-stu-id="8f79e-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="8f79e-244">Ponto Svcutil.exe para nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.</span><span class="sxs-lookup"><span data-stu-id="8f79e-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="8f79e-245">Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="8f79e-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="8f79e-246">Adicionar uma associação padrão</span><span class="sxs-lookup"><span data-stu-id="8f79e-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="8f79e-247">Nosso elemento de associação pode ser usado de duas maneiras a seguir:</span><span class="sxs-lookup"><span data-stu-id="8f79e-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="8f79e-248">Por meio de uma associação personalizada: uma associação personalizada permite que o usuário criar seu próprios associação com base em um conjunto arbitrário de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="8f79e-249">Usando uma associação fornecida pelo sistema que inclui o nosso elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-249">By using a system-provided binding that includes our binding element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8f79e-250">Fornece um número dessas associações definidas pelo sistema, como `BasicHttpBinding`, `NetTcpBinding`, e `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-250"> provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="8f79e-251">Cada uma dessas vinculações está associada um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="8f79e-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="8f79e-252">O exemplo implementa a associação de perfil em `SampleProfileUdpBinding`, que é derivado de <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="8f79e-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="8f79e-253">O `SampleProfileUdpBinding` contém até quatro elementos de associação nele: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, e `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="8f79e-254">Adicionando um padrão personalizado importador de associação</span><span class="sxs-lookup"><span data-stu-id="8f79e-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="8f79e-255">Svcutil.exe e `WsdlImporter` tipo, por padrão, reconhece e importa associações definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="8f79e-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="8f79e-256">Caso contrário, a associação é importada como um `CustomBinding` instância.</span><span class="sxs-lookup"><span data-stu-id="8f79e-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="8f79e-257">Para habilitar o Svcutil.exe e o `WsdlImporter` para importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizada.</span><span class="sxs-lookup"><span data-stu-id="8f79e-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="8f79e-258">Implementa um importador de associação padrão personalizada a `ImportEndpoint` método o `IWsdlImportExtension` interface para examinar o `CustomBinding` instância importada de metadados para ver se ele pode ter sido gerado por uma associação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="8f79e-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-259">Em geral, implementar um importador de associação padrão personalizado envolve verificando as propriedades dos elementos de associação importados para verificar que somente as propriedades que podem ser definidas por meio da associação padrão foram alterados e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="8f79e-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="8f79e-260">Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, para propagar as propriedades de elementos de associação para a instância de associação padrão que oferece suporte a associação padrão e comparar a associação elementos de associação padrão com os elementos de associação importados.</span><span class="sxs-lookup"><span data-stu-id="8f79e-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="8f79e-261">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="8f79e-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="8f79e-262">Para expor o nosso transporte por meio de configuração, devemos implementar duas seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="8f79e-263">A primeira é uma `BindingElementExtensionElement` para `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="8f79e-264">Isso é para que `CustomBinding` implementações podem fazer referência a nosso elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="8f79e-265">O segundo é um `Configuration` para nosso `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="8f79e-266">Elemento de extensão de elemento de associação</span><span class="sxs-lookup"><span data-stu-id="8f79e-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="8f79e-267">A seção `UdpTransportElement` é um `BindingElementExtensionElement` que expõe `UdpTransportBindingElement` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="8f79e-268">Com algumas substituições básico, definimos nosso nome da seção de configuração, o tipo de elemento de associação de nosso e como criar nosso elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="8f79e-269">Podemos pode registrar a seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8f79e-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-270">A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.</span><span class="sxs-lookup"><span data-stu-id="8f79e-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="8f79e-271">Seção de associação</span><span class="sxs-lookup"><span data-stu-id="8f79e-271">Binding Section</span></span>  
 <span data-ttu-id="8f79e-272">A seção `SampleProfileUdpBindingCollectionElement` é um `StandardBindingCollectionElement` que expõe `SampleProfileUdpBinding` para o sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="8f79e-273">A maior parte da implementação é delegada ao `SampleProfileUdpBindingConfigurationElement`, que é derivado de `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="8f79e-274">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`, funções e para mapear o `ConfigurationElement` associação.</span><span class="sxs-lookup"><span data-stu-id="8f79e-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="8f79e-275">Por fim, substituir o `OnApplyConfiguration` método no nosso `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8f79e-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-276">Para registrar esse manipulador com o sistema de configuração, adicionamos a seção a seguir ao arquivo de configuração relevantes.</span><span class="sxs-lookup"><span data-stu-id="8f79e-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-277">Em seguida, pode ser referenciada na seção de configuração do serviceModel.</span><span class="sxs-lookup"><span data-stu-id="8f79e-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="8f79e-278">O cliente e serviço de teste UDP</span><span class="sxs-lookup"><span data-stu-id="8f79e-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="8f79e-279">Código de teste para usar esse transporte de exemplo está disponível nos diretórios UdpTestService e UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="8f79e-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="8f79e-280">O código de serviço consiste em dois testes — um teste configura pontos de extremidade e associações de código e outro faz isso por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="8f79e-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="8f79e-281">Ambos os testes usam dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8f79e-281">Both tests use two endpoints.</span></span> <span data-ttu-id="8f79e-282">Um ponto de extremidade usa o `SampleUdpProfileBinding` com [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `true`.</span></span> <span data-ttu-id="8f79e-283">Outro ponto de extremidade usa uma associação personalizada com `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="8f79e-284">Isso é equivalente a usar `SampleUdpProfileBinding` com [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="8f79e-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `false`.</span></span> <span data-ttu-id="8f79e-285">Ambos os testes de criarem um serviço, adicionar um ponto de extremidade para cada associação, abra o serviço e aguarde até que o usuário pressionar ENTER antes de fechar o serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="8f79e-286">Quando você inicia o aplicativo de teste de serviço, você verá a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="8f79e-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="8f79e-287">Você pode executar o aplicativo de cliente de teste com os pontos de extremidade publicados.</span><span class="sxs-lookup"><span data-stu-id="8f79e-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="8f79e-288">O aplicativo de teste do cliente cria um cliente para cada ponto de extremidade e envia mensagens de cinco para cada ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8f79e-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="8f79e-289">A seguinte saída é no cliente.</span><span class="sxs-lookup"><span data-stu-id="8f79e-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="8f79e-290">A seguir está a saída completa no serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="8f79e-291">Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione a tecla ENTER no serviço e, em seguida, execute novamente o cliente de teste.</span><span class="sxs-lookup"><span data-stu-id="8f79e-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="8f79e-292">Você verá a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="8f79e-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="8f79e-293">Executando o cliente novamente produz o mesmo como os resultados anteriores.</span><span class="sxs-lookup"><span data-stu-id="8f79e-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="8f79e-294">Para gerar novamente o código de cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e em seguida, execute o seguinte Svcutil.exe do diretório raiz do exemplo.</span><span class="sxs-lookup"><span data-stu-id="8f79e-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="8f79e-295">Observe que o Svcutil.exe não gerar a configuração de extensão de associação para o `SampleProfileUdpBinding`, portanto, você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="8f79e-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f79e-296">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8f79e-296">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8f79e-297">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8f79e-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="8f79e-298">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8f79e-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8f79e-299">Consulte a seção "O UDP serviço e cliente de teste" anterior.</span><span class="sxs-lookup"><span data-stu-id="8f79e-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8f79e-300">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8f79e-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f79e-301">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8f79e-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8f79e-302">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="8f79e-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f79e-303">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8f79e-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

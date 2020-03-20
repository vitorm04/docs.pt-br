---
title: 'Transporte: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143766"
---
# <a name="transport-udp"></a><span data-ttu-id="d3425-102">Transporte: UDP</span><span class="sxs-lookup"><span data-stu-id="d3425-102">Transport: UDP</span></span>
<span data-ttu-id="d3425-103">A amostra udp transport demonstra como implementar o UDP unicast e o multicast como um transporte personalizado da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d3425-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="d3425-104">A amostra descreve o procedimento recomendado para a criação de um transporte personalizado em WCF, usando a estrutura do canal e seguindo as práticas recomendadas do WCF.</span><span class="sxs-lookup"><span data-stu-id="d3425-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="d3425-105">As etapas para criar um transporte personalizado são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3425-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="d3425-106">Decida qual dos padrões de troca de [mensagens](#MessageExchangePatterns) do canal (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) o ChannelFactory e o ChannelListener serão suportados.</span><span class="sxs-lookup"><span data-stu-id="d3425-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="d3425-107">Em seguida, decida se você suportará as variações de sessão dessas interfaces.</span><span class="sxs-lookup"><span data-stu-id="d3425-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="d3425-108">Crie uma fábrica de canais e ouvinte que suporte seu padrão de troca de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3425-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="d3425-109">Certifique-se de que quaisquer exceções específicas da rede <xref:System.ServiceModel.CommunicationException>sejam normalizadas para a classe derivada apropriada de .</span><span class="sxs-lookup"><span data-stu-id="d3425-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="d3425-110">Adicione [ \<](../../configure-apps/file-schema/wcf/bindings.md) um elemento de>de vinculação que adiciona o transporte personalizado a uma pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="d3425-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="d3425-111">Para obter mais informações, consulte [Adicionar um elemento de vinculação](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="d3425-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="d3425-112">Adicione uma seção de extensão de elemento de vinculação para expor o novo elemento de vinculação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="d3425-113">Adicione extensões de metadados para comunicar recursos a outros pontos finais.</span><span class="sxs-lookup"><span data-stu-id="d3425-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="d3425-114">Adicione uma vinculação que pré-configura uma pilha de elementos de vinculação de acordo com um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="d3425-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="d3425-115">Para obter mais informações, consulte [Adicionar uma vinculação padrão](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="d3425-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="d3425-116">Adicione uma seção de vinculação e um elemento de configuração de vinculação para expor a vinculação ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="d3425-117">Para obter mais informações, consulte [Adicionando suporte à configuração](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="d3425-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="d3425-118">Padrões de troca de mensagens</span><span class="sxs-lookup"><span data-stu-id="d3425-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="d3425-119">O primeiro passo para escrever um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte.</span><span class="sxs-lookup"><span data-stu-id="d3425-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="d3425-120">Há três deputados para escolher:</span><span class="sxs-lookup"><span data-stu-id="d3425-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="d3425-121">Datagrama (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="d3425-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="d3425-122">Ao usar um MEP datagram, um cliente envia uma mensagem usando uma troca de "fogo e esquecimento".</span><span class="sxs-lookup"><span data-stu-id="d3425-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="d3425-123">Uma troca de fogo e esquecimento é aquela que requer confirmação fora da banda de entrega bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="d3425-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="d3425-124">A mensagem pode ser perdida no trânsito e nunca chegar ao serviço.</span><span class="sxs-lookup"><span data-stu-id="d3425-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="d3425-125">Se a operação de envio for concluída com sucesso no final do cliente, não garante que o ponto final remoto tenha recebido a mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3425-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="d3425-126">O datagrama é um bloco fundamental para mensagens, pois você pode construir seus próprios protocolos em cima dele — incluindo protocolos confiáveis e protocolos seguros.</span><span class="sxs-lookup"><span data-stu-id="d3425-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="d3425-127">Os canais de <xref:System.ServiceModel.Channels.IOutputChannel> datagrama do cliente implementam os canais de datagrama de interface e serviço para implementar a <xref:System.ServiceModel.Channels.IInputChannel> interface.</span><span class="sxs-lookup"><span data-stu-id="d3425-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="d3425-128">Solicitação-Resposta (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="d3425-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="d3425-129">Neste MEP, uma mensagem é enviada, e uma resposta é recebida.</span><span class="sxs-lookup"><span data-stu-id="d3425-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="d3425-130">O padrão consiste em pares de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="d3425-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="d3425-131">Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e GETs do navegador.</span><span class="sxs-lookup"><span data-stu-id="d3425-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="d3425-132">Este padrão também é conhecido como Half-Duplex.</span><span class="sxs-lookup"><span data-stu-id="d3425-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="d3425-133">Neste MEP, os <xref:System.ServiceModel.Channels.IRequestChannel> canais do <xref:System.ServiceModel.Channels.IReplyChannel>cliente implementam e os canais de atendimento implementam.</span><span class="sxs-lookup"><span data-stu-id="d3425-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="d3425-134">Duplex (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="d3425-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="d3425-135">O MEP duplex permite que um número arbitrário de mensagens seja enviada por um cliente e recebida em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="d3425-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="d3425-136">O deputado duplex é como uma conversa telefônica, onde cada palavra sendo falada é uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="d3425-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="d3425-137">Como ambos os lados podem enviar e receber neste MEP, <xref:System.ServiceModel.Channels.IDuplexChannel>a interface implementada pelo cliente e canais de atendimento é .</span><span class="sxs-lookup"><span data-stu-id="d3425-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="d3425-138">Cada um desses deputados também pode apoiar as sessões.</span><span class="sxs-lookup"><span data-stu-id="d3425-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="d3425-139">A funcionalidade adicionada fornecida por um canal com reconhecimento de sessão é que correlaciona todas as mensagens enviadas e recebidas em um canal.</span><span class="sxs-lookup"><span data-stu-id="d3425-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="d3425-140">O padrão Solicitação-Resposta é uma sessão autônoma de duas mensagens, já que a solicitação e a resposta estão correlacionadas.</span><span class="sxs-lookup"><span data-stu-id="d3425-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="d3425-141">Em contraste, o padrão Solicitação-Resposta que suporta sessões implica que todos os pares de solicitação/resposta nesse canal estão correlacionados entre si.</span><span class="sxs-lookup"><span data-stu-id="d3425-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="d3425-142">Isso lhe dá um total de seis MEPs — Datagram, Request-Response, Duplex, Datagram com sessões, Request-Response com sessões e Duplex com sessões — para escolher.</span><span class="sxs-lookup"><span data-stu-id="d3425-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3425-143">Para o transporte UDP, o único MEP que é suportado é o Datagram, porque o UDP é inerentemente um protocolo de "fogo e esquecimento".</span><span class="sxs-lookup"><span data-stu-id="d3425-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="d3425-144">O ICommunicationObject e o ciclo de vida do objeto WCF</span><span class="sxs-lookup"><span data-stu-id="d3425-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="d3425-145">O WCF possui uma máquina de estado comum <xref:System.ServiceModel.Channels.IChannel>que <xref:System.ServiceModel.Channels.IChannelFactory>é <xref:System.ServiceModel.Channels.IChannelListener> usada para gerenciar o ciclo de vida de objetos como , e que são usados para comunicação.</span><span class="sxs-lookup"><span data-stu-id="d3425-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="d3425-146">Há cinco estados em que esses objetos de comunicação podem existir.</span><span class="sxs-lookup"><span data-stu-id="d3425-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="d3425-147">Esses estados são <xref:System.ServiceModel.CommunicationState> representados pela enumeração, e são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="d3425-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="d3425-148">Criado: Este é o <xref:System.ServiceModel.ICommunicationObject> estado de um quando é instanciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="d3425-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="d3425-149">Não ocorre entrada/saída (I/O) neste estado.</span><span class="sxs-lookup"><span data-stu-id="d3425-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="d3425-150">Abertura: Objetos transitam <xref:System.ServiceModel.ICommunicationObject.Open%2A> para este estado quando é chamado.</span><span class="sxs-lookup"><span data-stu-id="d3425-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="d3425-151">Neste ponto, as propriedades são imutáveis, e a entrada/saída pode começar.</span><span class="sxs-lookup"><span data-stu-id="d3425-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="d3425-152">Esta transição é válida apenas a partir do estado Criado.</span><span class="sxs-lookup"><span data-stu-id="d3425-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="d3425-153">Aberto: Objetos transitam para este estado quando o processo aberto é concluído.</span><span class="sxs-lookup"><span data-stu-id="d3425-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="d3425-154">Esta transição é válida apenas a partir do estado de abertura.</span><span class="sxs-lookup"><span data-stu-id="d3425-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="d3425-155">Neste ponto, o objeto é totalmente utilizável para transferência.</span><span class="sxs-lookup"><span data-stu-id="d3425-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="d3425-156">Fechamento: Objetos transitam <xref:System.ServiceModel.ICommunicationObject.Close%2A> para este estado quando é chamado para um desligamento gracioso.</span><span class="sxs-lookup"><span data-stu-id="d3425-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="d3425-157">Esta transição é válida apenas a partir do estado Aberto.</span><span class="sxs-lookup"><span data-stu-id="d3425-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="d3425-158">Fechado: No estado fechado, os objetos não são mais utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="d3425-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="d3425-159">Em geral, a maioria das configurações ainda é acessível para inspeção, mas nenhuma comunicação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="d3425-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="d3425-160">Este estado é equivalente a ser eliminado.</span><span class="sxs-lookup"><span data-stu-id="d3425-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="d3425-161">Defeituoso: No estado defeituoso, os objetos são acessíveis à inspeção, mas não podem mais ser utilizáveis.</span><span class="sxs-lookup"><span data-stu-id="d3425-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="d3425-162">Quando ocorre um erro não recuperável, o objeto transita para este estado.</span><span class="sxs-lookup"><span data-stu-id="d3425-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="d3425-163">A única transição válida deste `Closed` estado é para o estado.</span><span class="sxs-lookup"><span data-stu-id="d3425-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="d3425-164">Há eventos que disparam para cada transição de estado.</span><span class="sxs-lookup"><span data-stu-id="d3425-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="d3425-165">O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento, e faz com que o objeto transite imediatamente de seu estado atual para o estado fechado.</span><span class="sxs-lookup"><span data-stu-id="d3425-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="d3425-166">Ligar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> termina qualquer trabalho inacabado.</span><span class="sxs-lookup"><span data-stu-id="d3425-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="d3425-167">Fábrica de Canais e Ouvinte do Canal</span><span class="sxs-lookup"><span data-stu-id="d3425-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="d3425-168">O próximo passo na elaboração de um <xref:System.ServiceModel.Channels.IChannelFactory> transporte personalizado <xref:System.ServiceModel.Channels.IChannelListener> é criar uma implementação para canais de clientes e de canais de atendimento.</span><span class="sxs-lookup"><span data-stu-id="d3425-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="d3425-169">A camada do canal usa um padrão de fábrica para a construção de canais.</span><span class="sxs-lookup"><span data-stu-id="d3425-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="d3425-170">O WCF fornece ajudantes de classe base para este processo.</span><span class="sxs-lookup"><span data-stu-id="d3425-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="d3425-171">A <xref:System.ServiceModel.Channels.CommunicationObject> classe <xref:System.ServiceModel.ICommunicationObject> implementa e impõe a máquina estatal descrita anteriormente na Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="d3425-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="d3425-172">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe <xref:System.ServiceModel.Channels.CommunicationObject> implementa e fornece <xref:System.ServiceModel.Channels.ChannelFactoryBase> uma <xref:System.ServiceModel.Channels.ChannelListenerBase>classe de base unificada para e .</span><span class="sxs-lookup"><span data-stu-id="d3425-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="d3425-173">A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe trabalha <xref:System.ServiceModel.Channels.ChannelBase>em conjunto com , que <xref:System.ServiceModel.Channels.IChannel>é uma classe de base que implementa .</span><span class="sxs-lookup"><span data-stu-id="d3425-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="d3425-174">A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa e <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` consolida as `OnCreateChannel` sobrecargas em um método abstrato.</span><span class="sxs-lookup"><span data-stu-id="d3425-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="d3425-175">A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe <xref:System.ServiceModel.Channels.IChannelListener>implementa.</span><span class="sxs-lookup"><span data-stu-id="d3425-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="d3425-176">Cuida da gestão básica do Estado.</span><span class="sxs-lookup"><span data-stu-id="d3425-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="d3425-177">Nesta amostra, a implementação da fábrica está contida em UdpChannelFactory.cs e a implementação do ouvinte está contida em UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="d3425-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="d3425-178">As <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="d3425-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="d3425-179">A Fábrica de Canais UDP</span><span class="sxs-lookup"><span data-stu-id="d3425-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="d3425-180">O `UdpChannelFactory` derivado <xref:System.ServiceModel.Channels.ChannelFactoryBase>de .</span><span class="sxs-lookup"><span data-stu-id="d3425-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="d3425-181">A amostra <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> substitui-se para fornecer acesso à versão da mensagem do codificador de mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3425-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="d3425-182">A amostra também <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> se sobrepõe para que <xref:System.ServiceModel.Channels.BufferManager> possamos derrubar nossa instância de quando a máquina de estado faz a transição.</span><span class="sxs-lookup"><span data-stu-id="d3425-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="d3425-183">O canal de saída do UDP</span><span class="sxs-lookup"><span data-stu-id="d3425-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="d3425-184">Os `UdpOutputChannel` implementos. <xref:System.ServiceModel.Channels.IOutputChannel></span><span class="sxs-lookup"><span data-stu-id="d3425-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="d3425-185">O construtor valida os argumentos e <xref:System.Net.EndPoint> constrói um <xref:System.ServiceModel.EndpointAddress> objeto de destino com base no que é passado.</span><span class="sxs-lookup"><span data-stu-id="d3425-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="d3425-186">O canal pode ser fechado graciosamente ou sem graça.</span><span class="sxs-lookup"><span data-stu-id="d3425-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="d3425-187">Se o canal estiver fechado graciosamente, o soquete `OnClose` é fechado e uma chamada é feita para o método de classe base.</span><span class="sxs-lookup"><span data-stu-id="d3425-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="d3425-188">Se isso abrir uma exceção, a infra-estrutura liga `Abort` para garantir que o canal seja limpo.</span><span class="sxs-lookup"><span data-stu-id="d3425-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="d3425-189">Em seguida, `BeginSend()` / `EndSend()`implementamos `Send()` e .</span><span class="sxs-lookup"><span data-stu-id="d3425-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="d3425-190">Isso se divide em duas seções principais.</span><span class="sxs-lookup"><span data-stu-id="d3425-190">This breaks down into two main sections.</span></span> <span data-ttu-id="d3425-191">Primeiro serializamos a mensagem em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d3425-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="d3425-192">Em seguida, enviamos os dados resultantes no fio.</span><span class="sxs-lookup"><span data-stu-id="d3425-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="d3425-193">O UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="d3425-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="d3425-194">O `UdpChannelListener` que a amostra implementa <xref:System.ServiceModel.Channels.ChannelListenerBase> deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="d3425-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="d3425-195">Ele usa um único soquete UDP para receber datagramas.</span><span class="sxs-lookup"><span data-stu-id="d3425-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="d3425-196">O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono.</span><span class="sxs-lookup"><span data-stu-id="d3425-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="d3425-197">Os dados são então convertidos em mensagens usando o Quadro de Codificação de Mensagens.</span><span class="sxs-lookup"><span data-stu-id="d3425-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="d3425-198">Como o mesmo canal de datagrama representa mensagens que `UdpChannelListener` chegam de várias fontes, o é um ouvinte singleton.</span><span class="sxs-lookup"><span data-stu-id="d3425-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="d3425-199">Há, no máximo, <xref:System.ServiceModel.Channels.IChannel> um ativo associado a este ouvinte de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d3425-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="d3425-200">A amostra só gera outra se um canal `AcceptChannel` que é devolvido pelo método for posteriormente eliminado.</span><span class="sxs-lookup"><span data-stu-id="d3425-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="d3425-201">Quando uma mensagem é recebida, ela é enfileirada neste canal singleton.</span><span class="sxs-lookup"><span data-stu-id="d3425-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="d3425-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="d3425-202">UdpInputChannel</span></span>  
 <span data-ttu-id="d3425-203">A `UdpInputChannel` classe `IInputChannel`implementa.</span><span class="sxs-lookup"><span data-stu-id="d3425-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="d3425-204">Consiste em uma fila de mensagens recebidas que `UdpChannelListener`é preenchida pelo soquete.</span><span class="sxs-lookup"><span data-stu-id="d3425-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="d3425-205">Essas mensagens são enfileiradas `IInputChannel.Receive` pelo método.</span><span class="sxs-lookup"><span data-stu-id="d3425-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="d3425-206">Adicionando um elemento de vinculação</span><span class="sxs-lookup"><span data-stu-id="d3425-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="d3425-207">Agora que as fábricas e canais foram construídos, devemos expô-los ao tempo de execução serviceModel através de uma vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="d3425-208">Uma vinculação é uma coleção de elementos de ligação que representa a pilha de comunicação associada a um endereço de serviço.</span><span class="sxs-lookup"><span data-stu-id="d3425-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="d3425-209">Cada elemento na pilha é [ \<](../../configure-apps/file-schema/wcf/bindings.md) representado por um elemento de>de ligação.</span><span class="sxs-lookup"><span data-stu-id="d3425-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="d3425-210">Na amostra, o elemento `UdpTransportBindingElement`de ligação <xref:System.ServiceModel.Channels.TransportBindingElement>é , que deriva de .</span><span class="sxs-lookup"><span data-stu-id="d3425-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="d3425-211">Ele substitui os seguintes métodos para construir as fábricas associadas à nossa ligação.</span><span class="sxs-lookup"><span data-stu-id="d3425-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="d3425-212">Ele também contém membros `BindingElement` para clonagem e devolução do nosso esquema (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="d3425-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="d3425-213">Adicionando suporte a metadados para um elemento de vinculação de transporte</span><span class="sxs-lookup"><span data-stu-id="d3425-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="d3425-214">Para integrar nosso transporte ao sistema de metadados, devemos apoiar tanto a importação quanto a exportação da política.</span><span class="sxs-lookup"><span data-stu-id="d3425-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="d3425-215">Isso nos permite gerar clientes de nossa vinculação através da [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d3425-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="d3425-216">Adicionando suporte ao WSDL</span><span class="sxs-lookup"><span data-stu-id="d3425-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="d3425-217">O elemento de vinculação de transporte em uma vinculação é responsável pela exportação e importação de informações de endereçamento em metadados.</span><span class="sxs-lookup"><span data-stu-id="d3425-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="d3425-218">Ao usar uma vinculação SOAP, o elemento de ligação de transporte também deve exportar um URI de transporte correto em metadados.</span><span class="sxs-lookup"><span data-stu-id="d3425-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="d3425-219">Exportação wsdl</span><span class="sxs-lookup"><span data-stu-id="d3425-219">WSDL Export</span></span>  
 <span data-ttu-id="d3425-220">Para exportar informações `UdpTransportBindingElement` endereçadas, implementa a `IWsdlExportExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="d3425-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="d3425-221">O `ExportEndpoint` método adiciona as informações corretas de endereçamento à porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="d3425-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="d3425-222">A `UdpTransportBindingElement` implementação `ExportEndpoint` do método também exporta um URI de transporte quando o ponto final usa uma vinculação SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3425-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="d3425-223">Importação de WSDL</span><span class="sxs-lookup"><span data-stu-id="d3425-223">WSDL Import</span></span>  
 <span data-ttu-id="d3425-224">Para estender o sistema de importação WSDL para lidar com a importação dos endereços, devemos adicionar a seguinte configuração ao arquivo de configuração para Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d3425-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="d3425-225">Ao executar o Svcutil.exe, existem duas opções para obter Svcutil.exe para carregar as extensões de importação WSDL:</span><span class="sxs-lookup"><span data-stu-id="d3425-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="d3425-226">Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.</span><span class="sxs-lookup"><span data-stu-id="d3425-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d3425-227">Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="d3425-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="d3425-228">O `UdpBindingElementImporter` tipo implementa a `IWsdlImportExtension` interface.</span><span class="sxs-lookup"><span data-stu-id="d3425-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="d3425-229">O `ImportEndpoint` método importa o endereço da porta WSDL.</span><span class="sxs-lookup"><span data-stu-id="d3425-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="d3425-230">Adicionando suporte a políticas</span><span class="sxs-lookup"><span data-stu-id="d3425-230">Adding Policy Support</span></span>  
 <span data-ttu-id="d3425-231">O elemento de vinculação personalizado pode exportar afirmações de diretiva na vinculação WSDL para um ponto final de serviço para expressar as capacidades desse elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="d3425-232">Exportação de políticas</span><span class="sxs-lookup"><span data-stu-id="d3425-232">Policy Export</span></span>  
 <span data-ttu-id="d3425-233">O `UdpTransportBindingElement` tipo `IPolicyExportExtension` implementa para adicionar suporte à política de exportação.</span><span class="sxs-lookup"><span data-stu-id="d3425-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="d3425-234">Como resultado, `System.ServiceModel.MetadataExporter` inclui `UdpTransportBindingElement` na geração de políticas para qualquer vinculação que a inclua.</span><span class="sxs-lookup"><span data-stu-id="d3425-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="d3425-235">Em `IPolicyExportExtension.ExportPolicy`, adicionamos uma afirmação para UDP e outra afirmação se estivermos no modo multicast.</span><span class="sxs-lookup"><span data-stu-id="d3425-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="d3425-236">Isso porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenada entre ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="d3425-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="d3425-237">Como os elementos de vinculação de `IPolicyExportExtension` transporte personalizados são responsáveis pelo manuseio da abordagem, a implementação no também `UdpTransportBindingElement` deve lidar com a exportação das afirmações apropriadas da política ws-addressing para indicar a versão do WS-Addressing a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d3425-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="d3425-238">Importação de políticas</span><span class="sxs-lookup"><span data-stu-id="d3425-238">Policy Import</span></span>  
 <span data-ttu-id="d3425-239">Para estender o sistema de importação de políticas, devemos adicionar a seguinte configuração ao arquivo de configuração de Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d3425-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="d3425-240">Então implementamos `IPolicyImporterExtension` a partir`UdpBindingElementImporter`de nossa classe registrada ( ).</span><span class="sxs-lookup"><span data-stu-id="d3425-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="d3425-241">Em `ImportPolicy()`, nós olhamos através das afirmações em nosso namespace, e processar os para gerar o transporte e verificar se ele é multicast.</span><span class="sxs-lookup"><span data-stu-id="d3425-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="d3425-242">Também devemos remover as afirmações que lidamos da lista de afirmações vinculantes.</span><span class="sxs-lookup"><span data-stu-id="d3425-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="d3425-243">Novamente, ao executar o Svcutil.exe, há duas opções de integração:</span><span class="sxs-lookup"><span data-stu-id="d3425-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="d3425-244">Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.</span><span class="sxs-lookup"><span data-stu-id="d3425-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="d3425-245">Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="d3425-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="d3425-246">Adicionando uma vinculação padrão</span><span class="sxs-lookup"><span data-stu-id="d3425-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="d3425-247">Nosso elemento de ligação pode ser usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d3425-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="d3425-248">Através de uma vinculação personalizada: uma vinculação personalizada permite que o usuário crie sua própria vinculação com base em um conjunto arbitrário de elementos de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="d3425-249">Usando uma vinculação fornecida pelo sistema que inclui nosso elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="d3425-250">O WCF fornece uma série dessas ligações `BasicHttpBinding`definidas pelo sistema, tais como , `NetTcpBinding`e `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d3425-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="d3425-251">Cada uma dessas ligações está associada a um perfil bem definido.</span><span class="sxs-lookup"><span data-stu-id="d3425-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="d3425-252">A amostra implementa `SampleProfileUdpBinding`a vinculação <xref:System.ServiceModel.Channels.Binding>do perfil em , que deriva de .</span><span class="sxs-lookup"><span data-stu-id="d3425-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="d3425-253">O `SampleProfileUdpBinding` contém até quatro elementos `UdpTransportBindingElement` `TextMessageEncodingBindingElement CompositeDuplexBindingElement`de `ReliableSessionBindingElement`ligação dentro dele: , e .</span><span class="sxs-lookup"><span data-stu-id="d3425-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="d3425-254">Adicionando um importador de vinculação padrão personalizado</span><span class="sxs-lookup"><span data-stu-id="d3425-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="d3425-255">Svcutil.exe e `WsdlImporter` o tipo, por padrão, reconhece e importa vinculações definidas pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="d3425-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="d3425-256">Caso contrário, a vinculação `CustomBinding` é importada como instância.</span><span class="sxs-lookup"><span data-stu-id="d3425-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="d3425-257">Para habilitar svcutil.exe e `SampleProfileUdpBinding` `UdpBindingElementImporter` `WsdlImporter` importar o também atua como um importador de vinculação padrão personalizado.</span><span class="sxs-lookup"><span data-stu-id="d3425-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="d3425-258">Um importador de vinculação `ImportEndpoint` padrão `IWsdlImportExtension` personalizado implementa `CustomBinding` o método na interface para examinar a instância importada de metadados para ver se ele poderia ter sido gerado por uma vinculação padrão específica.</span><span class="sxs-lookup"><span data-stu-id="d3425-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="d3425-259">Geralmente, a implementação de um importador de vinculação padrão personalizado envolve verificar as propriedades dos elementos de ligação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela vinculação padrão foram alteradas e todas as outras propriedades são seus padrões.</span><span class="sxs-lookup"><span data-stu-id="d3425-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="d3425-260">Uma estratégia básica para implementar um importador de vinculação padrão é criar uma instância da vinculação padrão, propagar as propriedades dos elementos vinculantes à instância de vinculação padrão que a vinculação padrão suporta, e comparar a vinculação elementos da vinculação padrão com os elementos de ligação importados.</span><span class="sxs-lookup"><span data-stu-id="d3425-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="d3425-261">Adicionando suporte à configuração</span><span class="sxs-lookup"><span data-stu-id="d3425-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="d3425-262">Para expor nosso transporte através da configuração, devemos implementar duas seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="d3425-263">O primeiro `BindingElementExtensionElement` é `UdpTransportBindingElement`um para.</span><span class="sxs-lookup"><span data-stu-id="d3425-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="d3425-264">Isso é para `CustomBinding` que as implementações possam referenciar nosso elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="d3425-265">O segundo `Configuration` é `SampleProfileUdpBinding`um para o nosso.</span><span class="sxs-lookup"><span data-stu-id="d3425-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="d3425-266">Elemento de extensão do elemento de vinculação</span><span class="sxs-lookup"><span data-stu-id="d3425-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="d3425-267">A `UdpTransportElement` seção `BindingElementExtensionElement` é `UdpTransportBindingElement` uma que se expõe ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="d3425-268">Com algumas substituições básicas, definimos nosso nome da seção de configuração, o tipo de nosso elemento de vinculação e como criar nosso elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="d3425-269">Podemos então registrar nossa seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3425-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="d3425-270">A extensão pode ser referenciada a partir de vinculações personalizadas para usar UDP como transporte.</span><span class="sxs-lookup"><span data-stu-id="d3425-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="d3425-271">Seção de Vinculação</span><span class="sxs-lookup"><span data-stu-id="d3425-271">Binding Section</span></span>  
 <span data-ttu-id="d3425-272">A `SampleProfileUdpBindingCollectionElement` seção `StandardBindingCollectionElement` é `SampleProfileUdpBinding` uma que se expõe ao sistema de configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="d3425-273">A maior parte da implementação `SampleProfileUdpBindingConfigurationElement`é delegada `StandardBindingElement`ao , que deriva de .</span><span class="sxs-lookup"><span data-stu-id="d3425-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="d3425-274">O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding` `ConfigurationElement` , e funções para mapear a partir da vinculação.</span><span class="sxs-lookup"><span data-stu-id="d3425-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="d3425-275">Por fim, `OnApplyConfiguration` anular o `SampleProfileUdpBinding`método em nosso , como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3425-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d3425-276">Para registrar este manipulador com o sistema de configuração, adicionamos a seguinte seção ao arquivo de configuração relevante.</span><span class="sxs-lookup"><span data-stu-id="d3425-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d3425-277">Em seguida, ele pode ser referenciado a partir da seção de configuração serviceModel.</span><span class="sxs-lookup"><span data-stu-id="d3425-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="d3425-278">O serviço de teste e o cliente do UDP</span><span class="sxs-lookup"><span data-stu-id="d3425-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="d3425-279">O código de teste para o uso deste transporte de amostras está disponível nos diretórios UdpTestService e UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="d3425-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="d3425-280">O código de serviço consiste em dois testes — um teste configura vinculações e pontos finais a partir do código e o outro o faz através da configuração.</span><span class="sxs-lookup"><span data-stu-id="d3425-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="d3425-281">Ambos os testes usam dois pontos finais.</span><span class="sxs-lookup"><span data-stu-id="d3425-281">Both tests use two endpoints.</span></span> <span data-ttu-id="d3425-282">Um ponto final `SampleUdpProfileBinding` usa o conjunto `true`de>de Sessão [ \<confiável](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido para .</span><span class="sxs-lookup"><span data-stu-id="d3425-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="d3425-283">O outro ponto final usa `UdpTransportBindingElement`uma vinculação personalizada com .</span><span class="sxs-lookup"><span data-stu-id="d3425-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="d3425-284">Isso equivale ao `SampleUdpProfileBinding` uso com [ \<>de sessão confiável](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido para `false`.</span><span class="sxs-lookup"><span data-stu-id="d3425-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="d3425-285">Ambos os testes criam um serviço, adicionam um ponto final para cada vinculação, abrem o serviço e esperam que o usuário acerte ENTER antes de fechar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d3425-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="d3425-286">Ao iniciar o aplicativo de teste de serviço, você deve ver a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="d3425-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="d3425-287">Em seguida, você pode executar o aplicativo cliente de teste contra os pontos finais publicados.</span><span class="sxs-lookup"><span data-stu-id="d3425-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="d3425-288">O aplicativo de teste do cliente cria um cliente para cada ponto final e envia cinco mensagens para cada ponto final.</span><span class="sxs-lookup"><span data-stu-id="d3425-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="d3425-289">A seguinte saída está no cliente.</span><span class="sxs-lookup"><span data-stu-id="d3425-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="d3425-290">A seguir está a saída completa do serviço.</span><span class="sxs-lookup"><span data-stu-id="d3425-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="d3425-291">Para executar o aplicativo cliente contra pontos finais publicados usando a configuração, clique em ENTER no serviço e, em seguida, execute o cliente de teste novamente.</span><span class="sxs-lookup"><span data-stu-id="d3425-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="d3425-292">Você deve ver a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="d3425-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="d3425-293">Executar o cliente novamente rende o mesmo que os resultados anteriores.</span><span class="sxs-lookup"><span data-stu-id="d3425-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="d3425-294">Para regenerar o código e a configuração do cliente usando o Svcutil.exe, inicie o aplicativo de serviço e execute o seguinte Svcutil.exe a partir do diretório raiz da amostra.</span><span class="sxs-lookup"><span data-stu-id="d3425-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="d3425-295">Observe que o Svcutil.exe não gera `SampleProfileUdpBinding`a configuração de extensão de vinculação para o , portanto, você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="d3425-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3425-296">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d3425-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d3425-297">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3425-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="d3425-298">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3425-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d3425-299">Consulte a seção anterior "O Serviço de Teste e cliente udp".</span><span class="sxs-lookup"><span data-stu-id="d3425-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3425-300">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d3425-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3425-301">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d3425-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d3425-302">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="d3425-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3425-303">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d3425-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`

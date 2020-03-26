---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 7fa045dc6fd6e31eccf29e22ae2e212f59dfaec0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111862"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="82f9a-102">Lidando com exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="82f9a-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="82f9a-103">As exceções são usadas para comunicar erros localmente dentro do serviço ou na implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="82f9a-104">As falhas, por outro lado, são usadas para comunicar erros através dos limites de serviço, como do servidor para o cliente ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="82f9a-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="82f9a-105">Além das falhas, os canais de transporte geralmente usam mecanismos específicos de transporte para comunicar erros no nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f9a-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="82f9a-106">Por exemplo, o transporte HTTP usa códigos de status como o 404 para comunicar uma URL de ponto final não existente (não há ponto final para enviar uma falha).</span><span class="sxs-lookup"><span data-stu-id="82f9a-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="82f9a-107">Este documento consiste em três seções que fornecem orientação aos autores de canais personalizados.</span><span class="sxs-lookup"><span data-stu-id="82f9a-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="82f9a-108">A primeira seção fornece orientações sobre quando e como definir e lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="82f9a-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="82f9a-109">A segunda seção fornece orientação sobre a geração e o consumo de falhas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="82f9a-110">A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário de seu canal personalizado na solução de problemas em execução de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="82f9a-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="82f9a-111">Exceções</span><span class="sxs-lookup"><span data-stu-id="82f9a-111">Exceptions</span></span>  
 <span data-ttu-id="82f9a-112">Há duas coisas a ter em mente ao lançar uma exceção: Primeiro tem que ser de um tipo que permite que os usuários escrevam código correto que pode reagir adequadamente à exceção.</span><span class="sxs-lookup"><span data-stu-id="82f9a-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="82f9a-113">Em segundo lugar, ele tem que fornecer informações suficientes para o usuário entender o que deu errado, o impacto da falha e como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="82f9a-114">As seções a seguir dão orientações sobre tipos de exceção e mensagens para canais wcf (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="82f9a-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="82f9a-115">Há também orientação geral em torno de exceções no .NET no documento Diretrizes de Design para Exceções.</span><span class="sxs-lookup"><span data-stu-id="82f9a-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="82f9a-116">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="82f9a-116">Exception Types</span></span>  
 <span data-ttu-id="82f9a-117">Todas as exceções lançadas <xref:System.TimeoutException?displayProperty=nameWithType>pelos <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>canais devem ser <xref:System.ServiceModel.CommunicationException>um , ou um tipo derivado de .</span><span class="sxs-lookup"><span data-stu-id="82f9a-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="82f9a-118">(Exceções como <xref:System.ObjectDisposedException> também podem ser lançadas, mas apenas para indicar que o código de chamada usou indevidamente o canal.</span><span class="sxs-lookup"><span data-stu-id="82f9a-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="82f9a-119">Se um canal for usado corretamente, ele só deve jogar as exceções dadas.) O WCF fornece sete <xref:System.ServiceModel.CommunicationException> tipos de exceção que derivam e são projetados para serem usados por canais.</span><span class="sxs-lookup"><span data-stu-id="82f9a-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="82f9a-120">Existem <xref:System.ServiceModel.CommunicationException>outras exceções derivadas que são projetadas para serem usadas por outras partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="82f9a-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="82f9a-121">Esses tipos de exceção são:</span><span class="sxs-lookup"><span data-stu-id="82f9a-121">These exception types are:</span></span>  
  
|<span data-ttu-id="82f9a-122">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="82f9a-122">Exception Type</span></span>|<span data-ttu-id="82f9a-123">Significado</span><span class="sxs-lookup"><span data-stu-id="82f9a-123">Meaning</span></span>|<span data-ttu-id="82f9a-124">Conteúdo de exceção interna</span><span class="sxs-lookup"><span data-stu-id="82f9a-124">Inner Exception Content</span></span>|<span data-ttu-id="82f9a-125">Estratégia de recuperação</span><span class="sxs-lookup"><span data-stu-id="82f9a-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="82f9a-126">O endereço de ponto final especificado para ouvir já está em uso.</span><span class="sxs-lookup"><span data-stu-id="82f9a-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="82f9a-127">Se estiver presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="82f9a-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="82f9a-128">Por exemplo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-128">For example.</span></span> <span data-ttu-id="82f9a-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>ou <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="82f9a-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="82f9a-130">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="82f9a-131">O processo não é permitido acesso ao endereço de ponto final especificado para ouvir.</span><span class="sxs-lookup"><span data-stu-id="82f9a-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="82f9a-132">Se estiver presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="82f9a-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="82f9a-133">Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="82f9a-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="82f9a-134">Tente com credenciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="82f9a-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="82f9a-135">O <xref:System.ServiceModel.ICommunicationObject> que está sendo utilizado está no estado defeituoso (para obter mais informações, consulte [Entendendo alterações de estado](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="82f9a-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="82f9a-136">Observe que quando um objeto com várias chamadas pendentes transita para o estado com falha, apenas uma <xref:System.ServiceModel.CommunicationObjectFaultedException>chamada lança uma exceção relacionada à falha e o resto das chamadas lançam um .</span><span class="sxs-lookup"><span data-stu-id="82f9a-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="82f9a-137">Essa exceção é normalmente lançada porque um aplicativo ignora alguma exceção e tenta usar um objeto já defeituoso, possivelmente em um segmento diferente daquele que pegou a exceção original.</span><span class="sxs-lookup"><span data-stu-id="82f9a-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="82f9a-138">Se presente fornecer detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="82f9a-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="82f9a-139">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="82f9a-139">Create a new object.</span></span> <span data-ttu-id="82f9a-140">Observe que, dependendo <xref:System.ServiceModel.ICommunicationObject> do que causou a falha em primeiro lugar, pode haver outros trabalhos necessários para recuperar.</span><span class="sxs-lookup"><span data-stu-id="82f9a-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="82f9a-141">O <xref:System.ServiceModel.ICommunicationObject> que está sendo utilizado foi abortado (para mais informações, consulte [Entendendo mudanças de estado](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="82f9a-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="82f9a-142">Semelhante <xref:System.ServiceModel.CommunicationObjectFaultedException>a , esta exceção <xref:System.ServiceModel.ICommunicationObject.Abort%2A> indica que o aplicativo chamou o objeto, possivelmente de outro segmento, e o objeto não é mais utilizável por esse motivo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, this exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="82f9a-143">Se presente fornecer detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="82f9a-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="82f9a-144">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="82f9a-144">Create a new object.</span></span> <span data-ttu-id="82f9a-145">Note que dependendo do <xref:System.ServiceModel.ICommunicationObject> que causou o aborto em primeiro lugar, pode haver outros trabalhos necessários para recuperar.</span><span class="sxs-lookup"><span data-stu-id="82f9a-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="82f9a-146">O ponto final remoto do alvo não é ouvir.</span><span class="sxs-lookup"><span data-stu-id="82f9a-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="82f9a-147">Isso pode resultar de qualquer parte do endereço do ponto final ser incorreta, irresolúvel ou o ponto final estar para baixo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="82f9a-148">Exemplos incluem erro de DNS, queue manager não disponível e serviço não executado.</span><span class="sxs-lookup"><span data-stu-id="82f9a-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="82f9a-149">A exceção interna fornece detalhes, tipicamente do transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="82f9a-150">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-150">Try a different address.</span></span> <span data-ttu-id="82f9a-151">Alternativamente, o remetente pode esperar um pouco e tentar novamente no caso de o serviço foi para baixo</span><span class="sxs-lookup"><span data-stu-id="82f9a-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="82f9a-152">Os protocolos de comunicação, como descrito pela política do ponto final, são incompatíveis entre os pontos finais.</span><span class="sxs-lookup"><span data-stu-id="82f9a-152">The communication protocols, as described by the endpoint's policy, are mismatched between endpoints.</span></span> <span data-ttu-id="82f9a-153">Por exemplo, enquadrar a incompatibilidade de tipo de conteúdo ou o tamanho máximo da mensagem excedido.</span><span class="sxs-lookup"><span data-stu-id="82f9a-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="82f9a-154">Se presente fornecer mais informações sobre o erro de protocolo específico.</span><span class="sxs-lookup"><span data-stu-id="82f9a-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="82f9a-155">Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna quando a causa de erro está excedendo MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="82f9a-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="82f9a-156">Recuperação: Certifique-se de remetente e as configurações de protocolo recebidas coincidirem.</span><span class="sxs-lookup"><span data-stu-id="82f9a-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="82f9a-157">Uma maneira de fazer isso é reimportar os metadados (política) do ponto final do serviço e usar a vinculação gerada para recriar o canal.</span><span class="sxs-lookup"><span data-stu-id="82f9a-157">One way to do this is to re-import the service endpoint's metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="82f9a-158">O ponto final remoto é ouvir, mas não está preparado para processar mensagens.</span><span class="sxs-lookup"><span data-stu-id="82f9a-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="82f9a-159">Se estiver presente, a Exceção interna fornece os detalhes de falha soap ou de erro no nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="82f9a-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="82f9a-160">Recuperação: Aguarde e tente novamente a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="82f9a-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="82f9a-161">A operação não foi concluída dentro do período de tempo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="82f9a-162">Pode fornecer detalhes sobre o tempo hámenos.</span><span class="sxs-lookup"><span data-stu-id="82f9a-162">May provide details about the timeout.</span></span>|<span data-ttu-id="82f9a-163">Espere e tente novamente a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="82f9a-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="82f9a-164">Defina um novo tipo de exceção somente se esse tipo corresponder a uma estratégia de recuperação específica diferente de todos os tipos de exceção existentes.</span><span class="sxs-lookup"><span data-stu-id="82f9a-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="82f9a-165">Se você definir um novo tipo de <xref:System.ServiceModel.CommunicationException> exceção, ele deve derivar de ou de uma de suas classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="82f9a-166">Mensagens de Exceção</span><span class="sxs-lookup"><span data-stu-id="82f9a-166">Exception Messages</span></span>  
 <span data-ttu-id="82f9a-167">As mensagens de exceção são direcionadas ao usuário e não ao programa, por isso devem fornecer informações suficientes para ajudar o usuário a entender e resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="82f9a-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="82f9a-168">As três partes essenciais de uma boa mensagem de exceção são:</span><span class="sxs-lookup"><span data-stu-id="82f9a-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="82f9a-169">o que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="82f9a-169">What happened.</span></span> <span data-ttu-id="82f9a-170">Forneça uma descrição clara do problema usando termos que se relacionam com a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="82f9a-170">Provide a clear description of the problem using terms that relate to the user's experience.</span></span> <span data-ttu-id="82f9a-171">Por exemplo, uma mensagem de exceção ruim seria "Seção de configuração inválida".</span><span class="sxs-lookup"><span data-stu-id="82f9a-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="82f9a-172">Isso deixa o usuário se perguntando qual seção de configuração está incorreta e por que ela está incorreta.</span><span class="sxs-lookup"><span data-stu-id="82f9a-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="82f9a-173">Uma mensagem melhorada seria "Configuração inválida de configuração \<> vinculação".</span><span class="sxs-lookup"><span data-stu-id="82f9a-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="82f9a-174">Uma mensagem ainda melhor seria "Não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport".</span><span class="sxs-lookup"><span data-stu-id="82f9a-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="82f9a-175">Esta é uma mensagem muito específica usando termos e nomes que o usuário pode identificar facilmente no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-175">This is a very specific message using terms and names that the user can easily identify in the application's configuration file.</span></span> <span data-ttu-id="82f9a-176">No entanto, ainda faltam alguns componentes-chave.</span><span class="sxs-lookup"><span data-stu-id="82f9a-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="82f9a-177">O significado do erro.</span><span class="sxs-lookup"><span data-stu-id="82f9a-177">The significance of the error.</span></span> <span data-ttu-id="82f9a-178">A menos que a mensagem diga claramente o que o erro significa, é provável que o usuário se pergunte se é um erro fatal ou se pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="82f9a-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="82f9a-179">Em geral, as mensagens devem levar ao significado ou significado do erro.</span><span class="sxs-lookup"><span data-stu-id="82f9a-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="82f9a-180">Para melhorar o exemplo anterior, a mensagem poderia ser "ServiceHost falhou em abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport".</span><span class="sxs-lookup"><span data-stu-id="82f9a-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="82f9a-181">Como o usuário deve corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="82f9a-181">How the user should correct the problem.</span></span> <span data-ttu-id="82f9a-182">A parte mais importante da mensagem é ajudar o usuário a corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="82f9a-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="82f9a-183">A mensagem deve incluir algumas orientações ou dicas sobre o que verificar ou corrigir para remediar o problema.</span><span class="sxs-lookup"><span data-stu-id="82f9a-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="82f9a-184">Por exemplo, "ServiceHost falhou em abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport à vinculação chamada myBinding porque a vinculação já tem um transporte chamado myTransport.</span><span class="sxs-lookup"><span data-stu-id="82f9a-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="82f9a-185">Por favor, certifique-se de que há apenas um transporte na ligação".</span><span class="sxs-lookup"><span data-stu-id="82f9a-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="82f9a-186">Falhas de comunicação</span><span class="sxs-lookup"><span data-stu-id="82f9a-186">Communicating Faults</span></span>  
 <span data-ttu-id="82f9a-187">SOAP 1.1 e SOAP 1.2 definem uma estrutura específica para falhas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="82f9a-188">Existem algumas diferenças entre as duas especificações, mas, em geral, os tipos Mensagem e MensagemFalha são usados para criar e consumir falhas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="82f9a-189">![Lidar com exceções e falhas](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="82f9a-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="82f9a-190">SABÃO 1.2 Falha (esquerda) e SABÃO 1.1 Falha (direita).</span><span class="sxs-lookup"><span data-stu-id="82f9a-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="82f9a-191">Observe que no SOAP 1.1 apenas o elemento Falha é qualificado para namespace.</span><span class="sxs-lookup"><span data-stu-id="82f9a-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="82f9a-192">Soap define uma mensagem de falha como uma mensagem que `<env:Fault>`contém apenas `<env:Body>`um elemento de falha (um elemento cujo nome é ) como uma criança de .</span><span class="sxs-lookup"><span data-stu-id="82f9a-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="82f9a-193">O conteúdo do elemento de falha difere ligeiramente entre SOAP 1.1 e SOAP 1.2, conforme mostrado na figura 1.</span><span class="sxs-lookup"><span data-stu-id="82f9a-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="82f9a-194">No entanto, a <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> classe normaliza essas diferenças em um modelo de objeto:</span><span class="sxs-lookup"><span data-stu-id="82f9a-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```csharp
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 <span data-ttu-id="82f9a-195">A `Code` propriedade corresponde `env:Code` ao `faultCode` (ou em SOAP 1.1) e identifica o tipo de falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="82f9a-196">O SOAP 1.2 define cinco `faultCode` valores permitidos para (por exemplo, Remetente e Receptor) e define um `Subcode` elemento que pode conter qualquer valor de subcódigo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="82f9a-197">(Consulte a [especificação SOAP 1.2](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) para a lista de códigos de falha permitidos e seu significado.) O SOAP 1.1 tem um mecanismo `faultCode` ligeiramente diferente: ele define quatro valores (por exemplo, Cliente e Servidor) que podem ser `faultCodes`estendidos por meio da definição de notações totalmente novas ou usando a notação de ponto para criar mais específicos, por exemplo, Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="82f9a-197">(See the [SOAP 1.2 specification](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="82f9a-198">Quando você usa MessageFault para programar falhas, o FaultCode.Name e FaultCode.Namespace mapeia o nome e o namespace do SOAP 1.2 `env:Code` ou do SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="82f9a-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="82f9a-199">O FaultCode.SubCode `env:Subcode` mapeia para SOAP 1.2 e é nulo para SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="82f9a-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="82f9a-200">Você deve criar novos subcódigos de falha (ou novos códigos de falha se usar SOAP 1.1) se for interessante distinguir programáticamente uma falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="82f9a-201">Isso é análogo à criação de um novo tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="82f9a-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="82f9a-202">Você deve evitar usar a notação de ponto com códigos de falha SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="82f9a-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="82f9a-203">(O [Perfil Básico WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) também desencoraja o uso da notação de dot do código de falha.)</span><span class="sxs-lookup"><span data-stu-id="82f9a-203">(The [WS-I Basic Profile](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) also discourages the use of the fault code dot notation.)</span></span>  
  
```csharp
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 <span data-ttu-id="82f9a-204">A `Reason` propriedade corresponde `env:Reason` à `faultString` (ou em SOAP 1.1) uma descrição de leitura humana da condição de erro análoga à mensagem de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="82f9a-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception's message.</span></span> <span data-ttu-id="82f9a-205">A `FaultReason` classe (e SOAP `env:Reason/faultString`) tem suporte embutido para ter múltiplas traduções no interesse da globalização.</span><span class="sxs-lookup"><span data-stu-id="82f9a-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```csharp
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations
    {
       get;
    }  
  
 }  
```  
  
 <span data-ttu-id="82f9a-206">O conteúdo de detalhes de falha é exposto `GetDetail` \<em `GetReaderAtDetailContents`MessageFault usando vários métodos, incluindo o> T e ().</span><span class="sxs-lookup"><span data-stu-id="82f9a-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="82f9a-207">O detalhe da falha é um elemento opaco para carregar detalhes adicionais sobre a falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="82f9a-208">Isso é útil se houver algum detalhe estruturado arbitrário que você deseja carregar com a falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="82f9a-209">Gerando falhas</span><span class="sxs-lookup"><span data-stu-id="82f9a-209">Generating Faults</span></span>  
 <span data-ttu-id="82f9a-210">Esta seção explica o processo de gerar uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal.</span><span class="sxs-lookup"><span data-stu-id="82f9a-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="82f9a-211">Um exemplo típico é enviar de volta uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="82f9a-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="82f9a-212">Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, pelo contrário, deve lançar uma exceção e deixar que a camada acima decida se converter essa exceção em uma falha e como enviá-la.</span><span class="sxs-lookup"><span data-stu-id="82f9a-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="82f9a-213">Para ajudar nesta conversão, o `FaultConverter` canal deve fornecer uma implementação que pode converter a exceção lançada pelo canal personalizado para a falha apropriada.</span><span class="sxs-lookup"><span data-stu-id="82f9a-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="82f9a-214">`FaultConverter` é definido como:</span><span class="sxs-lookup"><span data-stu-id="82f9a-214">`FaultConverter` is defined as:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,
                                   out Message message);  
}  
```  
  
 <span data-ttu-id="82f9a-215">Cada canal que gera falhas `FaultConverter` personalizadas deve implementá-lo e devolvê-lo de uma chamada para `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="82f9a-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="82f9a-216">A `OnTryCreateFaultMessage` implementação personalizada deve converter a exceção em uma `FaultConverter`falha ou delegar para o canal interno .</span><span class="sxs-lookup"><span data-stu-id="82f9a-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel's `FaultConverter`.</span></span> <span data-ttu-id="82f9a-217">Se o canal for um transporte, ele deve converter a `FaultConverter` exceção `FaultConverter` ou delegar para o codificador ou o padrão fornecido no WCF .</span><span class="sxs-lookup"><span data-stu-id="82f9a-217">If the channel is a transport it must either convert the exception or delegate to the encoder's `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="82f9a-218">O `FaultConverter` padrão converte erros correspondentes às mensagens de falha especificadas por WS-Endereçamento e SOAP.</span><span class="sxs-lookup"><span data-stu-id="82f9a-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="82f9a-219">Aqui está `OnTryCreateFaultMessage` um exemplo de implementação.</span><span class="sxs-lookup"><span data-stu-id="82f9a-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```csharp
public override bool OnTryCreateFaultMessage(Exception exception,
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,
                   out message);  
#else  
    FaultConverter inner =
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="82f9a-220">Uma implicação deste padrão é que as exceções lançadas entre camadas para condições de erro que requerem falhas devem conter informações suficientes para o gerador de falhas correspondente para criar a falha correta.</span><span class="sxs-lookup"><span data-stu-id="82f9a-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="82f9a-221">Como um autor de canal personalizado, você pode definir tipos de exceção que correspondem a diferentes condições de falha se tais exceções ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="82f9a-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="82f9a-222">Observe que exceções que atravessam camadas de canal devem comunicar a condição de erro em vez de dados de falha opacos.</span><span class="sxs-lookup"><span data-stu-id="82f9a-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="82f9a-223">Categorias de falhas</span><span class="sxs-lookup"><span data-stu-id="82f9a-223">Fault Categories</span></span>  
 <span data-ttu-id="82f9a-224">Há geralmente três categorias de falhas:</span><span class="sxs-lookup"><span data-stu-id="82f9a-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="82f9a-225">Falhas que se espalharam por toda a pilha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="82f9a-226">Essas falhas podem ser encontradas em qualquer camada na pilha de canais, por exemplo, InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="82f9a-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="82f9a-227">Falhas que podem ser encontradas em qualquer lugar acima de uma determinada camada na pilha, por exemplo, alguns erros que pertencem a uma transação fluída ou a funções de segurança.</span><span class="sxs-lookup"><span data-stu-id="82f9a-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="82f9a-228">Falhas direcionadas a uma única camada na pilha, por exemplo, erros como falhas numéricas de seqüência WS-RM.</span><span class="sxs-lookup"><span data-stu-id="82f9a-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="82f9a-229">Categoria 1.</span><span class="sxs-lookup"><span data-stu-id="82f9a-229">Category 1.</span></span> <span data-ttu-id="82f9a-230">As falhas são geralmente falhas de Endereçamento ws e SOAP.</span><span class="sxs-lookup"><span data-stu-id="82f9a-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="82f9a-231">A `FaultConverter` classe base fornecida pelo WCF converte erros correspondentes às mensagens de falha especificadas pelo WS-Endereçamento e pelo SOAP para que você não precise lidar com a conversão dessas exceções você mesmo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="82f9a-232">Categoria 2.</span><span class="sxs-lookup"><span data-stu-id="82f9a-232">Category 2.</span></span> <span data-ttu-id="82f9a-233">As falhas ocorrem quando uma camada adiciona uma propriedade à mensagem que não consome completamente informações de mensagem relativas a essa camada.</span><span class="sxs-lookup"><span data-stu-id="82f9a-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="82f9a-234">Erros podem ser detectados mais tarde quando uma camada superior pede à propriedade da mensagem para processar ainda mais as informações da mensagem.</span><span class="sxs-lookup"><span data-stu-id="82f9a-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="82f9a-235">Esses canais devem `GetProperty` implementar o especificado anteriormente para permitir que a camada superior envie de volta a falha correta.</span><span class="sxs-lookup"><span data-stu-id="82f9a-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="82f9a-236">Um exemplo disso é o TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="82f9a-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="82f9a-237">Essa propriedade é adicionada à mensagem sem validar totalmente todos os dados no cabeçalho (isso pode envolver contato com o coordenador de transações distribuídas (DTC).</span><span class="sxs-lookup"><span data-stu-id="82f9a-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="82f9a-238">Categoria 3.</span><span class="sxs-lookup"><span data-stu-id="82f9a-238">Category 3.</span></span> <span data-ttu-id="82f9a-239">As falhas são geradas e enviadas por uma única camada no processador.</span><span class="sxs-lookup"><span data-stu-id="82f9a-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="82f9a-240">Portanto, todas as exceções estão contidas dentro da camada.</span><span class="sxs-lookup"><span data-stu-id="82f9a-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="82f9a-241">Para melhorar a consistência entre os canais e facilitar a manutenção, seu canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha mesmo para falhas internas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="82f9a-242">Interpretando falhas recebidas</span><span class="sxs-lookup"><span data-stu-id="82f9a-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="82f9a-243">Esta seção fornece orientação para gerar a exceção apropriada ao receber uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="82f9a-244">A árvore de decisão para o processamento de uma mensagem em cada camada da pilha é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="82f9a-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="82f9a-245">Se a camada considerar a mensagem inválida, a camada deverá fazer seu processamento de 'mensagem inválida'.</span><span class="sxs-lookup"><span data-stu-id="82f9a-245">If the layer considers the message to be invalid, the layer should do its 'invalid message' processing.</span></span> <span data-ttu-id="82f9a-246">Esse processamento é específico para a camada, mas pode incluir deixar cair a mensagem, rastrear ou lançar uma exceção que é convertida em uma falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="82f9a-247">Exemplos incluem o recebimento de uma mensagem que não está segura adequadamente ou o RM recebendo uma mensagem com um número de seqüência ruim.</span><span class="sxs-lookup"><span data-stu-id="82f9a-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="82f9a-248">Caso contrário, se a mensagem for uma mensagem de falha que se aplica especificamente à camada e a mensagem não for significativa fora da interação da camada, a camada deve lidar com a condição de erro.</span><span class="sxs-lookup"><span data-stu-id="82f9a-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer's interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="82f9a-249">Um exemplo disso é uma falha rm seqüenciada recusada que não tem sentido para camadas acima do canal RM e que implica a falha do canal RM e o lançamento de operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="82f9a-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="82f9a-250">Caso contrário, a mensagem deve ser devolvida de Solicitação() ou Receber().</span><span class="sxs-lookup"><span data-stu-id="82f9a-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="82f9a-251">Isso inclui casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falhou e não implica falhando no canal e jogando de operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="82f9a-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="82f9a-252">Para melhorar a usabilidade nesse caso, `GetProperty<FaultConverter>` a `FaultConverter` camada deve implementar e retornar uma classe `OnTryCreateException`derivada que pode converter a falha em uma exceção, substituindo .</span><span class="sxs-lookup"><span data-stu-id="82f9a-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="82f9a-253">O modelo de objeto a seguir suporta a conversão de mensagens em exceções:</span><span class="sxs-lookup"><span data-stu-id="82f9a-253">The following object model supports converting messages to exceptions:</span></span>  
  
```csharp
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,
                                 MessageFault fault,
                                 out Exception exception);  
}  
```  
  
 <span data-ttu-id="82f9a-254">Uma camada de `GetProperty<FaultConverter>` canal pode ser implementada para suportar a conversão de mensagens de falha em exceções.</span><span class="sxs-lookup"><span data-stu-id="82f9a-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="82f9a-255">Para isso, anule `OnTryCreateException` e inspecione a mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="82f9a-256">Se reconhecido, faça a conversão, caso contrário, peça ao canal interno para convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="82f9a-257">Os canais de `FaultConverter.GetDefaultFaultConverter` transporte devem delegar para obter o Conversor de falhas de endereçamento de SABÃO/WS padrão.</span><span class="sxs-lookup"><span data-stu-id="82f9a-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="82f9a-258">Uma implementação típica é assim:</span><span class="sxs-lookup"><span data-stu-id="82f9a-258">A typical implementation looks like this:</span></span>  
  
```csharp
public override bool OnTryCreateException(  
                            Message message,
                            MessageFault fault,
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="82f9a-259">Para condições específicas de falha que tenham cenários de `ProtocolException`recuperação distintos, considere definir uma classe derivada de .</span><span class="sxs-lookup"><span data-stu-id="82f9a-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="82f9a-260">Deveentender processamento</span><span class="sxs-lookup"><span data-stu-id="82f9a-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="82f9a-261">Soap define uma falha geral para sinalizar que um cabeçalho necessário não foi compreendido pelo receptor.</span><span class="sxs-lookup"><span data-stu-id="82f9a-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="82f9a-262">Essa falha é `mustUnderstand` conhecida como a falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="82f9a-263">No WCF, canais `mustUnderstand` personalizados nunca geram falhas.</span><span class="sxs-lookup"><span data-stu-id="82f9a-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="82f9a-264">Em vez disso, o WCF Dispatcher, que está localizado no topo da pilha de comunicação WCF, verifica se todos os cabeçalhos marcados como MustUnderstand=true foram compreendidos pela pilha subjacente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="82f9a-265">Se algum não foi `mustUnderstand` compreendido, uma falha é gerada nesse ponto.</span><span class="sxs-lookup"><span data-stu-id="82f9a-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="82f9a-266">(O usuário pode optar `mustUnderstand` por desativar esse processamento e fazer com que o aplicativo receba todos os cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="82f9a-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="82f9a-267">Nesse caso, o aplicativo é `mustUnderstand` responsável pela realização do processamento.) A falha gerada inclui um cabeçalho Não Entendido que contém os nomes de todos os cabeçalhos com MustUnderstand=true que não foram compreendidos.</span><span class="sxs-lookup"><span data-stu-id="82f9a-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="82f9a-268">Se o seu canal de protocolo envia um `mustUnderstand` cabeçalho personalizado com MustUnderstand=true e recebe uma falha, ele deve descobrir se essa falha é devido ao cabeçalho enviado.</span><span class="sxs-lookup"><span data-stu-id="82f9a-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="82f9a-269">Há dois membros `MessageFault` na classe que são úteis para isso:</span><span class="sxs-lookup"><span data-stu-id="82f9a-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="82f9a-270">`IsMustUnderstandFault`retorna `true` se a `mustUnderstand` falha for uma falha.</span><span class="sxs-lookup"><span data-stu-id="82f9a-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="82f9a-271">`WasHeaderNotUnderstood`retorna `true` se o cabeçalho com o nome e o namespace especificados estiver incluído na falha como um cabeçalho Não Entendido.</span><span class="sxs-lookup"><span data-stu-id="82f9a-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="82f9a-272">Caso contrário, ele retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="82f9a-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="82f9a-273">Se um canal emite um cabeçalho marcado MustUnderstand = true, então essa `mustUnderstand` camada também deve implementar o padrão de API de geração de exceção e deve converter falhas causadas por esse cabeçalho para uma exceção mais útil como descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="82f9a-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="82f9a-274">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="82f9a-274">Tracing</span></span>  
 <span data-ttu-id="82f9a-275">O .NET Framework fornece um mecanismo para rastrear a execução do programa como uma forma de ajudar a diagnosticar aplicações de produção ou problemas intermitentes onde não é possível apenas anexar um depurador e passar pelo código.</span><span class="sxs-lookup"><span data-stu-id="82f9a-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="82f9a-276">Os componentes principais deste <xref:System.Diagnostics?displayProperty=nameWithType> mecanismo estão no namespace e consistem em:</span><span class="sxs-lookup"><span data-stu-id="82f9a-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="82f9a-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a fonte de <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>informações de rastreamento a serem escritas, que é uma <xref:System.Diagnostics.TraceSource> classe base abstrata para ouvintes concretos que recebem as informações a serem rastreadas a partir da e a saída para um destino específico do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="82f9a-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="82f9a-278">Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> as saídas rastreiam informações para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="82f9a-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="82f9a-279">Finalmente, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>o que permite ao usuário do aplicativo controlar a verbosidade de rastreamento e é tipicamente especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="82f9a-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="82f9a-280">Além dos componentes principais, você pode usar a [Ferramenta de Visualização de Rastreamento de Serviço (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) para visualizar e pesquisar traços WCF.</span><span class="sxs-lookup"><span data-stu-id="82f9a-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="82f9a-281">A ferramenta foi projetada especificamente para rastrear arquivos <xref:System.Diagnostics.XmlWriterTraceListener>gerados pelo WCF e escritos usando .</span><span class="sxs-lookup"><span data-stu-id="82f9a-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="82f9a-282">A figura a seguir mostra os vários componentes envolvidos no rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="82f9a-283">![Lidar com exceções e falhas](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="82f9a-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="82f9a-284">Rastreamento de um canal personalizado</span><span class="sxs-lookup"><span data-stu-id="82f9a-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="82f9a-285">Os canais personalizados devem escrever mensagens de rastreamento para ajudar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="82f9a-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="82f9a-286">Isso envolve duas tarefas de alto <xref:System.Diagnostics.TraceSource> nível: instanciar um e chamar seus métodos para escrever traços.</span><span class="sxs-lookup"><span data-stu-id="82f9a-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="82f9a-287">Ao instanciar <xref:System.Diagnostics.TraceSource>um , a seqüência especificada torna-se o nome dessa fonte.</span><span class="sxs-lookup"><span data-stu-id="82f9a-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="82f9a-288">Este nome é usado para configurar (ativar/desativar/definir o nível de rastreamento) a fonte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="82f9a-289">Também aparece na própria saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="82f9a-290">Os canais personalizados devem usar um nome de origem exclusivo para ajudar os leitores da saída de rastreamento a entender de onde as informações de rastreamento vêm.</span><span class="sxs-lookup"><span data-stu-id="82f9a-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="82f9a-291">Usar o nome da assembléia que está escrevendo a informação como o nome da fonte de rastreamento é a prática comum.</span><span class="sxs-lookup"><span data-stu-id="82f9a-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="82f9a-292">Por exemplo, o WCF usa system.serviceModel como fonte de rastreamento de informações escritas a partir do conjunto System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="82f9a-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="82f9a-293">Uma vez que você tenha <xref:System.Diagnostics.TraceSource.TraceData%2A>uma <xref:System.Diagnostics.TraceSource.TraceEvent%2A>fonte <xref:System.Diagnostics.TraceSource.TraceInformation%2A> de rastreamento, você chama seus métodos ou métodos para escrever entradas de rastreamento para os ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="82f9a-294">Para cada entrada de rastreamento que você escreve, você precisa classificar <xref:System.Diagnostics.TraceEventType>o tipo de evento como um dos tipos de evento definidos em .</span><span class="sxs-lookup"><span data-stu-id="82f9a-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="82f9a-295">Esta classificação e a configuração do nível de rastreamento na configuração determinam se a entrada de rastreamento é saída para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="82f9a-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="82f9a-296">Por exemplo, definir o nível `Warning` `Warning`de `Error` `Critical` rastreamento na configuração permite e rastrear entradas a serem escritas, mas bloqueia informações e entradas Verbose.</span><span class="sxs-lookup"><span data-stu-id="82f9a-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="82f9a-297">Aqui está um exemplo de instanciar uma fonte de rastreamento e escrever uma entrada no nível de informação:</span><span class="sxs-lookup"><span data-stu-id="82f9a-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="82f9a-298">É altamente recomendável que você especifique um nome de origem de rastreamento exclusivo do seu canal personalizado para ajudar os leitores de saída a rastrear a entender de onde a saída veio.</span><span class="sxs-lookup"><span data-stu-id="82f9a-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="82f9a-299">Integrando-se com o Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="82f9a-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="82f9a-300">Os traços gerados pelo seu canal podem ser produzidos em um formato legível pela <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> Service Trace Viewer Tool [(SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) usando como ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="82f9a-301">Isso não é algo que você, como desenvolvedor de canais, precisa fazer.</span><span class="sxs-lookup"><span data-stu-id="82f9a-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="82f9a-302">Em vez disso, é o usuário do aplicativo (ou a pessoa que soluciona o aplicativo) que precisa configurar esse ouvinte de rastreamento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82f9a-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application's configuration file.</span></span> <span data-ttu-id="82f9a-303">Por exemplo, as seguintes saídas <xref:System.ServiceModel?displayProperty=nameWithType> `Microsoft.Samples.Udp` de configuração `TraceEventsFile.e2e`rastreiam informações de ambos e para o arquivo nomeado:</span><span class="sxs-lookup"><span data-stu-id="82f9a-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="82f9a-304">Rastreamento de dados estruturados</span><span class="sxs-lookup"><span data-stu-id="82f9a-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="82f9a-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>tem <xref:System.Diagnostics.TraceSource.TraceData%2A> um método que leva um ou mais objetos que devem ser incluídos na entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="82f9a-306">Em geral, <xref:System.Object.ToString%2A?displayProperty=nameWithType> o método é chamado em cada objeto e a seqüência resultante é escrita como parte da entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="82f9a-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="82f9a-307">Ao <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> usar para rastrear saque, você pode passar um <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> como objeto de dados para <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="82f9a-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="82f9a-308">A entrada de rastreamento resultante inclui o <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>XML fornecido pelo .</span><span class="sxs-lookup"><span data-stu-id="82f9a-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82f9a-309">Aqui está um exemplo de entrada com dados do aplicativo XML:</span><span class="sxs-lookup"><span data-stu-id="82f9a-309">Here is an example entry with XML application data:</span></span>  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 <span data-ttu-id="82f9a-310">O visualizador de rastreamento WCF entende `TraceRecord` o esquema do elemento mostrado anteriormente e extrai os dados de seus elementos infantis e os exibe em um formato tabular.</span><span class="sxs-lookup"><span data-stu-id="82f9a-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="82f9a-311">Seu canal deve usar esse esquema ao rastrear dados estruturados do aplicativo para ajudar os usuários do Svctraceviewer.exe a ler os dados.</span><span class="sxs-lookup"><span data-stu-id="82f9a-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 4f95907d4f88315f2815b84e2ceb4e069783438d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851270"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="b0109-102">Lidando com exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="b0109-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="b0109-103">As exceções são usadas para comunicar erros localmente no serviço ou na implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="b0109-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="b0109-104">As falhas, por outro lado, são usadas para comunicar erros entre limites de serviço, como do servidor para o cliente ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="b0109-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="b0109-105">Além das falhas, os canais de transporte geralmente usam mecanismos específicos de transporte para comunicar erros no nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="b0109-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="b0109-106">Por exemplo, o transporte HTTP usa códigos de status como 404 para comunicar uma URL de ponto de extremidade não existente (não há nenhum ponto de extremidade para enviar de volta uma falha).</span><span class="sxs-lookup"><span data-stu-id="b0109-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="b0109-107">Este documento consiste em três seções que fornecem orientação aos autores de canal personalizados.</span><span class="sxs-lookup"><span data-stu-id="b0109-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="b0109-108">A primeira seção fornece orientação sobre quando e como definir e lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="b0109-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="b0109-109">A segunda seção fornece orientação sobre como gerar e consumir falhas.</span><span class="sxs-lookup"><span data-stu-id="b0109-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="b0109-110">A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário do seu canal personalizado na solução de problemas de aplicativos em execução.</span><span class="sxs-lookup"><span data-stu-id="b0109-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="b0109-111">Exceções</span><span class="sxs-lookup"><span data-stu-id="b0109-111">Exceptions</span></span>  
 <span data-ttu-id="b0109-112">Há duas coisas a ter em mente ao lançar uma exceção: Primeiro, ele precisa ser de um tipo que permita que os usuários escrevam o código correto que possa reagir adequadamente à exceção.</span><span class="sxs-lookup"><span data-stu-id="b0109-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="b0109-113">Em segundo lugar, ele precisa fornecer informações suficientes para que o usuário entenda o que deu errado, o impacto da falha e como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="b0109-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="b0109-114">As seções a seguir fornecem orientação sobre tipos de exceção e mensagens para canais de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b0109-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="b0109-115">Também há orientações gerais sobre exceções no .NET no documento diretrizes de design para exceções.</span><span class="sxs-lookup"><span data-stu-id="b0109-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="b0109-116">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="b0109-116">Exception Types</span></span>  
 <span data-ttu-id="b0109-117">Todas as exceções geradas por canais devem ser <xref:System.TimeoutException?displayProperty=nameWithType>um <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, ou um tipo derivado de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b0109-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="b0109-118">(Exceções como <xref:System.ObjectDisposedException> também podem ser geradas, mas apenas para indicar que o código de chamada tenha usado o canal inutilizadomente.</span><span class="sxs-lookup"><span data-stu-id="b0109-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="b0109-119">Se um canal for usado corretamente, ele só deverá lançar as exceções determinadas.) O WCF fornece sete tipos de exceção que <xref:System.ServiceModel.CommunicationException> derivam de e são projetados para serem usados por canais.</span><span class="sxs-lookup"><span data-stu-id="b0109-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="b0109-120">Há outras <xref:System.ServiceModel.CommunicationException>exceções derivadas que são projetadas para serem usadas por outras partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="b0109-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="b0109-121">Esses tipos de exceção são:</span><span class="sxs-lookup"><span data-stu-id="b0109-121">These exception types are:</span></span>  
  
|<span data-ttu-id="b0109-122">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="b0109-122">Exception Type</span></span>|<span data-ttu-id="b0109-123">Significado</span><span class="sxs-lookup"><span data-stu-id="b0109-123">Meaning</span></span>|<span data-ttu-id="b0109-124">Conteúdo de exceção interna</span><span class="sxs-lookup"><span data-stu-id="b0109-124">Inner Exception Content</span></span>|<span data-ttu-id="b0109-125">Estratégia de recuperação</span><span class="sxs-lookup"><span data-stu-id="b0109-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="b0109-126">O endereço do ponto de extremidade especificado para escuta já está em uso.</span><span class="sxs-lookup"><span data-stu-id="b0109-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="b0109-127">Se presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="b0109-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="b0109-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0109-128">For example.</span></span> <span data-ttu-id="b0109-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>ou .<xref:System.Net.Sockets.SocketException></span><span class="sxs-lookup"><span data-stu-id="b0109-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="b0109-130">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="b0109-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="b0109-131">O processo não tem permissão para acessar o endereço do ponto de extremidade especificado para escuta.</span><span class="sxs-lookup"><span data-stu-id="b0109-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="b0109-132">Se presente, fornece mais detalhes sobre o erro de transporte que causou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="b0109-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="b0109-133">Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="b0109-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="b0109-134">Tente com credenciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="b0109-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="b0109-135">O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado está no estado com falha (para obter mais informações, consulte [noções básicas sobre alterações de estado](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="b0109-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="b0109-136">Observe que quando um objeto com várias chamadas pendentes faz a transição para o estado com falha, apenas uma chamada gera uma exceção que está relacionada à falha e o restante das chamadas lançam <xref:System.ServiceModel.CommunicationObjectFaultedException>um.</span><span class="sxs-lookup"><span data-stu-id="b0109-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="b0109-137">Essa exceção normalmente é gerada porque um aplicativo ignora alguma exceção e tenta usar um objeto já com falha, possivelmente em um thread diferente daquele que capturou a exceção original.</span><span class="sxs-lookup"><span data-stu-id="b0109-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="b0109-138">Se presente, fornece detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="b0109-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="b0109-139">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="b0109-139">Create a new object.</span></span> <span data-ttu-id="b0109-140">Observe que, dependendo do que causou a <xref:System.ServiceModel.ICommunicationObject> falha em primeiro lugar, pode haver outro trabalho necessário para a recuperação.</span><span class="sxs-lookup"><span data-stu-id="b0109-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="b0109-141">O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado foi anulado (para obter mais informações, consulte [noções básicas sobre alterações de estado](understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="b0109-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="b0109-142">Semelhante a <xref:System.ServiceModel.CommunicationObjectFaultedException>, sua exceção indica que o aplicativo foi <xref:System.ServiceModel.ICommunicationObject.Abort%2A> chamado no objeto, possivelmente de outro thread, e o objeto não pode mais ser usado por esse motivo.</span><span class="sxs-lookup"><span data-stu-id="b0109-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="b0109-143">Se presente, fornece detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="b0109-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="b0109-144">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="b0109-144">Create a new object.</span></span> <span data-ttu-id="b0109-145">Observe que, dependendo do que causou a <xref:System.ServiceModel.ICommunicationObject> anulação em primeiro lugar, pode haver outro trabalho necessário para a recuperação.</span><span class="sxs-lookup"><span data-stu-id="b0109-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="b0109-146">O ponto de extremidade remoto de destino não está escutando.</span><span class="sxs-lookup"><span data-stu-id="b0109-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="b0109-147">Isso pode resultar de qualquer parte do endereço do ponto de extremidade estar incorreta, não resolvível ou o ponto de extremidade estar inativo.</span><span class="sxs-lookup"><span data-stu-id="b0109-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="b0109-148">Os exemplos incluem erro DNS, Gerenciador de filas não disponível e serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="b0109-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="b0109-149">A exceção interna fornece detalhes, normalmente do transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="b0109-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="b0109-150">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="b0109-150">Try a different address.</span></span> <span data-ttu-id="b0109-151">Como alternativa, o remetente pode aguardar um pouco e tentar novamente no caso de o serviço estar inoperante</span><span class="sxs-lookup"><span data-stu-id="b0109-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="b0109-152">Os protocolos de comunicação, conforme descrito pela política do ponto de extremidade, não correspondem entre os pontos de extremidades.</span><span class="sxs-lookup"><span data-stu-id="b0109-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="b0109-153">Por exemplo, incompatibilidade de tipo de conteúdo de enquadramento ou tamanho máximo de mensagem excedido.</span><span class="sxs-lookup"><span data-stu-id="b0109-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="b0109-154">Se presente, fornece mais informações sobre o erro de protocolo específico.</span><span class="sxs-lookup"><span data-stu-id="b0109-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="b0109-155">Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna quando a causa do erro está excedendo MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="b0109-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="b0109-156">Automatiza Verifique se as configurações de protocolo remetente e recebido correspondem.</span><span class="sxs-lookup"><span data-stu-id="b0109-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="b0109-157">Uma maneira de fazer isso é importar novamente os metadados do ponto de extremidade de serviço (política) e usar a associação gerada para recriar o canal.</span><span class="sxs-lookup"><span data-stu-id="b0109-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="b0109-158">O ponto de extremidade remoto está escutando, mas não está preparado para processar mensagens.</span><span class="sxs-lookup"><span data-stu-id="b0109-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="b0109-159">Se estiver presente, a exceção interna fornecerá os detalhes de erro de nível de transporte ou falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0109-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="b0109-160">Automatiza Aguarde e repita a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="b0109-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="b0109-161">A operação não pôde ser concluída dentro do período de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b0109-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="b0109-162">Pode fornecer detalhes sobre o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b0109-162">May provide details about the timeout.</span></span>|<span data-ttu-id="b0109-163">Aguarde e repita a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="b0109-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="b0109-164">Defina um novo tipo de exceção somente se esse tipo corresponder a uma estratégia de recuperação específica diferente de todos os tipos de exceção existentes.</span><span class="sxs-lookup"><span data-stu-id="b0109-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="b0109-165">Se você definir um novo tipo de exceção, ele deverá derivar <xref:System.ServiceModel.CommunicationException> de ou de uma de suas classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="b0109-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="b0109-166">Mensagens de exceção</span><span class="sxs-lookup"><span data-stu-id="b0109-166">Exception Messages</span></span>  
 <span data-ttu-id="b0109-167">As mensagens de exceção são destinadas ao usuário não ao programa para que elas forneçam informações suficientes para ajudar o usuário a entender e resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="b0109-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="b0109-168">As três partes essenciais de uma boa mensagem de exceção são:</span><span class="sxs-lookup"><span data-stu-id="b0109-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="b0109-169">O que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="b0109-169">What happened.</span></span> <span data-ttu-id="b0109-170">Forneça uma descrição clara do problema usando termos relacionados à experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="b0109-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="b0109-171">Por exemplo, uma mensagem de exceção incorreta seria "seção de configuração inválida".</span><span class="sxs-lookup"><span data-stu-id="b0109-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="b0109-172">Isso deixa o usuário se perguntando qual seção de configuração está incorreta e por que está incorreta.</span><span class="sxs-lookup"><span data-stu-id="b0109-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="b0109-173">Uma mensagem aprimorada seria "inválida > \<da seção de configuração".</span><span class="sxs-lookup"><span data-stu-id="b0109-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="b0109-174">Uma mensagem ainda melhor seria "não é possível adicionar o transporte chamado mytransporte à associação chamada myBinding porque a associação já tem um transporte chamado mytransport".</span><span class="sxs-lookup"><span data-stu-id="b0109-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="b0109-175">Essa é uma mensagem muito específica usando os termos e nomes que o usuário pode identificar facilmente no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0109-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="b0109-176">No entanto, ainda existem alguns componentes-chave ausentes.</span><span class="sxs-lookup"><span data-stu-id="b0109-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="b0109-177">O significado do erro.</span><span class="sxs-lookup"><span data-stu-id="b0109-177">The significance of the error.</span></span> <span data-ttu-id="b0109-178">A menos que a mensagem declare claramente o que o erro significa, é provável que o usuário se pergunte se é um erro fatal ou se pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="b0109-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="b0109-179">Em geral, as mensagens devem conduzir o significado ou o significado do erro.</span><span class="sxs-lookup"><span data-stu-id="b0109-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="b0109-180">Para melhorar o exemplo anterior, a mensagem poderia ser "falha do ServiceHost ao abrir devido a um erro de configuração: Não é possível adicionar o transporte denominado mytransporte à associação chamada myBinding porque a associação já tem um transporte chamado mytransport ".</span><span class="sxs-lookup"><span data-stu-id="b0109-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="b0109-181">Como o usuário deve corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="b0109-181">How the user should correct the problem.</span></span> <span data-ttu-id="b0109-182">A parte mais importante da mensagem é ajudar o usuário a corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="b0109-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="b0109-183">A mensagem deve incluir algumas diretrizes ou dicas sobre o que verificar ou corrigir para corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="b0109-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="b0109-184">Por exemplo, "falha do ServiceHost ao abrir devido a um erro de configuração: Não é possível adicionar o transporte denominado mytransporte à associação chamada myBinding porque a associação já tem um transporte chamado mytransporte.</span><span class="sxs-lookup"><span data-stu-id="b0109-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="b0109-185">Verifique se há apenas um transporte na associação ".</span><span class="sxs-lookup"><span data-stu-id="b0109-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="b0109-186">Falhas de comunicação</span><span class="sxs-lookup"><span data-stu-id="b0109-186">Communicating Faults</span></span>  
 <span data-ttu-id="b0109-187">SOAP 1,1 e SOAP 1,2 definem uma estrutura específica para falhas.</span><span class="sxs-lookup"><span data-stu-id="b0109-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="b0109-188">Há algumas diferenças entre as duas especificações, mas, em geral, os tipos de mensagem e MessageFault são usados para criar e consumir falhas.</span><span class="sxs-lookup"><span data-stu-id="b0109-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="b0109-189">![Tratamento de exceções e falhas](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="b0109-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="b0109-190">Falha de SOAP 1,2 (esquerda) e falha de SOAP 1,1 (direita).</span><span class="sxs-lookup"><span data-stu-id="b0109-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="b0109-191">Observe que, em SOAP 1,1, somente o elemento fault é qualificado como namespace.</span><span class="sxs-lookup"><span data-stu-id="b0109-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="b0109-192">O SOAP define uma mensagem de falha como uma mensagem que contém apenas um elemento Fault (um elemento cujo `<env:Fault>`nome é) como um `<env:Body>`filho de.</span><span class="sxs-lookup"><span data-stu-id="b0109-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="b0109-193">O conteúdo do elemento Fault difere ligeiramente entre SOAP 1,1 e SOAP 1,2, como mostra a Figura 1.</span><span class="sxs-lookup"><span data-stu-id="b0109-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="b0109-194">No entanto <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> , a classe normaliza essas diferenças em um modelo de objeto:</span><span class="sxs-lookup"><span data-stu-id="b0109-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
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
  
 <span data-ttu-id="b0109-195">A `Code` propriedade corresponde `env:Code` ao (ou `faultCode` em SOAP 1,1) e identifica o tipo de falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="b0109-196">O SOAP 1,2 define cinco valores permitidos para `faultCode` (por exemplo, remetente e destinatário) e define um `Subcode` elemento que pode conter qualquer valor de subcódigo.</span><span class="sxs-lookup"><span data-stu-id="b0109-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="b0109-197">(Consulte a [especificação SOAP 1,2](https://go.microsoft.com/fwlink/?LinkId=95176) para obter a lista de códigos de falha permitidos e seu significado.) O SOAP 1,1 tem um mecanismo ligeiramente diferente: Ele define quatro `faultCode` valores (por exemplo, cliente e servidor) que podem ser estendidos definindo totalmente novos ou usando a notação de ponto para criar mais específicos `faultCodes`, por exemplo, Client. Authentication.</span><span class="sxs-lookup"><span data-stu-id="b0109-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="b0109-198">Quando você usa MessageFault para programar falhas, o FaultCode.Name e o FaultCode. namespace são mapeados para o nome e o namespace `env:Code` do SOAP 1,2 ou `faultCode`SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="b0109-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="b0109-199">O subcódigo FaultCode. é mapeado `env:Subcode` para para SOAP 1,2 e é nulo para SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="b0109-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="b0109-200">Você deve criar novos subcódigos de falha (ou novos códigos de falha se estiver usando SOAP 1,1) se for interessante distinguir programaticamente uma falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="b0109-201">Isso é análogo à criação de um novo tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="b0109-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="b0109-202">Evite usar a notação de ponto com os códigos de falha SOAP 1,1.</span><span class="sxs-lookup"><span data-stu-id="b0109-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="b0109-203">(O [perfil básico WS-I](https://go.microsoft.com/fwlink/?LinkId=95177) também desencoraja o uso da notação de ponto de código de falha.)</span><span class="sxs-lookup"><span data-stu-id="b0109-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
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
  
 <span data-ttu-id="b0109-204">A `Reason` propriedade corresponde `env:Reason` ao (ou `faultString` em SOAP 1,1) uma descrição legível por humanos da condição de erro análoga à mensagem de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b0109-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="b0109-205">A `FaultReason` classe (e SOAP `env:Reason/faultString`) tem suporte interno para ter várias traduções no interesse da globalização.</span><span class="sxs-lookup"><span data-stu-id="b0109-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
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
  
 <span data-ttu-id="b0109-206">Os conteúdos de detalhes de falhas são expostos em MessageFault usando vários métodos `GetDetail`, incluindo o `GetReaderAtDetailContents` \<T > e ().</span><span class="sxs-lookup"><span data-stu-id="b0109-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="b0109-207">O detalhe da falha é um elemento opaco para a realização de detalhes adicionais sobre a falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="b0109-208">Isso é útil se houver alguns detalhes estruturados arbitrários que você deseja transportar com a falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="b0109-209">Gerando falhas</span><span class="sxs-lookup"><span data-stu-id="b0109-209">Generating Faults</span></span>  
 <span data-ttu-id="b0109-210">Esta seção explica o processo de gerar uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal.</span><span class="sxs-lookup"><span data-stu-id="b0109-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="b0109-211">Um exemplo típico é enviar de volta uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="b0109-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="b0109-212">Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, em vez disso, ele deve gerar uma exceção e permitir que a camada acima decida se deseja converter essa exceção em uma falha e como enviá-la.</span><span class="sxs-lookup"><span data-stu-id="b0109-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="b0109-213">Para auxiliar nessa conversão, o canal deve fornecer uma `FaultConverter` implementação que possa converter a exceção gerada pelo canal personalizado para a falha apropriada.</span><span class="sxs-lookup"><span data-stu-id="b0109-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="b0109-214">`FaultConverter` é definido como:</span><span class="sxs-lookup"><span data-stu-id="b0109-214">`FaultConverter` is defined as:</span></span>  
  
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
  
 <span data-ttu-id="b0109-215">Cada canal que gera falhas personalizadas deve implementá `FaultConverter` -la e retorná-la `GetProperty<FaultConverter>`de uma chamada para.</span><span class="sxs-lookup"><span data-stu-id="b0109-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="b0109-216">A implementação `OnTryCreateFaultMessage` personalizada deve converter a exceção em uma falha ou delegar para o `FaultConverter`canal interno.</span><span class="sxs-lookup"><span data-stu-id="b0109-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="b0109-217">Se o canal for um transporte, ele deverá converter a exceção ou o delegado para o codificador `FaultConverter` ou o padrão `FaultConverter` fornecido no WCF.</span><span class="sxs-lookup"><span data-stu-id="b0109-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="b0109-218">O padrão `FaultConverter` converte erros correspondentes às mensagens de falha especificadas por WS-Addressing e SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0109-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="b0109-219">Aqui está um exemplo `OnTryCreateFaultMessage` de implementação.</span><span class="sxs-lookup"><span data-stu-id="b0109-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
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
  
 <span data-ttu-id="b0109-220">Uma implicação desse padrão é que as exceções geradas entre camadas para condições de erro que exigem falhas devem conter informações suficientes para o gerador de falhas correspondente criar a falha correta.</span><span class="sxs-lookup"><span data-stu-id="b0109-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="b0109-221">Como um autor de canal personalizado, você pode definir tipos de exceção que correspondam a diferentes condições de falha se essas exceções ainda não existirem.</span><span class="sxs-lookup"><span data-stu-id="b0109-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="b0109-222">Observe que as exceções que atravessam as camadas de canal devem comunicar a condição de erro em vez dos dados de falha opacos.</span><span class="sxs-lookup"><span data-stu-id="b0109-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="b0109-223">Categorias de falha</span><span class="sxs-lookup"><span data-stu-id="b0109-223">Fault Categories</span></span>  
 <span data-ttu-id="b0109-224">Em geral, há três categorias de falhas:</span><span class="sxs-lookup"><span data-stu-id="b0109-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="b0109-225">Falhas que são disseminadas em toda a pilha.</span><span class="sxs-lookup"><span data-stu-id="b0109-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="b0109-226">Essas falhas podem ser encontradas em qualquer camada na pilha de canais, por exemplo, InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="b0109-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="b0109-227">Falhas que podem ser encontradas em qualquer lugar acima de uma determinada camada na pilha, por exemplo, alguns erros que pertencem a uma transação fluida ou a funções de segurança.</span><span class="sxs-lookup"><span data-stu-id="b0109-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="b0109-228">Falhas direcionadas a uma única camada na pilha, por exemplo, erros como falhas de número de sequência do WS-RM.</span><span class="sxs-lookup"><span data-stu-id="b0109-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="b0109-229">Categoria 1.</span><span class="sxs-lookup"><span data-stu-id="b0109-229">Category 1.</span></span> <span data-ttu-id="b0109-230">As falhas geralmente são WS-Addressing e falhas de SOAP.</span><span class="sxs-lookup"><span data-stu-id="b0109-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="b0109-231">A classe `FaultConverter` base fornecida pelo WCF converte erros correspondentes a mensagens de falha especificadas por WS-Addressing e SOAP para que você não precise manipular a conversão dessas exceções por conta própria.</span><span class="sxs-lookup"><span data-stu-id="b0109-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="b0109-232">Categoria 2.</span><span class="sxs-lookup"><span data-stu-id="b0109-232">Category 2.</span></span> <span data-ttu-id="b0109-233">As falhas ocorrem quando uma camada adiciona uma propriedade à mensagem que não consome completamente as informações da mensagem que pertencem a essa camada.</span><span class="sxs-lookup"><span data-stu-id="b0109-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="b0109-234">Os erros podem ser detectados mais tarde, quando uma camada superior solicita que a propriedade de mensagem processe as informações da mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0109-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="b0109-235">Esses canais devem implementar o `GetProperty` especificado anteriormente para permitir que a camada superior envie de volta a falha correta.</span><span class="sxs-lookup"><span data-stu-id="b0109-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="b0109-236">Um exemplo disso é o TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="b0109-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="b0109-237">Essa propriedade é adicionada à mensagem sem validar completamente todos os dados no cabeçalho (isso pode envolver o contato com o coordenador de transações distribuídas (DTC).</span><span class="sxs-lookup"><span data-stu-id="b0109-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="b0109-238">Categoria 3.</span><span class="sxs-lookup"><span data-stu-id="b0109-238">Category 3.</span></span> <span data-ttu-id="b0109-239">As falhas são geradas e enviadas por uma única camada no processador.</span><span class="sxs-lookup"><span data-stu-id="b0109-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="b0109-240">Portanto, todas as exceções estão contidas na camada.</span><span class="sxs-lookup"><span data-stu-id="b0109-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="b0109-241">Para melhorar a consistência entre os canais e facilitar a manutenção, seu canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha mesmo para falhas internas.</span><span class="sxs-lookup"><span data-stu-id="b0109-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="b0109-242">Interpretando falhas recebidas</span><span class="sxs-lookup"><span data-stu-id="b0109-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="b0109-243">Esta seção fornece diretrizes para gerar a exceção apropriada ao receber uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="b0109-244">A árvore de decisão para processar uma mensagem em cada camada na pilha é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="b0109-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="b0109-245">Se a camada considerar a mensagem como inválida, a camada deverá fazer o processamento de ' mensagem inválida '.</span><span class="sxs-lookup"><span data-stu-id="b0109-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="b0109-246">Esse processamento é específico para a camada, mas pode incluir descartar a mensagem, rastrear ou lançar uma exceção que é convertida em uma falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="b0109-247">Exemplos incluem segurança que recebe uma mensagem que não está protegida corretamente ou que o RM recebe uma mensagem com um número de sequência inválido.</span><span class="sxs-lookup"><span data-stu-id="b0109-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="b0109-248">Caso contrário, se a mensagem for uma mensagem de falha que se aplica especificamente à camada e a mensagem não for significativa fora da interação da camada, a camada deverá tratar a condição de erro.</span><span class="sxs-lookup"><span data-stu-id="b0109-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="b0109-249">Um exemplo disso é que uma sequência RM recusou a falha que não faz sentido para camadas acima do canal do RM e que implica a falha no canal do RM e o lançamento de operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="b0109-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="b0109-250">Caso contrário, a mensagem deve ser retornada de Request () ou Receive ().</span><span class="sxs-lookup"><span data-stu-id="b0109-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="b0109-251">Isso inclui casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falhou e não implica a falha do canal e o lançamento de operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="b0109-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="b0109-252">Para melhorar a usabilidade nesse caso, a camada deve implementar `GetProperty<FaultConverter>` e retornar uma `FaultConverter` classe derivada que possa converter a falha em uma exceção substituindo `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="b0109-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="b0109-253">O modelo de objeto a seguir dá suporte à conversão de mensagens em exceções:</span><span class="sxs-lookup"><span data-stu-id="b0109-253">The following object model supports converting messages to exceptions:</span></span>  
  
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
  
 <span data-ttu-id="b0109-254">Uma camada de canal pode `GetProperty<FaultConverter>` implementar para dar suporte à conversão de mensagens de falha em exceções.</span><span class="sxs-lookup"><span data-stu-id="b0109-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="b0109-255">Para fazer isso, substitua `OnTryCreateException` e inspecione a mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="b0109-256">Se for reconhecido, faça a conversão, caso contrário, peça ao canal interno para convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="b0109-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="b0109-257">Os canais de transporte devem `FaultConverter.GetDefaultFaultConverter` delegar para obter o padrão SOAP/WS-Addressing com falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="b0109-258">Uma implementação típica tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="b0109-258">A typical implementation looks like this:</span></span>  
  
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
  
 <span data-ttu-id="b0109-259">Para condições de falha específicas que têm cenários de recuperação distintos, considere definir uma `ProtocolException`classe derivada de.</span><span class="sxs-lookup"><span data-stu-id="b0109-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="b0109-260">Processamento de MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="b0109-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="b0109-261">O SOAP define uma falha geral para sinalizar que um cabeçalho necessário não foi compreendido pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="b0109-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="b0109-262">Essa falha é conhecida como a `mustUnderstand` falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="b0109-263">No WCF, os canais personalizados nunca `mustUnderstand` geram falhas.</span><span class="sxs-lookup"><span data-stu-id="b0109-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="b0109-264">Em vez disso, o Dispatcher do WCF, que está localizado na parte superior da pilha de comunicação do WCF, verifica se todos os cabeçalhos que foram marcados como MustUnderstand = true foram compreendidos pela pilha subjacente.</span><span class="sxs-lookup"><span data-stu-id="b0109-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="b0109-265">Se algum não tiver sido compreendido, `mustUnderstand` uma falha será gerada nesse ponto.</span><span class="sxs-lookup"><span data-stu-id="b0109-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="b0109-266">(O usuário pode optar por desativar esse `mustUnderstand` processamento e fazer com que o aplicativo receba todos os cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b0109-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="b0109-267">Nesse caso, o aplicativo é responsável por executar `mustUnderstand` o processamento.) A falha gerada inclui um cabeçalho não compreendido que contém os nomes de todos os cabeçalhos com MustUnderstand = true que não foram compreendidos.</span><span class="sxs-lookup"><span data-stu-id="b0109-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="b0109-268">Se o canal de protocolo enviar um cabeçalho personalizado com MustUnderstand = true e receber `mustUnderstand` uma falha, ele deverá descobrir se a falha é devido ao cabeçalho enviado.</span><span class="sxs-lookup"><span data-stu-id="b0109-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="b0109-269">Há dois membros na `MessageFault` classe que são úteis para isso:</span><span class="sxs-lookup"><span data-stu-id="b0109-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
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
  
 <span data-ttu-id="b0109-270">`IsMustUnderstandFault`retorna `true` se a falha for uma `mustUnderstand` falha.</span><span class="sxs-lookup"><span data-stu-id="b0109-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="b0109-271">`WasHeaderNotUnderstood`retorna `true` se o cabeçalho com o nome e o namespace especificados está incluído na falha como um cabeçalho não compreendido.</span><span class="sxs-lookup"><span data-stu-id="b0109-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="b0109-272">Caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="b0109-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="b0109-273">Se um canal emitir um cabeçalho que está marcado como MustUnderstand = true, essa camada também deverá implementar o padrão de API de geração de exceção e `mustUnderstand` converter as falhas causadas por esse cabeçalho em uma exceção mais útil, conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b0109-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="b0109-274">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="b0109-274">Tracing</span></span>  
 <span data-ttu-id="b0109-275">O .NET Framework fornece um mecanismo para rastrear a execução do programa como uma maneira de ajudar a diagnosticar aplicativos de produção ou problemas intermitentes em que não é possível apenas anexar um depurador e percorrer o código.</span><span class="sxs-lookup"><span data-stu-id="b0109-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="b0109-276">Os principais componentes desse mecanismo estão no <xref:System.Diagnostics?displayProperty=nameWithType> namespace e consistem em:</span><span class="sxs-lookup"><span data-stu-id="b0109-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="b0109-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a fonte de informações de rastreamento a ser escrita <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>,, que é uma classe base abstrata para ouvintes concretos que recebem as informações a serem rastreadas <xref:System.Diagnostics.TraceSource> do e a saída para um destino específico do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="b0109-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="b0109-278">Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> gera informações de rastreamento para um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="b0109-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="b0109-279">Por fim <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>,, que permite que o usuário do aplicativo controle o detalhamento de rastreamento e normalmente é especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="b0109-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="b0109-280">Além dos componentes principais, você pode usar a [ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) para exibir e Pesquisar rastreamentos do WCF.</span><span class="sxs-lookup"><span data-stu-id="b0109-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="b0109-281">A ferramenta foi projetada especificamente para arquivos de rastreamento gerados pelo WCF e escrito usando <xref:System.Diagnostics.XmlWriterTraceListener>o.</span><span class="sxs-lookup"><span data-stu-id="b0109-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="b0109-282">A figura a seguir mostra os vários componentes envolvidos no rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="b0109-283">![Tratamento de exceções e falhas](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="b0109-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="b0109-284">Rastreamento de um canal personalizado</span><span class="sxs-lookup"><span data-stu-id="b0109-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="b0109-285">Os canais personalizados devem gravar mensagens de rastreamento para auxiliar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="b0109-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="b0109-286">Isso envolve duas tarefas de alto nível: Instanciar um <xref:System.Diagnostics.TraceSource> e chamar seus métodos para gravar rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="b0109-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="b0109-287">Ao instanciar um <xref:System.Diagnostics.TraceSource>, a cadeia de caracteres que você especifica se torna o nome dessa fonte.</span><span class="sxs-lookup"><span data-stu-id="b0109-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="b0109-288">Esse nome é usado para configurar (habilitar/desabilitar/definir o nível de rastreamento) a origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="b0109-289">Ele também aparece na saída de rastreamento em si.</span><span class="sxs-lookup"><span data-stu-id="b0109-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="b0109-290">Os canais personalizados devem usar um nome de origem exclusivo para ajudar os leitores da saída de rastreamento a entender de onde vêm as informações de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="b0109-291">O uso do nome do assembly que está gravando as informações como o nome da origem do rastreamento é a prática comum.</span><span class="sxs-lookup"><span data-stu-id="b0109-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="b0109-292">Por exemplo, o WCF usa System. ServiceModel como a origem do rastreamento para informações gravadas do assembly System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b0109-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="b0109-293">Depois de ter uma origem de rastreamento, você chama <xref:System.Diagnostics.TraceSource.TraceData%2A>seus <xref:System.Diagnostics.TraceSource.TraceEvent%2A>métodos, <xref:System.Diagnostics.TraceSource.TraceInformation%2A> ou para gravar entradas de rastreamento para os ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="b0109-294">Para cada entrada de rastreamento que você escreve, você precisa classificar o tipo de evento como um dos tipos de evento definidos <xref:System.Diagnostics.TraceEventType>em.</span><span class="sxs-lookup"><span data-stu-id="b0109-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="b0109-295">Essa classificação e a configuração de nível de rastreamento na configuração determinam se a entrada de rastreamento é a saída para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="b0109-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="b0109-296">Por exemplo, definir o nível de rastreamento na configuração `Warning` para `Warning` `Error` permitir e `Critical` rastrear entradas a serem gravadas, mas bloqueia informações e entradas detalhadas.</span><span class="sxs-lookup"><span data-stu-id="b0109-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="b0109-297">Aqui está um exemplo de instanciação de uma origem de rastreamento e gravação de uma entrada no nível de informação:</span><span class="sxs-lookup"><span data-stu-id="b0109-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="b0109-298">É altamente recomendável que você especifique um nome de origem de rastreamento que seja exclusivo para seu canal personalizado para ajudar os leitores de saída de rastreamento a entender de onde provém a saída.</span><span class="sxs-lookup"><span data-stu-id="b0109-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="b0109-299">Integração com o Visualizador de rastreamento</span><span class="sxs-lookup"><span data-stu-id="b0109-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="b0109-300">Os rastreamentos gerados pelo canal podem ser impressos em um formato legível pela [ferramenta do Visualizador de rastreamento de serviço (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) usando <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> o como o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="b0109-301">Isso não é algo que você, como desenvolvedor do canal, precisa fazer.</span><span class="sxs-lookup"><span data-stu-id="b0109-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="b0109-302">Em vez disso, é o usuário do aplicativo (ou a pessoa que está Solucionando problemas do aplicativo) que precisa configurar esse ouvinte de rastreamento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0109-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="b0109-303">Por exemplo, a configuração a seguir gera informações de rastreamento <xref:System.ServiceModel?displayProperty=nameWithType> de `Microsoft.Samples.Udp` e para o arquivo `TraceEventsFile.e2e`chamado:</span><span class="sxs-lookup"><span data-stu-id="b0109-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="b0109-304">Rastreando dados estruturados</span><span class="sxs-lookup"><span data-stu-id="b0109-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="b0109-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>tem um <xref:System.Diagnostics.TraceSource.TraceData%2A> método que usa um ou mais objetos que devem ser incluídos na entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="b0109-306">Em geral, o <xref:System.Object.ToString%2A?displayProperty=nameWithType> método é chamado em cada objeto e a cadeia de caracteres resultante é gravada como parte da entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="b0109-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="b0109-307">Ao usar <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> para os rastreamentos de saída, você <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> pode passar um como o <xref:System.Diagnostics.TraceSource.TraceData%2A>objeto de dados para.</span><span class="sxs-lookup"><span data-stu-id="b0109-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="b0109-308">A entrada de rastreamento resultante inclui o XML fornecido pelo <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0109-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b0109-309">Aqui está um exemplo de entrada com dados de aplicativo XML:</span><span class="sxs-lookup"><span data-stu-id="b0109-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="b0109-310">O Visualizador de rastreamento do WCF compreende o esquema `TraceRecord` do elemento mostrado anteriormente e extrai os dados de seus elementos filho e os exibe em um formato tabular.</span><span class="sxs-lookup"><span data-stu-id="b0109-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="b0109-311">Seu canal deve usar esse esquema ao rastrear dados de aplicativo estruturados para ajudar os usuários do SvcTraceViewer. exe a ler os dados.</span><span class="sxs-lookup"><span data-stu-id="b0109-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

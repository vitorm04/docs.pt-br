---
title: Lidando com exceções e falhas
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c51d78bb982ec0748cd74a67a4f4b747526a4b42
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483902"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="8ff50-102">Lidando com exceções e falhas</span><span class="sxs-lookup"><span data-stu-id="8ff50-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="8ff50-103">As exceções são usadas para comunicar erros localmente dentro do serviço ou a implementação do cliente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="8ff50-104">Falhas, por outro lado, são usadas para comunicar erros entre limites de serviço, como a do servidor para o cliente ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8ff50-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="8ff50-105">Além das falhas, os canais de transporte geralmente usam mecanismos de transporte específicos para comunicar erros de nível de transporte.</span><span class="sxs-lookup"><span data-stu-id="8ff50-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="8ff50-106">Por exemplo, o transporte HTTP usa códigos de status como 404 para comunicar uma URL de ponto de extremidade não existente (não há nenhum ponto de extremidade para enviar de volta uma falha).</span><span class="sxs-lookup"><span data-stu-id="8ff50-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="8ff50-107">Este documento consiste em três seções que fornecem orientação para os autores de canal personalizado.</span><span class="sxs-lookup"><span data-stu-id="8ff50-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="8ff50-108">A primeira seção fornece orientação sobre quando e como definir e lançar exceções.</span><span class="sxs-lookup"><span data-stu-id="8ff50-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="8ff50-109">A segunda seção fornece orientação sobre como gerar e consumir falhas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="8ff50-110">A terceira seção explica como fornecer informações de rastreamento para ajudar o usuário do seu canal personalizado na solução de problemas de aplicativos em execução.</span><span class="sxs-lookup"><span data-stu-id="8ff50-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="8ff50-111">Exceções</span><span class="sxs-lookup"><span data-stu-id="8ff50-111">Exceptions</span></span>  
 <span data-ttu-id="8ff50-112">Há duas coisas para ter em mente ao lançar uma exceção: primeiro ele deve ser de um tipo que permite aos usuários escrever código correto pode reagir adequadamente a exceção.</span><span class="sxs-lookup"><span data-stu-id="8ff50-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="8ff50-113">Em segundo lugar, ele deve fornecer informações suficientes para que o usuário para entender o que deu errado, o impacto da falha e como corrigi-lo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="8ff50-114">As seções a seguir oferecem orientação sobre tipos de exceção e mensagens para os canais do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8ff50-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="8ff50-115">Também há orientação geral sobre exceções no .NET nas diretrizes de Design para o documento de exceções.</span><span class="sxs-lookup"><span data-stu-id="8ff50-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="8ff50-116">Tipos de exceção</span><span class="sxs-lookup"><span data-stu-id="8ff50-116">Exception Types</span></span>  
 <span data-ttu-id="8ff50-117">Todas as exceções geradas pelos canais devem ser um <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, ou um tipo derivado de <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="8ff50-118">(Exceções, como <xref:System.ObjectDisposedException> também pode ser lançada, mas apenas para indicar que o código de chamada tem usado indevidamente o canal.</span><span class="sxs-lookup"><span data-stu-id="8ff50-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="8ff50-119">Se um canal for usado corretamente, ele deve apenas lançar as exceções de determinado.) O WCF fornece sete tipos de exceções que derivam de <xref:System.ServiceModel.CommunicationException> e foram projetados para ser usado pelos canais.</span><span class="sxs-lookup"><span data-stu-id="8ff50-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="8ff50-120">Há outros <xref:System.ServiceModel.CommunicationException>-derivado exceções que são projetadas para ser usado por outras partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="8ff50-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="8ff50-121">Esses tipos de exceção são:</span><span class="sxs-lookup"><span data-stu-id="8ff50-121">These exception types are:</span></span>  
  
|<span data-ttu-id="8ff50-122">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="8ff50-122">Exception Type</span></span>|<span data-ttu-id="8ff50-123">Significado</span><span class="sxs-lookup"><span data-stu-id="8ff50-123">Meaning</span></span>|<span data-ttu-id="8ff50-124">Conteúdo da exceção interna</span><span class="sxs-lookup"><span data-stu-id="8ff50-124">Inner Exception Content</span></span>|<span data-ttu-id="8ff50-125">Estratégia de recuperação</span><span class="sxs-lookup"><span data-stu-id="8ff50-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="8ff50-126">O endereço de ponto de extremidade especificado para escuta já está em uso.</span><span class="sxs-lookup"><span data-stu-id="8ff50-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="8ff50-127">Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="8ff50-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="8ff50-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8ff50-128">For example.</span></span> <span data-ttu-id="8ff50-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, ou <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="8ff50-130">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="8ff50-131">O processo não é permitido o acesso ao endereço do ponto de extremidade especificado para escuta.</span><span class="sxs-lookup"><span data-stu-id="8ff50-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="8ff50-132">Se estiver presente, fornece mais detalhes sobre o erro de transporte que provocou essa exceção.</span><span class="sxs-lookup"><span data-stu-id="8ff50-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="8ff50-133">Por exemplo, <xref:System.IO.PipeException>, ou <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="8ff50-134">Tente com credenciais diferentes.</span><span class="sxs-lookup"><span data-stu-id="8ff50-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="8ff50-135">O <xref:System.ServiceModel.ICommunicationObject> que está sendo usada está no estado com falha (para obter mais informações, consulte [Noções básicas sobre as alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="8ff50-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="8ff50-136">Observe que, quando um objeto com vários pendentes transições de chamadas para o estado de falha, apenas uma chamada gera uma exceção que está relacionada a falha e o restante do arremesso chamadas um <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="8ff50-137">Essa exceção é lançada normalmente porque ignora completamente uma exceção de um aplicativo e tenta usar um objeto já com defeito, possivelmente em um thread diferente daquele que capturou a exceção original.</span><span class="sxs-lookup"><span data-stu-id="8ff50-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="8ff50-138">Se estiver presente fornece detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="8ff50-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="8ff50-139">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="8ff50-139">Create a new object.</span></span> <span data-ttu-id="8ff50-140">Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para falhas em primeiro lugar, pode haver outro trabalho necessário para recuperar.</span><span class="sxs-lookup"><span data-stu-id="8ff50-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="8ff50-141">O <xref:System.ServiceModel.ICommunicationObject> que está sendo usado foi anulado (para obter mais informações, consulte [Noções básicas sobre as alterações de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="8ff50-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="8ff50-142">Semelhante ao <xref:System.ServiceModel.CommunicationObjectFaultedException>, sua exceção indica que o aplicativo tiver chamado <xref:System.ServiceModel.ICommunicationObject.Abort%2A> no objeto, possivelmente a partir de outro thread, e o objeto não é mais utilizável por esse motivo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="8ff50-143">Se estiver presente fornece detalhes sobre a exceção interna.</span><span class="sxs-lookup"><span data-stu-id="8ff50-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="8ff50-144">Crie um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="8ff50-144">Create a new object.</span></span> <span data-ttu-id="8ff50-145">Observe que, dependendo do que causou o <xref:System.ServiceModel.ICommunicationObject> para anular em primeiro lugar, pode haver outro trabalho necessário para recuperar.</span><span class="sxs-lookup"><span data-stu-id="8ff50-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="8ff50-146">O ponto de extremidade remoto de destino não está escutando.</span><span class="sxs-lookup"><span data-stu-id="8ff50-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="8ff50-147">Isso pode resultar de qualquer parte do endereço do ponto de extremidade que está sendo incorreta, pode resolver ou o ponto de extremidade que está sendo pressionada.</span><span class="sxs-lookup"><span data-stu-id="8ff50-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="8ff50-148">Os exemplos incluem erros DNS, Gerenciador de fila não está disponível e o serviço não está em execução.</span><span class="sxs-lookup"><span data-stu-id="8ff50-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="8ff50-149">A exceção interna fornece detalhes, normalmente de transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="8ff50-150">Tente um endereço diferente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-150">Try a different address.</span></span> <span data-ttu-id="8ff50-151">Como alternativa, o remetente pode Aguarde alguns instantes e tente novamente, caso o serviço foi desativado</span><span class="sxs-lookup"><span data-stu-id="8ff50-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="8ff50-152">Os protocolos de comunicação, conforme descrito pela política do ponto de extremidade, são incompatíveis entre pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8ff50-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="8ff50-153">Por exemplo, de enquadramento incompatibilidade de tipo de conteúdo ou o tamanho máximo de mensagem excedido.</span><span class="sxs-lookup"><span data-stu-id="8ff50-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="8ff50-154">Se estiver presente fornece mais informações sobre o erro de protocolo específico.</span><span class="sxs-lookup"><span data-stu-id="8ff50-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="8ff50-155">Por exemplo, <xref:System.ServiceModel.QuotaExceededException> é a exceção interna à causa do erro é exceder MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="8ff50-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="8ff50-156">Recuperação: Certifique-se o remetente e o protocolo recebido configurações correspondem.</span><span class="sxs-lookup"><span data-stu-id="8ff50-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="8ff50-157">Uma maneira de fazer isso é importar novamente os metadados do ponto de extremidade de serviço (política) e usar a ligação gerada para recriar o canal.</span><span class="sxs-lookup"><span data-stu-id="8ff50-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="8ff50-158">O ponto de extremidade remoto está escutando, mas não está preparado para processar mensagens.</span><span class="sxs-lookup"><span data-stu-id="8ff50-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="8ff50-159">Se estiver presente, a exceção interna fornece os detalhes do erro de nível de transporte ou falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ff50-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="8ff50-160">Recuperação: Aguarde e repita a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8ff50-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="8ff50-161">A operação não foi concluída dentro do período de tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8ff50-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="8ff50-162">Pode fornecer detalhes sobre o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8ff50-162">May provide details about the timeout.</span></span>|<span data-ttu-id="8ff50-163">Aguarde e repita a operação mais tarde.</span><span class="sxs-lookup"><span data-stu-id="8ff50-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="8ff50-164">Defina um novo tipo de exceção apenas se tipo corresponde a uma estratégia de recuperação específico diferente de todos os tipos de exceção existente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="8ff50-165">Se você definir um novo tipo de exceção, ele deve derivar de <xref:System.ServiceModel.CommunicationException> ou uma de suas classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="8ff50-166">Mensagens de exceção</span><span class="sxs-lookup"><span data-stu-id="8ff50-166">Exception Messages</span></span>  
 <span data-ttu-id="8ff50-167">Mensagens de exceção destinam-se o usuário não o programa para que eles devem fornecer informações suficientes para ajudar o usuário a entender e resolver o problema.</span><span class="sxs-lookup"><span data-stu-id="8ff50-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="8ff50-168">As três partes essenciais de uma mensagem de exceção boa são:</span><span class="sxs-lookup"><span data-stu-id="8ff50-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="8ff50-169">O que aconteceu.</span><span class="sxs-lookup"><span data-stu-id="8ff50-169">What happened.</span></span> <span data-ttu-id="8ff50-170">Forneça uma descrição clara do problema usando termos que se relacionam com a experiência do usuário.</span><span class="sxs-lookup"><span data-stu-id="8ff50-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="8ff50-171">Por exemplo, uma mensagem de exceção incorreto seria "seção de configuração inválido".</span><span class="sxs-lookup"><span data-stu-id="8ff50-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="8ff50-172">Isso deixa o usuário está se perguntando qual seção de configuração está incorreta e por que ele está incorreto.</span><span class="sxs-lookup"><span data-stu-id="8ff50-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="8ff50-173">Uma melhor mensagem seria "seção de configuração inválido \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="8ff50-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="8ff50-174">Uma mensagem ainda melhor seria "não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport".</span><span class="sxs-lookup"><span data-stu-id="8ff50-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="8ff50-175">Esta é uma mensagem muito específica usando nomes que o usuário pode identificar facilmente e termos no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="8ff50-176">No entanto, há ainda alguns componentes-chave ausente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="8ff50-177">O significado do erro.</span><span class="sxs-lookup"><span data-stu-id="8ff50-177">The significance of the error.</span></span> <span data-ttu-id="8ff50-178">A menos que a mensagem informa claramente o que significa que o erro, o usuário é provável que você esteja se perguntando se ele é um erro fatal ou se ele pode ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="8ff50-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="8ff50-179">Em geral, as mensagens devem começar com o significado ou a significância do erro.</span><span class="sxs-lookup"><span data-stu-id="8ff50-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="8ff50-180">Para melhorar o exemplo anterior, a mensagem poderia ser "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport".</span><span class="sxs-lookup"><span data-stu-id="8ff50-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="8ff50-181">Como o usuário deve corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="8ff50-181">How the user should correct the problem.</span></span> <span data-ttu-id="8ff50-182">A parte mais importante da mensagem está ajudando a correção do problema do usuário.</span><span class="sxs-lookup"><span data-stu-id="8ff50-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="8ff50-183">A mensagem deve incluir algumas diretrizes ou dicas sobre o que verificar ou corrigir para corrigir o problema.</span><span class="sxs-lookup"><span data-stu-id="8ff50-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="8ff50-184">Por exemplo, "ServiceHost falha ao abrir devido a um erro de configuração: não é possível adicionar o transporte chamado myTransport para a associação denominada myBinding porque a associação já tem um transporte chamado myTransport.</span><span class="sxs-lookup"><span data-stu-id="8ff50-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="8ff50-185">Verifique se há apenas um transporte na associação".</span><span class="sxs-lookup"><span data-stu-id="8ff50-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="8ff50-186">Falhas de comunicação</span><span class="sxs-lookup"><span data-stu-id="8ff50-186">Communicating Faults</span></span>  
 <span data-ttu-id="8ff50-187">SOAP 1.1 e SOAP 1.2 definem uma estrutura específica para falhas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="8ff50-188">Há algumas diferenças entre as duas especificações, mas em geral, os tipos de mensagem e MessageFault são usados para criar e consumir falhas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="8ff50-189">![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="8ff50-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="8ff50-190">SOAP 1.2 falha (à esquerda) e falha (à direita) do SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="8ff50-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="8ff50-191">Observe que, apenas o elemento de falha de SOAP 1.1, é o namespace qualificado.</span><span class="sxs-lookup"><span data-stu-id="8ff50-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="8ff50-192">O SOAP define uma mensagem de falha como uma mensagem que contém apenas um elemento de falha (um elemento cujo nome é `<env:Fault>`) como um filho de `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="8ff50-193">O conteúdo do elemento de falha diferem ligeiramente SOAP 1.1 e SOAP 1.2 conforme mostrado na Figura 1.</span><span class="sxs-lookup"><span data-stu-id="8ff50-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="8ff50-194">No entanto, o <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> classe normaliza essas diferenças em um modelo de objetos:</span><span class="sxs-lookup"><span data-stu-id="8ff50-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-195">O `Code` propriedade corresponde à `env:Code` (ou `faultCode` em SOAP 1.1) e identifica o tipo de falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="8ff50-196">O SOAP 1.2 define cinco valores possíveis para o `faultCode` (por exemplo, o remetente e receptor) e define um `Subcode` elemento que pode conter qualquer valor subcódigo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="8ff50-197">(Consulte a [especificação SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) para a lista de códigos de falha permitidos e seus significados.) SOAP 1.1 tem um mecanismo ligeiramente diferente: ele define quatro `faultCode` valores (por exemplo, cliente e servidor) que podem ser estendidas definindo totalmente novos ou usando a notação de ponto para criar mais específicos `faultCodes`, por exemplo, Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="8ff50-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="8ff50-198">Quando você usa MessageFault para falhas do programa, o FaultCode.Name e FaultCode.Namespace mapeia para o nome e namespace de SOAP 1.2 `env:Code` ou o SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="8ff50-199">O FaultCode.SubCode é mapeado para `env:Subcode` para SOAP 1.2 e é nula para SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="8ff50-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="8ff50-200">Você deve criar o novo subcódigos de falha (ou novos códigos de falha se usando o SOAP 1.1) se ele é interessante distinguir programaticamente uma falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="8ff50-201">Isso é análogo ao criar um novo tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="8ff50-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="8ff50-202">Você deve evitar usar a notação de ponto com códigos de falha de SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="8ff50-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="8ff50-203">(O [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) também desencoraja o uso da notação de ponto de código de falha.)</span><span class="sxs-lookup"><span data-stu-id="8ff50-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-204">O `Reason` propriedade corresponde à `env:Reason` (ou `faultString` em SOAP 1.1) uma descrição legível por humanos da condição de erro semelhante a mensagem de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8ff50-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="8ff50-205">O `FaultReason` classe (e o SOAP `env:Reason/faultString`) tem suporte interno para ter várias traduções com o intuito de globalização.</span><span class="sxs-lookup"><span data-stu-id="8ff50-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-206">O conteúdo de detalhe de falha é exposto na MessageFault usando vários métodos incluindo o `GetDetail` \<T > e `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="8ff50-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="8ff50-207">O detalhe da falha é um elemento opaco para carregar os detalhes adicionais sobre a falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="8ff50-208">Isso é útil quando há alguns detalhes estruturados arbitrária que você deseja realizar com a falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="8ff50-209">Gerar falhas</span><span class="sxs-lookup"><span data-stu-id="8ff50-209">Generating Faults</span></span>  
 <span data-ttu-id="8ff50-210">Esta seção explica o processo de geração de uma falha em resposta a uma condição de erro detectada em um canal ou em uma propriedade de mensagem criada pelo canal.</span><span class="sxs-lookup"><span data-stu-id="8ff50-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="8ff50-211">Um exemplo típico é enviar novamente uma falha em resposta a uma mensagem de solicitação que contém dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="8ff50-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="8ff50-212">Ao gerar uma falha, o canal personalizado não deve enviar a falha diretamente, em vez disso, ele deve lançar uma exceção e permitir que a camada acima decidir se deve converter essa exceção para uma falha e como enviá-lo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="8ff50-213">Para auxiliar nessa conversão, o canal deve fornecer um `FaultConverter` implementação que pode converter a exceção lançada pelo canal personalizado para a falha apropriada.</span><span class="sxs-lookup"><span data-stu-id="8ff50-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="8ff50-214">`FaultConverter` é definido como:</span><span class="sxs-lookup"><span data-stu-id="8ff50-214">`FaultConverter` is defined as:</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-215">Cada canal que gera falhas personalizadas deve implementar `FaultConverter` e retorná-lo de uma chamada para `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="8ff50-216">O custom `OnTryCreateFaultMessage` implementação deve converter a exceção em uma falha ou delegar para o canal interno `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="8ff50-217">Se o canal é um transporte ele deve converter a exceção ou delegar para o codificador `FaultConverter` ou o padrão `FaultConverter` fornecido no WCF.</span><span class="sxs-lookup"><span data-stu-id="8ff50-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="8ff50-218">O padrão `FaultConverter` converte erros correspondentes a mensagens de falha especificadas por WS-Addressing e SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ff50-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="8ff50-219">Aqui está um exemplo `OnTryCreateFaultMessage` implementação.</span><span class="sxs-lookup"><span data-stu-id="8ff50-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-220">Uma implicação desse padrão é que as exceções lançadas entre camadas para condições de erro que exigem falhas devem conter informações suficientes para que o gerador de falha correspondentes criar a falha corretos.</span><span class="sxs-lookup"><span data-stu-id="8ff50-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="8ff50-221">Como um autor de canal personalizado, você pode definir tipos de exceção que correspondem às condições de falha diferentes, se essas exceções ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="8ff50-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="8ff50-222">Observe que exceções percorrendo as camadas do canal devem se comunicar a condição de erro em vez de dados de falha opaco.</span><span class="sxs-lookup"><span data-stu-id="8ff50-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="8ff50-223">Categorias de falhas</span><span class="sxs-lookup"><span data-stu-id="8ff50-223">Fault Categories</span></span>  
 <span data-ttu-id="8ff50-224">Normalmente, há três categorias de falhas:</span><span class="sxs-lookup"><span data-stu-id="8ff50-224">There are generally three categories of faults:</span></span>  
  
1.  <span data-ttu-id="8ff50-225">Falhas que são difundidas em toda a pilha inteira.</span><span class="sxs-lookup"><span data-stu-id="8ff50-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="8ff50-226">Essas falhas pode ser encontradas em qualquer camada na pilha de canais, por exemplo InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="8ff50-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2.  <span data-ttu-id="8ff50-227">Falhas que podem ser encontraram em qualquer lugar acima de um determinado camada da pilha por exemplo, alguns erros que pertencem a uma transação fluída ou para funções de segurança.</span><span class="sxs-lookup"><span data-stu-id="8ff50-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3.  <span data-ttu-id="8ff50-228">Falhas que são direcionadas a uma única camada da pilha, por exemplo erros como falhas de número de sequência WS-RM.</span><span class="sxs-lookup"><span data-stu-id="8ff50-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="8ff50-229">Categoria de 1.</span><span class="sxs-lookup"><span data-stu-id="8ff50-229">Category 1.</span></span> <span data-ttu-id="8ff50-230">As falhas são geralmente WS-Addressing e falhas de SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ff50-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="8ff50-231">A base de `FaultConverter` classe fornecido pelo WCF erros converte correspondente a mensagens de falha especificado por WS-Addressing e SOAP para que você não precise lidar com essas exceções conversão por conta própria.</span><span class="sxs-lookup"><span data-stu-id="8ff50-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="8ff50-232">Categoria 2.</span><span class="sxs-lookup"><span data-stu-id="8ff50-232">Category 2.</span></span> <span data-ttu-id="8ff50-233">As falhas ocorrem quando uma camada adiciona uma propriedade para a mensagem que não consome completamente as informações de mensagem que pertencem a essa camada.</span><span class="sxs-lookup"><span data-stu-id="8ff50-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="8ff50-234">Erros podem ser detectados mais tarde, quando uma camada superior pergunta a propriedade de mensagem para processar ainda mais informações sobre a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8ff50-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="8ff50-235">Esses canais devem implementar o `GetProperty` especificado anteriormente para habilitar a camada superior enviar de volta a falha corretos.</span><span class="sxs-lookup"><span data-stu-id="8ff50-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="8ff50-236">Um exemplo disso é o TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="8ff50-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="8ff50-237">Essa propriedade é adicionada à mensagem sem validar completamente todos os dados no cabeçalho (fazer isso pode envolver a entrar em contato com o coordenador de transações distribuídas (DTC).</span><span class="sxs-lookup"><span data-stu-id="8ff50-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="8ff50-238">Categoria de 3.</span><span class="sxs-lookup"><span data-stu-id="8ff50-238">Category 3.</span></span> <span data-ttu-id="8ff50-239">Falhas somente são geradas e enviadas por uma única camada no processador.</span><span class="sxs-lookup"><span data-stu-id="8ff50-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="8ff50-240">Portanto todas as exceções estão contidas dentro da camada.</span><span class="sxs-lookup"><span data-stu-id="8ff50-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="8ff50-241">Para melhorar a consistência entre os canais e facilidade de manutenção, o seu canal personalizado deve usar o padrão especificado anteriormente para gerar mensagens de falha, mesmo para as falhas internas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="8ff50-242">Interpretando falhas recebidas</span><span class="sxs-lookup"><span data-stu-id="8ff50-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="8ff50-243">Esta seção fornece orientação para gerar a exceção apropriada ao receber uma mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="8ff50-244">A árvore de decisão para processar uma mensagem em todas as camadas da pilha é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8ff50-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1.  <span data-ttu-id="8ff50-245">Se a camada considera a mensagem a ser inválido, a camada deve fazer seu processamento 'mensagem inválida'.</span><span class="sxs-lookup"><span data-stu-id="8ff50-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="8ff50-246">Tal processamento é específico para a camada, mas poderia incluir a descartar a mensagem, rastreamento, ou gerar uma exceção que será convertida em uma falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="8ff50-247">Exemplos incluem segurança recebendo uma mensagem que não está devidamente protegida ou RM receber uma mensagem com um número de sequência incorreta.</span><span class="sxs-lookup"><span data-stu-id="8ff50-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2.  <span data-ttu-id="8ff50-248">Caso contrário, se a mensagem é uma mensagem de falha que se aplica especificamente à camada, e a mensagem não faz sentida fora de interação da camada, a camada deve lidar com a condição de erro.</span><span class="sxs-lookup"><span data-stu-id="8ff50-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="8ff50-249">Um exemplo disso é uma falha de sequência de RM recusada que não faz sentido para as camadas acima o canal do RM e isso implica que o canal do RM a falha e lançando a partir das operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="8ff50-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3.  <span data-ttu-id="8ff50-250">Caso contrário, a mensagem deve ser retornada do Request () ou Receive ().</span><span class="sxs-lookup"><span data-stu-id="8ff50-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="8ff50-251">Isso inclui os casos em que a camada reconhece a falha, mas a falha apenas indica que uma solicitação falhou e não implica a haver falha no canal e lançando a partir das operações pendentes.</span><span class="sxs-lookup"><span data-stu-id="8ff50-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="8ff50-252">Para melhorar a usabilidade, nesse caso, a camada deve implementar `GetProperty<FaultConverter>` e retornar um `FaultConverter` derivado da classe que pode converter a falha em uma exceção, substituindo `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="8ff50-253">O modelo de objeto a seguir dá suporte a mensagens converter exceções:</span><span class="sxs-lookup"><span data-stu-id="8ff50-253">The following object model supports converting messages to exceptions:</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-254">Uma camada de canais pode implementar `GetProperty<FaultConverter>` para dar suporte a mensagens de falha de conversão para exceções.</span><span class="sxs-lookup"><span data-stu-id="8ff50-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="8ff50-255">Para fazer isso, substitua `OnTryCreateException` e inspecionar a mensagem de falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="8ff50-256">Se reconhecidas, fazer a conversão, caso contrário, pergunte o canal interno para convertê-lo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="8ff50-257">Canais de transporte devem delegar ao `FaultConverter.GetDefaultFaultConverter` para obter o padrão FaultConverter SOAP/WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="8ff50-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="8ff50-258">Uma implementação típica tem esta aparência:</span><span class="sxs-lookup"><span data-stu-id="8ff50-258">A typical implementation looks like this:</span></span>  
  
```  
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
  
 <span data-ttu-id="8ff50-259">Para condições de falha específicos que têm os cenários de recuperação distintos, considere definir uma classe derivada de `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="8ff50-260">Processamento de MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="8ff50-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="8ff50-261">O SOAP define uma falha geral para sinalizar que um cabeçalho necessário não foi entendido pelo destinatário.</span><span class="sxs-lookup"><span data-stu-id="8ff50-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="8ff50-262">Essa falha é conhecida como o `mustUnderstand` falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="8ff50-263">No WCF, canais personalizados nunca geram `mustUnderstand` falhas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="8ff50-264">Em vez disso, o Dispatcher WCF, que está localizado na parte superior da pilha de comunicação do WCF, verifica que todos os cabeçalhos que foram marcados como MustUndestand = true foram entendidos pela pilha subjacente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="8ff50-265">Se qualquer não foram compreendidos, um `mustUnderstand` falha é gerada nesse ponto.</span><span class="sxs-lookup"><span data-stu-id="8ff50-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="8ff50-266">(O usuário pode optar por desativar isso `mustUnderstand` de processamento e fazer com que o aplicativo receber todos os cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8ff50-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="8ff50-267">Nesse caso, o aplicativo é responsável por executar `mustUnderstand` de processamento.) A falha gerada inclui um cabeçalho de NotUnderstood que contém os nomes de todos os cabeçalhos com MustUnderstand = true não foi compreendido.</span><span class="sxs-lookup"><span data-stu-id="8ff50-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="8ff50-268">Se o seu canal do protocolo envia um cabeçalho personalizado com MustUnderstand = true e recebe um `mustUnderstand` falha, ele deve descobrir se essa falha é devida ao cabeçalho enviado por ele.</span><span class="sxs-lookup"><span data-stu-id="8ff50-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="8ff50-269">Há dois membros no `MessageFault` classe são úteis para isso:</span><span class="sxs-lookup"><span data-stu-id="8ff50-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="8ff50-270">`IsMustUnderstandFault` Retorna `true` se a falha é um `mustUnderstand` falha.</span><span class="sxs-lookup"><span data-stu-id="8ff50-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="8ff50-271">`WasHeaderNotUnderstood` Retorna `true` se o cabeçalho com o nome especificado e o namespace está incluído na falha como um cabeçalho de NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="8ff50-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="8ff50-272">Caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="8ff50-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="8ff50-273">Se um canal emite um cabeçalho que está marcado como MustUnderstand = true, em seguida, essa camada também deve implementar o padrão de API de geração de exceção e deve converter `mustUnderstand` falhas causadas por aquele cabeçalho a uma exceção mais úteis, como descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8ff50-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="8ff50-274">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="8ff50-274">Tracing</span></span>  
 <span data-ttu-id="8ff50-275">O .NET Framework fornece um mecanismo para rastrear a execução de programa como uma maneira de ajudar a diagnosticar aplicativos de produção ou problemas intermitentes onde não é possível simplesmente anexar um depurador e percorrer o código.</span><span class="sxs-lookup"><span data-stu-id="8ff50-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="8ff50-276">Os principais componentes desse mecanismo estão no <xref:System.Diagnostics?displayProperty=nameWithType> namespace e consistem em:</span><span class="sxs-lookup"><span data-stu-id="8ff50-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
-   <span data-ttu-id="8ff50-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, que é a origem das informações de rastreamento a serem gravados <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, que é uma classe base abstrata para os ouvintes concretas que recebem as informações a ser rastreado do <xref:System.Diagnostics.TraceSource> e fazê-lo para um destino específica do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="8ff50-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="8ff50-278">Por exemplo, <xref:System.Diagnostics.XmlWriterTraceListener> informações para um arquivo XML de rastreamento de saídas.</span><span class="sxs-lookup"><span data-stu-id="8ff50-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="8ff50-279">Por fim, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, que permite que o usuário do aplicativo controlar o nível de detalhes de rastreamento e geralmente é especificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="8ff50-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
-   <span data-ttu-id="8ff50-280">Além dos componentes principais, você pode usar o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) para exibir e pesquisar WCF rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="8ff50-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="8ff50-281">A ferramenta foi criada especificamente para arquivos de rastreamento gerados pelo WCF e escritos usando <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="8ff50-282">A figura a seguir mostra os vários componentes envolvidos no rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="8ff50-283">![Tratando exceções e falhas](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="8ff50-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="8ff50-284">Rastreamento de um canal personalizado</span><span class="sxs-lookup"><span data-stu-id="8ff50-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="8ff50-285">Canais personalizados devem gravar mensagens de rastreamento para auxiliar no diagnóstico de problemas quando não é possível anexar um depurador ao aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="8ff50-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="8ff50-286">Isso envolve duas tarefas de alto níveis: instanciar um <xref:System.Diagnostics.TraceSource> e chamando seus métodos para gravar rastreamentos.</span><span class="sxs-lookup"><span data-stu-id="8ff50-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="8ff50-287">Ao instanciar um <xref:System.Diagnostics.TraceSource>, a cadeia de caracteres que você especifique se torna o nome dessa fonte.</span><span class="sxs-lookup"><span data-stu-id="8ff50-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="8ff50-288">Esse nome é usado para configurar a origem de rastreamento de (nível de rastreamento de habilitar/desabilitar/set).</span><span class="sxs-lookup"><span data-stu-id="8ff50-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="8ff50-289">Ele também aparece na saída em si.</span><span class="sxs-lookup"><span data-stu-id="8ff50-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="8ff50-290">Canais personalizados devem usar um nome exclusivo de origem para ajudar os leitores da saída do rastreamento entender de onde vêm as informações de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="8ff50-291">Usando o nome do assembly que está gravando as informações como o nome da origem de rastreamento é a prática comum.</span><span class="sxs-lookup"><span data-stu-id="8ff50-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="8ff50-292">Por exemplo, o WCF usa o System. ServiceModel como a origem de rastreamento de informações gravadas do assembly System. ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8ff50-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="8ff50-293">Depois de uma origem de rastreamento, você chama seu <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, ou <xref:System.Diagnostics.TraceSource.TraceInformation%2A> métodos para gravar entradas de rastreamento nos ouvintes de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="8ff50-294">Para cada entrada de rastreamento escrever, você precisa classificar o tipo de evento como um dos tipos de evento definidos no <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="8ff50-295">Essa classificação e a configuração de nível de rastreamento na configuração determinam se a entrada de rastreamento é enviado para o ouvinte.</span><span class="sxs-lookup"><span data-stu-id="8ff50-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="8ff50-296">Por exemplo, definindo o nível de rastreamento na configuração para `Warning` permite `Warning`, `Error` e `Critical` entradas a serem gravados, mas blocos de informações e detalhado de entradas de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="8ff50-297">Aqui está um exemplo de como criar uma instância de uma origem de rastreamento e gravar uma entrada no nível de informações:</span><span class="sxs-lookup"><span data-stu-id="8ff50-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ff50-298">É altamente recomendável que você especifique um nome de origem de rastreamento que é exclusivo para seu canal personalizado para ajudar os leitores de saída de rastreamento a entender de onde veio a saída.</span><span class="sxs-lookup"><span data-stu-id="8ff50-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="8ff50-299">A integração com o Visualizador de rastreamento</span><span class="sxs-lookup"><span data-stu-id="8ff50-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="8ff50-300">Rastreamentos gerados pelo seu canal podem ser a saída em um formato legível pela [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) usando <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> como o ouvinte de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="8ff50-301">Isso não é algo que você, como desenvolvedor de canal, precisa fazer.</span><span class="sxs-lookup"><span data-stu-id="8ff50-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="8ff50-302">Em vez disso, ele é o usuário do aplicativo (ou a pessoa que o aplicativo de solução de problemas) que precisa para configurar este ouvinte de rastreamento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8ff50-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="8ff50-303">Por exemplo, a configuração a seguir gera informações de rastreamento de ambos <xref:System.ServiceModel?displayProperty=nameWithType> e `Microsoft.Samples.Udp` para o arquivo chamado `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="8ff50-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="8ff50-304">Rastreamento de dados estruturados</span><span class="sxs-lookup"><span data-stu-id="8ff50-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="8ff50-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> tem um <xref:System.Diagnostics.TraceSource.TraceData%2A> método que usa um ou mais objetos que devem ser incluídos na entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="8ff50-306">Em geral, o <xref:System.Object.ToString%2A?displayProperty=nameWithType> método é chamado em cada objeto e a cadeia de caracteres resultante é gravada como parte da entrada de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8ff50-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="8ff50-307">Ao usar <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> para produzir rastreamentos, você pode passar uma <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> como o objeto de dados à <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="8ff50-308">A entrada de rastreamento resultante inclui o XML fornecido pelo <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ff50-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8ff50-309">Aqui está um exemplo de entrada com os dados de aplicativo de XML:</span><span class="sxs-lookup"><span data-stu-id="8ff50-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="8ff50-310">O Visualizador de rastreamento do WCF compreende o esquema do `TraceRecord` elemento mostrado anteriormente e extrai os dados de seus elementos filho e o exibe em um formato tabular.</span><span class="sxs-lookup"><span data-stu-id="8ff50-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="8ff50-311">Seu canal deve usar este esquema quando o rastreamento de dados estruturados de aplicativo para ajudar usuários Svctraceviewer.exe ler os dados.</span><span class="sxs-lookup"><span data-stu-id="8ff50-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

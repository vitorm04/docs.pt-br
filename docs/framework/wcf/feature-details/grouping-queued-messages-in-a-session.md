---
title: Agrupamento de mensagens em fila em uma sessão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892743"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="ef701-102">Agrupamento de mensagens em fila em uma sessão</span><span class="sxs-lookup"><span data-stu-id="ef701-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="ef701-103">O Windows Communication Foundation (WCF) fornece uma sessão que permite agrupar um conjunto de mensagens relacionadas para processamento por um único aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="ef701-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="ef701-104">As mensagens que fazem parte de uma sessão devem fazer parte da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="ef701-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="ef701-105">Como todas as mensagens fazem parte da mesma transação, se uma mensagem não for processada, toda a sessão será revertida.</span><span class="sxs-lookup"><span data-stu-id="ef701-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="ef701-106">As sessões têm comportamentos semelhantes em relação a filas de mensagens mortas e filas suspeitas.</span><span class="sxs-lookup"><span data-stu-id="ef701-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="ef701-107">A propriedade time to Live (TTL) definida em uma associação enfileirada configurada para sessões é aplicada à sessão como um todo.</span><span class="sxs-lookup"><span data-stu-id="ef701-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="ef701-108">Se apenas algumas das mensagens na sessão forem enviadas antes do tempo de vida expirar, toda a sessão será colocada na fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="ef701-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="ef701-109">Da mesma forma, quando as mensagens em uma sessão falham ao serem enviadas a um aplicativo da fila de aplicativos, toda a sessão é colocada na fila de suspeitas (se disponível).</span><span class="sxs-lookup"><span data-stu-id="ef701-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="ef701-110">Exemplo de agrupamento de mensagens</span><span class="sxs-lookup"><span data-stu-id="ef701-110">Message Grouping Example</span></span>  
 <span data-ttu-id="ef701-111">Um exemplo em que o agrupamento de mensagens é útil é ao implementar um aplicativo de processamento de pedidos como um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="ef701-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="ef701-112">Por exemplo, um cliente envia um pedido para esse aplicativo que contém vários itens.</span><span class="sxs-lookup"><span data-stu-id="ef701-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="ef701-113">Para cada item, o cliente faz uma chamada para o serviço, o que resulta em uma mensagem separada sendo enviada.</span><span class="sxs-lookup"><span data-stu-id="ef701-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="ef701-114">É possível que o forneça um para receber o primeiro item e o servidor B receba o segundo item.</span><span class="sxs-lookup"><span data-stu-id="ef701-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="ef701-115">Cada vez que um item é adicionado, o servidor que processa esse item tem que localizar a ordem apropriada e adicionar o item a ele, o que é altamente ineficiente.</span><span class="sxs-lookup"><span data-stu-id="ef701-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="ef701-116">Você ainda pode se deparar com essas ineficiências apenas com um único servidor manipulando todas as solicitações, porque o servidor deve manter o controle de todos os pedidos que estão sendo processados no momento e determinar a qual deles o novo item pertence.</span><span class="sxs-lookup"><span data-stu-id="ef701-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="ef701-117">O agrupamento de todas as solicitações de um único pedido simplifica muito a implementação desse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef701-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="ef701-118">O aplicativo cliente envia todos os itens para uma única ordem em uma sessão, portanto, quando o serviço processa o pedido, ele processa toda a sessão ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="ef701-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="ef701-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ef701-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="ef701-120">Para configurar um contrato de serviço para usar sessões</span><span class="sxs-lookup"><span data-stu-id="ef701-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="ef701-121">Defina um contrato de serviço que exija uma sessão.</span><span class="sxs-lookup"><span data-stu-id="ef701-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="ef701-122">Faça isso com o <xref:System.ServiceModel.ServiceContractAttribute> atributo especificando:</span><span class="sxs-lookup"><span data-stu-id="ef701-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="ef701-123">Marque as operações no contrato como unidirecional, pois esses métodos não retornam nada.</span><span class="sxs-lookup"><span data-stu-id="ef701-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="ef701-124">Isso é feito com o <xref:System.ServiceModel.OperationContractAttribute> atributo especificando:</span><span class="sxs-lookup"><span data-stu-id="ef701-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="ef701-125">Implemente o contrato de serviço e <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> especifique <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>um de.</span><span class="sxs-lookup"><span data-stu-id="ef701-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef701-126">Isso instancia o serviço apenas uma vez para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="ef701-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="ef701-127">Cada operação de serviço requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="ef701-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="ef701-128">Especifique isso com o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="ef701-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="ef701-129">A operação que conclui a transação também deve ser definida <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> como `true`.</span><span class="sxs-lookup"><span data-stu-id="ef701-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. <span data-ttu-id="ef701-130">Configure um ponto de extremidade que usa a associação `NetMsmqBinding` fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="ef701-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="ef701-131">Crie uma fila transacional usando <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="ef701-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="ef701-132">Você também pode criar a fila usando o MSMQ (enfileiramento de mensagens) ou o MMC.</span><span class="sxs-lookup"><span data-stu-id="ef701-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="ef701-133">Se você fizer isso, crie uma fila transacional.</span><span class="sxs-lookup"><span data-stu-id="ef701-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="ef701-134">Crie um host de serviço para o serviço usando <xref:System.ServiceModel.ServiceHost>o.</span><span class="sxs-lookup"><span data-stu-id="ef701-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="ef701-135">Abra o host de serviço para disponibilizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="ef701-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="ef701-136">Feche o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef701-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="ef701-137">Para configurar um cliente</span><span class="sxs-lookup"><span data-stu-id="ef701-137">To set up a client</span></span>  
  
1. <span data-ttu-id="ef701-138">Crie um escopo de transação para gravar na fila transacional.</span><span class="sxs-lookup"><span data-stu-id="ef701-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="ef701-139">Crie o cliente WCF usando a ferramenta do [Utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="ef701-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="ef701-140">Faça o pedido.</span><span class="sxs-lookup"><span data-stu-id="ef701-140">Place the order.</span></span>  
  
4. <span data-ttu-id="ef701-141">Feche o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="ef701-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef701-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef701-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ef701-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef701-143">Description</span></span>  
 <span data-ttu-id="ef701-144">O exemplo a seguir fornece o código para `IProcessOrder` o serviço e para um cliente que usa esse serviço.</span><span class="sxs-lookup"><span data-stu-id="ef701-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="ef701-145">Ele mostra como o WCF usa sessões enfileiradas para fornecer o comportamento de agrupamento.</span><span class="sxs-lookup"><span data-stu-id="ef701-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="ef701-146">Código para o serviço</span><span class="sxs-lookup"><span data-stu-id="ef701-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="ef701-147">Código para o cliente</span><span class="sxs-lookup"><span data-stu-id="ef701-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="ef701-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef701-148">See also</span></span>

- [<span data-ttu-id="ef701-149">Sessões e filas</span><span class="sxs-lookup"><span data-stu-id="ef701-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="ef701-150">Visão geral de filas</span><span class="sxs-lookup"><span data-stu-id="ef701-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)

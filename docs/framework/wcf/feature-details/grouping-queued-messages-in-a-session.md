---
title: "Agrupamento de mensagens em fila em uma sessão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aba045456d61b5ad687f1030dca3c26b083cdb58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="0a4f9-102">Agrupamento de mensagens em fila em uma sessão</span><span class="sxs-lookup"><span data-stu-id="0a4f9-102">Grouping Queued Messages in a Session</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0a4f9-103">Fornece uma sessão que permite agrupar um conjunto de mensagens relacionadas juntas para processamento por um único aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-103"> provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="0a4f9-104">As mensagens que fazem parte de uma sessão devem ser parte da mesma transação.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="0a4f9-105">Como todas as mensagens fazem parte da mesma transação, se uma mensagem falhar ao ser processada toda a sessão será revertida.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="0a4f9-106">Sessões têm comportamento semelhante em relação a filas de mensagens mortas e suspeitas.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="0a4f9-107">O tempo para a propriedade de vida (TTL) definida em uma associação enfileirada configurada para sessões é aplicado à sessão como um todo.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="0a4f9-108">Se apenas algumas das mensagens na sessão são enviadas antes que o TTL expire, toda a sessão é colocada na fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="0a4f9-109">Da mesma forma, quando as mensagens em uma sessão não ser enviada a um aplicativo da fila de aplicativos, toda a sessão é colocada na fila de suspeitas (se disponível).</span><span class="sxs-lookup"><span data-stu-id="0a4f9-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="0a4f9-110">Exemplo de agrupamento de mensagem</span><span class="sxs-lookup"><span data-stu-id="0a4f9-110">Message Grouping Example</span></span>  
 <span data-ttu-id="0a4f9-111">Um exemplo de onde o agrupamento de mensagens é útil é ao implementar um aplicativo de processamento de pedido como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-111">One example where grouping messages is helpful is when implementing an order-processing application as a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="0a4f9-112">Por exemplo, um cliente envia uma ordem para este aplicativo que contém um número de itens.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="0a4f9-113">Para cada item, o cliente faz uma chamada para o serviço, o que resulta em uma mensagem separada que está sendo enviada.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="0a4f9-114">É possível para que servem a receber o primeiro item e o servidor B para receber o segundo item.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="0a4f9-115">Cada vez que um item é adicionado, o servidor está processando o item tem que localizar o pedido apropriado e adicione o item a ele, que é altamente ineficiente.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="0a4f9-116">Você ainda tiver essas ineficiências com um único servidor tratar todas as solicitações, porque o servidor deve manter o controle de todos os pedidos sendo processados no momento e determinar qual o novo item pertence.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="0a4f9-117">Todas as solicitações de uma única ordem de agrupamento bastante simplifica a implementação de tal aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="0a4f9-118">O aplicativo cliente envia todos os itens de uma única ordem em uma sessão, para que quando o serviço processa o pedido, ele processa toda a sessão de uma vez.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="0a4f9-119">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="0a4f9-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="0a4f9-120">Para configurar um contrato de serviço para usar sessões</span><span class="sxs-lookup"><span data-stu-id="0a4f9-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="0a4f9-121">Defina um contrato de serviço que exige uma sessão.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="0a4f9-122">Fazer isso com o <xref:System.ServiceModel.OperationContractAttribute> de atributo e especificando por:</span><span class="sxs-lookup"><span data-stu-id="0a4f9-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="0a4f9-123">Marca as operações no contrato como unidirecional, pois esses métodos não retorna nada.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="0a4f9-124">Isso é feito com o <xref:System.ServiceModel.OperationContractAttribute> de atributo e especificando por:</span><span class="sxs-lookup"><span data-stu-id="0a4f9-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="0a4f9-125">Implementar o contrato de serviço e especifique um `InstanceContextMode` de `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="0a4f9-126">Isso cria uma instância de serviço somente uma vez para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="0a4f9-127">Cada operação de serviço exige uma transação.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="0a4f9-128">Especificar com o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="0a4f9-129">A operação que conclui a transação também deve definir `TransactionAutoComplete` para `true`.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="0a4f9-130">Configurar um ponto de extremidade que usa o fornecida pelo sistema `NetMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="0a4f9-131">Criar uma fila transacional usando <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="0a4f9-132">Você também pode criar a fila usando o serviço de enfileiramento de mensagens (MSMQ) ou o MMC.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="0a4f9-133">Se você fizer isso, crie uma fila transacional.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="0a4f9-134">Criar um host de serviço para o serviço usando <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="0a4f9-135">Abra o host de serviço para disponibilizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="0a4f9-136">Feche o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="0a4f9-137">Para configurar um cliente</span><span class="sxs-lookup"><span data-stu-id="0a4f9-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="0a4f9-138">Crie um escopo de transação para gravar na fila transacional.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="0a4f9-139">Criar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-139">Create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="0a4f9-140">Faz o pedido.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="0a4f9-141">Fechar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-141">Close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a4f9-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a4f9-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0a4f9-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a4f9-143">Description</span></span>  
 <span data-ttu-id="0a4f9-144">O exemplo a seguir fornece o código para o `IProcessOrder` de serviço e para um cliente que usa este serviço.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="0a4f9-145">Ele mostra como [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa na fila de sessões para fornecer o comportamento do agrupamento.</span><span class="sxs-lookup"><span data-stu-id="0a4f9-145">It shows how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="0a4f9-146">Código do serviço</span><span class="sxs-lookup"><span data-stu-id="0a4f9-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="0a4f9-147">Código do cliente</span><span class="sxs-lookup"><span data-stu-id="0a4f9-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="0a4f9-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a4f9-148">See Also</span></span>  
 [<span data-ttu-id="0a4f9-149">Sessões e filas</span><span class="sxs-lookup"><span data-stu-id="0a4f9-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="0a4f9-150">Visão geral de filas</span><span class="sxs-lookup"><span data-stu-id="0a4f9-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)

---
title: 'Como: Troca de mensagens na fila com pontos de extremidade do WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 9ee071eb88be504f7fde29b61d3a39327f0b467f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693432"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a><span data-ttu-id="68634-102">Como: Troca de mensagens na fila com pontos de extremidade do WCF</span><span class="sxs-lookup"><span data-stu-id="68634-102">How to: Exchange Queued Messages with WCF Endpoints</span></span>
<span data-ttu-id="68634-103">Filas Certifique-se de que o sistema de mensagens confiável pode ocorrer entre um cliente e um serviço Windows Communication Foundation (WCF), mesmo se o serviço não está disponível no momento da comunicação.</span><span class="sxs-lookup"><span data-stu-id="68634-103">Queues ensure that reliable messaging can occur between a client and a Windows Communication Foundation (WCF) service, even if the service is not available at the time of communication.</span></span> <span data-ttu-id="68634-104">Os procedimentos a seguir mostram como garantir a comunicação durável entre um cliente e um serviço usando o padrão na fila de vinculação ao implementar o serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="68634-104">The following procedures show how to ensure durable communication between a client and a service by using the standard queued binding when implementing the WCF service.</span></span>  
  
 <span data-ttu-id="68634-105">Esta seção explica como usar <xref:System.ServiceModel.NetMsmqBinding> para comunicação em fila entre um cliente WCF e um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="68634-105">This section explains how to use <xref:System.ServiceModel.NetMsmqBinding> for queued communication between a WCF client and a WCF service.</span></span>  
  
### <a name="to-use-queuing-in-a-wcf-service"></a><span data-ttu-id="68634-106">Para usar o enfileiramento de mensagens em um serviço WCF</span><span class="sxs-lookup"><span data-stu-id="68634-106">To use queuing in a WCF service</span></span>  
  
1.  <span data-ttu-id="68634-107">Definir um contrato de serviço usando uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68634-107">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="68634-108">Marcar as operações na interface que fazem parte do contrato de serviço com o <xref:System.ServiceModel.OperationContractAttribute> e especificá-los como unidirecional, porque não há resposta para o método é retornada.</span><span class="sxs-lookup"><span data-stu-id="68634-108">Mark the operations in the interface that are part of the service contract with the <xref:System.ServiceModel.OperationContractAttribute> and specify them as one-way because no response to the method is returned.</span></span> <span data-ttu-id="68634-109">O código a seguir fornece um contrato de serviço de exemplo e sua definição de operação.</span><span class="sxs-lookup"><span data-stu-id="68634-109">The following code provides an example service contract and its operation definition.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  <span data-ttu-id="68634-110">Quando o contrato de serviço passa tipos definidos pelo usuário, você deve definir contratos de dados para esses tipos.</span><span class="sxs-lookup"><span data-stu-id="68634-110">When the service contract passes user-defined types, you must define data contracts for those types.</span></span> <span data-ttu-id="68634-111">O código a seguir mostra dois contratos de dados, `PurchaseOrder` e `PurchaseOrderLineItem`.</span><span class="sxs-lookup"><span data-stu-id="68634-111">The following code shows two data contracts, `PurchaseOrder` and `PurchaseOrderLineItem`.</span></span> <span data-ttu-id="68634-112">Esses dois tipos definem os dados que são enviados para o serviço.</span><span class="sxs-lookup"><span data-stu-id="68634-112">These two types define data that is sent to the service.</span></span> <span data-ttu-id="68634-113">(Observe que as classes que definem esse contrato de dados também definem uma série de métodos.</span><span class="sxs-lookup"><span data-stu-id="68634-113">(Note that the classes that define this data contract also define a number of methods.</span></span> <span data-ttu-id="68634-114">Esses métodos não são considerados parte do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="68634-114">These methods are not considered part of the data contract.</span></span> <span data-ttu-id="68634-115">Somente os membros que são declarados com o `DataMember` atributo fazem parte do contrato de dados.)</span><span class="sxs-lookup"><span data-stu-id="68634-115">Only those members that are declared with the `DataMember` attribute are part of the data contract.)</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  <span data-ttu-id="68634-116">Implemente os métodos do contrato de serviço definidos na interface em uma classe.</span><span class="sxs-lookup"><span data-stu-id="68634-116">Implement the methods of the service contract defined in the interface in a class.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     <span data-ttu-id="68634-117">Observe que o <xref:System.ServiceModel.OperationBehaviorAttribute> colocado no `SubmitPurchaseOrder` método.</span><span class="sxs-lookup"><span data-stu-id="68634-117">Notice the <xref:System.ServiceModel.OperationBehaviorAttribute> placed on the `SubmitPurchaseOrder` method.</span></span> <span data-ttu-id="68634-118">Isso especifica que esta operação deve ser chamada dentro de uma transação e que a transação é concluída automaticamente quando o método for concluído.</span><span class="sxs-lookup"><span data-stu-id="68634-118">This specifies that this operation must be called within a transaction and that the transaction automatically completes when the method completes.</span></span>  
  
4.  <span data-ttu-id="68634-119">Criar uma fila transacional usando <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="68634-119">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="68634-120">Você pode optar por criar a fila usando o Microsoft Management Console (MMC) do Microsoft Message Queuing (MSMQ) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="68634-120">You can choose to create the queue using Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) instead.</span></span> <span data-ttu-id="68634-121">Nesse caso, certifique-se de que criar uma fila transacional.</span><span class="sxs-lookup"><span data-stu-id="68634-121">If so, make sure you create a transactional queue.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  <span data-ttu-id="68634-122">Definir um <xref:System.ServiceModel.Description.ServiceEndpoint> na configuração que especifica o endereço do serviço e usa o padrão de <xref:System.ServiceModel.NetMsmqBinding> associação.</span><span class="sxs-lookup"><span data-stu-id="68634-122">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the service address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding.</span></span> <span data-ttu-id="68634-123">Para obter mais informações sobre como usar a configuração do WCF, consulte [Configurando o Windows Communication Foundation aplicativos](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="68634-123">For more information about using WCF configuration, see [Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
  
  
6.  <span data-ttu-id="68634-124">Criar um host para o `OrderProcessing` usando <xref:System.ServiceModel.ServiceHost> que lê as mensagens da fila e processa-os.</span><span class="sxs-lookup"><span data-stu-id="68634-124">Create a host for the `OrderProcessing` service using <xref:System.ServiceModel.ServiceHost> that reads messages from the queue and processes them.</span></span> <span data-ttu-id="68634-125">Abra o host de serviço para disponibilizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="68634-125">Open the service host to make the service available.</span></span> <span data-ttu-id="68634-126">Exiba uma mensagem que informa o usuário pressione qualquer tecla para encerrar o serviço.</span><span class="sxs-lookup"><span data-stu-id="68634-126">Display a message that tells the user to press any key to terminate the service.</span></span> <span data-ttu-id="68634-127">Chamar `ReadLine` espera para a chave para ser pressionado e, em seguida, feche o serviço.</span><span class="sxs-lookup"><span data-stu-id="68634-127">Call `ReadLine` to wait for the key to be pressed and then close the service.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a><span data-ttu-id="68634-128">Para criar um cliente para o serviço em fila</span><span class="sxs-lookup"><span data-stu-id="68634-128">To create a client for the queued service</span></span>  
  
1.  <span data-ttu-id="68634-129">O exemplo a seguir mostra como executar o aplicativo de hospedagem e use a ferramenta de Svcutil.exe para criar o cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="68634-129">The following example shows how to run the hosting application and use the Svcutil.exe tool to create the WCF client.</span></span>  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  <span data-ttu-id="68634-130">Definir um <xref:System.ServiceModel.Description.ServiceEndpoint> na configuração que especifica o endereço e usa o padrão de <xref:System.ServiceModel.NetMsmqBinding> de associação, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="68634-130">Define a <xref:System.ServiceModel.Description.ServiceEndpoint> in configuration that specifies the address and uses the standard <xref:System.ServiceModel.NetMsmqBinding> binding, as shown in the following example.</span></span>  
  
  
  
3.  <span data-ttu-id="68634-131">Criar um escopo de transação para gravar na fila transacional, a chamada a `SubmitPurchaseOrder` operação e fechar o cliente do WCF, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="68634-131">Create a transaction scope to write to the transactional queue, call the `SubmitPurchaseOrder` operation and close the WCF client, as shown in the following example.</span></span>  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="68634-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68634-132">Example</span></span>  
 <span data-ttu-id="68634-133">Os exemplos a seguir mostram o código de serviço, aplicativo de hospedagem, arquivo App. config e incluídas neste exemplo de código do cliente.</span><span class="sxs-lookup"><span data-stu-id="68634-133">The following examples show the service code, hosting application, App.config file, and client code included for this example.</span></span>  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="68634-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68634-134">See also</span></span>
- <xref:System.ServiceModel.NetMsmqBinding>
- [<span data-ttu-id="68634-135">Associação transacionada do MSMQ</span><span class="sxs-lookup"><span data-stu-id="68634-135">Transacted MSMQ Binding</span></span>](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [<span data-ttu-id="68634-136">Enfileiramento no WCF</span><span class="sxs-lookup"><span data-stu-id="68634-136">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="68634-137">Como: Trocar mensagens com pontos de extremidade do WCF e aplicativos do serviço de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="68634-137">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="68634-138">Windows Communication Foundation para Enfileiramento de Mensagens</span><span class="sxs-lookup"><span data-stu-id="68634-138">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="68634-139">Instalando o Enfileiramento de Mensagens (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="68634-139">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="68634-140">Exemplos de associação de integração de enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="68634-140">Message Queuing Integration Binding Samples</span></span>](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)
- [<span data-ttu-id="68634-141">Enfileiramento de mensagens para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="68634-141">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="68634-142">Segurança de mensagem através do enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="68634-142">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)

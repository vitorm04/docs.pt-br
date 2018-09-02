---
title: Enfileiramento de mensagens para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 983fd2ef7338e24c67e3556849e73c2feaf97a60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423368"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="29cb5-102">Enfileiramento de mensagens para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="29cb5-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="29cb5-103">Este exemplo demonstra como um aplicativo de enfileiramento de mensagens (MSMQ) pode enviar uma mensagem MSMQ a um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="29cb5-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="29cb5-104">O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="29cb5-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="29cb5-105">O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com as filas.</span><span class="sxs-lookup"><span data-stu-id="29cb5-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="29cb5-106">Uma mensagem MSMQ não tem um cabeçalho de ação, portanto, não é possível mapear diferentes mensagens MSMQ para contratos de operação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="29cb5-107">Portanto, pode haver apenas um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="29cb5-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="29cb5-108">Se você quiser definir mais de um contrato de operação para o serviço, o aplicativo deve fornecer informações sobre qual cabeçalho da mensagem do MSMQ (por exemplo, o rótulo ou uma correlationID) pode ser usado para decidir qual contrato de operação para o qual expedir.</span><span class="sxs-lookup"><span data-stu-id="29cb5-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="29cb5-109">Isso é demonstrado na [Demux personalizado](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="29cb5-109">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="29cb5-110">A mensagem do MSMQ não contém informações sobre qual cabeçalhos são mapeados para os parâmetros diferentes do contrato da operação.</span><span class="sxs-lookup"><span data-stu-id="29cb5-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="29cb5-111">O parâmetro é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), que contém a mensagem MSMQ subjacente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="29cb5-112">O tipo "T" no <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) classe representa os dados que são serializados no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="29cb5-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="29cb5-113">Neste exemplo, o `PurchaseOrder` tipo é serializado no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="29cb5-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="29cb5-114">O código de exemplo a seguir mostra o contrato de serviço do serviço de processamento de pedidos.</span><span class="sxs-lookup"><span data-stu-id="29cb5-114">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 <span data-ttu-id="29cb5-115">O serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="29cb5-115">The service is self hosted.</span></span> <span data-ttu-id="29cb5-116">Ao usar o MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="29cb5-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="29cb5-117">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="29cb5-117">This can be done manually or through code.</span></span> <span data-ttu-id="29cb5-118">Neste exemplo, o serviço verifica a existência da fila e cria-se necessário.</span><span class="sxs-lookup"><span data-stu-id="29cb5-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="29cb5-119">O nome da fila é lido do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="29cb5-119">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get the MSMQ queue name from the application settings in   
    // configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
    // Create the MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
    …  
}  
```

 <span data-ttu-id="29cb5-120">O serviço cria e abre um <xref:System.ServiceModel.ServiceHost> para o `OrderProcessorService`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="29cb5-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>  

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
{  
    serviceHost.Open();  
    Console.WriteLine("The service is ready.");  
    Console.WriteLine("Press <ENTER> to terminate service.");  
    Console.ReadLine();  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="29cb5-121">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="29cb5-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29cb5-122">O nome da fila usa um ponto (.) para o computador local e os separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="29cb5-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="29cb5-123">O endereço do ponto de extremidade WCF Especifica um esquema FormatName e usa localhost para o computador local.</span><span class="sxs-lookup"><span data-stu-id="29cb5-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="29cb5-124">O endereço da fila de cada nome de formato de MSMQ diretrizes de endereçamento segue o esquema FormatName.</span><span class="sxs-lookup"><span data-stu-id="29cb5-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="29cb5-125">O aplicativo cliente é um aplicativo de MSMQ que usa o <xref:System.Messaging.MessageQueue.Send%2A> método para enviar uma mensagem de durável e transacional para a fila, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="29cb5-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>  

```csharp
//Connect to the queue.  
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);  
  
// Create the purchase order.  
PurchaseOrder po = new PurchaseOrder();  
po.CustomerId = "somecustomer.com";  
po.PONumber = Guid.NewGuid().ToString();  
  
PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
lineItem1.ProductId = "Blue Widget";  
lineItem1.Quantity = 54;  
lineItem1.UnitCost = 29.99F;  
  
PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
lineItem2.ProductId = "Red Widget";  
lineItem2.Quantity = 890;  
lineItem2.UnitCost = 45.89F;  
  
po.orderLineItems = new PurchaseOrderLineItem[2];  
po.orderLineItems[0] = lineItem1;  
po.orderLineItems[1] = lineItem2;  
  
// Submit the purchase order.  
Message msg = new Message();  
msg.Body = po;  
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
  
    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
    // Complete the transaction.  
    scope.Complete();  
  
}  
Console.WriteLine("Placed the order:{0}", po);  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```

 <span data-ttu-id="29cb5-126">Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="29cb5-127">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="29cb5-128">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="29cb5-129">Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="29cb5-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="29cb5-130">Por exemplo, executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receberia suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="29cb5-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="29cb5-131">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="29cb5-131">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="29cb5-132">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29cb5-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="29cb5-133">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="29cb5-134">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="29cb5-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="29cb5-135">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="29cb5-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="29cb5-136">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="29cb5-136">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="29cb5-137">Abra o Gerenciador do servidor no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29cb5-137">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="29cb5-138">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="29cb5-138">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="29cb5-139">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="29cb5-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="29cb5-140">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="29cb5-140">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="29cb5-141">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="29cb5-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="29cb5-142">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29cb5-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="29cb5-143">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29cb5-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="29cb5-144">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="29cb5-144">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="29cb5-145">Copie os arquivos de programa de serviço na pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="29cb5-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="29cb5-146">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="29cb5-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="29cb5-147">No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="29cb5-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="29cb5-148">No computador do serviço, inicie Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="29cb5-148">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="29cb5-149">No computador cliente, inicie Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="29cb5-149">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29cb5-150">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="29cb5-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="29cb5-151">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="29cb5-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29cb5-152">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="29cb5-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29cb5-153">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="29cb5-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="29cb5-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29cb5-154">See Also</span></span>  
 [<span data-ttu-id="29cb5-155">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="29cb5-155">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="29cb5-156">Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="29cb5-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="29cb5-157">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="29cb5-157">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)

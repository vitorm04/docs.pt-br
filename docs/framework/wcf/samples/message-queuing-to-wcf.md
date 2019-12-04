---
title: Enfileiramento de mensagens para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 4daa3694287f93aa42a139ed701578e26433bc44
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714834"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="f8350-102">Enfileiramento de mensagens para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f8350-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="f8350-103">Este exemplo demonstra como um aplicativo MSMQ (enfileiramento de mensagens) pode enviar uma mensagem MSMQ para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8350-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f8350-104">O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="f8350-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="f8350-105">O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com filas.</span><span class="sxs-lookup"><span data-stu-id="f8350-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="f8350-106">Uma mensagem MSMQ não tem um cabeçalho Action, portanto, não é possível mapear diferentes mensagens MSMQ para contratos de operação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f8350-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="f8350-107">Portanto, pode haver apenas um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="f8350-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="f8350-108">Se você quiser definir mais de um contrato de operação para o serviço, o aplicativo deverá fornecer informações sobre qual cabeçalho na mensagem MSMQ (por exemplo, o rótulo ou CorrelationId) pode ser usado para decidir qual contrato de operação deve ser redespachado.</span><span class="sxs-lookup"><span data-stu-id="f8350-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>
  
 <span data-ttu-id="f8350-109">A mensagem MSMQ não contém informações sobre quais cabeçalhos são mapeados para os diferentes parâmetros do contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="f8350-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="f8350-110">O parâmetro é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), que contém a mensagem do MSMQ subjacente.</span><span class="sxs-lookup"><span data-stu-id="f8350-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="f8350-111">O tipo "T" na classe <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) representa os dados que são serializados no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8350-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="f8350-112">Neste exemplo, o tipo de `PurchaseOrder` é serializado no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8350-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="f8350-113">O código de exemplo a seguir mostra o contrato de serviço do serviço de processamento de pedidos.</span><span class="sxs-lookup"><span data-stu-id="f8350-113">The following sample code shows the service contract of the order processing service.</span></span>  

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

 <span data-ttu-id="f8350-114">O serviço é hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="f8350-114">The service is self hosted.</span></span> <span data-ttu-id="f8350-115">Ao usar o MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="f8350-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="f8350-116">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="f8350-116">This can be done manually or through code.</span></span> <span data-ttu-id="f8350-117">Neste exemplo, o serviço verifica a existência da fila e a cria, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f8350-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="f8350-118">O nome da fila é lido no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f8350-118">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="f8350-119">O serviço cria e abre um <xref:System.ServiceModel.ServiceHost> para o `OrderProcessorService`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8350-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="f8350-120">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="f8350-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f8350-121">O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="f8350-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f8350-122">O endereço do ponto de extremidade do WCF especifica um esquema MSMQ. FormatName e usa localhost para o computador local.</span><span class="sxs-lookup"><span data-stu-id="f8350-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="f8350-123">O endereço da fila de cada diretriz de endereçamento de nome de formato MSMQ segue o esquema MSMQ. FormatName.</span><span class="sxs-lookup"><span data-stu-id="f8350-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="f8350-124">O aplicativo cliente é um aplicativo MSMQ que usa o método <xref:System.Messaging.MessageQueue.Send%2A> para enviar uma mensagem durável e transacional para a fila, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f8350-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="f8350-125">Quando você executa o exemplo, as atividades de cliente e serviço são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="f8350-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f8350-126">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="f8350-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f8350-127">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="f8350-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="f8350-128">Observe que, como o enfileiramento está em uso, o cliente e o serviço não precisam estar em funcionamento ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="f8350-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="f8350-129">Por exemplo, você pode executar o cliente, desligá-lo e, em seguida, iniciar o serviço e ele ainda receberia suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="f8350-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="f8350-130">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f8350-130">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="f8350-131">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8350-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f8350-132">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="f8350-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f8350-133">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="f8350-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f8350-134">Você pode executar o serviço primeiro para criar a fila ou pode criar um por meio do Gerenciador de filas MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8350-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f8350-135">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="f8350-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f8350-136">Abra Gerenciador do Servidor no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f8350-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f8350-137">Expanda a guia **recursos** .</span><span class="sxs-lookup"><span data-stu-id="f8350-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f8350-138">Clique com o botão direito do mouse em **filas de mensagens particulares**e selecione **nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="f8350-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f8350-139">Marque a caixa **transacional** .</span><span class="sxs-lookup"><span data-stu-id="f8350-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f8350-140">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="f8350-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f8350-141">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8350-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="f8350-142">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8350-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="f8350-143">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="f8350-143">To run the sample across computers</span></span>

1. <span data-ttu-id="f8350-144">Copie os arquivos de programa do serviço da pasta \service\bin\, na pasta específica do idioma, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="f8350-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="f8350-145">Copie os arquivos de programas do cliente da pasta \client\bin\, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="f8350-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="f8350-146">No arquivo client. exe. config, altere o orderQueueName para especificar o nome do computador de serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="f8350-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="f8350-147">No computador do serviço, inicie o Service. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f8350-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="f8350-148">No computador cliente, inicie o Client. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f8350-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8350-149">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f8350-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f8350-150">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f8350-150">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f8350-151">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="f8350-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8350-152">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f8350-152">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="f8350-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8350-153">See also</span></span>

- [<span data-ttu-id="f8350-154">Filas no WCF</span><span class="sxs-lookup"><span data-stu-id="f8350-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f8350-155">Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="f8350-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="f8350-156">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="f8350-156">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)

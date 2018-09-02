---
title: Windows Communication Foundation para enfileiramento de mensagens
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ea0723d178b37b1ff2581981f8f49a6953c913cc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403614"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="33f8a-102">Windows Communication Foundation para enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="33f8a-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="33f8a-103">Este exemplo demonstra como um aplicativo do Windows Communication Foundation (WCF) pode enviar uma mensagem a um aplicativo de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="33f8a-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="33f8a-104">O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="33f8a-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="33f8a-105">O serviço e o cliente não precisa estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="33f8a-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="33f8a-106">O serviço recebe mensagens da fila e processa ordens.</span><span class="sxs-lookup"><span data-stu-id="33f8a-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="33f8a-107">O serviço cria uma fila transacional e configura um manipulador de mensagem da mensagem recebida, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33f8a-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  

```csharp
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```

 <span data-ttu-id="33f8a-108">Quando uma mensagem é recebida na fila, o manipulador de mensagens `ProcessOrder` é invocado.</span><span class="sxs-lookup"><span data-stu-id="33f8a-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  

```csharp
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```

 <span data-ttu-id="33f8a-109">O serviço extrai a `ProcessOrder` do MSMQ corpo da mensagem e processa o pedido.</span><span class="sxs-lookup"><span data-stu-id="33f8a-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="33f8a-110">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="33f8a-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="33f8a-111">O nome da fila usa um ponto (.) para o computador local e os separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="33f8a-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="33f8a-112">O cliente cria uma ordem de compra e envia a ordem de compra dentro do escopo de uma transação, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33f8a-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  

```csharp
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```

 <span data-ttu-id="33f8a-113">O cliente usa uma cliente personalizado em ordem para enviar a mensagem do MSMQ para a fila.</span><span class="sxs-lookup"><span data-stu-id="33f8a-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="33f8a-114">Como o aplicativo que recebe e processa a mensagem é um aplicativo do MSMQ e não é um aplicativo WCF, não há nenhum contrato de serviço implícita entre os dois aplicativos.</span><span class="sxs-lookup"><span data-stu-id="33f8a-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="33f8a-115">Portanto, não podemos criar um proxy usando a ferramenta Svcutil.exe nesse cenário.</span><span class="sxs-lookup"><span data-stu-id="33f8a-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="33f8a-116">O cliente personalizado é essencialmente o mesmo para todos os aplicativos do WCF que usam o `MsmqIntegration` associação para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="33f8a-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="33f8a-117">Ao contrário de outros clientes, ele não inclui uma variedade de operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="33f8a-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="33f8a-118">Ele é apenas uma operação de mensagem de envio.</span><span class="sxs-lookup"><span data-stu-id="33f8a-118">It is a submit message operation only.</span></span>  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```

 <span data-ttu-id="33f8a-119">Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="33f8a-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="33f8a-120">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="33f8a-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="33f8a-121">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="33f8a-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="33f8a-122">Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="33f8a-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="33f8a-123">Por exemplo, executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receberia suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="33f8a-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33f8a-124">Este exemplo requer a instalação do serviço de enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="33f8a-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="33f8a-125">Consulte as instruções de instalação [enfileiramento](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="33f8a-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="33f8a-126">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="33f8a-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="33f8a-127">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f8a-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="33f8a-128">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="33f8a-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="33f8a-129">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="33f8a-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="33f8a-130">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="33f8a-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="33f8a-131">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="33f8a-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="33f8a-132">Abra o Gerenciador do servidor no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33f8a-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="33f8a-133">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="33f8a-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="33f8a-134">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="33f8a-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="33f8a-135">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="33f8a-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="33f8a-136">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="33f8a-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="33f8a-137">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f8a-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="33f8a-138">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33f8a-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="33f8a-139">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="33f8a-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="33f8a-140">Copie os arquivos de programa de serviço na pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="33f8a-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="33f8a-141">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="33f8a-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="33f8a-142">No arquivo Client.exe.config, altere o endereço do ponto de extremidade do cliente para especificar o nome do computador do serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="33f8a-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="33f8a-143">No computador do serviço, inicie Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="33f8a-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="33f8a-144">No computador cliente, inicie Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="33f8a-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33f8a-145">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="33f8a-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="33f8a-146">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="33f8a-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33f8a-147">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="33f8a-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33f8a-148">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="33f8a-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="33f8a-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33f8a-149">See Also</span></span>  
 [<span data-ttu-id="33f8a-150">Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="33f8a-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="33f8a-151">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="33f8a-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)

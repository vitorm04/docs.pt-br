---
title: Demux personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 540469571f06f9c2ab38f9754a40aae5a3c3b267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-demux"></a><span data-ttu-id="0cbbe-102">Demux personalizado</span><span class="sxs-lookup"><span data-stu-id="0cbbe-102">Custom Demux</span></span>
<span data-ttu-id="0cbbe-103">Este exemplo demonstra como cabeçalhos de mensagens MSMQ podem ser mapeados para operações de serviço diferentes para que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços que usam <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> não está limitado a usar uma operação de serviço, conforme demonstrado no [enfileiramento O Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) e [Windows Communication Foundation para enfileiramento](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemplos.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="0cbbe-104">O serviço neste exemplo é um aplicativo de console auto-hospedado para que você possa observar o serviço que recebe as mensagens em fila.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="0cbbe-105">O contrato de serviço é `IOrderProcessor`e define um serviço unidirecional que é adequado para uso com filas.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  
  
```  
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```  
  
 <span data-ttu-id="0cbbe-106">Uma mensagem MSMQ não tem um cabeçalho de ação.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="0cbbe-107">Não é possível mapear mensagens MSMQ diferentes para contratos de operação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="0cbbe-108">Portanto, pode haver apenas um contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="0cbbe-109">Para superar essa limitação, o serviço implementa o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> método o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="0cbbe-110">O <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> método permite que o serviço mapear um determinado cabeçalho da mensagem para uma operação de serviço específico.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="0cbbe-111">Neste exemplo, o cabeçalho do rótulo da mensagem é mapeado para as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="0cbbe-112">O `Name` parâmetro do contrato da operação determina qual operação de serviço deve ser distribuída para um rótulo de determinada mensagem.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="0cbbe-113">Por exemplo, se o cabeçalho do rótulo da mensagem contém "SubmitPurchaseOrder", a operação de serviço "SubmitPurchaseOrder" é invocada.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 <span data-ttu-id="0cbbe-114">O serviço deve implementar o <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> método o <xref:System.ServiceModel.Description.IContractBehavior> interface conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="0cbbe-115">Isso se aplica a custom `OperationSelector` no tempo de execução de expedição do serviço do framework.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 <span data-ttu-id="0cbbe-116">Uma mensagem deve passar pelo dispatcher <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> antes de obter a OperationSelector.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="0cbbe-117">Por padrão uma mensagem será rejeitada se a ação não pode ser encontrada em qualquer contrato implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="0cbbe-118">Para evitar essa verificação, implementamos um <xref:System.ServiceModel.Description.IEndpointBehavior> chamado `MatchAllFilterBehavior`, que permite que qualquer mensagem para passar o `ContractFilter` aplicando o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 <span data-ttu-id="0cbbe-119">Quando uma mensagem é recebida pelo serviço, a operação de serviço apropriado é enviada usando as informações fornecidas pelo cabeçalho de rótulo.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="0cbbe-120">O corpo da mensagem é desserializado em um `PurchaseOrder` do objeto, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 <span data-ttu-id="0cbbe-121">O serviço é hospedado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-121">The service is self-hosted.</span></span> <span data-ttu-id="0cbbe-122">Ao usar o MSMQ, a fila que é usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="0cbbe-123">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-123">This can be done manually or through code.</span></span> <span data-ttu-id="0cbbe-124">Neste exemplo, o serviço contém código para verificar a existência da fila e cria-se a fila não existe.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="0cbbe-125">O nome da fila é lida do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-125">The queue name is read from the configuration file.</span></span>  
  
```  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 <span data-ttu-id="0cbbe-126">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cbbe-127">O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="0cbbe-128">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endereço de ponto de extremidade Especifica um esquema FormatName e usa localhost para o computador local.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-128">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="0cbbe-129">O que segue o esquema é um endereço de fila corretamente formatado de acordo com o nome do formato de MSMQ diretrizes de endereçamento.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="0cbbe-130">Este exemplo requer a instalação do [enfileiramento](http://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="0cbbe-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="0cbbe-131">Inicie o serviço e execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="0cbbe-132">A saída a seguir é vista no cliente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-132">The following output is seen on the client.</span></span>  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="0cbbe-133">A saída a seguir deve ser vista no serviço.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-133">The following output must be seen on the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cbbe-134">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0cbbe-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0cbbe-135">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cbbe-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0cbbe-136">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="0cbbe-137">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="0cbbe-138">Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="0cbbe-139">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="0cbbe-140">Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0cbbe-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="0cbbe-141">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="0cbbe-142">Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="0cbbe-143">Verifique o **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="0cbbe-144">Digite `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="0cbbe-145">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cbbe-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="0cbbe-146">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0cbbe-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0cbbe-147">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="0cbbe-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="0cbbe-148">Copie os arquivos de programa do serviço da pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="0cbbe-149">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="0cbbe-150">No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="0cbbe-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="0cbbe-151">No computador do serviço, inicie Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="0cbbe-152">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0cbbe-153">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0cbbe-154">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0cbbe-155">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cbbe-156">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0cbbe-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="0cbbe-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cbbe-157">See Also</span></span>  
 [<span data-ttu-id="0cbbe-158">Enfileiramento no WCF</span><span class="sxs-lookup"><span data-stu-id="0cbbe-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="0cbbe-159">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="0cbbe-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)

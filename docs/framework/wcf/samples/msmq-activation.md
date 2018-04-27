---
title: Ativação de MSMQ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0f8077e425464d5a9f33662366377d573719659
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="msmq-activation"></a><span data-ttu-id="9071b-102">Ativação de MSMQ</span><span class="sxs-lookup"><span data-stu-id="9071b-102">MSMQ Activation</span></span>
<span data-ttu-id="9071b-103">Este exemplo demonstra como hospedar aplicativos no serviço de ativação de processo para Windows (WAS) que são lidos a partir de uma fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9071b-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="9071b-104">Este exemplo usa o `netMsmqBinding` e se baseia o [comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="9071b-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="9071b-105">Nesse caso, o serviço é um aplicativo Web hospedado e o cliente é auto-hospedado e saídas para o console para observar o status das ordens de compra enviada.</span><span class="sxs-lookup"><span data-stu-id="9071b-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9071b-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="9071b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9071b-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9071b-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9071b-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9071b-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="9071b-109">\<InstallDrive>:\WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="9071b-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="9071b-110">Se este diretório não existir, vá para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t blank"e o Windows Workflow Foundation (WF) exemplos para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] para baixar todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9071b-110">If this directory does not exist, go to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank"  and Windows Workflow Foundation (WF) Samples for [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] to download all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9071b-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9071b-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="9071b-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="9071b-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="9071b-113">Processo de ativação do WAS (serviço Windows), o novo mecanismo de ativação de processo para [!INCLUDE[lserver](../../../../includes/lserver-md.md)], fornece recursos como IIS que estavam anteriormente disponíveis somente para aplicativos baseados em HTTP para aplicativos que usam protocolos não HTTP.</span><span class="sxs-lookup"><span data-stu-id="9071b-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="9071b-114"> usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas nos protocolos não HTTP com suporte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], como TCP, Pipes nomeados e MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9071b-114"> uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="9071b-115">A funcionalidade para receber solicitações por meio de protocolos não HTTP é hospedada por serviços gerenciados do Windows em execução no SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="9071b-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="9071b-116">O serviço de adaptador de escuta NET. MSMQ (NetMsmqActivator) ativa aplicativos na fila com base em mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="9071b-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="9071b-117">O cliente envia ordens de compra para o serviço de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="9071b-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="9071b-118">O serviço recebe as ordens em uma transação e processá-las.</span><span class="sxs-lookup"><span data-stu-id="9071b-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="9071b-119">O serviço, em seguida, chama novamente o cliente com o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="9071b-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="9071b-120">Para facilitar a comunicação bidirecional o cliente e o serviço usam filas para enfileirar as ordens de compra e o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="9071b-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="9071b-121">O contrato de serviço `IOrderProcessor` define as operações de serviço unidirecional que funcionam com o enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9071b-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="9071b-122">A operação de serviço usa o ponto de extremidade de resposta para enviar o status de ordem para o cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="9071b-123">Endereço do ponto de extremidade de resposta é o URI da fila usada para enviar o status do pedido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="9071b-124">Aplicativo de processamento de pedidos implementa esse contrato.</span><span class="sxs-lookup"><span data-stu-id="9071b-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="9071b-125">O contrato de resposta para enviar o status do pedido é especificado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="9071b-126">O cliente implementa o contrato de status de ordem.</span><span class="sxs-lookup"><span data-stu-id="9071b-126">The client implements the order status contract.</span></span> <span data-ttu-id="9071b-127">O serviço usa o cliente gerada deste contrato para enviar o status do pedido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="9071b-128">A operação de serviço processa o pedido de compra enviado.</span><span class="sxs-lookup"><span data-stu-id="9071b-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="9071b-129">O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicada à operação de serviço para especificar a inscrição automática na transação que é usada para receber a mensagem da fila e o preenchimento automático da transação após a conclusão da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="9071b-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="9071b-130">O `Orders` classe encapsula a funcionalidade de ordem de processamento.</span><span class="sxs-lookup"><span data-stu-id="9071b-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="9071b-131">Nesse caso, ele adiciona o pedido de compra para um dicionário.</span><span class="sxs-lookup"><span data-stu-id="9071b-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="9071b-132">A transação que a operação de serviço inscrita em está disponível para as operações de `Orders` classe.</span><span class="sxs-lookup"><span data-stu-id="9071b-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="9071b-133">A operação de serviço, além de processamento de ordem de compra enviado, responde ao cliente sobre o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="9071b-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }  
```  
  
 <span data-ttu-id="9071b-134">O cliente de associação a ser usado é especificado usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9071b-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="9071b-135">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9071b-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="9071b-136">O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9071b-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9071b-137">O endereço de nome e o ponto de extremidade de fila MSMQ usam convenções de endereçamento ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="9071b-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="9071b-138">O nome da fila MSMQ usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="9071b-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="9071b-139">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endereço de ponto de extremidade Especifica um NET. MSMQ: esquema, use "localhost" para o computador local e usa barras em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="9071b-139">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="9071b-140">Para ler de uma fila que está hospedada no computador remoto, substitua o "." e "localhost" como nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="9071b-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="9071b-141">Um arquivo. svc com o nome da classe é usado para hospedar o código de serviço no WAS.</span><span class="sxs-lookup"><span data-stu-id="9071b-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="9071b-142">O próprio arquivo SVC contém uma diretiva para criar o `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="9071b-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="9071b-143">O arquivo SVC também contém uma diretiva de assembly para garantir que o System.Transactions.dll é carregado.</span><span class="sxs-lookup"><span data-stu-id="9071b-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="9071b-144">O cliente cria um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="9071b-144">The client creates a transaction scope.</span></span> <span data-ttu-id="9071b-145">Comunicação com o serviço ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica, onde todas as mensagens de êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="9071b-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="9071b-146">A transação é confirmada chamando `Complete` no escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="9071b-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
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
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 <span data-ttu-id="9071b-147">O código do cliente implementa a `IOrderStatus` contrato receber o status do pedido do serviço.</span><span class="sxs-lookup"><span data-stu-id="9071b-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="9071b-148">Nesse caso, exibe o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="9071b-148">In this case, it prints out the order status.</span></span>  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 <span data-ttu-id="9071b-149">A fila de status de ordem é criada no `Main` método.</span><span class="sxs-lookup"><span data-stu-id="9071b-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="9071b-150">A configuração do cliente inclui a configuração de serviço de status de ordem para hospedar o serviço de status de ordem, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9071b-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```csharp  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="9071b-151">Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas no servidor e janelas de console do cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="9071b-152">Você pode ver o servidor de mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="9071b-153">Pressione ENTER em cada janela de console para desligar o servidor e o cliente.</span><span class="sxs-lookup"><span data-stu-id="9071b-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="9071b-154">O cliente exibe as informações de status de ordem enviadas pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="9071b-154">The client displays the order status information sent by the server:</span></span>  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9071b-155">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9071b-155">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9071b-156">Certifique-se de que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] está instalado, como ele é necessário para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="9071b-156">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed, as it is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="9071b-157">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9071b-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="9071b-158">Além disso, você deve instalar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de ativação não HTTP:</span><span class="sxs-lookup"><span data-stu-id="9071b-158">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="9071b-159">Do **iniciar** menu, escolha **painel de controle**.</span><span class="sxs-lookup"><span data-stu-id="9071b-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="9071b-160">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="9071b-160">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="9071b-161">Clique em **ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="9071b-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4.  <span data-ttu-id="9071b-162">Em **resumo dos recursos**, clique em **adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="9071b-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5.  <span data-ttu-id="9071b-163">Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.</span><span class="sxs-lookup"><span data-stu-id="9071b-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="9071b-164">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9071b-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="9071b-165">Execute o cliente ao executar client.exe em uma janela de comando.</span><span class="sxs-lookup"><span data-stu-id="9071b-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="9071b-166">Isso cria a fila e envia uma mensagem a ele.</span><span class="sxs-lookup"><span data-stu-id="9071b-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="9071b-167">Deixe o cliente em execução para ver o resultado do serviço de ler a mensagem</span><span class="sxs-lookup"><span data-stu-id="9071b-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5.  <span data-ttu-id="9071b-168">O serviço de ativação MSMQ é executado como serviço de rede por padrão.</span><span class="sxs-lookup"><span data-stu-id="9071b-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="9071b-169">Portanto, a fila que é usada para ativar o aplicativo deve ter receber e inspecionar permissões para serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="9071b-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="9071b-170">Isso pode ser adicionado usando o MMC de enfileiramento de mensagens:</span><span class="sxs-lookup"><span data-stu-id="9071b-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1.  <span data-ttu-id="9071b-171">Do **iniciar** menu, clique em **executar**, em seguida, digite `Compmgmt.msc` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="9071b-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2.  <span data-ttu-id="9071b-172">Em **serviços e aplicativos**, expanda **enfileiramento**.</span><span class="sxs-lookup"><span data-stu-id="9071b-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3.  <span data-ttu-id="9071b-173">Clique em **filas particulares**.</span><span class="sxs-lookup"><span data-stu-id="9071b-173">Click **Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="9071b-174">Clique em fila (servicemodelsamples/Service.svc) e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9071b-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5.  <span data-ttu-id="9071b-175">Sobre o **segurança** , clique em **adicionar** e dê a inspeção e receber permissões para serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="9071b-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6.  <span data-ttu-id="9071b-176">Configure o Windows processo Activation Service (WAS) para dar suporte à ativação de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9071b-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="9071b-177">Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado AddMsmqSiteBinding.cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="9071b-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="9071b-178">Para dar suporte à ativação do NET. MSMQ, site da Web padrão primeiro deve ser associado ao protocolo NET. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9071b-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="9071b-179">Isso pode ser feito usando o appcmd.exe, que é instalado com o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] conjunto de ferramentas de gerenciamento.</span><span class="sxs-lookup"><span data-stu-id="9071b-179">This can be done using appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="9071b-180">Em um prompt de comando com privilégios elevados (administrador), execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="9071b-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="9071b-181">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="9071b-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="9071b-182">Este comando adiciona uma associação de site do MSMQ para o site da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="9071b-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="9071b-183">Embora todos os aplicativos dentro de um site compartilham uma associação de NET. MSMQ comuns, cada aplicativo pode habilitar o suporte do NET. MSMQ individualmente.</span><span class="sxs-lookup"><span data-stu-id="9071b-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="9071b-184">Para habilitar o NET. MSMQ para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="9071b-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="9071b-185">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="9071b-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="9071b-186">Este comando permite que o aplicativo /servicemodelsamples ser acessados usando http://localhost/servicemodelsamples e net.msmq://localhost/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="9071b-186">This command enables the /servicemodelsamples application to be accessed using http://localhost/servicemodelsamples and net.msmq://localhost/servicemodelsamples.</span></span>  
  
7.  <span data-ttu-id="9071b-187">Se você não o fez anteriormente, certifique-se de que o serviço de ativação MSMQ está habilitado.</span><span class="sxs-lookup"><span data-stu-id="9071b-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="9071b-188">Do **iniciar** menu, clique em **executar**e o tipo `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="9071b-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="9071b-189">Pesquisar a lista de serviços para o **adaptador de escuta NET. MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="9071b-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="9071b-190">Clique com botão direito e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9071b-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="9071b-191">Definir o **o tipo de inicialização** para **automático**, clique em **aplicar** e clique no **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="9071b-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="9071b-192">Esta etapa deve ser feita apenas uma vez antes do primeiro uso do serviço de adaptador de escuta NET. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9071b-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8.  <span data-ttu-id="9071b-193">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9071b-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="9071b-194">Além disso, altere o código no cliente que envia a ordem de compra para refletir o nome do computador no URI da fila ao enviar o pedido de compra.</span><span class="sxs-lookup"><span data-stu-id="9071b-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="9071b-195">Use o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="9071b-195">Use the following code:</span></span>  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="9071b-196">Remova a associação de site do NET. MSMQ adicionado para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="9071b-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="9071b-197">Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado RemoveMsmqSiteBinding.cmd localizado no diretório de exemplo:</span><span class="sxs-lookup"><span data-stu-id="9071b-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="9071b-198">Remova NET. MSMQ da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="9071b-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="9071b-199">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="9071b-199">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="9071b-200">Remova a associação do site MSMQ executando o seguinte comando em um prompt de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="9071b-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="9071b-201">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="9071b-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="9071b-202">Executar o arquivo em lotes será redefinido DefaultAppPool para ser executado usando o .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="9071b-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="9071b-203">Por padrão, com o `netMsmqBinding` transporte de associação de segurança está habilitada.</span><span class="sxs-lookup"><span data-stu-id="9071b-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="9071b-204">Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinar o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="9071b-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="9071b-205">Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="9071b-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="9071b-206">Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="9071b-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="9071b-207">Se você executar esse exemplo em um computador que não faz parte de um domínio, o seguinte erro foi recebido: "Mensagem interna do usuário certificado do enfileiramento de mensagens não existe".</span><span class="sxs-lookup"><span data-stu-id="9071b-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="9071b-208">Para executar o exemplo em um computador associado a um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9071b-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="9071b-209">Se o computador não fizer parte de um domínio, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação como none, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9071b-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  <span data-ttu-id="9071b-210">Altere a configuração no servidor e o cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="9071b-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9071b-211">Configuração `security mode` para `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel` e `Message` segurança `None`.</span><span class="sxs-lookup"><span data-stu-id="9071b-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="9071b-212">Para habilitar a ativação em um computador associado a um grupo de trabalho, o serviço de ativação e o processo de trabalho devem ser executados com uma conta de usuário específica (deve ser o mesmo para ambos) e a fila deve ter as ACLs para a conta de usuário específico.</span><span class="sxs-lookup"><span data-stu-id="9071b-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="9071b-213">Para alterar a identidade do processo de trabalho é executado:</span><span class="sxs-lookup"><span data-stu-id="9071b-213">To change the identity that the worker process runs under:</span></span>  
  
    1.  <span data-ttu-id="9071b-214">Execute Inetmgr.exe.</span><span class="sxs-lookup"><span data-stu-id="9071b-214">Run Inetmgr.exe.</span></span>  
  
    2.  <span data-ttu-id="9071b-215">Em **Pools de aplicativos**, com o botão direito do **AppPool** (normalmente **DefaultAppPool**) e escolha **definir padrões do Pool de aplicativos...** .</span><span class="sxs-lookup"><span data-stu-id="9071b-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3.  <span data-ttu-id="9071b-216">Altere as propriedades de identidade para usar a conta de usuário específico.</span><span class="sxs-lookup"><span data-stu-id="9071b-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="9071b-217">Para alterar a identidade que o serviço de ativação é executado:</span><span class="sxs-lookup"><span data-stu-id="9071b-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1.  <span data-ttu-id="9071b-218">Execute Services.msc.</span><span class="sxs-lookup"><span data-stu-id="9071b-218">Run Services.msc.</span></span>  
  
    2.  <span data-ttu-id="9071b-219">Clique com botão direito do **Net.MsmqListener adaptador**e escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="9071b-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4.  <span data-ttu-id="9071b-220">Alterar a conta no **LogOn** guia.</span><span class="sxs-lookup"><span data-stu-id="9071b-220">Change the account in the **LogOn** tab.</span></span>  
  
5.  <span data-ttu-id="9071b-221">Grupo de trabalho, o serviço também deve executar usando um token irrestrito.</span><span class="sxs-lookup"><span data-stu-id="9071b-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="9071b-222">Para fazer isso, execute o seguinte em uma janela de comando:</span><span class="sxs-lookup"><span data-stu-id="9071b-222">To do this, run the following in a command window:</span></span>  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9071b-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9071b-223">See Also</span></span>  
 [<span data-ttu-id="9071b-224">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="9071b-224">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)

---
title: Ativação de MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 038f4d7e3d713cfe4134ea98f7858ef71f29bab4
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895246"
---
# <a name="msmq-activation"></a><span data-ttu-id="3962f-102">Ativação de MSMQ</span><span class="sxs-lookup"><span data-stu-id="3962f-102">MSMQ Activation</span></span>

<span data-ttu-id="3962f-103">Este exemplo demonstra como hospedar aplicativos no WAS (serviço de ativação de processos do Windows) que são lidos de uma fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="3962f-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="3962f-104">Este exemplo usa o `netMsmqBinding` e é baseado no exemplo de [comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md) .</span><span class="sxs-lookup"><span data-stu-id="3962f-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="3962f-105">O serviço, nesse caso, é um aplicativo hospedado na Web e o cliente é hospedado internamente e saídas para o console para observar o status dos pedidos de compra enviados.</span><span class="sxs-lookup"><span data-stu-id="3962f-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="3962f-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3962f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="3962f-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3962f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3962f-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3962f-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="3962f-109">\<InstallDrive>:\WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="3962f-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="3962f-110">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="3962f-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3962f-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3962f-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="3962f-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="3962f-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="3962f-113">O WAS (serviço de ativação de processos do Windows), o novo [!INCLUDE[lserver](../../../../includes/lserver-md.md)]mecanismo de ativação do processo do, fornece recursos semelhantes ao IIS que estavam disponíveis anteriormente apenas para aplicativos baseados em http para aplicativos que usam protocolos não-http.</span><span class="sxs-lookup"><span data-stu-id="3962f-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="3962f-114">O Windows Communication Foundation (WCF) usa a interface do adaptador do ouvinte para comunicar solicitações de ativação recebidas em protocolos não HTTP com suporte do WCF, como TCP, pipes nomeados e MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3962f-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="3962f-115">A funcionalidade para receber solicitações em protocolos não HTTP é hospedada por serviços gerenciados do Windows em execução no SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="3962f-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="3962f-116">O serviço de adaptador de escuta net. MSMQ (NetMsmqActivator) ativa os aplicativos em fila com base nas mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="3962f-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="3962f-117">O cliente envia pedidos de compra para o serviço de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="3962f-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="3962f-118">O serviço recebe os pedidos em uma transação e os processa.</span><span class="sxs-lookup"><span data-stu-id="3962f-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="3962f-119">Em seguida, o serviço chama o cliente com o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="3962f-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="3962f-120">Para facilitar a comunicação bidirecional, o cliente e o serviço usam filas para enfileirar ordens de compra e status do pedido.</span><span class="sxs-lookup"><span data-stu-id="3962f-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="3962f-121">O contrato `IOrderProcessor` de serviço define as operações de serviço unidirecionais que funcionam com o enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="3962f-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="3962f-122">A operação de serviço usa o ponto de extremidade de resposta para enviar status do pedido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="3962f-123">O endereço do ponto de extremidade de resposta é o URI da fila usada para enviar o status do pedido de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="3962f-124">O aplicativo de processamento de pedidos implementa esse contrato.</span><span class="sxs-lookup"><span data-stu-id="3962f-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="3962f-125">O contrato de resposta para o qual enviar o status do pedido é especificado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="3962f-126">O cliente implementa o contrato de status do pedido.</span><span class="sxs-lookup"><span data-stu-id="3962f-126">The client implements the order status contract.</span></span> <span data-ttu-id="3962f-127">O serviço usa o cliente gerado deste contrato para enviar o status do pedido de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="3962f-128">A operação de serviço processa a ordem de compra enviada.</span><span class="sxs-lookup"><span data-stu-id="3962f-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="3962f-129">O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicado à operação de serviço para especificar a inscrição automática na transação que é usada para receber a mensagem da fila e a conclusão automática da transação na conclusão da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="3962f-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="3962f-130">A `Orders` classe encapsula a funcionalidade de processamento de pedidos.</span><span class="sxs-lookup"><span data-stu-id="3962f-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="3962f-131">Nesse caso, ele adiciona a ordem de compra a um dicionário.</span><span class="sxs-lookup"><span data-stu-id="3962f-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="3962f-132">A transação na qual a operação de serviço inscrito está disponível para as operações na `Orders` classe.</span><span class="sxs-lookup"><span data-stu-id="3962f-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="3962f-133">A operação de serviço, além de processar a ordem de compra enviada, responde de volta ao cliente sobre o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="3962f-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

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
}
```

<span data-ttu-id="3962f-134">A associação de cliente a ser usada é especificada usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3962f-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="3962f-135">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3962f-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="3962f-136">O ponto de extremidade para o serviço é definido na seção System. serviceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3962f-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="3962f-137">O nome da fila MSMQ e o endereço do ponto de extremidade usam convenções de endereçamento ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="3962f-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="3962f-138">O nome da fila MSMQ usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="3962f-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="3962f-139">O endereço do ponto de extremidade do WCF especifica um net. MSMQ: esquema, usa "localhost" para o computador local e usa barras invertidas em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="3962f-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="3962f-140">Para ler de uma fila que está hospedada no computador remoto, substitua "." e "localhost" pelo nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="3962f-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="3962f-141">Um arquivo. svc com o nome da classe é usado para hospedar o código do serviço no WAS.</span><span class="sxs-lookup"><span data-stu-id="3962f-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="3962f-142">O próprio arquivo Service. svc contém uma diretiva para criar o `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="3962f-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="3962f-143">O arquivo Service. svc também contém uma diretiva de assembly para garantir que System. Transactions. dll seja carregado.</span><span class="sxs-lookup"><span data-stu-id="3962f-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="3962f-144">O cliente cria um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="3962f-144">The client creates a transaction scope.</span></span> <span data-ttu-id="3962f-145">A comunicação com o serviço ocorre dentro do escopo da transação, fazendo com que ele seja tratado como uma unidade atômica onde todas as mensagens são bem sucedidas ou falham.</span><span class="sxs-lookup"><span data-stu-id="3962f-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="3962f-146">A transação é confirmada `Complete` chamando o escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="3962f-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

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

<span data-ttu-id="3962f-147">O código do cliente implementa `IOrderStatus` o contrato para receber o status do pedido do serviço.</span><span class="sxs-lookup"><span data-stu-id="3962f-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="3962f-148">Nesse caso, ele imprime o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="3962f-148">In this case, it prints out the order status.</span></span>

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

<span data-ttu-id="3962f-149">A fila status do pedido é criada no `Main` método.</span><span class="sxs-lookup"><span data-stu-id="3962f-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="3962f-150">A configuração do cliente inclui a configuração do serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3962f-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
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

<span data-ttu-id="3962f-151">Quando você executa o exemplo, as atividades de cliente e serviço são exibidas nas janelas do console do servidor e do cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="3962f-152">Você pode ver o servidor receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="3962f-153">Pressione ENTER em cada janela do console para desligar o servidor e o cliente.</span><span class="sxs-lookup"><span data-stu-id="3962f-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="3962f-154">O cliente exibe as informações de status do pedido enviadas pelo servidor:</span><span class="sxs-lookup"><span data-stu-id="3962f-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3962f-155">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3962f-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3962f-156">Verifique se o IIS 7,0 está instalado, pois ele é necessário para a ativação do WAS.</span><span class="sxs-lookup"><span data-stu-id="3962f-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="3962f-157">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3962f-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="3962f-158">Além disso, você deve instalar os componentes de ativação não HTTP do WCF:</span><span class="sxs-lookup"><span data-stu-id="3962f-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="3962f-159">No menu **Iniciar**, selecione **Painel de Controle**.</span><span class="sxs-lookup"><span data-stu-id="3962f-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="3962f-160">Selecione **programas e recursos**.</span><span class="sxs-lookup"><span data-stu-id="3962f-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="3962f-161">Clique em **Ativar ou desativar recursos do Windows**.</span><span class="sxs-lookup"><span data-stu-id="3962f-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="3962f-162">Em **Resumo de recursos**, clique em **Adicionar recursos**.</span><span class="sxs-lookup"><span data-stu-id="3962f-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="3962f-163">Expanda o nó **Microsoft .NET Framework 3,0** e verifique o Windows Communication Foundation recurso de **ativação não http** .</span><span class="sxs-lookup"><span data-stu-id="3962f-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="3962f-164">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3962f-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="3962f-165">Execute o cliente executando o Client. exe em uma janela de comando.</span><span class="sxs-lookup"><span data-stu-id="3962f-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="3962f-166">Isso cria a fila e envia uma mensagem a ela.</span><span class="sxs-lookup"><span data-stu-id="3962f-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="3962f-167">Deixe o cliente em execução para ver o resultado do serviço que está lendo a mensagem</span><span class="sxs-lookup"><span data-stu-id="3962f-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="3962f-168">Por padrão, o serviço de ativação MSMQ é executado como serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="3962f-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="3962f-169">Portanto, a fila usada para ativar o aplicativo deve ter permissões RECEIVE e Peek para o serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="3962f-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="3962f-170">Isso pode ser adicionado usando o MMC do enfileiramento de mensagens:</span><span class="sxs-lookup"><span data-stu-id="3962f-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="3962f-171">No menu **Iniciar** , clique em **executar**, digite `Compmgmt.msc` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="3962f-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="3962f-172">Em **serviços e aplicativos**, expanda **enfileiramento de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="3962f-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="3962f-173">Clique em **filas particulares**.</span><span class="sxs-lookup"><span data-stu-id="3962f-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="3962f-174">Clique com o botão direito do mouse na fila (servicemodelsamples/Service. svc) e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3962f-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="3962f-175">Na guia **segurança** , clique em **Adicionar** e dê permissões de Peek e recebimento ao serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="3962f-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="3962f-176">Configure o WAS (serviço de ativação de processos do Windows) para dar suporte à ativação do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3962f-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="3962f-177">Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado AddMsmqSiteBinding. cmd localizado no diretório de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3962f-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="3962f-178">Para dar suporte à ativação do NET. MSMQ, o site padrão deve primeiro ser associado ao protocolo net. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3962f-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="3962f-179">Isso pode ser feito usando o Appcmd. exe, que é instalado com o conjunto de ferramentas de gerenciamento do IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="3962f-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="3962f-180">Em um prompt de comando elevado (administrador), execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="3962f-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="3962f-181">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="3962f-181">This command is a single line of text.</span></span>

        <span data-ttu-id="3962f-182">Esse comando adiciona uma associação de site net. MSMQ ao site da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="3962f-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="3962f-183">Embora todos os aplicativos em um site compartilhem uma associação net. MSMQ comum, cada aplicativo pode habilitar o suporte net. MSMQ individualmente.</span><span class="sxs-lookup"><span data-stu-id="3962f-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="3962f-184">Para habilitar net. MSMQ para o aplicativo/servicemodelsamples, execute o comando a seguir em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="3962f-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="3962f-185">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="3962f-185">This command is a single line of text.</span></span>

        <span data-ttu-id="3962f-186">Esse comando permite que o aplicativo/servicemodelsamples seja acessado `net.msmq://localhost/servicemodelsamples`usando `http://localhost/servicemodelsamples` e.</span><span class="sxs-lookup"><span data-stu-id="3962f-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="3962f-187">Se você não tiver feito isso anteriormente, verifique se o serviço de ativação MSMQ está habilitado.</span><span class="sxs-lookup"><span data-stu-id="3962f-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="3962f-188">No menu **Iniciar** , clique em **executar**e digite `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="3962f-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="3962f-189">Pesquise a lista de serviços para o **adaptador de escuta net. MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="3962f-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="3962f-190">Clique com o botão direito do mouse e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3962f-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="3962f-191">Defina o **tipo de inicialização** como **automático**, clique em **aplicar** e clique no botão **Iniciar** .</span><span class="sxs-lookup"><span data-stu-id="3962f-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="3962f-192">Essa etapa deve ser feita apenas uma vez antes do primeiro uso do serviço do adaptador de escuta net. MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3962f-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="3962f-193">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3962f-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="3962f-194">Além disso, altere o código no cliente que envia a ordem de compra para refletir o nome do computador no URI da fila ao enviar a ordem de compra.</span><span class="sxs-lookup"><span data-stu-id="3962f-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="3962f-195">Use o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3962f-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="3962f-196">Remova a associação de site net. MSMQ que você adicionou para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="3962f-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="3962f-197">Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado RemoveMsmqSiteBinding. cmd localizado no diretório de exemplo:</span><span class="sxs-lookup"><span data-stu-id="3962f-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="3962f-198">Remova net. MSMQ da lista de protocolos habilitados executando o comando a seguir em um prompt de comandos com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="3962f-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="3962f-199">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="3962f-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="3962f-200">Remova a associação de site net. MSMQ executando o comando a seguir em um prompt de comando elevado.</span><span class="sxs-lookup"><span data-stu-id="3962f-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="3962f-201">Esse comando é uma única linha de texto.</span><span class="sxs-lookup"><span data-stu-id="3962f-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="3962f-202">A execução do arquivo em lotes redefinirá o DefaultAppPool para ser executado usando .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="3962f-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="3962f-203">Por padrão, com `netMsmqBinding` o transporte de associação, a segurança é habilitada.</span><span class="sxs-lookup"><span data-stu-id="3962f-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="3962f-204">Duas propriedades `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntas, determinam o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="3962f-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="3962f-205">Por padrão, o modo de autenticação é `Windows` definido como e o nível de proteção `Sign`é definido como.</span><span class="sxs-lookup"><span data-stu-id="3962f-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="3962f-206">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="3962f-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="3962f-207">Se você executar esse exemplo em um computador que não faz parte de um domínio, o seguinte erro será recebido: "O certificado interno do enfileiramento de mensagens do usuário não existe".</span><span class="sxs-lookup"><span data-stu-id="3962f-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="3962f-208">Para executar o exemplo em um computador ingressado em um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3962f-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="3962f-209">Se o computador não fizer parte de um domínio, desative a segurança de transporte definindo o modo de autenticação e o nível de proteção como nenhum, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="3962f-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="3962f-210">Altere a configuração no servidor e no cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="3962f-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3962f-211">A `security mode` configuração `None` `MsmqAuthenticationMode`como éequivalente`Message` à configuração `None`e à segurança para. `MsmqProtectionLevel`</span><span class="sxs-lookup"><span data-stu-id="3962f-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="3962f-212">Para habilitar a ativação em um computador ingressado em um grupo de trabalho, o serviço de ativação e o processo de trabalho devem ser executados com uma conta de usuário específica (deve ser o mesmo para ambos) e a fila deve ter ACLs para a conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="3962f-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="3962f-213">Para alterar a identidade sob a qual o processo de trabalho é executado:</span><span class="sxs-lookup"><span data-stu-id="3962f-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="3962f-214">Execute inetmgr. exe.</span><span class="sxs-lookup"><span data-stu-id="3962f-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="3962f-215">Em **pools de aplicativos**, clique com o botão direito do mouse no **AppPool** (normalmente **DefaultAppPool**) e escolha **definir padrões do pool de aplicativos...** .</span><span class="sxs-lookup"><span data-stu-id="3962f-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="3962f-216">Altere as propriedades de identidade para usar a conta de usuário específica.</span><span class="sxs-lookup"><span data-stu-id="3962f-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="3962f-217">Para alterar a identidade em que o serviço de ativação é executado:</span><span class="sxs-lookup"><span data-stu-id="3962f-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="3962f-218">Execute Services. msc.</span><span class="sxs-lookup"><span data-stu-id="3962f-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="3962f-219">Clique com o botão direito do mouse no **adaptador net. MsmqListener**e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3962f-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="3962f-220">Altere a conta na guia **logon** .</span><span class="sxs-lookup"><span data-stu-id="3962f-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="3962f-221">No grupo de trabalho, o serviço também deve ser executado usando um token irrestrito.</span><span class="sxs-lookup"><span data-stu-id="3962f-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="3962f-222">Para fazer isso, execute o seguinte em uma janela de comando:</span><span class="sxs-lookup"><span data-stu-id="3962f-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="3962f-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3962f-223">See also</span></span>

- [<span data-ttu-id="3962f-224">Exemplos de persistência e de hospedagem do AppFabric</span><span class="sxs-lookup"><span data-stu-id="3962f-224">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)

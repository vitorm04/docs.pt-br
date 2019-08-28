---
title: Comunicação bidirecional
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 379197ee3dc041351f0b13ad1e336824a0f411ed
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038714"
---
# <a name="two-way-communication"></a><span data-ttu-id="b9c39-102">Comunicação bidirecional</span><span class="sxs-lookup"><span data-stu-id="b9c39-102">Two-Way Communication</span></span>
<span data-ttu-id="b9c39-103">Este exemplo demonstra como executar a comunicação em fila de duas vias transacionada no MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b9c39-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="b9c39-104">Este exemplo usa a `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="b9c39-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="b9c39-105">Nesse caso, o serviço é um aplicativo de console auto-hospedado que permite que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="b9c39-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9c39-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b9c39-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b9c39-107">Este exemplo é baseado na [associação MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)transacionada.</span><span class="sxs-lookup"><span data-stu-id="b9c39-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="b9c39-108">Na comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="b9c39-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="b9c39-109">O cliente envia mensagens para uma fila e o serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="b9c39-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="b9c39-110">O serviço e o cliente, portanto, não precisam estar em execução ao mesmo tempo para se comunicarem usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="b9c39-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="b9c39-111">Este exemplo demonstra a comunicação bidirecional usando filas.</span><span class="sxs-lookup"><span data-stu-id="b9c39-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="b9c39-112">O cliente envia pedidos de compra para a fila de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="b9c39-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="b9c39-113">O serviço recebe os pedidos, processa a ordem e, em seguida, chama o cliente com o status da ordem da fila dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="b9c39-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="b9c39-114">Para facilitar a comunicação bidirecional, o cliente e o serviço usam filas para enfileirar ordens de compra e status do pedido.</span><span class="sxs-lookup"><span data-stu-id="b9c39-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="b9c39-115">O contrato `IOrderProcessor` de serviço define operações de serviço unidirecionais que se adaptam ao uso do enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="b9c39-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="b9c39-116">A operação de serviço inclui o ponto de extremidade de resposta a ser usado para enviar os status do pedido para.</span><span class="sxs-lookup"><span data-stu-id="b9c39-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="b9c39-117">O ponto de extremidade de resposta é o URI da fila para enviar o status do pedido de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="b9c39-118">O aplicativo de processamento de pedidos implementa esse contrato.</span><span class="sxs-lookup"><span data-stu-id="b9c39-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="b9c39-119">O contrato de resposta para enviar o status da ordem é especificado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="b9c39-120">O cliente implementa o contrato de status do pedido.</span><span class="sxs-lookup"><span data-stu-id="b9c39-120">The client implements the order status contract.</span></span> <span data-ttu-id="b9c39-121">O serviço usa o proxy gerado deste contrato para enviar o status do pedido de volta para o cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="b9c39-122">A operação de serviço processa a ordem de compra enviada.</span><span class="sxs-lookup"><span data-stu-id="b9c39-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="b9c39-123">O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicado à operação de serviço para especificar a inscrição automática em uma transação que é usada para receber a mensagem da fila e a conclusão automática de transações na conclusão da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c39-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="b9c39-124">A `Orders` classe encapsula a funcionalidade de processamento de pedidos.</span><span class="sxs-lookup"><span data-stu-id="b9c39-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="b9c39-125">Nesse caso, ele adiciona a ordem de compra a um dicionário.</span><span class="sxs-lookup"><span data-stu-id="b9c39-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="b9c39-126">A transação na qual a operação de serviço inscrito está disponível para as operações na `Orders` classe.</span><span class="sxs-lookup"><span data-stu-id="b9c39-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="b9c39-127">A operação de serviço, além de processar a ordem de compra enviada, responde de volta ao cliente no status do pedido.</span><span class="sxs-lookup"><span data-stu-id="b9c39-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="b9c39-128">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9c39-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="b9c39-129">O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9c39-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9c39-130">O nome da fila MSMQ e o endereço do ponto de extremidade usam convenções de endereçamento ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="b9c39-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="b9c39-131">O nome da fila MSMQ usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="b9c39-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="b9c39-132">O endereço do ponto de extremidade do Windows Communication Foundation (WCF) especifica um net. MSMQ: esquema, usa "localhost" para o computador local e usa barras invertidas em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="b9c39-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="b9c39-133">Para ler de uma fila hospedada no computador remoto, substitua "." e "localhost" pelo nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="b9c39-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="b9c39-134">O serviço é hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-134">The service is self hosted.</span></span> <span data-ttu-id="b9c39-135">Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="b9c39-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="b9c39-136">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="b9c39-136">This can be done manually or through code.</span></span> <span data-ttu-id="b9c39-137">Neste exemplo, o serviço verifica a existência da fila e a cria, se necessário.</span><span class="sxs-lookup"><span data-stu-id="b9c39-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="b9c39-138">O nome da fila é lido no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b9c39-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="b9c39-139">O endereço base é usado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c39-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="b9c39-140">O cliente cria uma transação.</span><span class="sxs-lookup"><span data-stu-id="b9c39-140">The client creates a transaction.</span></span> <span data-ttu-id="b9c39-141">A comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ela seja tratada como uma unidade atômica onde todas as mensagens são bem sucedidas ou falham.</span><span class="sxs-lookup"><span data-stu-id="b9c39-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="b9c39-142">O código do cliente implementa `IOrderStatus` o contrato para receber o status do pedido do serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c39-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="b9c39-143">Nesse caso, ele imprime o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="b9c39-143">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,   
                                                           status);  
    }  
}  
```

 <span data-ttu-id="b9c39-144">A fila status do pedido é criada no `Main` método.</span><span class="sxs-lookup"><span data-stu-id="b9c39-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="b9c39-145">A configuração do cliente inclui a configuração do serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="b9c39-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service   
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
              binding="netMsmqBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b9c39-146">Quando você executa o exemplo, as atividades de cliente e serviço são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c39-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b9c39-147">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="b9c39-148">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="b9c39-149">O serviço exibe as informações da ordem de compra e indica que está enviando de volta o status do pedido para a fila status do pedido.</span><span class="sxs-lookup"><span data-stu-id="b9c39-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="b9c39-150">O cliente exibe as informações de status do pedido enviadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c39-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b9c39-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b9c39-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b9c39-152">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b9c39-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b9c39-153">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b9c39-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b9c39-154">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b9c39-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9c39-155">Se você usar svcutil. exe para regenerar a configuração para este exemplo, certifique-se de modificar os nomes dos pontos de extremidade na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="b9c39-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="b9c39-156">Por padrão, com <xref:System.ServiceModel.NetMsmqBinding>a segurança de transporte está habilitada.</span><span class="sxs-lookup"><span data-stu-id="b9c39-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="b9c39-157">Há duas propriedades relevantes para a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> segurança de transporte do MSMQ e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` , por padrão, o modo de autenticação `Windows` é definido como e o nível de `Sign`proteção é definido como.</span><span class="sxs-lookup"><span data-stu-id="b9c39-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="b9c39-158">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio e a opção de integração do Active Directory para o MSMQ deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="b9c39-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="b9c39-159">Se você executar esse exemplo em um computador que não atenda a esses critérios, receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="b9c39-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="b9c39-160">Para executar o exemplo em um computador ingressado em um grupo de trabalho ou sem integração com o Active Directory</span><span class="sxs-lookup"><span data-stu-id="b9c39-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="b9c39-161">Se o seu computador não fizer parte de um domínio ou não tiver a integração do Active Directory instalada, desative a segurança de transporte definindo o modo de autenticação `None` e o nível de proteção como mostrado na seguinte configuração de exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9c39-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"   
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="b9c39-162">Desativar a segurança para uma configuração de cliente gera o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b9c39-162">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service   
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
                    binding="netMsmqBinding"   
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="b9c39-163">O serviço para este exemplo cria uma associação no `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="b9c39-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="b9c39-164">Adicione uma linha de código depois que a associação é instanciada para definir o modo de `None`segurança como.</span><span class="sxs-lookup"><span data-stu-id="b9c39-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="b9c39-165">Certifique-se de alterar a configuração no servidor e no cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="b9c39-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9c39-166">A `security mode` configuração `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>como éequivalente`Message` à configuração `None`ou à segurança para. <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A></span><span class="sxs-lookup"><span data-stu-id="b9c39-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b9c39-167">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b9c39-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9c39-168">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b9c39-168">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b9c39-169">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="b9c39-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9c39-170">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b9c39-170">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  

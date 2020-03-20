---
title: Comunicação bidirecional
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143753"
---
# <a name="two-way-communication"></a><span data-ttu-id="0e413-102">Comunicação bidirecional</span><span class="sxs-lookup"><span data-stu-id="0e413-102">Two-Way Communication</span></span>
<span data-ttu-id="0e413-103">Esta amostra demonstra como executar a comunicação transacionada em fila bidirecional sobre o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="0e413-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="0e413-104">Esta amostra `netMsmqBinding` usa a ligação.</span><span class="sxs-lookup"><span data-stu-id="0e413-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="0e413-105">Neste caso, o serviço é um aplicativo de console auto-hospedado que permite observar o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="0e413-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e413-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="0e413-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0e413-107">Esta amostra é baseada na [vinculação MSMQ transacionada](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="0e413-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="0e413-108">Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="0e413-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="0e413-109">O cliente envia mensagens para uma fila, e o serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="0e413-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="0e413-110">O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="0e413-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="0e413-111">Esta amostra demonstra comunicação em duas vias usando filas.</span><span class="sxs-lookup"><span data-stu-id="0e413-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="0e413-112">O cliente envia ordens de compra para a fila dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="0e413-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="0e413-113">O serviço recebe os pedidos, processa o pedido e, em seguida, liga de volta para o cliente com o status da ordem da fila no âmbito de uma transação.</span><span class="sxs-lookup"><span data-stu-id="0e413-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="0e413-114">Para facilitar a comunicação bidirecional, o cliente e o serviço usam filas para enfileirar pedidos de compra e status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="0e413-115">O contrato `IOrderProcessor` de serviço define operações de serviço unidirecional que se adequam ao uso de filas.</span><span class="sxs-lookup"><span data-stu-id="0e413-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="0e413-116">A operação de serviço inclui o ponto final de resposta a ser usado para enviar os status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="0e413-117">O ponto final de resposta é o URI da fila para enviar o status do pedido de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="0e413-118">O aplicativo de processamento de pedidos implementa este contrato.</span><span class="sxs-lookup"><span data-stu-id="0e413-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="0e413-119">O contrato de resposta para enviar status do pedido é especificado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="0e413-120">O cliente implementa o contrato de status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-120">The client implements the order status contract.</span></span> <span data-ttu-id="0e413-121">O serviço usa o proxy gerado deste contrato para enviar o status do pedido de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="0e413-122">A operação do serviço processa a ordem de compra submetida.</span><span class="sxs-lookup"><span data-stu-id="0e413-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="0e413-123">O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicado à operação de serviço para especificar o alistamento automático em uma transação que é usada para receber a mensagem da fila e conclusão automática das transações após a conclusão da operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="0e413-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="0e413-124">A `Orders` classe encapsula a funcionalidade de processamento de pedidos.</span><span class="sxs-lookup"><span data-stu-id="0e413-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="0e413-125">Neste caso, adiciona a ordem de compra a um dicionário.</span><span class="sxs-lookup"><span data-stu-id="0e413-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="0e413-126">A transação em que a operação de serviço `Orders` se alistou está disponível para as operações da classe.</span><span class="sxs-lookup"><span data-stu-id="0e413-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="0e413-127">A operação do serviço, além de processar a ordem de compra enviada, responde ao cliente sobre o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="0e413-128">O nome da fila MSMQ é especificado em uma seção Deconfiguração do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0e413-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="0e413-129">O ponto final do serviço é definido na seção System.ServiceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0e413-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e413-130">O nome da fila MSMQ e o endereço de ponto final usam convenções de endereçamento ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="0e413-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="0e413-131">O nome da fila MSMQ usa um ponto (.) para a máquina local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="0e413-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="0e413-132">O endereço de ponto final da Windows Communication Foundation (WCF) especifica um net.msmq: esquema, usa "localhost" para a máquina local e usa barras para a frente em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="0e413-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="0e413-133">Para ler a partir de uma fila hospedada na máquina remota, substitua o "." e "localhost" para o nome da máquina remota.</span><span class="sxs-lookup"><span data-stu-id="0e413-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="0e413-134">O serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="0e413-134">The service is self hosted.</span></span> <span data-ttu-id="0e413-135">Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="0e413-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="0e413-136">Isso pode ser feito manualmente ou através de código.</span><span class="sxs-lookup"><span data-stu-id="0e413-136">This can be done manually or through code.</span></span> <span data-ttu-id="0e413-137">Nesta amostra, o serviço verifica a existência da fila e a cria, se necessário.</span><span class="sxs-lookup"><span data-stu-id="0e413-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="0e413-138">O nome da fila é lido no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0e413-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="0e413-139">O endereço base é usado pela [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="0e413-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="0e413-140">O cliente cria uma transação.</span><span class="sxs-lookup"><span data-stu-id="0e413-140">The client creates a transaction.</span></span> <span data-ttu-id="0e413-141">A comunicação com a fila ocorre no âmbito da transação, fazendo com que ela seja tratada como uma unidade atômica onde todas as mensagens tenham sucesso ou falhem.</span><span class="sxs-lookup"><span data-stu-id="0e413-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="0e413-142">O código do `IOrderStatus` cliente implementa o contrato para receber o status do pedido do serviço.</span><span class="sxs-lookup"><span data-stu-id="0e413-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="0e413-143">Neste caso, ele imprime o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="0e413-144">A fila de status do `Main` pedido é criada no método.</span><span class="sxs-lookup"><span data-stu-id="0e413-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="0e413-145">A configuração do cliente inclui a configuração de serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado na configuração de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e413-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="0e413-146">Quando você executa a amostra, as atividades de cliente e serviço são exibidas nas janelas de serviço e console do cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0e413-147">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="0e413-148">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="0e413-149">O serviço exibe as informações da ordem de compra e indica que está enviando de volta o status do pedido para a fila de status do pedido.</span><span class="sxs-lookup"><span data-stu-id="0e413-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```console  
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
  
 <span data-ttu-id="0e413-150">O cliente exibe as informações de status do pedido enviadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="0e413-150">The client displays the order status information sent by the service.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0e413-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="0e413-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0e413-152">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e413-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0e413-153">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e413-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0e413-154">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0e413-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e413-155">Se você usar Svcutil.exe para regenerar a configuração para esta amostra, certifique-se de modificar os nomes de ponto final na configuração do cliente para corresponder ao código do cliente.</span><span class="sxs-lookup"><span data-stu-id="0e413-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="0e413-156">Por padrão <xref:System.ServiceModel.NetMsmqBinding>com o , a segurança de transporte está ativada.</span><span class="sxs-lookup"><span data-stu-id="0e413-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="0e413-157">Existem duas propriedades relevantes para a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` segurança de transporte MSMQ `Windows` e, por padrão, o modo de autenticação é definido para e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="0e413-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="0e413-158">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio e a opção de integração ativa de diretórios para O MSMQ deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="0e413-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="0e413-159">Se você executar esta amostra em um computador que não satisfaça esses critérios, você receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="0e413-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="0e413-160">Para executar a amostra em um computador junto a um grupo de trabalho ou sem integração de diretório ativo</span><span class="sxs-lookup"><span data-stu-id="0e413-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="0e413-161">Se o computador não fizer parte de um domínio ou não tiver a integração ativa do diretório `None` instalada, desligue a segurança do transporte definindo o modo de autenticação e o nível de proteção para o que for mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="0e413-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2. <span data-ttu-id="0e413-162">Desativar a segurança de uma configuração de cliente gera o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0e413-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3. <span data-ttu-id="0e413-163">O serviço para esta amostra `OrderProcessorService`cria uma vinculação no .</span><span class="sxs-lookup"><span data-stu-id="0e413-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="0e413-164">Adicione uma linha de código depois que a vinculação `None`for instanciada para definir o modo de segurança para .</span><span class="sxs-lookup"><span data-stu-id="0e413-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="0e413-165">Certifique-se de alterar a configuração no servidor e no cliente antes de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="0e413-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0e413-166">A `security mode` `None` configuração é <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> equivalente `Message` à `None`configuração ou segurança a .</span><span class="sxs-lookup"><span data-stu-id="0e413-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0e413-167">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="0e413-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0e413-168">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="0e413-168">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0e413-169">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="0e413-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0e413-170">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="0e413-170">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  

---
title: Comunicação bidirecional
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9eb37e7e307bc9748113e5580ee96c8863d3ef89
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="two-way-communication"></a><span data-ttu-id="1814e-102">Comunicação bidirecional</span><span class="sxs-lookup"><span data-stu-id="1814e-102">Two-Way Communication</span></span>
<span data-ttu-id="1814e-103">Este exemplo demonstra como executar transacionado uma comunicação bidirecional em fila em relação ao MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1814e-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="1814e-104">Este exemplo usa o `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="1814e-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="1814e-105">Nesse caso, o serviço é um aplicativo de console auto-hospedado que permite que você observe o serviço de recebimento de mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="1814e-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1814e-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1814e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1814e-107">Este exemplo se baseia o [transacionado associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="1814e-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="1814e-108">Comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="1814e-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="1814e-109">O cliente envia mensagens a uma fila e o serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="1814e-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="1814e-110">O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="1814e-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="1814e-111">Este exemplo demonstra a comunicação de 2 vias usando filas.</span><span class="sxs-lookup"><span data-stu-id="1814e-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="1814e-112">O cliente envia ordens de compra para a fila de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="1814e-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="1814e-113">O serviço recebe as ordens de, processa o pedido e, em seguida, chama novamente o cliente com o status do pedido da fila de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="1814e-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="1814e-114">Para facilitar a comunicação bidirecional o cliente e o serviço usam filas para enfileirar as ordens de compra e o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="1814e-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="1814e-115">O contrato de serviço `IOrderProcessor` define as operações de serviço unidirecional que atendem o uso de enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1814e-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="1814e-116">A operação de serviço inclui o ponto de extremidade para usar para enviar os status da ordem de resposta.</span><span class="sxs-lookup"><span data-stu-id="1814e-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="1814e-117">O ponto de extremidade de resposta é o URI da fila para enviar o status do pedido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="1814e-118">Aplicativo de processamento de pedidos implementa esse contrato.</span><span class="sxs-lookup"><span data-stu-id="1814e-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="1814e-119">O contrato de resposta para enviar o status do pedido é especificado pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="1814e-120">O cliente implementa o contrato de status de ordem.</span><span class="sxs-lookup"><span data-stu-id="1814e-120">The client implements the order status contract.</span></span> <span data-ttu-id="1814e-121">O serviço usa o proxy gerado deste contrato para enviar o status do pedido para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="1814e-122">A operação de serviço processa o pedido de compra enviado.</span><span class="sxs-lookup"><span data-stu-id="1814e-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="1814e-123">O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicada à operação de serviço para especificar a inscrição automática em uma transação que é usada para receber a mensagem da fila e o preenchimento automático de transações após a conclusão da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="1814e-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="1814e-124">O `Orders` classe encapsula a funcionalidade de ordem de processamento.</span><span class="sxs-lookup"><span data-stu-id="1814e-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="1814e-125">Nesse caso, ele adiciona o pedido de compra para um dicionário.</span><span class="sxs-lookup"><span data-stu-id="1814e-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="1814e-126">A transação que a operação de serviço inscrita em está disponível para as operações de `Orders` classe.</span><span class="sxs-lookup"><span data-stu-id="1814e-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="1814e-127">A operação de serviço, além de processamento de ordem de compra enviado, responde ao cliente o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="1814e-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="1814e-128">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1814e-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="1814e-129">O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1814e-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1814e-130">O endereço de nome e o ponto de extremidade de fila MSMQ usam convenções de endereçamento ligeiramente diferentes.</span><span class="sxs-lookup"><span data-stu-id="1814e-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="1814e-131">O nome da fila MSMQ usa um ponto (.) para os separadores de máquina e barra invertida locais em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="1814e-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="1814e-132">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endereço de ponto de extremidade Especifica um NET. MSMQ: esquema, use "localhost" para a máquina local e usa barras em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="1814e-132">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="1814e-133">Para ler de uma fila que está hospedada no computador remoto, substitua o "." e "localhost" como o nome do computador remoto.</span><span class="sxs-lookup"><span data-stu-id="1814e-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="1814e-134">O serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="1814e-134">The service is self hosted.</span></span> <span data-ttu-id="1814e-135">Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="1814e-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="1814e-136">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="1814e-136">This can be done manually or through code.</span></span> <span data-ttu-id="1814e-137">Neste exemplo, o serviço verifica a existência da fila e cria, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1814e-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="1814e-138">O nome da fila é lida do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1814e-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="1814e-139">O endereço base é usado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1814e-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="1814e-140">O cliente cria uma transação.</span><span class="sxs-lookup"><span data-stu-id="1814e-140">The client creates a transaction.</span></span> <span data-ttu-id="1814e-141">Comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica, onde todas as mensagens de êxito ou falha.</span><span class="sxs-lookup"><span data-stu-id="1814e-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="1814e-142">O código do cliente implementa a `IOrderStatus` contrato receber o status do pedido do serviço.</span><span class="sxs-lookup"><span data-stu-id="1814e-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="1814e-143">Nesse caso, exibe o status do pedido.</span><span class="sxs-lookup"><span data-stu-id="1814e-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="1814e-144">A fila de status de ordem é criada no `Main` método.</span><span class="sxs-lookup"><span data-stu-id="1814e-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="1814e-145">A configuração do cliente inclui a configuração de serviço de status de ordem para hospedar o serviço de status de ordem, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1814e-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="1814e-146">Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1814e-147">Você pode ver as mensagens de recebimento de serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="1814e-148">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="1814e-149">O serviço exibe as informações de ordem de compra e indica que ele está retornando o status do pedido para a fila de status de ordem.</span><span class="sxs-lookup"><span data-stu-id="1814e-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="1814e-150">O cliente exibe as informações de status de ordem enviadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="1814e-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1814e-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1814e-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1814e-152">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1814e-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1814e-153">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1814e-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1814e-154">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1814e-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1814e-155">Se você usar o Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar os nomes de ponto de extremidade na configuração do cliente para coincidir com o código do cliente.</span><span class="sxs-lookup"><span data-stu-id="1814e-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="1814e-156">Por padrão, com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada.</span><span class="sxs-lookup"><span data-stu-id="1814e-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="1814e-157">Há duas propriedades relevantes para a segurança de transporte MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="1814e-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="1814e-158">Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do active directory para o MSMQ deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="1814e-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="1814e-159">Se você executar esse exemplo em um computador que não atendam a esses critérios, você receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="1814e-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="1814e-160">Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do active directory</span><span class="sxs-lookup"><span data-stu-id="1814e-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="1814e-161">Se o computador não faz parte de um domínio ou não tem integração do active directory instalada, desativar a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="1814e-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="1814e-162">Desativar a segurança para uma configuração de cliente gera o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1814e-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="1814e-163">O serviço para este exemplo cria uma associação no `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="1814e-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="1814e-164">Adicionar uma linha de código após a associação é instanciada para definir o modo de segurança para `None`.</span><span class="sxs-lookup"><span data-stu-id="1814e-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="1814e-165">Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="1814e-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1814e-166">Configuração `security mode` para `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ou `Message` segurança `None`.</span><span class="sxs-lookup"><span data-stu-id="1814e-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1814e-167">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1814e-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1814e-168">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1814e-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1814e-169">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1814e-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1814e-170">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1814e-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="1814e-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1814e-171">See Also</span></span>

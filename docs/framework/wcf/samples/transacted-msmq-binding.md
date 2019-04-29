---
title: Associação transacionada do MSMQ
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 259ca8059ac1c4f62636a2320d5eb64daa7f56cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759980"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="7d88e-102">Associação transacionada do MSMQ</span><span class="sxs-lookup"><span data-stu-id="7d88e-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="7d88e-103">Este exemplo demonstra como realizar a comunicação em fila transacionada usando o serviço de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="7d88e-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="7d88e-104">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="7d88e-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="7d88e-105">Comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="7d88e-106">Mais precisamente, o cliente envia mensagens a uma fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="7d88e-107">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-107">The service receives messages from the queue.</span></span> <span data-ttu-id="7d88e-108">O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="7d88e-109">Quando as transações são usadas para enviar e receber mensagens, há, na verdade, duas transações separadas.</span><span class="sxs-lookup"><span data-stu-id="7d88e-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="7d88e-110">Quando o cliente envia mensagens dentro do escopo de uma transação, a transação é local para o cliente e o Gerenciador de fila do cliente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="7d88e-111">Quando o serviço recebe mensagens dentro do escopo da transação, a transação é local para o serviço e o Gerenciador de fila de recebimento.</span><span class="sxs-lookup"><span data-stu-id="7d88e-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="7d88e-112">É muito importante lembrar-se de que o cliente e o serviço não estão participando na mesma transação; em vez disso, eles estão usando transações diferentes ao executar suas operações (como enviar e receber) com a fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="7d88e-113">Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="7d88e-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="7d88e-114">As mensagens enviadas para a fila, em seguida, são recebidas pelo serviço de dentro do escopo de transação definido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="7d88e-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="7d88e-115">O contrato de serviço é `IOrderProcessor`, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d88e-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="7d88e-116">A interface define um serviço unidirecional que é adequado para uso com as filas.</span><span class="sxs-lookup"><span data-stu-id="7d88e-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="7d88e-117">O comportamento de serviço define um comportamento de operação com `TransactionScopeRequired` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="7d88e-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="7d88e-118">Isso garante que o mesmo escopo da transação que é usado para recuperar a mensagem da fila é usado por qualquer gerenciadores de recursos acessados pelo método.</span><span class="sxs-lookup"><span data-stu-id="7d88e-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="7d88e-119">Ela também garante que, se o método gera uma exceção, a mensagem é retornada para a fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="7d88e-120">Sem definir esse comportamento de operação, um canal em fila cria uma transação para ler a mensagem da fila e confirma a ele automaticamente antes de expedição, de modo que, se a operação falhar, a mensagem será perdida.</span><span class="sxs-lookup"><span data-stu-id="7d88e-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="7d88e-121">O cenário mais comum é para operações de serviço para se inscrever na transação que é usada para ler a mensagem da fila, conforme demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d88e-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

<span data-ttu-id="7d88e-122">O serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="7d88e-122">The service is self hosted.</span></span> <span data-ttu-id="7d88e-123">Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="7d88e-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="7d88e-124">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="7d88e-124">This can be done manually or through code.</span></span> <span data-ttu-id="7d88e-125">Neste exemplo, o serviço contém código para verificar a existência da fila e criar a fila se ela não existir.</span><span class="sxs-lookup"><span data-stu-id="7d88e-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="7d88e-126">O nome da fila é lido do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7d88e-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="7d88e-127">O endereço base é usado pelas [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7d88e-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
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

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="7d88e-128">O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7d88e-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="7d88e-129">O nome da fila usa um ponto (.) para o computador local e os separadores de barra invertida em seu caminho ao criar a fila usando <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="7d88e-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="7d88e-130">O ponto de extremidade do Windows Communication Foundation (WCF) usa o endereço da fila com o esquema de NET. MSMQ, usa "localhost" para indicar o computador local e usa barras "/" em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="7d88e-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="7d88e-131">O cliente cria um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="7d88e-131">The client creates a transaction scope.</span></span> <span data-ttu-id="7d88e-132">A comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica em que todas as mensagens são enviadas para a fila ou nenhuma das mensagens são enviadas para a fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="7d88e-133">A transação é confirmada chamando <xref:System.Transactions.TransactionScope.Complete%2A> no escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="7d88e-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="7d88e-134">Para verificar se as transações estão funcionando, modificar o cliente pelo escopo da transação de comentário, conforme mostrado no código de exemplo a seguir, recompile a solução e executar o cliente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="7d88e-135">Porque a transação não for concluída, as mensagens não são enviadas para a fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="7d88e-136">Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="7d88e-137">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="7d88e-138">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="7d88e-139">Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="7d88e-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="7d88e-140">Executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda recebe as mensagens.</span><span class="sxs-lookup"><span data-stu-id="7d88e-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d88e-141">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7d88e-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7d88e-142">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d88e-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7d88e-143">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="7d88e-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="7d88e-144">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="7d88e-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="7d88e-145">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7d88e-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="7d88e-146">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="7d88e-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="7d88e-147">Abra o Gerenciador de servidores no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7d88e-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="7d88e-148">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="7d88e-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="7d88e-149">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="7d88e-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="7d88e-150">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="7d88e-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="7d88e-151">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="7d88e-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="7d88e-152">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d88e-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="7d88e-153">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d88e-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="7d88e-154">Por padrão com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada.</span><span class="sxs-lookup"><span data-stu-id="7d88e-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="7d88e-155">Há duas propriedades relevantes para a segurança do transporte MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="7d88e-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="7d88e-156">Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="7d88e-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="7d88e-157">Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do Active Directory para o MSMQ deve estar instalada.</span><span class="sxs-lookup"><span data-stu-id="7d88e-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="7d88e-158">Se você executar esse exemplo em um computador que não atendem a esses critérios, você receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="7d88e-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="7d88e-159">Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do Active Directory</span><span class="sxs-lookup"><span data-stu-id="7d88e-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="7d88e-160">Se o computador não fizer parte de um domínio ou não tem integração do Active Directory instalada, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no código de configuração de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d88e-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="7d88e-161">Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="7d88e-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d88e-162">Definindo `security mode` à `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, e `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="7d88e-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d88e-163">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7d88e-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7d88e-164">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7d88e-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7d88e-165">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="7d88e-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d88e-166">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7d88e-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`

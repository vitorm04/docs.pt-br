---
title: Correlação de mensagem
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 0f5124b8172a7a4d553d19e08309affb48e7468c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714859"
---
# <a name="message-correlation"></a><span data-ttu-id="1cd27-102">Correlação de mensagem</span><span class="sxs-lookup"><span data-stu-id="1cd27-102">Message Correlation</span></span>
<span data-ttu-id="1cd27-103">Este exemplo demonstra como um aplicativo MSMQ (enfileiramento de mensagens) pode enviar uma mensagem MSMQ para um serviço Windows Communication Foundation (WCF) e como as mensagens podem ser correlacionadas entre os aplicativos do remetente e do destinatário em um cenário de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="1cd27-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="1cd27-104">Este exemplo usa a associação msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="1cd27-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="1cd27-105">O serviço, nesse caso, é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="1cd27-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="1cd27-106">k</span><span class="sxs-lookup"><span data-stu-id="1cd27-106">k</span></span>  
  
 <span data-ttu-id="1cd27-107">O serviço processa a mensagem recebida do remetente e envia uma mensagem de resposta de volta para o remetente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="1cd27-108">O remetente correlaciona a resposta recebida para a solicitação que ele enviou originalmente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="1cd27-109">As propriedades `MessageID` e `CorrelationID` da mensagem são usadas para correlacionar as mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="1cd27-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="1cd27-110">O contrato de serviço `IOrderProcessor` define uma operação de serviço unidirecional que é adequada para uso com o enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="1cd27-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="1cd27-111">Uma mensagem MSMQ não tem um cabeçalho Action, portanto, não é possível mapear diferentes mensagens MSMQ para contratos de operação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="1cd27-112">Portanto, pode haver apenas um contrato de operação nesse caso.</span><span class="sxs-lookup"><span data-stu-id="1cd27-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="1cd27-113">Se você quiser definir mais contratos de operação no serviço, o aplicativo deverá fornecer informações sobre qual cabeçalho na mensagem MSMQ (por exemplo, o rótulo ou CorrelationId) pode ser usado para decidir qual contrato de operação deve ser despachado.</span><span class="sxs-lookup"><span data-stu-id="1cd27-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> 
  
 <span data-ttu-id="1cd27-114">A mensagem MSMQ também não contém informações sobre quais cabeçalhos são mapeados para os diferentes parâmetros do contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="1cd27-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="1cd27-115">Portanto, pode haver apenas um parâmetro no contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="1cd27-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="1cd27-116">O parâmetro é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, que contém a mensagem do MSMQ subjacente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="1cd27-117">O tipo "T" na classe `MsmqMessage<T>` representa os dados que são serializados no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cd27-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="1cd27-118">Neste exemplo, o tipo de `PurchaseOrder` é serializado no corpo da mensagem MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cd27-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="1cd27-119">A operação de serviço processa a ordem de compra e exibe o conteúdo da ordem de compra e seu status na janela do console de serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="1cd27-120">O <xref:System.ServiceModel.OperationBehaviorAttribute> configura a operação para se inscrever em uma transação com a fila e marcar a transação como concluída quando a operação retorna.</span><span class="sxs-lookup"><span data-stu-id="1cd27-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="1cd27-121">O `PurchaseOrder` contém os detalhes do pedido que devem ser processados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="1cd27-122">O serviço usa uma `OrderResponseClient` de cliente personalizada para enviar a mensagem MSMQ para a fila.</span><span class="sxs-lookup"><span data-stu-id="1cd27-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="1cd27-123">Como o aplicativo que recebe e processa a mensagem é um aplicativo MSMQ e não um aplicativo WCF, não há nenhum contrato de serviço implícito entre os dois aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1cd27-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="1cd27-124">Portanto, não podemos criar um proxy usando a ferramenta svcutil. exe neste cenário.</span><span class="sxs-lookup"><span data-stu-id="1cd27-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="1cd27-125">O proxy personalizado é essencialmente o mesmo para todos os aplicativos WCF que usam a associação de `msmqIntegrationBinding` para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="1cd27-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="1cd27-126">Ao contrário de outros proxies, ele não inclui uma variedade de operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="1cd27-127">É apenas uma operação de envio de mensagem.</span><span class="sxs-lookup"><span data-stu-id="1cd27-127">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="1cd27-128">O serviço é hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-128">The service is self hosted.</span></span> <span data-ttu-id="1cd27-129">Ao usar o transporte de integração do MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="1cd27-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="1cd27-130">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="1cd27-130">This can be done manually or through code.</span></span> <span data-ttu-id="1cd27-131">Neste exemplo, o serviço contém <xref:System.Messaging> código para verificar a existência da fila e criá-la, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1cd27-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="1cd27-132">O nome da fila é lido no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1cd27-132">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
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

 <span data-ttu-id="1cd27-133">A fila MSMQ para a qual as solicitações de pedido são enviadas é especificada na seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1cd27-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="1cd27-134">Os pontos de extremidade de cliente e de serviço são definidos na seção System. serviceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="1cd27-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="1cd27-135">Ambos especificam a associação de `msmqIntegrationbinding`.</span><span class="sxs-lookup"><span data-stu-id="1cd27-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="1cd27-136">O aplicativo cliente usa <xref:System.Messaging> para enviar uma mensagem durável e transacional para a fila.</span><span class="sxs-lookup"><span data-stu-id="1cd27-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="1cd27-137">O corpo da mensagem contém a ordem de compra.</span><span class="sxs-lookup"><span data-stu-id="1cd27-137">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="1cd27-138">A fila MSMQ da qual as respostas de pedidos são recebidas é especificada em uma seção appSettings do arquivo de configuração, conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="1cd27-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd27-139">O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="1cd27-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="1cd27-140">O endereço do ponto de extremidade do WCF especifica um esquema MSMQ. FormatName e usa "localhost" para o computador local.</span><span class="sxs-lookup"><span data-stu-id="1cd27-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="1cd27-141">Um nome de formato formado corretamente segue MSMQ. FormatName no URI de acordo com as diretrizes do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cd27-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="1cd27-142">O aplicativo cliente salva o `messageID` da mensagem de solicitação de pedido que ele envia para o serviço e aguarda uma resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="1cd27-143">Quando uma resposta chega na fila, o cliente a correlaciona com a mensagem de pedido enviada usando a propriedade `correlationID` da mensagem, que contém a `messageID` da mensagem de pedido que o cliente enviou para o serviço originalmente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="1cd27-144">Quando você executa o exemplo, as atividades de cliente e serviço são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1cd27-145">Você pode ver o serviço receber mensagens do cliente e enviar uma resposta de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="1cd27-146">O cliente exibe a resposta recebida do serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-146">The client displays the response received from the service.</span></span> <span data-ttu-id="1cd27-147">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd27-148">Este exemplo requer a instalação do MSMQ (enfileiramento de mensagens).</span><span class="sxs-lookup"><span data-stu-id="1cd27-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="1cd27-149">Consulte as instruções de instalação do MSMQ na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="1cd27-149">See the MSMQ installation instructions in the See Also section.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="1cd27-150">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1cd27-150">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="1cd27-151">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cd27-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1cd27-152">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1cd27-153">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="1cd27-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1cd27-154">Você pode executar o serviço primeiro para criar a fila ou pode criar um por meio do Gerenciador de filas MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1cd27-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1cd27-155">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="1cd27-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="1cd27-156">Abra Gerenciador do Servidor no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1cd27-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="1cd27-157">Expanda a guia **recursos** .</span><span class="sxs-lookup"><span data-stu-id="1cd27-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="1cd27-158">Clique com o botão direito do mouse em **filas de mensagens particulares**e selecione **nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="1cd27-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="1cd27-159">Marque a caixa **transacional** .</span><span class="sxs-lookup"><span data-stu-id="1cd27-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="1cd27-160">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="1cd27-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="1cd27-161">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cd27-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="1cd27-162">Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1cd27-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="1cd27-163">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="1cd27-163">To run the sample across computers</span></span>

1. <span data-ttu-id="1cd27-164">Copie os arquivos de programa do serviço da pasta \service\bin\, na pasta específica do idioma, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="1cd27-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="1cd27-165">Copie os arquivos de programas do cliente da pasta \client\bin\, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="1cd27-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="1cd27-166">No arquivo client. exe. config, altere o orderQueueName para especificar o nome do computador de serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="1cd27-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="1cd27-167">No arquivo Service. exe. config, altere o endereço do ponto de extremidade do cliente para especificar o nome do computador cliente em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="1cd27-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="1cd27-168">No computador do serviço, inicie o Service. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="1cd27-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="1cd27-169">No computador cliente, inicie o Client. exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="1cd27-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1cd27-170">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1cd27-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1cd27-171">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1cd27-171">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1cd27-172">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="1cd27-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cd27-173">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1cd27-173">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="1cd27-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cd27-174">See also</span></span>

- [<span data-ttu-id="1cd27-175">Enfileiramento no WCF</span><span class="sxs-lookup"><span data-stu-id="1cd27-175">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [<span data-ttu-id="1cd27-176">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="1cd27-176">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)

---
title: "Correlação de mensagem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef105626d2427f0ea6dd49f696b78ffac4834f92
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="message-correlation"></a><span data-ttu-id="9e6fb-102">Correlação de mensagem</span><span class="sxs-lookup"><span data-stu-id="9e6fb-102">Message Correlation</span></span>
<span data-ttu-id="9e6fb-103">Este exemplo demonstra como um aplicativo de serviço de enfileiramento de mensagens (MSMQ) pode enviar uma mensagem MSMQ para um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço e como as mensagens podem ser correlacionadas entre remetente e destinatário aplicativos em um cenário de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="9e6fb-104">Este exemplo usa a associação de msmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="9e6fb-105">Nesse caso, o serviço é um aplicativo de console auto-hospedado para permitir que você observar o serviço que recebe as mensagens em fila.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="9e6fb-106">K</span><span class="sxs-lookup"><span data-stu-id="9e6fb-106">k</span></span>  
  
 <span data-ttu-id="9e6fb-107">O serviço processa a mensagem recebida do remetente e envia uma mensagem de resposta de volta ao remetente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="9e6fb-108">O remetente correlaciona a resposta recebido para a solicitação que ela enviada originalmente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="9e6fb-109">O `MessageID` e `CorrelationID` propriedades da mensagem são usadas para correlacionar as mensagens de solicitação e resposta.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>  
  
 <span data-ttu-id="9e6fb-110">O `IOrderProcessor` contrato de serviço define uma operação de serviço unidirecional que é adequada para uso com o enfileiramento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="9e6fb-111">Uma mensagem MSMQ não tem um cabeçalho de ação, portanto, não é possível mapear mensagens MSMQ diferentes para contratos de operação automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="9e6fb-112">Portanto, pode haver apenas um contrato de operação nesse caso.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="9e6fb-113">Se você deseja definir contratos de operação mais no serviço, o aplicativo deve fornecer informações sobre quais cabeçalho o MSMQ mensagem (por exemplo, o rótulo ou correlationID) pode ser usada para decidir qual contrato de operação para enviar.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span> <span data-ttu-id="9e6fb-114">Isso é demonstrado no [Demux personalizado](../../../../docs/framework/wcf/samples/custom-demux.md).</span><span class="sxs-lookup"><span data-stu-id="9e6fb-114">This is demonstrated in the [Custom Demux](../../../../docs/framework/wcf/samples/custom-demux.md).</span></span>  
  
 <span data-ttu-id="9e6fb-115">A mensagem do MSMQ também não contêm informações sobre qual cabeçalhos são mapeados para os parâmetros diferentes do contrato da operação.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="9e6fb-116">Portanto, pode haver somente um parâmetro no contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="9e6fb-117">O parâmetro é do tipo <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` que contém a mensagem MSMQ subjacente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-117">The parameter is of type <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` which contains the underlying MSMQ message.</span></span> <span data-ttu-id="9e6fb-118">O tipo "T" no `MsmqMessage<T>` classe representa os dados que são serializados no corpo da mensagem do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="9e6fb-119">Neste exemplo, o `PurchaseOrder` tipo é serializado no corpo da mensagem do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```  
  
 <span data-ttu-id="9e6fb-120">A operação de serviço processa a ordem de compra e exibe o conteúdo da ordem de compra e seu status na janela do console de serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="9e6fb-121">O <xref:System.ServiceModel.OperationBehaviorAttribute> configura a operação para se inscrever em uma transação com a fila e marcar a transação concluída quando a operação retorna.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="9e6fb-122">O `PurchaseOrder` contém os detalhes do pedido que devem ser processados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="9e6fb-123">O serviço usa um cliente personalizado `OrderResponseClient` para enviar a mensagem do MSMQ para a fila.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="9e6fb-124">Como o aplicativo que recebe e processa a mensagem é um aplicativo do MSMQ e não um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, não há nenhum contrato de serviço implícita entre os dois aplicativos.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-124">Because the application that receives and processes the message is an MSMQ application and not a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="9e6fb-125">Portanto, não é possível criar um proxy usando a ferramenta Svcutil.exe neste cenário.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="9e6fb-126">O proxy personalizado é essencialmente o mesmo para todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos que usam o `msmqIntegrationBinding` associação para enviar mensagens.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-126">The custom proxy is essentially the same for all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="9e6fb-127">Ao contrário de outros proxies, ele não inclui uma variedade de operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="9e6fb-128">É uma operação de enviar mensagem somente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-128">It is a submit message operation only.</span></span>  
  
```  
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
  
 <span data-ttu-id="9e6fb-129">O serviço é auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-129">The service is self hosted.</span></span> <span data-ttu-id="9e6fb-130">Ao usar o transporte de integração do MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9e6fb-131">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-131">This can be done manually or through code.</span></span> <span data-ttu-id="9e6fb-132">Neste exemplo, o serviço contém <xref:System.Messaging> código para verificar a existência da fila e crie-o se necessário.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="9e6fb-133">O nome da fila é lida do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-133">The queue name is read from the configuration file.</span></span>  
  
```  
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
  
 <span data-ttu-id="9e6fb-134">A fila MSMQ para o qual as solicitações de ordem são enviadas é especificada na seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="9e6fb-135">Os pontos de extremidade do cliente e de serviço são definidos na seção System. ServiceModel do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="9e6fb-136">Especificar o `msmqIntegrationbinding` associação.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-136">Both specify the `msmqIntegrationbinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="9e6fb-137">O aplicativo cliente usa <xref:System.Messaging> para enviar uma mensagem durável e transacional à fila.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="9e6fb-138">Corpo da mensagem contém a ordem de compra.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-138">The message's body contains the purchase order.</span></span>  
  
```  
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
  
 <span data-ttu-id="9e6fb-139">A fila MSMQ recebidas do qual as respostas de ordem for especificada em uma seção appSettings do arquivo de configuração, conforme mostrado no exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e6fb-140">O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="9e6fb-141">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endereço de ponto de extremidade Especifica um esquema FormatName e usa "localhost" para o computador local.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-141">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="9e6fb-142">Um nome de formato formado corretamente segue FormatName no URI de acordo com as diretrizes MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 <span data-ttu-id="9e6fb-143">A salva de aplicativo cliente a `messageID` da mensagem de solicitação de ordem que ele envia para o serviço e aguarda uma resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="9e6fb-144">Depois que uma resposta chega na fila de cliente correlaciona com a mensagem de ordem-enviada usando o `correlationID` propriedade da mensagem, que contém o `messageID` da ordem de uma mensagem de que o cliente enviado originalmente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>  
  
```  
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
  
 <span data-ttu-id="9e6fb-145">Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9e6fb-146">Você pode ver as mensagens de recebimento de serviço do cliente e envia uma resposta de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="9e6fb-147">O cliente exibe a resposta recebida do serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-147">The client displays the response received from the service.</span></span> <span data-ttu-id="9e6fb-148">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e6fb-149">Este exemplo requer a instalação do enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="9e6fb-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="9e6fb-150">Consulte as instruções de instalação do MSMQ na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-150">See the MSMQ installation instructions in the See Also section.</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="9e6fb-151">A configuração, compilação, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="9e6fb-151">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9e6fb-152">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e6fb-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9e6fb-153">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="9e6fb-154">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="9e6fb-155">Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="9e6fb-156">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-156">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="9e6fb-157">Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e6fb-157">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="9e6fb-158">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-158">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="9e6fb-159">Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="9e6fb-160">Verifique o **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-160">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="9e6fb-161">Digite `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="9e6fb-162">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e6fb-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="9e6fb-163">Para executar o exemplo de configuração de um único computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9e6fb-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9e6fb-164">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="9e6fb-164">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="9e6fb-165">Copie os arquivos de programa do serviço da pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="9e6fb-166">Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="9e6fb-167">No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="9e6fb-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="9e6fb-168">No arquivo Service.exe.config, altere o endereço de ponto de extremidade do cliente para especificar o nome do computador cliente, em vez de ".".</span><span class="sxs-lookup"><span data-stu-id="9e6fb-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>  
  
5.  <span data-ttu-id="9e6fb-169">No computador do serviço, inicie Service.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-169">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
6.  <span data-ttu-id="9e6fb-170">No computador cliente, inicie o Client.exe em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-170">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9e6fb-171">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9e6fb-172">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9e6fb-173">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9e6fb-174">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9e6fb-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a><span data-ttu-id="9e6fb-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e6fb-175">See Also</span></span>  
 [<span data-ttu-id="9e6fb-176">Enfileiramento no WCF</span><span class="sxs-lookup"><span data-stu-id="9e6fb-176">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="9e6fb-177">Enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="9e6fb-177">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)

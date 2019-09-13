---
title: Filas de mensagens de inatividade
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: c8fea29fc420ea6bb922c93ea08e0e23d5bb941d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928672"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="741a1-102">Filas de mensagens de inatividade</span><span class="sxs-lookup"><span data-stu-id="741a1-102">Dead Letter Queues</span></span>
<span data-ttu-id="741a1-103">Este exemplo demonstra como tratar e processar mensagens que falharam na entrega.</span><span class="sxs-lookup"><span data-stu-id="741a1-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="741a1-104">Ele se baseia no exemplo de [associação MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) .</span><span class="sxs-lookup"><span data-stu-id="741a1-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="741a1-105">Este exemplo usa a `netMsmqBinding` associação.</span><span class="sxs-lookup"><span data-stu-id="741a1-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="741a1-106">O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="741a1-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="741a1-107">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="741a1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="741a1-108">Este exemplo demonstra cada fila de mensagens mortas do aplicativo que está disponível [!INCLUDE[wv](../../../../includes/wv-md.md)]apenas no.</span><span class="sxs-lookup"><span data-stu-id="741a1-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="741a1-109">O exemplo pode ser modificado para usar as filas padrão de todo o sistema para o MSMQ 3,0 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] no [!INCLUDE[wxp](../../../../includes/wxp-md.md)]e no.</span><span class="sxs-lookup"><span data-stu-id="741a1-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>

 <span data-ttu-id="741a1-110">Na comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="741a1-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="741a1-111">Mais precisamente, o cliente envia mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="741a1-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="741a1-112">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="741a1-112">The service receives messages from the queue.</span></span> <span data-ttu-id="741a1-113">O serviço e o cliente, portanto, não precisam estar em execução ao mesmo tempo para se comunicarem usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="741a1-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="741a1-114">Como a comunicação em fila pode envolver uma determinada quantidade de dormência, talvez você queira associar um valor de vida útil na mensagem para garantir que a mensagem não seja entregue ao aplicativo se ela tiver passado o tempo.</span><span class="sxs-lookup"><span data-stu-id="741a1-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="741a1-115">Também há casos em que um aplicativo deve ser informado se uma mensagem com falha na entrega.</span><span class="sxs-lookup"><span data-stu-id="741a1-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="741a1-116">Em todos esses casos, como quando a vida útil na mensagem expirou ou a entrega da mensagem falhou, a mensagem é colocada em uma fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="741a1-117">O aplicativo de envio pode, então, ler as mensagens na fila de mensagens mortas e tomar medidas corretivas que variam de nenhuma ação para corrigir os motivos da entrega com falha e reenviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="741a1-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="741a1-118">A fila de mensagens mortas na `NetMsmqBinding` associação é expressa nas seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="741a1-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="741a1-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>a propriedade para expressar o tipo de fila de mensagens mortas exigido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="741a1-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="741a1-120">Essa enumeração tem os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="741a1-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="741a1-121">`None`: Nenhuma fila de mensagens mortas é exigida pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="741a1-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="741a1-122">`System`: A fila de mensagens mortas do sistema é usada para armazenar mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="741a1-123">A fila de mensagens mortas do sistema é compartilhada por todos os aplicativos em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="741a1-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="741a1-124">`Custom`: Uma fila de mensagens mortas personalizada especificada usando a <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> propriedade é usada para armazenar mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="741a1-125">Este recurso está disponível apenas no [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="741a1-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="741a1-126">Isso é usado quando o aplicativo deve usar sua própria fila de mensagens mortas em vez de compartilhá-lo com outros aplicativos em execução no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="741a1-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="741a1-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>Propriedade para expressar a fila específica a ser usada como uma fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="741a1-128">Isso está disponível apenas no [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="741a1-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="741a1-129">Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação e especifica um valor arbitrariamente baixo para "vida útil" para essas mensagens (cerca de 2 segundos).</span><span class="sxs-lookup"><span data-stu-id="741a1-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="741a1-130">O cliente também especifica uma fila de mensagens mortas personalizada a ser usada para enfileirar as mensagens que expiraram.</span><span class="sxs-lookup"><span data-stu-id="741a1-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="741a1-131">O aplicativo cliente pode ler as mensagens na fila de mensagens mortas e tentar enviar a mensagem novamente ou corrigir o erro que fez com que a mensagem original fosse colocada na fila de mensagens mortas e enviar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="741a1-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="741a1-132">No exemplo, o cliente exibe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="741a1-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="741a1-133">O contrato de serviço `IOrderProcessor`é, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="741a1-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="741a1-134">O código de serviço no exemplo é o da [associação MSMQ transacionada](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="741a1-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="741a1-135">A comunicação com o serviço ocorre dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="741a1-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="741a1-136">O serviço lê as mensagens da fila, executa a operação e, em seguida, exibe os resultados da operação.</span><span class="sxs-lookup"><span data-stu-id="741a1-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="741a1-137">O aplicativo também cria uma fila de mensagens mortas para mensagem de inatividade.</span><span class="sxs-lookup"><span data-stu-id="741a1-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

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
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="741a1-138">A configuração do cliente especifica uma duração curta para a mensagem alcançar o serviço.</span><span class="sxs-lookup"><span data-stu-id="741a1-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="741a1-139">Se a mensagem não puder ser transmitida dentro da duração especificada, a mensagem expirará e será movida para a fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="741a1-140">É possível que o cliente entregue a mensagem à fila de serviço dentro do tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="741a1-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="741a1-141">Para garantir que você veja o serviço de mensagens mortas em ação, execute o cliente antes de iniciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="741a1-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="741a1-142">A mensagem atinge o tempo limite e é entregue ao serviço de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="741a1-143">O aplicativo deve definir qual fila usar como sua fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="741a1-144">Se nenhuma fila for especificada, a fila de mensagens mortas transacionais em todo o sistema padrão será usada para enfileirar mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="741a1-145">Neste exemplo, o aplicativo cliente especifica sua própria fila de mensagens mortas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="741a1-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="741a1-146">O serviço de mensagens mortas lê mensagens da fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="741a1-147">O serviço de mensagem de mensagens mortas implementa `IOrderProcessor` o contrato.</span><span class="sxs-lookup"><span data-stu-id="741a1-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="741a1-148">No entanto, sua implementação não processa pedidos.</span><span class="sxs-lookup"><span data-stu-id="741a1-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="741a1-149">O serviço de mensagem de mensagens mortas é um serviço de cliente e não tem o recurso de processar pedidos.</span><span class="sxs-lookup"><span data-stu-id="741a1-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="741a1-150">A fila de mensagens mortas é uma fila de cliente e é local para o Gerenciador de filas de cliente.</span><span class="sxs-lookup"><span data-stu-id="741a1-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="741a1-151">A implementação do serviço de mensagens mortas verifica o motivo da falha na entrega de uma mensagem e faz medidas corretivas.</span><span class="sxs-lookup"><span data-stu-id="741a1-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="741a1-152">O motivo para uma falha de mensagem é capturado em duas enumerações <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> e <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="741a1-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="741a1-153">Você pode recuperar o <xref:System.ServiceModel.Channels.MsmqMessageProperty> <xref:System.ServiceModel.OperationContext> do conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="741a1-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="741a1-154">As mensagens na fila de mensagens mortas são aquelas que são endereçadas ao serviço que está processando a mensagem.</span><span class="sxs-lookup"><span data-stu-id="741a1-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="741a1-155">Portanto, quando o serviço de mensagem de inatividade lê mensagens da fila, a camada de canal Windows Communication Foundation (WCF) localiza a incompatibilidade em pontos de extremidade e não despacha a mensagem.</span><span class="sxs-lookup"><span data-stu-id="741a1-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="741a1-156">Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas é recebida pelo serviço de mensagem de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="741a1-157">Para receber uma mensagem que é endereçada a um ponto de extremidade diferente, um filtro de endereço para corresponder a qualquer `ServiceBehavior`endereço é especificado no.</span><span class="sxs-lookup"><span data-stu-id="741a1-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="741a1-158">Isso é necessário para processar com êxito as mensagens que são lidas da fila de mensagens mortas.</span><span class="sxs-lookup"><span data-stu-id="741a1-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="741a1-159">Neste exemplo, o serviço mensagem de mensagens mortas reenvia a mensagem se o motivo da falha é que a mensagem atingiu o tempo limite. Por todos os outros motivos, ele exibe a falha de entrega, conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="741a1-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="741a1-160">O exemplo a seguir mostra a configuração de uma mensagem de mensagens mortas:</span><span class="sxs-lookup"><span data-stu-id="741a1-160">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="741a1-161">Ao executar o exemplo, há três executáveis a serem executados para ver como a fila de mensagens mortas funciona para cada aplicativo; o cliente, o serviço e um serviço de mensagens mortas que lê da fila de mensagens mortas para cada aplicativo e reenvia a mensagem para o serviço.</span><span class="sxs-lookup"><span data-stu-id="741a1-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="741a1-162">Todos são aplicativos de console com saída em janelas de console.</span><span class="sxs-lookup"><span data-stu-id="741a1-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="741a1-163">Como o enfileiramento está em uso, o cliente e o serviço não precisam estar em funcionamento ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="741a1-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="741a1-164">Você pode executar o cliente, desligá-lo e, em seguida, iniciar o serviço e ele ainda receberá suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="741a1-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="741a1-165">Você deve iniciar o serviço e desligá-lo para que a fila possa ser criada.</span><span class="sxs-lookup"><span data-stu-id="741a1-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="741a1-166">Ao executar o cliente, o cliente exibe a mensagem:</span><span class="sxs-lookup"><span data-stu-id="741a1-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="741a1-167">O cliente tentou enviar a mensagem, mas com um tempo limite curto, a mensagem expirou e agora está na fila na fila de mensagens mortas para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="741a1-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="741a1-168">Em seguida, você executa o serviço de mensagens mortas, que lê a mensagem e exibe o código de erro e reenvia a mensagem de volta para o serviço.</span><span class="sxs-lookup"><span data-stu-id="741a1-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="741a1-169">O serviço é iniciado e, em seguida, lê a mensagem reenviada e a processa.</span><span class="sxs-lookup"><span data-stu-id="741a1-169">The service starts and then reads the resent message and processes it.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="741a1-170">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="741a1-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="741a1-171">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="741a1-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="741a1-172">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="741a1-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="741a1-173">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="741a1-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="741a1-174">Você pode executar o serviço primeiro para criar a fila ou pode criar um por meio do Gerenciador de filas MSMQ.</span><span class="sxs-lookup"><span data-stu-id="741a1-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="741a1-175">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="741a1-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="741a1-176">Abra Gerenciador do Servidor no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="741a1-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="741a1-177">Expanda a guia **recursos** .</span><span class="sxs-lookup"><span data-stu-id="741a1-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="741a1-178">Clique com o botão direito do mouse em **filas de mensagens particulares**e selecione **nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="741a1-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="741a1-179">Marque a caixa **transacional** .</span><span class="sxs-lookup"><span data-stu-id="741a1-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="741a1-180">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="741a1-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="741a1-181">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="741a1-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="741a1-182">Para executar o exemplo em uma configuração de computador único ou entre computadores, altere os nomes da fila adequadamente, substituindo localhost pelo nome completo do computador e siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="741a1-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="741a1-183">Para executar o exemplo em um computador ingressado em um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="741a1-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="741a1-184">Se o computador não fizer parte de um domínio, desative a segurança de transporte definindo o modo de autenticação e o `None` nível de proteção como mostrado na seguinte configuração de exemplo:</span><span class="sxs-lookup"><span data-stu-id="741a1-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="741a1-185">Verifique se o ponto de extremidade está associado à associação definindo o atributo `bindingConfiguration` do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="741a1-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="741a1-186">Certifique-se de alterar a configuração no DeadLetterService, no servidor e no cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="741a1-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="741a1-187">A `security mode` configuração `None` `MsmqAuthenticationMode`como éequivalente`Message` à configuração `None`e à segurança para. `MsmqProtectionLevel`</span><span class="sxs-lookup"><span data-stu-id="741a1-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="741a1-188">Comentários</span><span class="sxs-lookup"><span data-stu-id="741a1-188">Comments</span></span>
 <span data-ttu-id="741a1-189">Por padrão, com `netMsmqBinding` o transporte de associação, a segurança é habilitada.</span><span class="sxs-lookup"><span data-stu-id="741a1-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="741a1-190">Duas propriedades `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntas, determinam o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="741a1-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="741a1-191">Por padrão, o modo de autenticação é `Windows` definido como e o nível de proteção `Sign`é definido como.</span><span class="sxs-lookup"><span data-stu-id="741a1-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="741a1-192">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="741a1-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="741a1-193">Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "O certificado interno do enfileiramento de mensagens do usuário não existe".</span><span class="sxs-lookup"><span data-stu-id="741a1-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="741a1-194">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="741a1-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="741a1-195">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="741a1-195">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="741a1-196">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="741a1-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="741a1-197">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="741a1-197">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  

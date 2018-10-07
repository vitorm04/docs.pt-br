---
title: Tratamento de mensagens suspeitas no MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4555a6d322cbf9ca43aca0f93bc6eafe021fa569
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846210"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="2b39a-102">Tratamento de mensagens suspeitas no MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="2b39a-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="2b39a-103">Este exemplo demonstra como executar manipulação em um serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="2b39a-104">Este exemplo se baseia a [transacionada de associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="2b39a-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="2b39a-105">Este exemplo usa `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="2b39a-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="2b39a-106">O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="2b39a-107">Comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="2b39a-108">Mais precisamente, o cliente envia mensagens a uma fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="2b39a-109">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-109">The service receives messages from the queue.</span></span> <span data-ttu-id="2b39a-110">O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="2b39a-111">Uma mensagem suspeita é uma mensagem que é lida repetidamente em uma fila quando o serviço de ler a mensagem não é possível processar a mensagem e, portanto, encerra a transação sob a qual a mensagem é lida.</span><span class="sxs-lookup"><span data-stu-id="2b39a-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="2b39a-112">Nesses casos, a mensagem for repetida novamente.</span><span class="sxs-lookup"><span data-stu-id="2b39a-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="2b39a-113">Isso pode, teoricamente, vá para sempre se houver um problema com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b39a-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="2b39a-114">Observe que isso só pode ocorrer ao usar transações para ler a fila e chamar a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b39a-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="2b39a-115">Com base na versão do MSMQ, NetMsmqBinding dá suporte à detecção de limitado para detecção de total de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="2b39a-116">Depois que a mensagem foi detectada como adulterados, podem ser manipulado de diversas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2b39a-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="2b39a-117">Novamente, com base na versão do MSMQ, NetMsmqBinding dá suporte à manipulação de limitado para tratamento completo de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="2b39a-118">Este exemplo ilustra as funcionalidades de suspeitas limitadas fornecidas em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] plataforma e as funcionalidades de completo suspeitas fornecidas em [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b39a-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="2b39a-119">Em ambos os exemplos, o objetivo é mover a mensagem suspeita da fila para outra fila que pode ser atendida por um serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="2b39a-120">MSMQ v4.0 Poison exemplo de tratamento</span><span class="sxs-lookup"><span data-stu-id="2b39a-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="2b39a-121">No [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ fornece um recurso de fila de mensagens suspeitas de subpropriedades que pode ser usado para armazenar mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="2b39a-122">Este exemplo demonstra a prática recomendada de lidar com mensagens suspeitas usando [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b39a-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="2b39a-123">A detecção de mensagens suspeitas em [!INCLUDE[wv](../../../../includes/wv-md.md)] é bastante sofisticado.</span><span class="sxs-lookup"><span data-stu-id="2b39a-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="2b39a-124">Há 3 propriedades que ajudam com a detecção.</span><span class="sxs-lookup"><span data-stu-id="2b39a-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="2b39a-125">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é o número de vezes que uma determinada mensagem é lida novamente a fila e expedidas para o aplicativo para processamento.</span><span class="sxs-lookup"><span data-stu-id="2b39a-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="2b39a-126">Uma mensagem é lida novamente na fila quando ele é colocado de volta na fila porque a mensagem não pode ser enviada para o aplicativo ou o aplicativo reverterá a transação na operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b39a-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="2b39a-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> é o número de vezes que a mensagem será movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="2b39a-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="2b39a-128">Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é atingido, a mensagem será movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="2b39a-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="2b39a-129">A propriedade <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> é o tempo de espera após o qual a mensagem é movida da fila de repetição volta para a fila principal.</span><span class="sxs-lookup"><span data-stu-id="2b39a-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="2b39a-130">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido como 0.</span><span class="sxs-lookup"><span data-stu-id="2b39a-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="2b39a-131">A mensagem será tentada novamente.</span><span class="sxs-lookup"><span data-stu-id="2b39a-131">The message is tried again.</span></span> <span data-ttu-id="2b39a-132">Se todas as tentativas de ler a mensagem tiverem falhado, a mensagem é marcada como suspeita.</span><span class="sxs-lookup"><span data-stu-id="2b39a-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="2b39a-133">Depois que a mensagem é marcada como suspeita, a mensagem será abordada acordo com as configurações de <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeração.</span><span class="sxs-lookup"><span data-stu-id="2b39a-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="2b39a-134">Para reiterar os valores possíveis:</span><span class="sxs-lookup"><span data-stu-id="2b39a-134">To reiterate the possible values:</span></span>

-   <span data-ttu-id="2b39a-135">Falha (padrão): para o ouvinte e também o host de serviço de falha.</span><span class="sxs-lookup"><span data-stu-id="2b39a-135">Fault (default): To fault the listener and also the service host.</span></span>

-   <span data-ttu-id="2b39a-136">Soltar: Para remover a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b39a-136">Drop: To drop the message.</span></span>

-   <span data-ttu-id="2b39a-137">Move: Mover a mensagem para a subfila de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="2b39a-138">Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b39a-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

-   <span data-ttu-id="2b39a-139">Rejeitar: Para rejeitar a mensagem, enviando a mensagem de volta ao remetente da inatividade fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="2b39a-140">Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b39a-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="2b39a-141">O exemplo demonstra como usar o `Move` disposição para a mensagem suspeita.</span><span class="sxs-lookup"><span data-stu-id="2b39a-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="2b39a-142">`Move` faz com que a mensagem Mover para a subfila suspeita.</span><span class="sxs-lookup"><span data-stu-id="2b39a-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="2b39a-143">O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com as filas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="2b39a-144">A operação de serviço exibe uma mensagem informando que está processando o pedido.</span><span class="sxs-lookup"><span data-stu-id="2b39a-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="2b39a-145">Para demonstrar a funcionalidade de mensagens suspeitas, o `SubmitPurchaseOrder` operação de serviço lança uma exceção ao reverter a transação em uma invocação aleatória do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b39a-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="2b39a-146">Isso faz com que a mensagem a ser colocado de volta na fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="2b39a-147">Eventualmente, a mensagem é marcada como suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="2b39a-148">A configuração está definida para mover a mensagem suspeita para a subfila suspeita.</span><span class="sxs-lookup"><span data-stu-id="2b39a-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="2b39a-149">A configuração de serviço inclui as seguintes propriedades de mensagem suspeita: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, e `receiveErrorHandling` conforme mostrado no seguinte arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b39a-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="2b39a-150">Processamento de mensagens da fila de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="2b39a-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="2b39a-151">O serviço de mensagens suspeitas lê as mensagens da fila de mensagens suspeitas final e as processa.</span><span class="sxs-lookup"><span data-stu-id="2b39a-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="2b39a-152">Mensagens na fila de mensagens suspeitas são mensagens que são resolvidas para o serviço que está processando a mensagem, o que poderia ser diferente do ponto de extremidade de serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="2b39a-153">Portanto, quando o serviço de mensagens suspeitas lê as mensagens da fila, a camada de canais do WCF localiza a incompatibilidade nos pontos de extremidade e não despachar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b39a-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="2b39a-154">Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="2b39a-155">Para continuar a receber a mensagem, mesmo se a mensagem é endereçada a um ponto de extremidade diferente, devemos adicionar um `ServiceBehavior` para endereços de filtro em que o critério de correspondência é para corresponder a qualquer ponto de extremidade de serviço a mensagem é endereçada ao.</span><span class="sxs-lookup"><span data-stu-id="2b39a-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="2b39a-156">Isso é necessário para processar com êxito mensagens lidas da fila de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="2b39a-157">A implementação do serviço de mensagens suspeitas em si é muito semelhante à implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="2b39a-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="2b39a-158">Ele implementa o contrato e processa os pedidos.</span><span class="sxs-lookup"><span data-stu-id="2b39a-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="2b39a-159">O exemplo de código é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="2b39a-159">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="2b39a-160">Ao contrário da ordem de serviço que lê mensagens da fila de ordem de processamento, o serviço de mensagens suspeitas lê mensagens da fila de suspeitas de subpropriedades.</span><span class="sxs-lookup"><span data-stu-id="2b39a-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="2b39a-161">Fila de mensagens suspeitas é uma subfila da fila principal, é denominada "suspeitas" e é automaticamente gerada pelo MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2b39a-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="2b39a-162">Para acessá-lo, forneça o nome de fila principal, seguido por um ";" e o subfila nome, nesse caso-"suspeita", conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2b39a-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="2b39a-163">No exemplo de v MSMQ 3.0, o nome da fila de mensagens suspeitas não é uma subfila, em vez disso, a fila que mudamos a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b39a-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="2b39a-164">Quando você executar o exemplo, o cliente, serviços e atividades de serviço de mensagens suspeitas são exibidas nas janelas do console.</span><span class="sxs-lookup"><span data-stu-id="2b39a-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="2b39a-165">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="2b39a-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="2b39a-166">Pressione ENTER em cada janela de console para interromper os serviços.</span><span class="sxs-lookup"><span data-stu-id="2b39a-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="2b39a-167">O serviço é iniciado em execução, o processamento de pedidos e aleatoriamente começa a encerrar o processamento.</span><span class="sxs-lookup"><span data-stu-id="2b39a-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="2b39a-168">Se a mensagem indicar que ele processou a ordem, você pode executar o cliente novamente para enviar outra mensagem até que você veja que o serviço terminou, na verdade, uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b39a-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="2b39a-169">Com base nas configurações feitas suspeitas, a mensagem a tentativa de uma vez para o processamento antes de movê-lo para a fila de mensagens suspeitas final.</span><span class="sxs-lookup"><span data-stu-id="2b39a-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="2b39a-170">Inicie o serviço de mensagens suspeitas ao ler a mensagem inviabilizada da fila de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="2b39a-171">Neste exemplo, o serviço de mensagens suspeitas lê a mensagem e processa-os.</span><span class="sxs-lookup"><span data-stu-id="2b39a-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="2b39a-172">Você pode ver que a ordem de compra que foi encerrada e adulterada é lido pelo serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="2b39a-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2b39a-173">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2b39a-173">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="2b39a-174">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2b39a-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="2b39a-175">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="2b39a-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="2b39a-176">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="2b39a-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="2b39a-177">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2b39a-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="2b39a-178">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="2b39a-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="2b39a-179">Abra o Gerenciador de servidores no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2b39a-179">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="2b39a-180">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="2b39a-180">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="2b39a-181">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="2b39a-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="2b39a-182">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="2b39a-182">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="2b39a-183">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="2b39a-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="2b39a-184">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2b39a-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4.  <span data-ttu-id="2b39a-185">Para executar o exemplo em uma configuração ou entre computadores, alterar os nomes de fila para refletir o nome do host real em vez do localhost e siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2b39a-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="2b39a-186">Por padrão com o `netMsmqBinding` transporte de associação de segurança está habilitada.</span><span class="sxs-lookup"><span data-stu-id="2b39a-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="2b39a-187">Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinam o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="2b39a-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="2b39a-188">Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="2b39a-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="2b39a-189">Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="2b39a-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="2b39a-190">Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "Mensagem interna do usuário certificado do enfileiramento de mensagens não existe".</span><span class="sxs-lookup"><span data-stu-id="2b39a-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="2b39a-191">Para executar o exemplo em um computador associado a um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2b39a-191">To run the sample on a computer joined to a workgroup</span></span>

1.  <span data-ttu-id="2b39a-192">Se seu computador não fizer parte de um domínio, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação como `None` conforme mostrado no seguinte exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="2b39a-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="2b39a-193">Certifique-se de que o ponto de extremidade está associado com a associação, definindo o atributo bindingConfiguration de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2b39a-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2.  <span data-ttu-id="2b39a-194">Certifique-se de que você altera a configuração no PoisonMessageServer, server e o cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2b39a-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2b39a-195">Definindo `security mode` à `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel`, e `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="2b39a-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="2b39a-196">Ordem de Meta para troca de dados trabalhar, registramos uma URL com associação de http.</span><span class="sxs-lookup"><span data-stu-id="2b39a-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="2b39a-197">Isso requer que o serviço é executado em uma janela de comando com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="2b39a-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="2b39a-198">Caso contrário, você receberá uma exceção, como: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="2b39a-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b39a-199">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2b39a-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2b39a-200">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2b39a-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2b39a-201">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2b39a-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2b39a-202">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2b39a-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
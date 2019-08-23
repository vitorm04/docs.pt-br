---
title: Tratamento de mensagens suspeitas no MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 88ce22c9376313db26a5cbe377bdc8aaee83c118
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965566"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="c8a4d-102">Tratamento de mensagens suspeitas no MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="c8a4d-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="c8a4d-103">Este exemplo demonstra como executar a manipulação de mensagens suspeitas em um serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="c8a4d-104">Este exemplo é baseado no exemplo de [associação MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) transacionado.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="c8a4d-105">Este exemplo usa `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="c8a4d-106">O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="c8a4d-107">Na comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="c8a4d-108">Mais precisamente, o cliente envia mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="c8a4d-109">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-109">The service receives messages from the queue.</span></span> <span data-ttu-id="c8a4d-110">O serviço e o cliente, portanto, não precisam estar em execução ao mesmo tempo para se comunicarem usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="c8a4d-111">Uma mensagem suspeita é uma mensagem que é lida repetidamente de uma fila quando o serviço que lê a mensagem não pode processar a mensagem e, portanto, encerra a transação sob a qual a mensagem é lida.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="c8a4d-112">Nesses casos, a mensagem é repetida novamente.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="c8a4d-113">Teoricamente, isso pode ser usado para sempre se houver um problema com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="c8a4d-114">Observe que isso só pode ocorrer quando você usa transações para ler da fila e invocar a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="c8a4d-115">Com base na versão do MSMQ, o NetMsmqBinding dá suporte à detecção limitada para detecção completa de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="c8a4d-116">Depois que a mensagem for detectada como inviabilizada, ela poderá ser tratada de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="c8a4d-117">Novamente, com base na versão do MSMQ, o NetMsmqBinding dá suporte ao tratamento limitado para o tratamento total de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="c8a4d-118">Este exemplo ilustra as instalações suspeitas limitadas [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] fornecidas [!INCLUDE[wxp](../../../../includes/wxp-md.md)] no e na plataforma e as instalações completas [!INCLUDE[wv](../../../../includes/wv-md.md)]de suspeitas fornecidas no.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="c8a4d-119">Em ambos os exemplos, o objetivo é mover a mensagem suspeita para fora da fila para outra fila que pode ser atendida por um serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="c8a4d-120">Exemplo de tratamento inviabilizado do MSMQ v 4.0</span><span class="sxs-lookup"><span data-stu-id="c8a4d-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="c8a4d-121">No [!INCLUDE[wv](../../../../includes/wv-md.md)], o MSMQ fornece um recurso de subfilas suspeitas que pode ser usado para armazenar mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="c8a4d-122">Este exemplo demonstra a prática recomendada de lidar com mensagens suspeitas [!INCLUDE[wv](../../../../includes/wv-md.md)]usando o.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="c8a4d-123">A detecção de mensagens suspeitas no [!INCLUDE[wv](../../../../includes/wv-md.md)] é bastante sofisticada.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="c8a4d-124">Há três propriedades que ajudam na detecção.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="c8a4d-125">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é o número de vezes que uma determinada mensagem é relida da fila e despachada para o aplicativo para processamento.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="c8a4d-126">Uma mensagem é relida da fila quando é colocada de volta na fila porque a mensagem não pode ser expedida para o aplicativo ou o aplicativo reverte a transação na operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="c8a4d-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>é o número de vezes que a mensagem é movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="c8a4d-128">Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> for atingido, a mensagem será movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="c8a4d-129">A propriedade <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> é o intervalo de tempo após o qual a mensagem é movida da fila de repetição de volta para a fila principal.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="c8a4d-130">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido como 0.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="c8a4d-131">A mensagem é tentada novamente.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-131">The message is tried again.</span></span> <span data-ttu-id="c8a4d-132">Se todas as tentativas de ler a mensagem tiverem falhado, a mensagem será marcada como inviabilizada.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="c8a4d-133">Depois que a mensagem é marcada como inviabilizada, a mensagem é tratada de acordo com as configurações na <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeração.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="c8a4d-134">Para reiterar os valores possíveis:</span><span class="sxs-lookup"><span data-stu-id="c8a4d-134">To reiterate the possible values:</span></span>

- <span data-ttu-id="c8a4d-135">Falha (padrão): Para falhar o ouvinte e também o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-135">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="c8a4d-136">Suspensa Para descartar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-136">Drop: To drop the message.</span></span>

- <span data-ttu-id="c8a4d-137">Prosseguir Para mover a mensagem para a subfila de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="c8a4d-138">Esse valor está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8a4d-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

- <span data-ttu-id="c8a4d-139">Rejeitar Para rejeitar a mensagem, envie a mensagem de volta para a fila de mensagens mortas do remetente.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="c8a4d-140">Esse valor está disponível apenas em [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c8a4d-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="c8a4d-141">O exemplo demonstra o uso `Move` da disposição para a mensagem suspeita.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="c8a4d-142">`Move`faz com que a mensagem seja movida para a subfila de envenenamento.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-142">`Move` causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="c8a4d-143">O contrato de serviço `IOrderProcessor`é, que define um serviço unidirecional que é adequado para uso com filas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="c8a4d-144">A operação de serviço exibe uma mensagem informando que está processando a ordem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="c8a4d-145">Para demonstrar a funcionalidade de mensagem suspeita, `SubmitPurchaseOrder` a operação de serviço gera uma exceção para reverter a transação em uma invocação aleatória do serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="c8a4d-146">Isso faz com que a mensagem seja colocada de volta na fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="c8a4d-147">Eventualmente, a mensagem é marcada como suspeita.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="c8a4d-148">A configuração é definida para mover a mensagem suspeita para a subfila de suspeita.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

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

 <span data-ttu-id="c8a4d-149">A configuração de serviço inclui as seguintes propriedades de mensagem `receiveRetryCount`suspeita `maxRetryCycles`: `retryCycleDelay`,, `receiveErrorHandling` e conforme mostrado no arquivo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="c8a4d-150">Processando mensagens da fila de mensagens suspeitas</span><span class="sxs-lookup"><span data-stu-id="c8a4d-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="c8a4d-151">O serviço de mensagens suspeitas lê mensagens da fila final de mensagens suspeitas e as processa.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="c8a4d-152">As mensagens na fila de mensagens suspeitas são mensagens endereçadas ao serviço que está processando a mensagem, que pode ser diferente do ponto de extremidade do serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="c8a4d-153">Portanto, quando o serviço de mensagens suspeitas lê mensagens da fila, a camada de canal do WCF localiza a incompatibilidade em pontos de extremidade e não despacha a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="c8a4d-154">Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="c8a4d-155">Para continuar a receber a mensagem mesmo que a mensagem seja endereçada a um ponto de extremidade diferente, devemos `ServiceBehavior` adicionar um para filtrar endereços em que o critério de correspondência é corresponder a qualquer ponto de extremidade de serviço ao qual a mensagem é endereçada.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="c8a4d-156">Isso é necessário para processar com êxito as mensagens que você leu da fila de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="c8a4d-157">A própria implementação do serviço de mensagens suspeitas é muito semelhante à implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="c8a4d-158">Ele implementa o contrato e processa os pedidos.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="c8a4d-159">O exemplo de código é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-159">The code example is as follows.</span></span>

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

 <span data-ttu-id="c8a4d-160">Ao contrário do serviço de processamento de pedidos que lê mensagens da fila de pedidos, o serviço de mensagens suspeitas lê as mensagens da subfila de suspeita.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="c8a4d-161">A fila de suspeitas é uma subfila da fila principal, denominada "suspeita" e é gerada automaticamente pelo MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="c8a4d-162">Para acessá-lo, forneça o nome da fila principal seguido por um ";" e o nome da subfila, neste caso, "suspeita", conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c8a4d-163">No exemplo do MSMQ v 3.0, o nome da fila suspeita não é uma subfila, e sim a fila para a qual movemos a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="c8a4d-164">Quando você executa o exemplo, as atividades cliente, serviço e serviço de mensagens suspeitas são exibidas em janelas de console.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="c8a4d-165">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="c8a4d-166">Pressione ENTER em cada janela do console para desligar os serviços.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="c8a4d-167">O serviço inicia a execução, processando pedidos e, aleatoriamente, começa a encerrar o processamento.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="c8a4d-168">Se a mensagem indicar que ele processou a ordem, você poderá executar o cliente novamente para enviar outra mensagem até ver que o serviço, na verdade, terminou uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="c8a4d-169">Com base nas configurações suspeitas configuradas, a mensagem é tentada uma vez para processamento antes de movê-la para a fila de suspeitas final.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

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

 <span data-ttu-id="c8a4d-170">Inicie o serviço de mensagens suspeitas para ler a mensagem inviabilizada da fila de suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="c8a4d-171">Neste exemplo, o serviço de mensagens suspeitas lê a mensagem e a processa.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="c8a4d-172">Você pode ver que a ordem de compra terminada e inviabilizada é lida pelo serviço de mensagens suspeitas.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8a4d-173">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c8a4d-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c8a4d-174">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8a4d-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c8a4d-175">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="c8a4d-176">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="c8a4d-177">Você pode executar o serviço primeiro para criar a fila ou pode criar um por meio do Gerenciador de filas MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="c8a4d-178">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="c8a4d-179">Abra Gerenciador do Servidor no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-179">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="c8a4d-180">Expanda a guia **recursos** .</span><span class="sxs-lookup"><span data-stu-id="c8a4d-180">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="c8a4d-181">Clique com o botão direito do mouse em **filas de mensagens particulares**e selecione **nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="c8a4d-182">Marque a caixa transacional.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-182">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="c8a4d-183">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="c8a4d-184">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8a4d-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="c8a4d-185">Para executar o exemplo em uma configuração de computador único ou entre computadores, altere os nomes de fila para refletir o nome de host real em vez de localhost e siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c8a4d-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="c8a4d-186">Por padrão, com `netMsmqBinding` o transporte de associação, a segurança é habilitada.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="c8a4d-187">Duas propriedades `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntas, determinam o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="c8a4d-188">Por padrão, o modo de autenticação é definido `Windows` como e o nível de proteção é `Sign`definido como.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="c8a4d-189">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="c8a4d-190">Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "O certificado interno do enfileiramento de mensagens do usuário não existe".</span><span class="sxs-lookup"><span data-stu-id="c8a4d-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="c8a4d-191">Para executar o exemplo em um computador ingressado em um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c8a4d-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="c8a4d-192">Se o computador não fizer parte de um domínio, desative a segurança de transporte definindo o modo de autenticação e o `None` nível de proteção como mostrado na seguinte configuração de exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8a4d-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="c8a4d-193">Verifique se o ponto de extremidade está associado à associação definindo o atributo bindingConfiguration do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="c8a4d-194">Certifique-se de alterar a configuração no PoisonMessageServer, no servidor e no cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c8a4d-195">A `security mode` configuração `None` como é equivalente à `MsmqAuthenticationMode`configuração `MsmqProtectionLevel`, e `Message` à segurança `None`para.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="c8a4d-196">Para que o Meta Data Exchange funcione, registramos uma URL com associação http.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="c8a4d-197">Isso requer que o serviço seja executado em uma janela de comandos com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="c8a4d-198">Caso contrário, você obterá uma exceção, `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`como:.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8a4d-199">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c8a4d-200">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c8a4d-201">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8a4d-202">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c8a4d-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`

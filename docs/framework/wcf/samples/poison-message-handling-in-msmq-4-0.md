---
title: Tratamento de mensagens suspeitas no MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144234"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="7f40c-102">Tratamento de mensagens suspeitas no MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="7f40c-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="7f40c-103">Esta amostra demonstra como realizar o manuseio de mensagens venenosas em um serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="7f40c-104">Esta amostra é baseada na amostra [de ligação MSMQ transacionada.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)</span><span class="sxs-lookup"><span data-stu-id="7f40c-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="7f40c-105">Este exemplo usa `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="7f40c-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="7f40c-106">O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="7f40c-107">Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="7f40c-108">Mais precisamente, o cliente envia mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="7f40c-109">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-109">The service receives messages from the queue.</span></span> <span data-ttu-id="7f40c-110">O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="7f40c-111">Uma mensagem venenosa é uma mensagem que é repetidamente lida de uma fila quando o serviço que lê a mensagem não pode processar a mensagem e, portanto, encerra a transação a qual a mensagem é lida.</span><span class="sxs-lookup"><span data-stu-id="7f40c-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="7f40c-112">Nesses casos, a mensagem é repetidanovamente.</span><span class="sxs-lookup"><span data-stu-id="7f40c-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="7f40c-113">Isso pode, teoricamente, continuar para sempre se houver um problema com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f40c-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="7f40c-114">Isso só pode ocorrer quando você usa transações para ler da fila e invocar a operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="7f40c-115">Com base na versão do MSMQ, o NetMsmqBinding suporta detecção limitada à detecção completa de mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="7f40c-116">Depois que a mensagem for detectada como envenenada, então ela pode ser tratada de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="7f40c-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="7f40c-117">Mais uma vez, com base na versão do MSMQ, o NetMsmqBinding suporta o manuseio limitado para o manuseio completo de mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="7f40c-118">Esta amostra ilustra as instalações de veneno limitadas fornecidas no Windows Server 2003 e na plataforma Windows XP e as instalações completas de veneno fornecidas no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7f40c-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="7f40c-119">Em ambas as amostras, o objetivo é mover a mensagem venenosa para fora da fila para outra fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="7f40c-120">Essa fila pode então ser atendida por um serviço de mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="7f40c-121">MSMQ v4.0 Amostra de manuseio de veneno</span><span class="sxs-lookup"><span data-stu-id="7f40c-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="7f40c-122">No Windows Vista, o MSMQ fornece uma instalação de subfila venenosa que pode ser usada para armazenar mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="7f40c-123">Esta amostra demonstra a melhor prática de lidar com mensagens venenosas usando o Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7f40c-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="7f40c-124">A detecção de mensagens venenosas no Windows Vista é sofisticada.</span><span class="sxs-lookup"><span data-stu-id="7f40c-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="7f40c-125">Existem 3 propriedades que ajudam na detecção.</span><span class="sxs-lookup"><span data-stu-id="7f40c-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="7f40c-126">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> número é de vezes que uma determinada mensagem é relê da fila e enviada para o aplicativo para processamento.</span><span class="sxs-lookup"><span data-stu-id="7f40c-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="7f40c-127">Uma mensagem é releia da fila quando é colocada de volta na fila porque a mensagem não pode ser enviada para o aplicativo ou o aplicativo reverte a transação na operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="7f40c-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>é o número de vezes que a mensagem é movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="7f40c-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="7f40c-129">Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é alcançado, a mensagem é movida para a fila de repetição.</span><span class="sxs-lookup"><span data-stu-id="7f40c-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="7f40c-130">A <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> propriedade é o atraso de tempo após o qual a mensagem é movida da fila de repetição de volta para a fila principal.</span><span class="sxs-lookup"><span data-stu-id="7f40c-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="7f40c-131">O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido para 0.</span><span class="sxs-lookup"><span data-stu-id="7f40c-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="7f40c-132">A mensagem é testada novamente.</span><span class="sxs-lookup"><span data-stu-id="7f40c-132">The message is tried again.</span></span> <span data-ttu-id="7f40c-133">Se todas as tentativas de ler a mensagem falharam, então a mensagem será marcada como envenenada.</span><span class="sxs-lookup"><span data-stu-id="7f40c-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="7f40c-134">Uma vez que a mensagem é marcada como envenenada, <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> a mensagem é tratada de acordo com as configurações da enumeração.</span><span class="sxs-lookup"><span data-stu-id="7f40c-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="7f40c-135">Para reiterar os possíveis valores:</span><span class="sxs-lookup"><span data-stu-id="7f40c-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="7f40c-136">Falha (padrão): Para culpar o ouvinte e também o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="7f40c-137">Solte: Para soltar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f40c-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="7f40c-138">Mova-se: Para mover a mensagem para a subfila da mensagem venenosa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="7f40c-139">Este valor está disponível apenas no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7f40c-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="7f40c-140">Rejeitar: Para rejeitar a mensagem, envie a mensagem de volta para a fila de letras mortas do remetente.</span><span class="sxs-lookup"><span data-stu-id="7f40c-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="7f40c-141">Este valor está disponível apenas no Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="7f40c-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="7f40c-142">A amostra demonstra `Move` o uso da disposição para a mensagem venenosa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="7f40c-143">`Move`faz com que a mensagem se mova para a subfila do veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="7f40c-144">O contrato `IOrderProcessor`de serviço é , que define um serviço unidirecional que é adequado para uso com filas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="7f40c-145">A operação de serviço exibe uma mensagem informando que está processando o pedido.</span><span class="sxs-lookup"><span data-stu-id="7f40c-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="7f40c-146">Para demonstrar a funcionalidade da `SubmitPurchaseOrder` mensagem venenosa, a operação de serviço lança uma exceção para reverter a transação em uma invocação aleatória do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="7f40c-147">Isso faz com que a mensagem seja colocada de volta na fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="7f40c-148">Eventualmente, a mensagem é marcada como veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="7f40c-149">A configuração está configurada para mover a mensagem venenosa para a fila do veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

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

 <span data-ttu-id="7f40c-150">A configuração do serviço inclui `receiveRetryCount`as `maxRetryCycles` `retryCycleDelay`seguintes `receiveErrorHandling` propriedades de mensagem venenosa: , , e como mostrado no arquivo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="7f40c-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="7f40c-151">Processamento de mensagens da fila da mensagem venenosa</span><span class="sxs-lookup"><span data-stu-id="7f40c-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="7f40c-152">O serviço de mensagens venenosas lê mensagens da fila final da mensagem venenosa e as processa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="7f40c-153">Mensagens na fila da mensagem venenosa são mensagens que são dirigidas ao serviço que está processando a mensagem, o que pode ser diferente do ponto final do serviço de mensagem venenosa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="7f40c-154">Portanto, quando o serviço de mensagem venenosa lê mensagens da fila, a camada do canal WCF encontra a incompatibilidade em pontos finais e não despacha a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f40c-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="7f40c-155">Neste caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="7f40c-156">Para continuar a receber a mensagem mesmo que a mensagem seja `ServiceBehavior` endereçada a um ponto final diferente, devemos adicionar um endereço para filtrar onde o critério de correspondência é corresponder a qualquer ponto final de serviço a que a mensagem seja endereçada.</span><span class="sxs-lookup"><span data-stu-id="7f40c-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="7f40c-157">Isso é necessário para processar com sucesso as mensagens que você lê da fila da mensagem venenosa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="7f40c-158">A implementação do serviço de mensagens venenosas em si é muito semelhante à implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="7f40c-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="7f40c-159">Implementa o contrato e processa as ordens.</span><span class="sxs-lookup"><span data-stu-id="7f40c-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="7f40c-160">O exemplo de código é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="7f40c-160">The code example is as follows.</span></span>

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

 <span data-ttu-id="7f40c-161">Ao contrário do serviço de processamento de pedidos que lê mensagens da fila de pedidos, o serviço de mensagens venenosas lê mensagens da subfila do veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="7f40c-162">A fila de veneno é uma subfila da fila principal, é chamada de "veneno" e é gerada automaticamente pelo MSMQ.</span><span class="sxs-lookup"><span data-stu-id="7f40c-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="7f40c-163">Para acessá-lo, forneça o nome principal da fila seguido de ";" e o nome da subfila, neste caso -"veneno", como mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="7f40c-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="7f40c-164">Na amostra de MSMQ v3.0, o nome da fila de veneno não é uma subfila, mas a fila para a que movemos a mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f40c-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="7f40c-165">Quando você executa a amostra, as atividades de serviço de mensagem de cliente, serviço e veneno são exibidas nas janelas do console.</span><span class="sxs-lookup"><span data-stu-id="7f40c-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="7f40c-166">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="7f40c-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="7f40c-167">Pressione ENTER em cada janela do console para desligar os serviços.</span><span class="sxs-lookup"><span data-stu-id="7f40c-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="7f40c-168">O serviço começa a ser executado, processando pedidos e aleatoriamente começa a encerrar o processamento.</span><span class="sxs-lookup"><span data-stu-id="7f40c-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="7f40c-169">Se a mensagem indicar que processou o pedido, você pode executar o cliente novamente para enviar outra mensagem até que você veja que o serviço realmente encerrou uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="7f40c-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="7f40c-170">Com base nas configurações de veneno configuradas, a mensagem é tentada uma vez para processamento antes de movê-la para a fila final de veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
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

 <span data-ttu-id="7f40c-171">Inicie o serviço de mensagens venenosas para ler a mensagem envenenada da fila do veneno.</span><span class="sxs-lookup"><span data-stu-id="7f40c-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="7f40c-172">Neste exemplo, o serviço de mensagens venenosas lê a mensagem e a processa.</span><span class="sxs-lookup"><span data-stu-id="7f40c-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="7f40c-173">Você pode ver que a ordem de compra que foi terminada e envenenada é lida pelo serviço de mensagens venenosas.</span><span class="sxs-lookup"><span data-stu-id="7f40c-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f40c-174">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="7f40c-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7f40c-175">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f40c-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7f40c-176">Se o serviço for executado primeiro, ele verificará se a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="7f40c-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="7f40c-177">Se a fila não estiver presente, o serviço criará uma.</span><span class="sxs-lookup"><span data-stu-id="7f40c-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="7f40c-178">Você pode executar o serviço primeiro para criar a fila, ou você pode criar um através do MSMQ Queue Manager.</span><span class="sxs-lookup"><span data-stu-id="7f40c-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="7f40c-179">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="7f40c-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="7f40c-180">Gerente de servidor aberto no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7f40c-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="7f40c-181">Expanda a guia **Recursos.**</span><span class="sxs-lookup"><span data-stu-id="7f40c-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="7f40c-182">Clique com o botão direito do mouse em Filas de **mensagens privadas**e selecione **Nova** **fila privada**.</span><span class="sxs-lookup"><span data-stu-id="7f40c-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="7f40c-183">Verifique a **caixa transacional.**</span><span class="sxs-lookup"><span data-stu-id="7f40c-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="7f40c-184">Digite `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="7f40c-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="7f40c-185">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f40c-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="7f40c-186">Para executar a amostra em uma configuração de computador único ou cruzado, altere os nomes da fila para refletir o nome real do host em vez do host local e siga as instruções em [Executando as Amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .</span><span class="sxs-lookup"><span data-stu-id="7f40c-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="7f40c-187">Por padrão, `netMsmqBinding` com o transporte vinculativo, a segurança é ativada.</span><span class="sxs-lookup"><span data-stu-id="7f40c-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="7f40c-188">Duas `MsmqAuthenticationMode` propriedades, `MsmqProtectionLevel`e, juntas, determinam o tipo de segurança de transporte.</span><span class="sxs-lookup"><span data-stu-id="7f40c-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="7f40c-189">Por padrão, o modo de `Windows` autenticação é definido `Sign`e o nível de proteção é definido como .</span><span class="sxs-lookup"><span data-stu-id="7f40c-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="7f40c-190">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio.</span><span class="sxs-lookup"><span data-stu-id="7f40c-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="7f40c-191">Se você executar esta amostra em um computador que não faz parte de um domínio, você receberá o seguinte erro: "O certificado de fila de mensagens internas do usuário não existe".</span><span class="sxs-lookup"><span data-stu-id="7f40c-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="7f40c-192">Para executar a amostra em um computador junto a um grupo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7f40c-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="7f40c-193">Se o computador não fizer parte de um domínio, desligue a segurança `None` do transporte definindo o modo de autenticação e o nível de proteção para, conforme mostrado na seguinte configuração de amostra:</span><span class="sxs-lookup"><span data-stu-id="7f40c-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="7f40c-194">Certifique-se de que o ponto final está associado à vinculação definindo o atributo de configuração do ponto final.</span><span class="sxs-lookup"><span data-stu-id="7f40c-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="7f40c-195">Certifique-se de alterar a configuração no PoisonMessageServer, servidor e cliente antes de executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="7f40c-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7f40c-196">A `security mode` `None` configuração é `MsmqAuthenticationMode` `MsmqProtectionLevel`equivalente `Message` à `None`configuração e segurança a .</span><span class="sxs-lookup"><span data-stu-id="7f40c-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="7f40c-197">Para que o Meta Data Exchange funcione, registramos uma URL com http binding.</span><span class="sxs-lookup"><span data-stu-id="7f40c-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="7f40c-198">Isso requer que o serviço seja executado em uma janela de comando elevada.</span><span class="sxs-lookup"><span data-stu-id="7f40c-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="7f40c-199">Caso contrário, você terá uma `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`exceção como: .</span><span class="sxs-lookup"><span data-stu-id="7f40c-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7f40c-200">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="7f40c-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7f40c-201">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7f40c-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7f40c-202">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="7f40c-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f40c-203">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="7f40c-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`

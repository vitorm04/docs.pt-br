---
title: Comunicação em fila volátil
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 8ed10262d319664d404e6beb630593cb93748a7d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715276"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="6e6b8-102">Comunicação em fila volátil</span><span class="sxs-lookup"><span data-stu-id="6e6b8-102">Volatile Queued Communication</span></span>

<span data-ttu-id="6e6b8-103">Este exemplo demonstra como executar comunicação volátil em fila no transporte do MSMQ (enfileiramento de mensagens).</span><span class="sxs-lookup"><span data-stu-id="6e6b8-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="6e6b8-104">Este exemplo usa <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="6e6b8-105">O serviço, nesse caso, é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="6e6b8-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6e6b8-107">Na comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="6e6b8-108">Mais precisamente, o cliente envia mensagens para uma fila.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="6e6b8-109">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-109">The service receives messages from the queue.</span></span> <span data-ttu-id="6e6b8-110">O serviço e o cliente, portanto, não precisam estar em execução ao mesmo tempo para se comunicarem usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="6e6b8-111">Quando você envia uma mensagem sem garantias, o MSMQ só faz um melhor esforço para entregar a mensagem, diferentemente das garantias em que o MSMQ garante que a mensagem seja entregue ou, se não puder ser entregue, permite que você saiba que a mensagem não pode ser entregue.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="6e6b8-112">Em determinados cenários, talvez você queira enviar uma mensagem volátil sem garantias em uma fila, quando a entrega oportuna for mais importante do que a perda de mensagens.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="6e6b8-113">As mensagens voláteis não sobrevivem a falhas do Gerenciador de filas.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="6e6b8-114">Portanto, se o Gerenciador de filas falhar, a fila não transacional usada para armazenar mensagens voláteis sobreviverá, mas as mensagens não serão armazenadas no disco.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="6e6b8-115">Não é possível enviar mensagens voláteis sem garantias dentro do escopo de uma transação usando o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="6e6b8-116">Você também deve criar uma fila não transacional para enviar mensagens voláteis.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="6e6b8-117">O contrato de serviço neste exemplo é `IStockTicker` que define serviços unidirecionais que são mais adequados para uso com o enfileiramento.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="6e6b8-118">A operação de serviço exibe o preço e o símbolo da cotação de ações, conforme mostrado no código de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6e6b8-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="6e6b8-119">O serviço é hospedado internamente.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-119">The service is self hosted.</span></span> <span data-ttu-id="6e6b8-120">Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="6e6b8-121">Isso pode ser feito manualmente ou por meio de código.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-121">This can be done manually or through code.</span></span> <span data-ttu-id="6e6b8-122">Neste exemplo, o serviço contém o código para verificar a existência da fila e criá-la, se necessário.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="6e6b8-123">O nome da fila é lido no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="6e6b8-124">O endereço base é usado pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="6e6b8-125">O nome da fila MSMQ é especificado na seção appSettings do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="6e6b8-126">O ponto de extremidade para o serviço é definido na seção System. serviceModel do arquivo de configuração e especifica a associação de `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="6e6b8-127">O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho ao criar uma fila usando <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="6e6b8-128">O endereço do ponto de extremidade do Windows Communication Foundation (WCF) especifica um net. MSMQ: esquema, usa "localhost" para o computador local e barras invertidas em seu caminho.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="6e6b8-129">As garantias e durabilidade ou volatilidade de mensagens também são especificadas na configuração.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="6e6b8-130">Como o exemplo envia mensagens em fila usando uma fila não transacional, as mensagens transacionais não podem ser enviadas para a fila.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="6e6b8-131">Quando você executa o exemplo, as atividades de cliente e serviço são exibidas nas janelas do console do cliente e do serviço.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="6e6b8-132">Você pode ver o serviço receber mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="6e6b8-133">Pressione ENTER em cada janela do console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="6e6b8-134">Observe que, como o enfileiramento está em uso, o cliente e o serviço não precisam estar em funcionamento ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="6e6b8-135">Você pode executar o cliente, desligá-lo e, em seguida, iniciar o serviço e ele ainda receberá suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6e6b8-136">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="6e6b8-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6e6b8-137">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b8-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6e6b8-138">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b8-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="6e6b8-139">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b8-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="6e6b8-140">Por padrão, com a <xref:System.ServiceModel.NetMsmqBinding>, a segurança de transporte está habilitada.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="6e6b8-141">Há duas propriedades pertinentes para a segurança de transporte do MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="6e6b8-142">Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio e a opção de integração do Active Directory para o MSMQ deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="6e6b8-143">Se você executar esse exemplo em um computador que não atenda a esses critérios, receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="6e6b8-144">Para executar o exemplo em um computador ingressado em um grupo de trabalho ou sem integração com o Active Directory</span><span class="sxs-lookup"><span data-stu-id="6e6b8-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="6e6b8-145">Se o seu computador não fizer parte de um domínio ou não tiver a integração do Active Directory instalada, desative a segurança de transporte definindo o modo de autenticação e o nível de proteção como `None`, conforme mostrado no código de configuração de exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6e6b8-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="6e6b8-146">Certifique-se de alterar a configuração no servidor e no cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6e6b8-147">Definir `security mode` como `None` é equivalente a definir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>e segurança de `Message` para `None`.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e6b8-148">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6e6b8-149">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6e6b8-150">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e6b8-151">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="6e6b8-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`

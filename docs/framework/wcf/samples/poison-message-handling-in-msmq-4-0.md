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
# <a name="poison-message-handling-in-msmq-40"></a>Tratamento de mensagens suspeitas no MSMQ 4.0
Esta amostra demonstra como realizar o manuseio de mensagens venenosas em um serviço. Esta amostra é baseada na amostra [de ligação MSMQ transacionada.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) Este exemplo usa `netMsmqBinding`. O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.

 Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens para uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.

 Uma mensagem venenosa é uma mensagem que é repetidamente lida de uma fila quando o serviço que lê a mensagem não pode processar a mensagem e, portanto, encerra a transação a qual a mensagem é lida. Nesses casos, a mensagem é repetidanovamente. Isso pode, teoricamente, continuar para sempre se houver um problema com a mensagem. Isso só pode ocorrer quando você usa transações para ler da fila e invocar a operação do serviço.

 Com base na versão do MSMQ, o NetMsmqBinding suporta detecção limitada à detecção completa de mensagens venenosas. Depois que a mensagem for detectada como envenenada, então ela pode ser tratada de várias maneiras. Mais uma vez, com base na versão do MSMQ, o NetMsmqBinding suporta o manuseio limitado para o manuseio completo de mensagens venenosas.

 Esta amostra ilustra as instalações de veneno limitadas fornecidas no Windows Server 2003 e na plataforma Windows XP e as instalações completas de veneno fornecidas no Windows Vista. Em ambas as amostras, o objetivo é mover a mensagem venenosa para fora da fila para outra fila. Essa fila pode então ser atendida por um serviço de mensagens venenosas.

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Amostra de manuseio de veneno
 No Windows Vista, o MSMQ fornece uma instalação de subfila venenosa que pode ser usada para armazenar mensagens venenosas. Esta amostra demonstra a melhor prática de lidar com mensagens venenosas usando o Windows Vista.

 A detecção de mensagens venenosas no Windows Vista é sofisticada. Existem 3 propriedades que ajudam na detecção. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> número é de vezes que uma determinada mensagem é relê da fila e enviada para o aplicativo para processamento. Uma mensagem é releia da fila quando é colocada de volta na fila porque a mensagem não pode ser enviada para o aplicativo ou o aplicativo reverte a transação na operação do serviço. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>é o número de vezes que a mensagem é movida para a fila de repetição. Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é alcançado, a mensagem é movida para a fila de repetição. A <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> propriedade é o atraso de tempo após o qual a mensagem é movida da fila de repetição de volta para a fila principal. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido para 0. A mensagem é testada novamente. Se todas as tentativas de ler a mensagem falharam, então a mensagem será marcada como envenenada.

 Uma vez que a mensagem é marcada como envenenada, <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> a mensagem é tratada de acordo com as configurações da enumeração. Para reiterar os possíveis valores:

- Falha (padrão): Para culpar o ouvinte e também o host de serviço.

- Solte: Para soltar a mensagem.

- Mova-se: Para mover a mensagem para a subfila da mensagem venenosa. Este valor está disponível apenas no Windows Vista.

- Rejeitar: Para rejeitar a mensagem, envie a mensagem de volta para a fila de letras mortas do remetente. Este valor está disponível apenas no Windows Vista.

 A amostra demonstra `Move` o uso da disposição para a mensagem venenosa. `Move`faz com que a mensagem se mova para a subfila do veneno.

 O contrato `IOrderProcessor`de serviço é , que define um serviço unidirecional que é adequado para uso com filas.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 A operação de serviço exibe uma mensagem informando que está processando o pedido. Para demonstrar a funcionalidade da `SubmitPurchaseOrder` mensagem venenosa, a operação de serviço lança uma exceção para reverter a transação em uma invocação aleatória do serviço. Isso faz com que a mensagem seja colocada de volta na fila. Eventualmente, a mensagem é marcada como veneno. A configuração está configurada para mover a mensagem venenosa para a fila do veneno.

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

 A configuração do serviço inclui `receiveRetryCount`as `maxRetryCycles` `retryCycleDelay`seguintes `receiveErrorHandling` propriedades de mensagem venenosa: , , e como mostrado no arquivo de configuração a seguir.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Processamento de mensagens da fila da mensagem venenosa
 O serviço de mensagens venenosas lê mensagens da fila final da mensagem venenosa e as processa.

 Mensagens na fila da mensagem venenosa são mensagens que são dirigidas ao serviço que está processando a mensagem, o que pode ser diferente do ponto final do serviço de mensagem venenosa. Portanto, quando o serviço de mensagem venenosa lê mensagens da fila, a camada do canal WCF encontra a incompatibilidade em pontos finais e não despacha a mensagem. Neste caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens venenosas. Para continuar a receber a mensagem mesmo que a mensagem seja `ServiceBehavior` endereçada a um ponto final diferente, devemos adicionar um endereço para filtrar onde o critério de correspondência é corresponder a qualquer ponto final de serviço a que a mensagem seja endereçada. Isso é necessário para processar com sucesso as mensagens que você lê da fila da mensagem venenosa.

 A implementação do serviço de mensagens venenosas em si é muito semelhante à implementação do serviço. Implementa o contrato e processa as ordens. O exemplo de código é o seguinte.

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

 Ao contrário do serviço de processamento de pedidos que lê mensagens da fila de pedidos, o serviço de mensagens venenosas lê mensagens da subfila do veneno. A fila de veneno é uma subfila da fila principal, é chamada de "veneno" e é gerada automaticamente pelo MSMQ. Para acessá-lo, forneça o nome principal da fila seguido de ";" e o nome da subfila, neste caso -"veneno", como mostrado na configuração da amostra a seguir.

> [!NOTE]
> Na amostra de MSMQ v3.0, o nome da fila de veneno não é uma subfila, mas a fila para a que movemos a mensagem.

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

 Quando você executa a amostra, as atividades de serviço de mensagem de cliente, serviço e veneno são exibidas nas janelas do console. Você pode ver o serviço receber mensagens do cliente. Pressione ENTER em cada janela do console para desligar os serviços.

 O serviço começa a ser executado, processando pedidos e aleatoriamente começa a encerrar o processamento. Se a mensagem indicar que processou o pedido, você pode executar o cliente novamente para enviar outra mensagem até que você veja que o serviço realmente encerrou uma mensagem. Com base nas configurações de veneno configuradas, a mensagem é tentada uma vez para processamento antes de movê-la para a fila final de veneno.

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

 Inicie o serviço de mensagens venenosas para ler a mensagem envenenada da fila do veneno. Neste exemplo, o serviço de mensagens venenosas lê a mensagem e a processa. Você pode ver que a ordem de compra que foi terminada e envenenada é lida pelo serviço de mensagens venenosas.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Se o serviço for executado primeiro, ele verificará se a fila está presente. Se a fila não estiver presente, o serviço criará uma. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um através do MSMQ Queue Manager. Siga estas etapas para criar uma fila no Windows 2008.

    1. Gerente de servidor aberto no Visual Studio 2012.

    2. Expanda a guia **Recursos.**

    3. Clique com o botão direito do mouse em Filas de **mensagens privadas**e selecione **Nova** **fila privada**.

    4. Verifique a **caixa transacional.**

    5. Digite `ServiceModelSamplesTransacted` como o nome da nova fila.

3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Para executar a amostra em uma configuração de computador único ou cruzado, altere os nomes da fila para refletir o nome real do host em vez do host local e siga as instruções em [Executando as Amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .

 Por padrão, `netMsmqBinding` com o transporte vinculativo, a segurança é ativada. Duas `MsmqAuthenticationMode` propriedades, `MsmqProtectionLevel`e, juntas, determinam o tipo de segurança de transporte. Por padrão, o modo de `Windows` autenticação é definido `Sign`e o nível de proteção é definido como . Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio. Se você executar esta amostra em um computador que não faz parte de um domínio, você receberá o seguinte erro: "O certificado de fila de mensagens internas do usuário não existe".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar a amostra em um computador junto a um grupo de trabalho

1. Se o computador não fizer parte de um domínio, desligue a segurança `None` do transporte definindo o modo de autenticação e o nível de proteção para, conforme mostrado na seguinte configuração de amostra:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Certifique-se de que o ponto final está associado à vinculação definindo o atributo de configuração do ponto final.

2. Certifique-se de alterar a configuração no PoisonMessageServer, servidor e cliente antes de executar a amostra.

    > [!NOTE]
    > A `security mode` `None` configuração é `MsmqAuthenticationMode` `MsmqProtectionLevel`equivalente `Message` à `None`configuração e segurança a .  
  
3. Para que o Meta Data Exchange funcione, registramos uma URL com http binding. Isso requer que o serviço seja executado em uma janela de comando elevada. Caso contrário, você terá uma `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`exceção como: .  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`

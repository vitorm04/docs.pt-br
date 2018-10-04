---
title: Tratamento de mensagens suspeitas no MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4555a6d322cbf9ca43aca0f93bc6eafe021fa569
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266514"
---
# <a name="poison-message-handling-in-msmq-40"></a>Tratamento de mensagens suspeitas no MSMQ 4.0
Este exemplo demonstra como executar manipulação em um serviço de mensagens suspeitas. Este exemplo se baseia a [transacionada de associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo. Este exemplo usa `netMsmqBinding`. O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.

 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.

 Uma mensagem suspeita é uma mensagem que é lida repetidamente em uma fila quando o serviço de ler a mensagem não é possível processar a mensagem e, portanto, encerra a transação sob a qual a mensagem é lida. Nesses casos, a mensagem for repetida novamente. Isso pode, teoricamente, vá para sempre se houver um problema com a mensagem. Observe que isso só pode ocorrer ao usar transações para ler a fila e chamar a operação de serviço.

 Com base na versão do MSMQ, NetMsmqBinding dá suporte à detecção de limitado para detecção de total de mensagens suspeitas. Depois que a mensagem foi detectada como adulterados, podem ser manipulado de diversas maneiras. Novamente, com base na versão do MSMQ, NetMsmqBinding dá suporte à manipulação de limitado para tratamento completo de mensagens suspeitas.

 Este exemplo ilustra as funcionalidades de suspeitas limitadas fornecidas em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] plataforma e as funcionalidades de completo suspeitas fornecidas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Em ambos os exemplos, o objetivo é mover a mensagem suspeita da fila para outra fila que pode ser atendida por um serviço de mensagens suspeitas.

## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v4.0 Poison exemplo de tratamento
 No [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ fornece um recurso de fila de mensagens suspeitas de subpropriedades que pode ser usado para armazenar mensagens suspeitas. Este exemplo demonstra a prática recomendada de lidar com mensagens suspeitas usando [!INCLUDE[wv](../../../../includes/wv-md.md)].

 A detecção de mensagens suspeitas em [!INCLUDE[wv](../../../../includes/wv-md.md)] é bastante sofisticado. Há 3 propriedades que ajudam com a detecção. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é o número de vezes que uma determinada mensagem é lida novamente a fila e expedidas para o aplicativo para processamento. Uma mensagem é lida novamente na fila quando ele é colocado de volta na fila porque a mensagem não pode ser enviada para o aplicativo ou o aplicativo reverterá a transação na operação de serviço. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> é o número de vezes que a mensagem será movida para a fila de repetição. Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é atingido, a mensagem será movida para a fila de repetição. A propriedade <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> é o tempo de espera após o qual a mensagem é movida da fila de repetição volta para a fila principal. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido como 0. A mensagem será tentada novamente. Se todas as tentativas de ler a mensagem tiverem falhado, a mensagem é marcada como suspeita.

 Depois que a mensagem é marcada como suspeita, a mensagem será abordada acordo com as configurações de <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeração. Para reiterar os valores possíveis:

-   Falha (padrão): para o ouvinte e também o host de serviço de falha.

-   Soltar: Para remover a mensagem.

-   Move: Mover a mensagem para a subfila de mensagens suspeitas. Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].

-   Rejeitar: Para rejeitar a mensagem, enviando a mensagem de volta ao remetente da inatividade fila. Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].

 O exemplo demonstra como usar o `Move` disposição para a mensagem suspeita. `Move` faz com que a mensagem Mover para a subfila suspeita.

 O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com as filas.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 A operação de serviço exibe uma mensagem informando que está processando o pedido. Para demonstrar a funcionalidade de mensagens suspeitas, o `SubmitPurchaseOrder` operação de serviço lança uma exceção ao reverter a transação em uma invocação aleatória do serviço. Isso faz com que a mensagem a ser colocado de volta na fila. Eventualmente, a mensagem é marcada como suspeitas. A configuração está definida para mover a mensagem suspeita para a subfila suspeita.

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

 A configuração de serviço inclui as seguintes propriedades de mensagem suspeita: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, e `receiveErrorHandling` conforme mostrado no seguinte arquivo de configuração.

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

## <a name="processing-messages-from-the-poison-message-queue"></a>Processamento de mensagens da fila de mensagens suspeitas
 O serviço de mensagens suspeitas lê as mensagens da fila de mensagens suspeitas final e as processa.

 Mensagens na fila de mensagens suspeitas são mensagens que são resolvidas para o serviço que está processando a mensagem, o que poderia ser diferente do ponto de extremidade de serviço de mensagens suspeitas. Portanto, quando o serviço de mensagens suspeitas lê as mensagens da fila, a camada de canais do WCF localiza a incompatibilidade nos pontos de extremidade e não despachar a mensagem. Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens suspeitas. Para continuar a receber a mensagem, mesmo se a mensagem é endereçada a um ponto de extremidade diferente, devemos adicionar um `ServiceBehavior` para endereços de filtro em que o critério de correspondência é para corresponder a qualquer ponto de extremidade de serviço a mensagem é endereçada ao. Isso é necessário para processar com êxito mensagens lidas da fila de mensagens suspeitas.

 A implementação do serviço de mensagens suspeitas em si é muito semelhante à implementação do serviço. Ele implementa o contrato e processa os pedidos. O exemplo de código é da seguinte maneira.

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

 Ao contrário da ordem de serviço que lê mensagens da fila de ordem de processamento, o serviço de mensagens suspeitas lê mensagens da fila de suspeitas de subpropriedades. Fila de mensagens suspeitas é uma subfila da fila principal, é denominada "suspeitas" e é automaticamente gerada pelo MSMQ. Para acessá-lo, forneça o nome de fila principal, seguido por um ";" e o subfila nome, nesse caso-"suspeita", conforme mostrado no seguinte exemplo de configuração.

> [!NOTE]
>  No exemplo de v MSMQ 3.0, o nome da fila de mensagens suspeitas não é uma subfila, em vez disso, a fila que mudamos a mensagem.

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

 Quando você executar o exemplo, o cliente, serviços e atividades de serviço de mensagens suspeitas são exibidas nas janelas do console. Você pode ver as mensagens de recebimento do serviço do cliente. Pressione ENTER em cada janela de console para interromper os serviços.

 O serviço é iniciado em execução, o processamento de pedidos e aleatoriamente começa a encerrar o processamento. Se a mensagem indicar que ele processou a ordem, você pode executar o cliente novamente para enviar outra mensagem até que você veja que o serviço terminou, na verdade, uma mensagem. Com base nas configurações feitas suspeitas, a mensagem a tentativa de uma vez para o processamento antes de movê-lo para a fila de mensagens suspeitas final.

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

 Inicie o serviço de mensagens suspeitas ao ler a mensagem inviabilizada da fila de mensagens suspeitas. Neste exemplo, o serviço de mensagens suspeitas lê a mensagem e processa-os. Você pode ver que a ordem de compra que foi encerrada e adulterada é lido pelo serviço de mensagens suspeitas.

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

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ. Siga estas etapas para criar uma fila no Windows 2008.

    1.  Abra o Gerenciador de servidores no Visual Studio 2012.

    2.  Expanda o **recursos** guia.

    3.  Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.

    4.  Verifique as **transacional** caixa.

    5.  Insira `ServiceModelSamplesTransacted` como o nome da nova fila.

3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Para executar o exemplo em uma configuração ou entre computadores, alterar os nomes de fila para refletir o nome do host real em vez do localhost e siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

 Por padrão com o `netMsmqBinding` transporte de associação de segurança está habilitada. Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinam o tipo de segurança de transporte. Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio. Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "Mensagem interna do usuário certificado do enfileiramento de mensagens não existe".

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar o exemplo em um computador associado a um grupo de trabalho

1.  Se seu computador não fizer parte de um domínio, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação como `None` conforme mostrado no seguinte exemplo de configuração:

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     Certifique-se de que o ponto de extremidade está associado com a associação, definindo o atributo bindingConfiguration de um ponto de extremidade.

2.  Certifique-se de que você altera a configuração no PoisonMessageServer, server e o cliente antes de executar o exemplo.

    > [!NOTE]
    >  Definindo `security mode` à `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel`, e `Message` security `None`.  
  
3.  Ordem de Meta para troca de dados trabalhar, registramos uma URL com associação de http. Isso requer que o serviço é executado em uma janela de comando com privilégios elevados. Caso contrário, você receberá uma exceção, como: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
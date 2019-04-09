---
title: Filas de mensagens de inatividade
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 2a6ed86b04cd110dcf71efb1a6b0560fc5d45467
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177925"
---
# <a name="dead-letter-queues"></a>Filas de mensagens de inatividade
Este exemplo demonstra como manipular e processar as mensagens com falha na entrega. Ele se baseia a [associação de MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo. Este exemplo usa o `netMsmqBinding` associação. O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.

> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

> [!NOTE]
>  Este exemplo demonstra cada fila de mensagens mortas do aplicativo só está disponível em [!INCLUDE[wv](../../../../includes/wv-md.md)]. O exemplo pode ser modificado para usar as filas de todo o sistema padrão para o MSMQ 3.0 em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)].

 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.

 Como a comunicação em fila pode envolver um determinado período de dormência, você talvez queira associar um valor time-to-live na mensagem para garantir que a mensagem não for entregue ao aplicativo se ele tiver ficado após a hora. Também há casos, em que um aplicativo deve ser informado se uma mensagem de falha na entrega. Em todos esses casos, como quando o tempo de vida da mensagem expirou ou a mensagem de falha na entrega, a mensagem é colocada em uma fila de mensagens mortas. O aplicativo de envio, em seguida, pode ler as mensagens na fila de inatividade e tomar ações corretivas que variam de nenhuma ação para corrigir os motivos da falha na entrega e reenviar a mensagem.

 Fila de inatividade no `NetMsmqBinding` associação é expresso nas seguintes propriedades:

-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> propriedade para expressar o tipo de fila de inatividade exigido pelo cliente. Esta enumeração tem os seguintes valores:

-   `None`: Nenhuma fila de inatividade é exigida pelo cliente.

-   `System`: A fila de inatividade do sistema é usada para armazenar mensagens de inatividade. A fila de inatividade do sistema é compartilhada por todos os aplicativos em execução no computador.

-   `Custom`: Uma fila de inatividade personalizada especificada usando o <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> propriedade é usada para armazenar mensagens de inatividade. Esse recurso só está disponível em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Isso é usado quando o aplicativo deve usar sua própria fila de mensagens mortas, em vez de compartilhá-la com outros aplicativos em execução no mesmo computador.

-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> propriedade para expressar a fila específica a ser usada como uma fila de inatividade. Isso está disponível apenas no [!INCLUDE[wv](../../../../includes/wv-md.md)].

 Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação e especifica um valor baixo arbitrariamente para "time-to-live" para essas mensagens (cerca de 2 segundos). O cliente também especifica uma fila mortas personalizada para usar a opção de enfileirar as mensagens que expiraram.

 O aplicativo cliente pode ler as mensagens na fila de inatividade e a enviar a mensagem de repetição ou corrigir o erro que causou a mensagem original a ser colocado na fila de inatividade e enviar a mensagem. No exemplo, o cliente exibirá uma mensagem de erro.

 O contrato de serviço é `IOrderProcessor`, conforme mostrado no código de exemplo a seguir.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 O código de serviço no exemplo é do [associação de MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 A comunicação com o serviço ocorre dentro do escopo de uma transação. O serviço lê as mensagens da fila, executa a operação e, em seguida, exibe os resultados da operação. O aplicativo também cria uma fila de inatividade para mensagens mortas.

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

 A configuração do cliente especifica uma duração curta para a mensagem alcançar o serviço. Se a mensagem não pode ser transmitida dentro da duração especificada, a mensagem expira e é movida para a fila de inatividade.

> [!NOTE]
>  É possível que o cliente envie a mensagem à fila de serviço dentro do tempo especificado. Para garantir que você vê o serviço de inatividade em ação, você deve executar o cliente antes de iniciar o serviço. A mensagem expira e é entregue ao serviço de inatividade.

 O aplicativo deve definir qual fila a ser usada como sua fila de inatividade. Se nenhuma fila for especificada, a fila de inatividade padrão em todo o sistema transacional é usada para mensagens de inatividade da fila. Neste exemplo, o aplicativo cliente especifica sua própria fila de inatividade do aplicativo.

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

 O serviço de mensagens mortas lê as mensagens da fila de inatividade. O serviço de mensagens mortas implementa o `IOrderProcessor` contrato. Sua implementação no entanto não é para processar pedidos. O serviço de mensagens mortas é um serviço de cliente e não tem o recurso para processar pedidos.

> [!NOTE]
>  A fila de inatividade é uma fila do cliente e é local para o Gerenciador de fila do cliente.

 A implementação do serviço de mensagens mortas verifica o motivo pelo qual que uma mensagem de falha na entrega e leva de medidas corretivas. O motivo da falha de uma mensagem for capturado no duas enumerações, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> e <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>. Você pode recuperar o <xref:System.ServiceModel.Channels.MsmqMessageProperty> do <xref:System.ServiceModel.OperationContext> conforme mostrado no código de exemplo a seguir:

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succed ", po);
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

 Mensagens na fila de inatividade são mensagens que são resolvidas para o serviço que está processando a mensagem. Portanto, quando o serviço de mensagens mortas lê as mensagens da fila, a camada de canais do Windows Communication Foundation (WCF) localiza a incompatibilidade nos pontos de extremidade e não despachar a mensagem. Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas é recebida pelo serviço de mensagens mortas. Para receber uma mensagem que é endereçada a um ponto de extremidade diferente, um filtro de endereço para correspondência de qualquer endereço é especificado no `ServiceBehavior`. Isso é necessário para processar com êxito mensagens que são lidas da fila de inatividade.

 Neste exemplo, o serviço de mensagens mortas reenvia a mensagem se o motivo da falha é que a mensagem atingiu o tempo limite. Para todos os outros motivos, ele exibe a falha de entrega, conforme mostrado no código de exemplo a seguir:

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

 O exemplo a seguir mostra a configuração de uma mensagem de inatividade:

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

 Executar o exemplo, há 3 executáveis sejam rodados para ver como a fila de inatividade funciona para cada aplicativo. o cliente, serviço e um serviço de inatividade que lê da fila de inatividade para cada aplicativo e reenvia a mensagem para o serviço. Todos são aplicativos de console com saída nas janelas do console.

> [!NOTE]
>  Porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda recebe suas mensagens. Você deve iniciar o serviço e desligá-lo para que a fila pode ser criada.

 Ao executar o cliente, o cliente exibirá a mensagem:

```
Press <ENTER> to terminate client.
```

 O cliente tentou enviar a mensagem, mas com um tempo limite curto, a mensagem expirou e está agora na fila na fila de inatividade para cada aplicativo.

 Em seguida, executar o serviço de inatividade, que lê a mensagem e exibe o código de erro e reenvia a mensagem de volta para o serviço.

```
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 O serviço é iniciado e, em seguida, lê a mensagem resent e processa-os.

```
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

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ. Siga estas etapas para criar uma fila no Windows 2008.

    1.  Abra o Gerenciador de servidores no Visual Studio 2012.

    2.  Expanda o **recursos** guia.

    3.  Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.

    4.  Verifique as **transacional** caixa.

    5.  Insira `ServiceModelSamplesTransacted` como o nome da nova fila.

3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Para executar o exemplo em uma fila de alteração de configuração ou entre computadores nomes apropriadamente, substituindo o localhost pelo nome completo do computador e siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar o exemplo em um computador associado a um grupo de trabalho

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

     Verifique se o ponto de extremidade está associado com a associação, definindo o ponto de extremidade `bindingConfiguration` atributo.

2.  Certifique-se de que você altera a configuração no DeadLetterService, server e o cliente antes de executar o exemplo.

    > [!NOTE]
    >  Definindo `security mode` à `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel` e `Message` security `None`.

## <a name="comments"></a>Comentários
 Por padrão com o `netMsmqBinding` transporte de associação de segurança está habilitada. Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinam o tipo de segurança de transporte. Por padrão, o modo de autenticação está definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio. Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "Mensagem do usuário interna certificado do enfileiramento de mensagens não existe".

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  

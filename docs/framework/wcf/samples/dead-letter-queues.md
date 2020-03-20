---
title: Filas de mensagens de inatividade
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144942"
---
# <a name="dead-letter-queues"></a>Filas de mensagens de inatividade
Esta amostra demonstra como lidar e processar mensagens que falharam na entrega. Baseia-se na amostra [de ligação MSMQ transacionada.](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) Esta amostra `netMsmqBinding` usa a ligação. O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.

> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.

> [!NOTE]
> Esta amostra demonstra cada fila de letras mortas do aplicativo que só está disponível no Windows Vista. A amostra pode ser modificada para usar as filas padrão em todo o sistema para o MSMQ 3.0 no Windows Server 2003 e no Windows XP.

 Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens para uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.

 Como a comunicação enfileirada pode envolver uma certa quantidade de dormência, você pode querer associar um valor de tempo ao vivo na mensagem para garantir que a mensagem não seja entregue ao aplicativo se ela tiver passado do tempo. Há também casos em que um aplicativo deve ser informado se uma mensagem falhou na entrega. Em todos esses casos, como quando o tempo de vida da mensagem expirou ou a mensagem falhou na entrega, a mensagem é colocada em uma fila de letras mortas. O aplicativo de envio pode então ler as mensagens na fila da letra morta e tomar ações corretivas que vão desde nenhuma ação até corrigir as razões para a entrega falha e reenviar a mensagem.

 A fila de letras `NetMsmqBinding` mortas na vinculação é expressa nas seguintes propriedades:

- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>propriedade para expressar o tipo de fila de letras mortas exigida pelo cliente. Esta enumeração tem os seguintes valores:

- `None`: Não é necessária fila de letras mortas pelo cliente.

- `System`: A fila de letras mortas do sistema é usada para armazenar mensagens mortas. A fila de letras mortas do sistema é compartilhada por todos os aplicativos em execução no computador.

- `Custom`: Uma fila personalizada de letras <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> mortas especificada usando a propriedade é usada para armazenar mensagens mortas. Este recurso só está disponível no Windows Vista. Isso é usado quando o aplicativo deve usar sua própria fila de letras mortas em vez de compartilhá-la com outros aplicativos em execução no mesmo computador.

- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>propriedade para expressar a fila específica para usar como uma fila de letras mortas. Isso está disponível apenas no Windows Vista.

 Nesta amostra, o cliente envia um lote de mensagens para o serviço dentro do escopo de uma transação e especifica um valor arbitrariamente baixo para "tempo de vida" para essas mensagens (cerca de 2 segundos). O cliente também especifica uma fila de letras mortas personalizada para usar para enfileirar as mensagens que expiraram.

 O aplicativo cliente pode ler as mensagens na fila da letra morta e tentar novamente enviar a mensagem ou corrigir o erro que fez com que a mensagem original fosse colocada na fila da letra morta e enviasse a mensagem. Na amostra, o cliente exibe uma mensagem de erro.

 O contrato `IOrderProcessor`de serviço é, conforme mostrado no código de amostra a seguir.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 O código de serviço na amostra é o da [Vinculação MSMQ Transacionada](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).

 A comunicação com o serviço ocorre no âmbito de uma transação. O serviço lê mensagens da fila, realiza a operação e, em seguida, exibe os resultados da operação. O aplicativo também cria uma fila de letras mortas para mensagens de letra morta.

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

 A configuração do cliente especifica uma curta duração para que a mensagem chegue ao serviço. Se a mensagem não puder ser transmitida dentro da duração especificada, a mensagem expirará e será transferida para a fila da letra morta.

> [!NOTE]
> É possível que o cliente entregue a mensagem na fila de serviço dentro do tempo especificado. Para garantir que você veja o serviço de letras mortas em ação, você deve executar o cliente antes de iniciar o serviço. A mensagem se estende e é entregue ao serviço de cartas mortas.

 O aplicativo deve definir qual fila usar como sua fila de letras mortas. Se nenhuma fila for especificada, a fila de letras mortas transacionais em todo o sistema será usada para enfileirar mensagens mortas. Neste exemplo, o aplicativo cliente especifica sua própria fila de letras mortas de aplicativo.

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

 O serviço de mensagens de carta morta lê mensagens da fila da carta morta. O serviço de mensagens `IOrderProcessor` de carta morta implementa o contrato. Sua implementação, no entanto, não é para processar ordens. O serviço de mensagem de letra morta é um serviço ao cliente e não tem a facilidade de processar pedidos.

> [!NOTE]
> A fila de letras mortas é uma fila de clientes e é local para o gerente da fila do cliente.

 A implementação do serviço de mensagens de letra morta verifica o motivo pelo qual uma mensagem falhou na entrega e toma medidas corretivas. A razão para uma falha de mensagem <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> é <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>capturada em duas enumerações, e . Você pode <xref:System.ServiceModel.Channels.MsmqMessageProperty> recuperar <xref:System.ServiceModel.OperationContext> o do mostrado no seguinte código de amostra:

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

 Mensagens na fila da letra morta são mensagens que são endereçadas ao serviço que está processando a mensagem. Portanto, quando o serviço de mensagens de letra morta lê mensagens da fila, a camada do canal do Windows Communication Foundation (WCF) encontra a incompatibilidade em pontos finais e não envia a mensagem. Neste caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas é recebida pelo serviço de mensagem de letra morta. Para receber uma mensagem endereçada a um ponto final diferente, um `ServiceBehavior`filtro de endereço para corresponder a qualquer endereço é especificado no . Isso é necessário para processar com sucesso mensagens que são lidas da fila de letras mortas.

 Nesta amostra, o serviço de mensagem de letra morta reenvia a mensagem se a razão da falha é que a mensagem está descronometrada. Por todas as outras razões, ele exibe a falha de entrega, como mostrado no seguinte código de amostra:

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

 A amostra a seguir mostra a configuração de uma mensagem de letra morta:

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

 Ao executar a amostra, há 3 executáveis a serem executados para ver como funciona a fila de letras mortas para cada aplicativo; o cliente, o serviço e um serviço de letra morta que lê da fila de letras mortas para cada aplicativo e reenvia a mensagem para o serviço. Todos são aplicativos de console com saída nas janelas do console.

> [!NOTE]
> Como a fila está em uso, o cliente e o serviço não têm que estar funcionando ao mesmo tempo. Você pode executar o cliente, desligá-lo e, em seguida, iniciar o serviço e ele ainda recebe suas mensagens. Você deve iniciar o serviço e desligá-lo para que a fila possa ser criada.

 Ao executar o cliente, o cliente exibe a mensagem:

```console
Press <ENTER> to terminate client.
```

 O cliente tentou enviar a mensagem, mas com um curto intervalo, a mensagem expirou e agora está na fila da letra morta para cada aplicativo.

 Em seguida, execute o serviço de letras mortas, que lê a mensagem e exibe o código de erro e reenvia a mensagem de volta ao serviço.

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

 O serviço começa e depois lê a mensagem ressentida e processa-a.

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

### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Se o serviço for executado primeiro, ele verificará se a fila está presente. Se a fila não estiver presente, o serviço criará uma. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um através do MSMQ Queue Manager. Siga estas etapas para criar uma fila no Windows 2008.

    1. Gerente de servidor aberto no Visual Studio 2012.

    2. Expanda a guia **Recursos.**

    3. Clique com o botão direito do mouse em Filas de **mensagens privadas**e selecione **Nova** **fila privada**.

    4. Verifique a **caixa transacional.**

    5. Digite `ServiceModelSamplesTransacted` como o nome da nova fila.

3. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Para executar a amostra em uma configuração única ou entre computadors, altere os nomes da fila de configuração adequadamente, substituindo o host local pelo nome completo do computador e siga as instruções em [Executando as Amostras da Fundação de Comunicação do Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar a amostra em um computador junto a um grupo de trabalho

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

     Certifique-se de que o ponto final está `bindingConfiguration` associado à vinculação definindo o atributo do ponto final.

2. Certifique-se de alterar a configuração no DeadLetterService, servidor e cliente antes de executar a amostra.

    > [!NOTE]
    > A `security mode` `None` configuração é `MsmqAuthenticationMode` `MsmqProtectionLevel` equivalente `Message` à `None`configuração e segurança a .

## <a name="comments"></a>Comentários
 Por padrão, `netMsmqBinding` com o transporte vinculativo, a segurança é ativada. Duas `MsmqAuthenticationMode` propriedades, `MsmqProtectionLevel`e, juntas, determinam o tipo de segurança de transporte. Por padrão, o modo `Windows` de autenticação está `Sign`definido para e o nível de proteção é definido como . Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio. Se você executar esta amostra em um computador que não faz parte de um domínio, você receberá o seguinte erro: "O certificado de fila de mensagens internas do usuário não existe".

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  

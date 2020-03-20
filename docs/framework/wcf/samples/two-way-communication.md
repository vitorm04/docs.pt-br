---
title: Comunicação bidirecional
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 56f789fe185cb2885c215e9512e82ae2fbb64a36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143753"
---
# <a name="two-way-communication"></a>Comunicação bidirecional
Esta amostra demonstra como executar a comunicação transacionada em fila bidirecional sobre o MSMQ. Esta amostra `netMsmqBinding` usa a ligação. Neste caso, o serviço é um aplicativo de console auto-hospedado que permite observar o serviço que recebe mensagens enfileiradas.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra é baseada na [vinculação MSMQ transacionada](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila. O cliente envia mensagens para uma fila, e o serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.  
  
 Esta amostra demonstra comunicação em duas vias usando filas. O cliente envia ordens de compra para a fila dentro do escopo de uma transação. O serviço recebe os pedidos, processa o pedido e, em seguida, liga de volta para o cliente com o status da ordem da fila no âmbito de uma transação. Para facilitar a comunicação bidirecional, o cliente e o serviço usam filas para enfileirar pedidos de compra e status do pedido.  
  
 O contrato `IOrderProcessor` de serviço define operações de serviço unidirecional que se adequam ao uso de filas. A operação de serviço inclui o ponto final de resposta a ser usado para enviar os status do pedido. O ponto final de resposta é o URI da fila para enviar o status do pedido de volta ao cliente. O aplicativo de processamento de pedidos implementa este contrato.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string
                                  reportOrderStatusTo);  
}
```
  
 O contrato de resposta para enviar status do pedido é especificado pelo cliente. O cliente implementa o contrato de status do pedido. O serviço usa o proxy gerado deste contrato para enviar o status do pedido de volta ao cliente.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 A operação do serviço processa a ordem de compra submetida. O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicado à operação de serviço para especificar o alistamento automático em uma transação que é usada para receber a mensagem da fila e conclusão automática das transações após a conclusão da operação do serviço. A `Orders` classe encapsula a funcionalidade de processamento de pedidos. Neste caso, adiciona a ordem de compra a um dicionário. A transação em que a operação de serviço `Orders` se alistou está disponível para as operações da classe.  
  
 A operação do serviço, além de processar a ordem de compra enviada, responde ao cliente sobre o status do pedido.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 O nome da fila MSMQ é especificado em uma seção Deconfiguração do arquivo de configuração. O ponto final do serviço é definido na seção System.ServiceModel do arquivo de configuração.  
  
> [!NOTE]
> O nome da fila MSMQ e o endereço de ponto final usam convenções de endereçamento ligeiramente diferentes. O nome da fila MSMQ usa um ponto (.) para a máquina local e separadores de barra invertida em seu caminho. O endereço de ponto final da Windows Communication Foundation (WCF) especifica um net.msmq: esquema, usa "localhost" para a máquina local e usa barras para a frente em seu caminho. Para ler a partir de uma fila hospedada na máquina remota, substitua o "." e "localhost" para o nome da máquina remota.  
  
 O serviço é auto-hospedado. Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou através de código. Nesta amostra, o serviço verifica a existência da fila e a cria, se necessário. O nome da fila é lido no arquivo de configuração. O endereço base é usado pela [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderProcessorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```

 O cliente cria uma transação. A comunicação com a fila ocorre no âmbito da transação, fazendo com que ela seja tratada como uma unidade atômica onde todas as mensagens tenham sucesso ou falhem.  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 O código do `IOrderStatus` cliente implementa o contrato para receber o status do pedido do serviço. Neste caso, ele imprime o status do pedido.  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,
                                                           status);  
    }  
}  
```

 A fila de status do `Main` pedido é criada no método. A configuração do cliente inclui a configuração de serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado na configuração de amostra a seguir.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
              binding="netMsmqBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 Quando você executa a amostra, as atividades de cliente e serviço são exibidas nas janelas de serviço e console do cliente. Você pode ver o serviço receber mensagens do cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
 O serviço exibe as informações da ordem de compra e indica que está enviando de volta o status do pedido para a fila de status do pedido.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 O cliente exibe as informações de status do pedido enviadas pelo serviço.  
  
```console  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Se você usar Svcutil.exe para regenerar a configuração para esta amostra, certifique-se de modificar os nomes de ponto final na configuração do cliente para corresponder ao código do cliente.  
  
 Por padrão <xref:System.ServiceModel.NetMsmqBinding>com o , a segurança de transporte está ativada. Existem duas propriedades relevantes para a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` segurança de transporte MSMQ `Windows` e, por padrão, o modo de autenticação é definido para e o nível de proteção é definido como `Sign`. Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio e a opção de integração ativa de diretórios para O MSMQ deve ser instalada. Se você executar esta amostra em um computador que não satisfaça esses critérios, você receberá um erro.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar a amostra em um computador junto a um grupo de trabalho ou sem integração de diretório ativo  
  
1. Se o computador não fizer parte de um domínio ou não tiver a integração ativa do diretório `None` instalada, desligue a segurança do transporte definindo o modo de autenticação e o nível de proteção para o que for mostrado na seguinte configuração de amostra:  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. Desativar a segurança de uma configuração de cliente gera o seguinte:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"
                    binding="netMsmqBinding"
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. O serviço para esta amostra `OrderProcessorService`cria uma vinculação no . Adicione uma linha de código depois que a vinculação `None`for instanciada para definir o modo de segurança para .  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Certifique-se de alterar a configuração no servidor e no cliente antes de executar a amostra.  
  
    > [!NOTE]
    > A `security mode` `None` configuração é <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> equivalente `Message` à `None`configuração ou segurança a .  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  

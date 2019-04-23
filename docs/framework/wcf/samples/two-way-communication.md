---
title: Comunicação bidirecional
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 6ce0d15bca15fff52ea6c4ab210dd08664e19824
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770913"
---
# <a name="two-way-communication"></a>Comunicação bidirecional
Este exemplo demonstra como executar transacionado uma comunicação bidirecional em fila em relação ao MSMQ. Este exemplo usa o `netMsmqBinding` associação. Nesse caso, o serviço é um aplicativo de console auto-hospedado que permite que você observe o recebimento de mensagens na fila de serviço.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo se baseia a [transacionada de associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. O cliente envia mensagens para uma fila e o serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 Este exemplo demonstra o uso de filas de comunicação de 2 vias. O cliente envia ordens de compra para a fila de dentro do escopo de uma transação. O serviço recebe as ordens, processa o pedido e, em seguida, chama de volta o cliente com o status da ordem da fila de dentro do escopo de uma transação. Para facilitar a comunicação bidirecional o cliente e o serviço usam filas para enfileirar as ordens de compra e o status do pedido.  
  
 O contrato de serviço `IOrderProcessor` define as operações de serviço unidirecional que acordo com o uso de enfileiramento de mensagens. A operação de serviço inclui o ponto de extremidade a usar para enviar os status da ordem de resposta. O ponto de extremidade de resposta é o URI da fila para enviar o status do pedido para o cliente. Aplicativo de processamento de pedidos implementa esse contrato.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 O contrato de resposta para enviar o status do pedido é especificado pelo cliente. O cliente implementa o contrato de status do pedido. O serviço usa o proxy gerado deste contrato para enviar o status da ordem de volta ao cliente.  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 A operação de serviço processa a ordem de compra enviado. O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicada à operação de serviço para especificar a inscrição automática em uma transação que é usada para receber a mensagem da fila e o preenchimento automático de transações após a conclusão da operação de serviço. O `Orders` classe encapsula a funcionalidade de ordem de processamento. Nesse caso, ele adiciona a ordem de compra em um dicionário. A transação que a operação de serviço inscrita em está disponível para operações no `Orders` classe.  
  
 A operação de serviço, além de processamento de ordem de compra enviado, respostas de volta para o cliente sobre o status do pedido.  

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

 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração. O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração.  
  
> [!NOTE]
>  O endereço de ponto de extremidade e o nome da fila MSMQ usar convenções de endereçamento ligeiramente diferentes. O nome da fila MSMQ usa um ponto (.) para que os separadores de máquina e a barra invertida locais em seu caminho. O endereço de ponto de extremidade do Windows Communication Foundation (WCF) especifica um NET. MSMQ: esquema, usa "localhost" para o computador local e usa barras "/" em seu caminho. Para ler de uma fila que está hospedada no computador remoto, substitua o "." e "localhost" para o nome do computador remoto.  
  
 O serviço é auto-hospedado. Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço verifica a existência da fila e cria-lo, se necessário. O nome da fila é lido do arquivo de configuração. O endereço base é usado pelas [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.  

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

 O cliente cria uma transação. A comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica em que todas as mensagens de êxito ou falha.  

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

 O código do cliente implementa o `IOrderStatus` de contrato para receber o status do pedido do serviço. Nesse caso, ele imprime o status do pedido.  

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

 A fila de status do pedido é criada no `Main` método. A configuração do cliente inclui a configuração de serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado no seguinte exemplo de configuração.  
  
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
  
 Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente. Você pode ver as mensagens de recebimento do serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
 O serviço exibe as informações de ordem de compra e indica que ele está enviando novamente o status do pedido para a fila de status do pedido.  
  
```  
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
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Se você usar Svcutil.exe para gerar novamente a configuração para este exemplo, certifique-se de modificar os nomes de ponto de extremidade na configuração do cliente para coincidir com o código do cliente.  
  
 Por padrão com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada. Há duas propriedades relevantes para a segurança do transporte MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do active directory para o MSMQ deve estar instalada. Se você executar esse exemplo em um computador que não atendem a esses critérios, você receberá um erro.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do Active Directory  
  
1. Se o computador não fizer parte de um domínio ou não tem integração do Active Directory instalada, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no seguinte exemplo de configuração:  
  
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
  
2. Desativação da segurança para uma configuração de cliente gera o seguinte:  
  
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
  
3. O serviço para este exemplo cria uma associação no `OrderProcessorService`. Adicionar uma linha de código depois que a associação é instanciada para definir o modo de segurança para `None`.  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.  
  
    > [!NOTE]
    >  Definindo `security mode` à `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ou `Message` security `None`.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  

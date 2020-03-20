---
title: Sessões e filas
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144089"
---
# <a name="sessions-and-queues"></a>Sessões e filas
Esta amostra demonstra como enviar e receber um conjunto de mensagens relacionadas em comunicação enfileirada sobre o transporte de Fila de Mensagens (MSMQ). Esta amostra `netMsmqBinding` usa a ligação. O serviço é um aplicativo de console auto-hospedado para permitir que você observe o serviço que recebe mensagens enfileiradas.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 Na comunicação enfileirada, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens para uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar funcionando ao mesmo tempo para se comunicar usando uma fila.  
  
 Às vezes, um cliente envia um conjunto de mensagens que estão relacionadas entre si em um grupo. Quando as mensagens devem ser processadas em conjunto ou em uma ordem especificada, uma fila pode ser usada para agrulá-las juntas, para processamento por um único aplicativo receptor. Isso é particularmente importante quando há vários aplicativos de recepção em um grupo de servidores e é necessário garantir que um grupo de mensagens seja processado pelo mesmo aplicativo receptor. As sessões em fila são um mecanismo usado para enviar e receber um conjunto de mensagens relacionadas que devem ser processadas de uma só vez. As sessões em fila exigem uma transação para exibir esse padrão.  
  
 Na amostra, o cliente envia uma série de mensagens para o serviço como parte de uma sessão no âmbito de uma única transação.  
  
 O contrato `IOrderTaker`de serviço é , que define um serviço unidirecional que é adequado para uso com filas. O <xref:System.ServiceModel.SessionMode> usado no contrato mostrado no código de amostra a seguir indica que as mensagens fazem parte da sessão.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 O serviço define as operações de serviço de tal forma que a primeira operação se aliste em uma transação, mas não complete automaticamente a transação. As operações subseqüentes também se alistam na mesma transação, mas não são automaticamente concluídas. A última operação na sessão completa automaticamente a transação. Assim, a mesma transação é utilizada para diversas invocações de operação no contrato de prestação de serviços. Se alguma das operações abrir uma exceção, a transação volta e a sessão é colocada de volta na fila. Após a conclusão bem sucedida da última operação, a transação é cometida. O serviço `PerSession` usa <xref:System.ServiceModel.InstanceContextMode> como para receber todas as mensagens em uma sessão na mesma instância do serviço.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 O serviço é auto-hospedado. Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou através de código. Nesta amostra, o <xref:System.Messaging> serviço contém código para verificar a existência da fila e cria-a, se necessário. O nome da fila é lido <xref:System.Configuration.ConfigurationManager.AppSettings%2A> no arquivo de configuração usando a classe.  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
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

 O nome da fila MSMQ é especificado em uma seção Deconfiguração do arquivo de configuração. O ponto final do serviço é definido na seção system.serviceModel `netMsmqBinding` do arquivo de configuração e especifica a vinculação.  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 O cliente cria um escopo de transação. Todas as mensagens da sessão são enviadas para a fila dentro do escopo da transação, fazendo com que ela seja tratada como uma unidade atômica onde todas as mensagens tenham sucesso ou falhem. A transação é <xref:System.Transactions.TransactionScope.Complete%2A>cometida por chamada .  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> Você pode usar apenas uma única transação para todas as mensagens da sessão e todas as mensagens da sessão devem ser enviadas antes de cometer a transação. Fechar o cliente encerra a sessão. Portanto, o cliente deve ser fechado antes que a transação seja concluída para enviar todas as mensagens da sessão para a fila.  
  
 Quando você executa a amostra, as atividades de cliente e serviço são exibidas nas janelas de serviço e console do cliente. Você pode ver o serviço receber mensagens do cliente. Pressione ENTER em cada janela do console para desligar o serviço e o cliente. Note que, como a fila está em uso, o cliente e o serviço não precisa estar funcionando ao mesmo tempo. Você pode executar o cliente, desligá-lo e, em seguida, iniciar o serviço e ele ainda recebe suas mensagens.  
  
 Sobre o cliente.  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 No serviço.  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C#, C++ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Por padrão <xref:System.ServiceModel.NetMsmqBinding>com o , a segurança de transporte está ativada. Existem duas propriedades relevantes para a <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> segurança <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` de transporte MSMQ, `Windows` ou seja, e, por padrão, o modo de autenticação é definido para e o nível de proteção é definido como `Sign`. Para que o MSMQ forneça o recurso de autenticação e assinatura, ele deve fazer parte de um domínio e a opção de integração ativa de diretórios para O MSMQ deve ser instalada. Se você executar esta amostra em um computador que não satisfaça esses critérios, você receberá um erro.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar a amostra em um computador junto a um grupo de trabalho ou sem integração de diretório ativo  
  
1. Se o computador não fizer parte de um domínio ou não tiver a integração ativa do diretório `None` instalada, desligue a segurança do transporte definindo o modo de autenticação e o nível de proteção para o mostrado na configuração da amostra a seguir.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. Certifique-se de alterar a configuração no servidor e no cliente antes de executar a amostra.  
  
    > [!NOTE]
    > `None` Definir o modo de <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>segurança <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>é `Message` equivalente `None`à configuração e segurança a .  

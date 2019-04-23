---
title: Sessões e filas
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 623077450157b0bf87b85a85309adc10511b32b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769509"
---
# <a name="sessions-and-queues"></a>Sessões e filas
Este exemplo demonstra como enviar e receber um conjunto de mensagens relacionadas em comunicação em fila por meio do transporte de enfileiramento de mensagens (MSMQ). Este exemplo usa o `netMsmqBinding` associação. O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 Às vezes, um cliente envia um conjunto de mensagens que estão relacionados uns aos outros em um grupo. Quando as mensagens devem ser processadas em conjunto ou em uma ordem especificada, uma fila pode ser usada para agrupá-los, para processamento por um único aplicativo de recebimento. Isso é particularmente importante quando há vários aplicativos de recebimento em um grupo de servidores e é necessário garantir que um grupo de mensagens é processado pelo mesmo aplicativo de recebimento. Sessões na fila são um mecanismo usado para enviar e receber um conjunto relacionado de mensagens que deve ser processado ao mesmo tempo. Sessões na fila requerem uma transação exibem esse padrão.  
  
 No exemplo, o cliente envia um número de mensagens para o serviço como parte de uma sessão dentro do escopo de uma única transação.  
  
 O contrato de serviço é `IOrderTaker`, que define um serviço unidirecional que é adequado para uso com as filas. O <xref:System.ServiceModel.SessionMode> usado no contrato mostrado no seguinte código de exemplo indica que as mensagens são parte da sessão.  

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

 O serviço define as operações de serviço de forma que a primeira operação inscreve-se em uma transação, mas não conclui a transação automaticamente. As operações subsequentes também se inscrever na mesma transação, mas não são concluídos automaticamente. A última operação na sessão preenche automaticamente a transação. Assim, a mesma transação é usada para várias invocações de operação no contrato de serviço. Se qualquer uma das operações lançar uma exceção, em seguida, a transação será revertida e a sessão é colocada de volta na fila. Após a conclusão bem-sucedida da última operação, a transação é confirmada. O serviço usa `PerSession` como o <xref:System.ServiceModel.InstanceContextMode> para receber todas as mensagens em uma sessão na mesma instância do serviço.  

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

 O serviço é auto-hospedado. Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço contém <xref:System.Messaging> código para verificar a existência da fila e cria-lo, se necessário. O nome da fila é lida do arquivo de configuração usando o <xref:System.Configuration.ConfigurationManager.AppSettings%2A> classe.  

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

 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração. O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração e especifica o `netMsmqBinding` associação.  
  
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
  
 O cliente cria um escopo de transação. Todas as mensagens na sessão são enviadas para a fila de dentro do escopo de transação, fazendo com que ele será tratado como uma unidade atômica em que todas as mensagens de êxito ou falha. A transação é confirmada chamando <xref:System.Transactions.TransactionScope.Complete%2A>.  

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
>  Você pode usar apenas uma única transação para todas as mensagens na sessão e todas as mensagens na sessão devem ser enviadas antes de confirmar a transação. Fechar o cliente fecha a sessão. Portanto, o cliente deve ser fechado antes que a transação seja concluída para enviar todas as mensagens na sessão para a fila.  
  
 Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente. Você pode ver as mensagens de recebimento do serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente. Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda recebe suas mensagens.  
  
 No cliente.  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 No serviço.  
  
```  
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
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição de c#, C++ ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Por padrão com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada. Há duas propriedades relevantes para a segurança do transporte MSMQ, ou seja, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do active directory para o MSMQ deve estar instalada. Se você executar esse exemplo em um computador que não atendem a esses critérios, você receberá um erro.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do Active Directory  
  
1. Se o computador não fizer parte de um domínio ou não tem integração do Active Directory instalada, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no seguinte exemplo de configuração.  
  
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
  
2. Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.  
  
    > [!NOTE]
    >  Configurar o modo de segurança para `None` equivale a definir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, e `Message` security `None`.  

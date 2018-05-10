---
title: Correlação de mensagem
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: 7105c66153625b4a7a2b9a2d61a2ab2821cab2af
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="message-correlation"></a>Correlação de mensagem
Este exemplo demonstra como um aplicativo de serviço de enfileiramento de mensagens (MSMQ) pode enviar uma mensagem MSMQ a um serviço do Windows Communication Foundation (WCF) e como as mensagens podem ser correlacionadas entre remetente e destinatário aplicativos em um cenário de solicitação/resposta. Este exemplo usa a associação de msmqIntegrationBinding. Nesse caso, o serviço é um aplicativo de console auto-hospedado para permitir que você observar o serviço que recebe as mensagens em fila. K  
  
 O serviço processa a mensagem recebida do remetente e envia uma mensagem de resposta de volta ao remetente. O remetente correlaciona a resposta recebido para a solicitação que ela enviada originalmente. O `MessageID` e `CorrelationID` propriedades da mensagem são usadas para correlacionar as mensagens de solicitação e resposta.  
  
 O `IOrderProcessor` contrato de serviço define uma operação de serviço unidirecional que é adequada para uso com o enfileiramento de mensagens. Uma mensagem MSMQ não tem um cabeçalho de ação, portanto, não é possível mapear mensagens MSMQ diferentes para contratos de operação automaticamente. Portanto, pode haver apenas um contrato de operação nesse caso. Se você deseja definir contratos de operação mais no serviço, o aplicativo deve fornecer informações sobre quais cabeçalho o MSMQ mensagem (por exemplo, o rótulo ou correlationID) pode ser usada para decidir qual contrato de operação para enviar. Isso é demonstrado no [Demux personalizado](../../../../docs/framework/wcf/samples/custom-demux.md).  
  
 A mensagem do MSMQ também não contêm informações sobre qual cabeçalhos são mapeados para os parâmetros diferentes do contrato da operação. Portanto, pode haver somente um parâmetro no contrato de operação. O parâmetro é do tipo <!--zz <xref:System.ServiceModel.MSMQIntegration.MsmqMessage%601>`MsmqMessage<T>`--> , `System.ServiceModel.MSMQIntegration.MsmqMessage` que contém a mensagem MSMQ subjacente. O tipo "T" no `MsmqMessage<T>` classe representa os dados que são serializados no corpo da mensagem do MSMQ. Neste exemplo, o `PurchaseOrder` tipo é serializado no corpo da mensagem do MSMQ.  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[ServiceKnownType(typeof(PurchaseOrder))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
```

 A operação de serviço processa a ordem de compra e exibe o conteúdo da ordem de compra e seu status na janela do console de serviço. O <xref:System.ServiceModel.OperationBehaviorAttribute> configura a operação para se inscrever em uma transação com a fila e marcar a transação concluída quando a operação retorna. O `PurchaseOrder` contém os detalhes do pedido que devem ser processados pelo serviço.  

```csharp
// Service class that implements the service contract.  
public class OrderProcessorService : IOrderProcessor  
{  
   [OperationBehavior(TransactionScopeRequired = true,   
          TransactionAutoComplete = true)]  
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)  
   {  
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;  
       Random statusIndexer = new Random();  
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
       Console.WriteLine("Processing {0} ", po);  
       //Send a response to the client that the order has been received   
         and is pending fullfillment.   
       SendResponse(ordermsg);  
    }  
  
    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)  
    {  
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");  
  
        //Set the correlation ID such that the client can correlate the response to the order.  
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);  
        orderResponsemsg.CorrelationId = ordermsg.Id;  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.SendOrderResponse(orderResponsemsg);  
            scope.Complete();  
        }  
  
        client.Close();  
    }  
}  
```

 O serviço usa um cliente personalizado `OrderResponseClient` para enviar a mensagem do MSMQ para a fila. Como o aplicativo que recebe e processa a mensagem é um aplicativo do MSMQ e não é um aplicativo WCF, não há nenhum contrato de serviço implícita entre os dois aplicativos. Portanto, não é possível criar um proxy usando a ferramenta Svcutil.exe neste cenário.  
  
 O proxy personalizado é essencialmente o mesmo para todos os aplicativos do WCF que usam o `msmqIntegrationBinding` associação para enviar mensagens. Ao contrário de outros proxies, ele não inclui uma variedade de operações de serviço. É uma operação de enviar mensagem somente.  

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderResponse  
{  
  
    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]  
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse  
{  
  
    public OrderResponseClient()  
    { }  
  
    public OrderResponseClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SendOrderResponse(msg);  
    }  
}  
```

 O serviço é auto-hospedado. Ao usar o transporte de integração do MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço contém <xref:System.Messaging> código para verificar a existência da fila e crie-o se necessário. O nome da fila é lida do arquivo de configuração.  

```csharp
public static void Main()  
{  
       // Get the MSMQ queue name from application settings in configuration.  
      string queueName =   
                ConfigurationManager.AppSettings["orderQueueName"];  
      // Create the transacted MSMQ queue if necessary.  
      if (!MessageQueue.Exists(queueName))  
                MessageQueue.Create(queueName, true);  
     // Create a ServiceHost for the OrderProcessorService type.  
     using (ServiceHost serviceHost = new   
                   ServiceHost(typeof(OrderProcessorService)))  
     {  
            serviceHost.Open();  
            // The service can now be accessed.  
            Console.WriteLine("The service is ready.");  
            Console.WriteLine("Press <ENTER> to terminate service.");  
            Console.ReadLine();  
            // Close the ServiceHost to shutdown the service.  
            serviceHost.Close();  
      }  
}  
```
  
 A fila MSMQ para o qual as solicitações de ordem são enviadas é especificada na seção appSettings do arquivo de configuração. Os pontos de extremidade do cliente e de serviço são definidos na seção System. ServiceModel do arquivo de configuração. Especificar o `msmqIntegrationbinding` associação.  
  
```xml  
<appSettings>  
  <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
  
<system.serviceModel>  
  <client>  
    <endpoint    name="OrderResponseEndpoint"   
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"  
              binding="msmqIntegrationBinding"  
              bindingConfiguration="OrderProcessorBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">  
    </endpoint>  
  </client>  
  
  <services>  
    <service   
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"  
                            binding="msmqIntegrationBinding"  
                bindingConfiguration="OrderProcessorBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">  
      </endpoint>  
    </service>  
  </services>  
  
  <bindings>  
    <msmqIntegrationBinding>  
      <binding name="OrderProcessorBinding" >  
        <security mode="None" />  
      </binding>  
    </msmqIntegrationBinding>  
  </bindings>  
  
</system.serviceModel>  
```  
  
 O aplicativo cliente usa <xref:System.Messaging> para enviar uma mensagem durável e transacional à fila. Corpo da mensagem contém a ordem de compra.  

```csharp
static void PlaceOrder()  
{  
    //Connect to the queue  
    MessageQueue orderQueue =   
            new MessageQueue(  
                    ConfigurationManager.AppSettings["orderQueueName"])   
    // Create the purchase order.  
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
  
    Message msg = new Message();  
    msg.UseDeadLetterQueue = true;  
    msg.Body = po;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new      
     TransactionScope(TransactionScopeOption.Required))  
    {  
        // Submit the purchase order.  
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);  
        // Complete the transaction.  
        scope.Complete();  
    }  
    //Save the messageID for order response correlation.  
    orderMessageID = msg.Id;  
    Console.WriteLine("Placed the order, waiting for response...");  
}  
```

 A fila MSMQ recebidas do qual as respostas de ordem for especificada em uma seção appSettings do arquivo de configuração, conforme mostrado no exemplo de configuração.  
  
> [!NOTE]
>  O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho. O endereço de ponto de extremidade do WCF Especifica um esquema FormatName e usa "localhost" para o computador local. Um nome de formato formado corretamente segue FormatName no URI de acordo com as diretrizes MSMQ.  
  
```xml  
<appSettings>  
    <add key=" orderResponseQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
 A salva de aplicativo cliente a `messageID` da mensagem de solicitação de ordem que ele envia para o serviço e aguarda uma resposta do serviço. Depois que uma resposta chega na fila de cliente correlaciona com a mensagem de ordem-enviada usando o `correlationID` propriedade da mensagem, que contém o `messageID` da ordem de uma mensagem de que o cliente enviado originalmente para o serviço.  

```csharp
static void DisplayOrderStatus()  
{  
    MessageQueue orderResponseQueue = new   
     MessageQueue(ConfigurationManager.AppSettings              
                  ["orderResponseQueueName"]);  
    //Create a transaction scope.  
    bool responseReceived = false;  
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;  
    while (!responseReceived)  
    {  
       Message responseMsg;  
       using (TransactionScope scope2 = new    
         TransactionScope(TransactionScopeOption.Required))  
       {  
          //Receive the Order Response message.  
          responseMsg =   
              orderResponseQueue.Receive  
                   (MessageQueueTransactionType.Automatic);  
          scope2.Complete();  
     }  
     responseMsg.Formatter = new   
     System.Messaging.XmlMessageFormatter(new Type[] {   
         typeof(PurchaseOrder) });  
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;  
    //Check if the response is for the order placed.  
    if (orderMessageID == responseMsg.CorrelationId)  
    {  
       responseReceived = true;  
       Console.WriteLine("Status of current Order: OrderID-{0},Order   
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
    else  
    {  
       Console.WriteLine("Status of previous Order: OrderID-{0},Order    
            Status-{1}", responsepo.PONumber, responsepo.Status);  
    }  
  }  
}  
```

 Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente. Você pode ver as mensagens de recebimento de serviço do cliente e envia uma resposta de volta ao cliente. O cliente exibe a resposta recebida do serviço. Pressione ENTER em cada janela de console para desligar o serviço e o cliente.  
  
> [!NOTE]
>  Este exemplo requer a instalação do enfileiramento de mensagens (MSMQ). Consulte as instruções de instalação do MSMQ na seção Consulte também.  
  
### <a name="to-setup-build-and-run-the-sample"></a>A configuração, compilação, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ. Siga estas etapas para criar uma fila no Windows 2008.  
  
    1.  Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Expanda o **recursos** guia.  
  
    3.  Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.  
  
    4.  Verifique o **transacional** caixa.  
  
    5.  Digite `ServiceModelSamplesTransacted` como o nome da nova fila.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo de configuração de um único computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Copie os arquivos de programa do serviço da pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.  
  
2.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
3.  No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".  
  
4.  No arquivo Service.exe.config, altere o endereço de ponto de extremidade do cliente para especificar o nome do computador cliente, em vez de ".".  
  
5.  No computador do serviço, inicie Service.exe em um prompt de comando.  
  
6.  No computador cliente, inicie o Client.exe em um prompt de comando.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Enfileiramento de mensagens](http://go.microsoft.com/fwlink/?LinkId=94968)

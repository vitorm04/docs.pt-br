---
title: Demux personalizado
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: e88672f152b87740feef1345b3eac213916a1527
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805558"
---
# <a name="custom-demux"></a>Demux personalizado
Este exemplo demonstra como cabeçalhos de mensagens MSMQ podem ser mapeados para operações de serviço diferentes, para que o Windows Communication Foundation (WCF) serviços que usam <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> não está limitado a usar uma operação de serviço, conforme demonstrado no [ Mensagens do enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) e [Windows Communication Foundation para enfileiramento](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemplos.  
  
 O serviço neste exemplo é um aplicativo de console auto-hospedado para que você possa observar o serviço que recebe as mensagens em fila.  
  
 O contrato de serviço é `IOrderProcessor`e define um serviço unidirecional que é adequado para uso com filas.  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 Uma mensagem MSMQ não tem um cabeçalho de ação. Não é possível mapear mensagens MSMQ diferentes para contratos de operação automaticamente. Portanto, pode haver apenas um contrato de operação. Para superar essa limitação, o serviço implementa o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> método o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface. O <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> método permite que o serviço mapear um determinado cabeçalho da mensagem para uma operação de serviço específico. Neste exemplo, o cabeçalho do rótulo da mensagem é mapeado para as operações de serviço. O `Name` parâmetro do contrato da operação determina qual operação de serviço deve ser distribuída para um rótulo de determinada mensagem. Por exemplo, se o cabeçalho do rótulo da mensagem contém "SubmitPurchaseOrder", a operação de serviço "SubmitPurchaseOrder" é invocada.  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 O serviço deve implementar o <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> método o <xref:System.ServiceModel.Description.IContractBehavior> interface conforme mostrado no código de exemplo a seguir. Isso se aplica a custom `OperationSelector` no tempo de execução de expedição do serviço do framework.  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 Uma mensagem deve passar pelo dispatcher <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> antes de obter a OperationSelector. Por padrão uma mensagem será rejeitada se a ação não pode ser encontrada em qualquer contrato implementado pelo serviço. Para evitar essa verificação, implementamos um <xref:System.ServiceModel.Description.IEndpointBehavior> chamado `MatchAllFilterBehavior`, que permite que qualquer mensagem para passar o `ContractFilter` aplicando o <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> da seguinte maneira.  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 Quando uma mensagem é recebida pelo serviço, a operação de serviço apropriado é enviada usando as informações fornecidas pelo cabeçalho de rótulo. O corpo da mensagem é desserializado em um `PurchaseOrder` do objeto, como mostrado no código de exemplo a seguir.  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 O serviço é hospedado automaticamente. Ao usar o MSMQ, a fila que é usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço contém código para verificar a existência da fila e cria-se a fila não existe. O nome da fila é lida do arquivo de configuração.  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
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

 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração.  
  
> [!NOTE]
>  O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho. O endereço de ponto de extremidade do WCF Especifica um esquema FormatName e usa localhost para o computador local. O que segue o esquema é um endereço de fila corretamente formatado de acordo com o nome do formato de MSMQ diretrizes de endereçamento.  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  Este exemplo requer a instalação do [enfileiramento](http://go.microsoft.com/fwlink/?LinkId=95143).  
  
 Inicie o serviço e execute o cliente.  
  
 A saída a seguir é vista no cliente.  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 A saída a seguir deve ser vista no serviço.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ. Siga estas etapas para criar uma fila no Windows 2008.  
  
    1.  Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Expanda o **recursos** guia.  
  
    3.  Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.  
  
    4.  Verifique o **transacional** caixa.  
  
    5.  Digite `ServiceModelSamplesTransacted` como o nome da nova fila.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  Copie os arquivos de programa do serviço da pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.  
  
2.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
3.  No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".  
  
4.  No computador do serviço, inicie Service.exe em um prompt de comando.  
  
5.  No computador cliente, inicie o Client.exe em um prompt de comando.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>Consulte também  
 [Enfileiramento no WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Enfileiramento de mensagens](http://go.microsoft.com/fwlink/?LinkId=95143)

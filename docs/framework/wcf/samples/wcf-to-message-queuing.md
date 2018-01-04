---
title: Windows Communication Foundation para enfileiramento de mensagens
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90013752ed03f24c0995bc837efde5f20bf272c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation para enfileiramento de mensagens
Este exemplo demonstra como um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo pode enviar uma mensagem para um aplicativo de serviço de enfileiramento de mensagens (MSMQ). O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila. O serviço e o cliente não precisa estar em execução ao mesmo tempo.  
  
 O serviço recebe mensagens da fila e processa ordens. O serviço cria uma fila transacional e configura um manipulador de mensagem da mensagem recebida, conforme mostrado no código de exemplo a seguir.  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
```  
  
 Quando uma mensagem é recebida da fila, o manipulador de mensagens `ProcessOrder` é invocado.  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
```  
  
 O serviço extrai o `ProcessOrder` corpo da mensagem de que o MSMQ e processa o pedido.  
  
 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no exemplo de configuração.  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho.  
  
 O cliente cria uma ordem de compra e envia a ordem de compra dentro do escopo de uma transação, conforme mostrado no código de exemplo a seguir.  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 O cliente usa uma cliente personalizado na ordem para enviar a mensagem do MSMQ para a fila. Como o aplicativo que recebe e processa a mensagem é um aplicativo do MSMQ e não um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, não há nenhum contrato de serviço implícita entre os dois aplicativos. Portanto, não podemos criar um proxy usando a ferramenta Svcutil.exe neste cenário.  
  
 O cliente personalizado é essencialmente o mesmo para todos os [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos que usam o `MsmqIntegration` associação para enviar mensagens. Ao contrário de outros clientes, ele não inclui uma variedade de operações de serviço. É uma operação de enviar mensagem somente.  
  
```  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente. Você pode ver as mensagens de recebimento de serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente. Observe que como enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Por exemplo, executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receberia suas mensagens.  
  
> [!NOTE]
>  Este exemplo requer a instalação do enfileiramento de mensagens. Consulte as instruções de instalação em [enfileiramento](http://go.microsoft.com/fwlink/?LinkId=94968).  
  
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
  
3.  No arquivo Client.exe.config, altere o endereço de ponto de extremidade do cliente para especificar o nome do computador do serviço em vez de ".".  
  
4.  No computador do serviço, inicie Service.exe em um prompt de comando.  
  
5.  No computador cliente, inicie o Client.exe em um prompt de comando.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Consulte também  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Enfileiramento de mensagens](http://go.microsoft.com/fwlink/?LinkId=94968)

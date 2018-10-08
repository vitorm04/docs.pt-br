---
title: Enfileiramento de mensagens para o Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: cbbbab700a6602fa02160733c383a0fcaa84297b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850668"
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Enfileiramento de mensagens para o Windows Communication Foundation
Este exemplo demonstra como um aplicativo de enfileiramento de mensagens (MSMQ) pode enviar uma mensagem MSMQ a um serviço do Windows Communication Foundation (WCF). O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.  
  
 O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com as filas. Uma mensagem MSMQ não tem um cabeçalho de ação, portanto, não é possível mapear diferentes mensagens MSMQ para contratos de operação automaticamente. Portanto, pode haver apenas um contrato de operação. Se você quiser definir mais de um contrato de operação para o serviço, o aplicativo deve fornecer informações sobre qual cabeçalho da mensagem do MSMQ (por exemplo, o rótulo ou uma correlationID) pode ser usado para decidir qual contrato de operação para o qual expedir.
  
 A mensagem do MSMQ não contém informações sobre qual cabeçalhos são mapeados para os parâmetros diferentes do contrato da operação. O parâmetro é do tipo <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), que contém a mensagem MSMQ subjacente. O tipo "T" no <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) classe representa os dados que são serializados no corpo da mensagem MSMQ. Neste exemplo, o `PurchaseOrder` tipo é serializado no corpo da mensagem MSMQ.  
  
 O código de exemplo a seguir mostra o contrato de serviço do serviço de processamento de pedidos.  

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 O serviço é auto-hospedado. Ao usar o MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço verifica a existência da fila e cria-se necessário. O nome da fila é lido do arquivo de configuração.

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 O serviço cria e abre um <xref:System.ServiceModel.ServiceHost> para o `OrderProcessorService`, conforme mostrado no código de exemplo a seguir.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no seguinte exemplo de configuração.

> [!NOTE]
>  O nome da fila usa um ponto (.) para o computador local e os separadores de barra invertida em seu caminho. O endereço do ponto de extremidade WCF Especifica um esquema FormatName e usa localhost para o computador local. O endereço da fila de cada nome de formato de MSMQ diretrizes de endereçamento segue o esquema FormatName.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 O aplicativo cliente é um aplicativo de MSMQ que usa o <xref:System.Messaging.MessageQueue.Send%2A> método para enviar uma mensagem de durável e transacional para a fila, conforme mostrado no código de exemplo a seguir.

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente. Você pode ver as mensagens de recebimento do serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente. Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Por exemplo, executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receberia suas mensagens.

### <a name="to-setup-build-and-run-the-sample"></a>A configuração, compilação, e executar o exemplo

1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ. Siga estas etapas para criar uma fila no Windows 2008.

    1.  Abra o Gerenciador de servidores no Visual Studio 2012.

    2.  Expanda o **recursos** guia.

    3.  Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.

    4.  Verifique as **transacional** caixa.

    5.  Insira `ServiceModelSamplesTransacted` como o nome da nova fila.

3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Para executar o exemplo em uma configuração de computador único, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores

1.  Copie os arquivos de programa de serviço na pasta \service\bin\, sob a pasta de idioma específico, para o computador do serviço.

2.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.

3.  No arquivo Client.exe.config, altere o orderQueueName para especificar o nome do computador do serviço em vez de ".".

4.  No computador do serviço, inicie Service.exe em um prompt de comando.

5.  No computador cliente, inicie Client.exe em um prompt de comando.

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Consulte também  
 [Filas no WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Como trocar mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Enfileiramento de mensagens](https://go.microsoft.com/fwlink/?LinkId=94968)

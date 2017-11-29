---
title: "Associação transacionada do MSMQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 247627cdf52f7e08490cc95d88b4dd4ab539d97e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-msmq-binding"></a>Associação transacionada do MSMQ
Este exemplo demonstra como executar transacionada comunicação em fila usando o serviço de enfileiramento de mensagens (MSMQ).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 Quando transações são usadas para enviar e receber mensagens, há realmente duas transações separadas. Quando o cliente envia mensagens dentro do escopo de uma transação, a transação é local para o cliente e o Gerenciador de filas do cliente. Quando o serviço recebe mensagens dentro do escopo da transação, a transação é local para o serviço e o Gerenciador de fila de recebimento. É muito importante lembrar-se de que o cliente e o serviço não estão participando na mesma transação; em vez disso, eles estão usando transações diferentes ao executar as operações (como enviar e receber) com a fila.  
  
 Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação. As mensagens enviadas para a fila, em seguida, são recebidas pelo serviço de dentro do escopo de transação definido pelo serviço.  
  
 O contrato de serviço é `IOrderProcessor`, conforme mostrado no código de exemplo a seguir. A interface define um serviço unidirecional que é adequado para uso com filas.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 O comportamento de serviço define um comportamento de operação com `TransactionScopeRequired` definido como `true`. Isso garante que o mesmo escopo de transação que é usado para recuperar a mensagem da fila é usado por qualquer gerenciadores de recursos acessados pelo método. Ela também garante que, se o método gera uma exceção, a mensagem é retornada para a fila. Sem configurar esse comportamento de operação, um canal em fila cria uma transação para ler a mensagem da fila e confirma automaticamente antes de expedição, de modo que, se a operação falhar, a mensagem será perdida. O cenário mais comum é para operações de serviço para se inscrever na transação que é usada para ler a mensagem da fila, conforme demonstrado no código a seguir.  
  
```  
 // This service class that implements the service contract.  
 // This added code writes output to the console window.  
 public class OrderProcessorService : IOrderProcessor  
 {  
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
     public void SubmitPurchaseOrder(PurchaseOrder po)  
     {  
         Orders.Add(po);  
         Console.WriteLine("Processing {0} ", po);  
     }  
  …  
}  
```  
  
 O serviço é auto-hospedado. Ao usar o transporte MSMQ, a fila usada deve ser criada com antecedência. Isso pode ser feito manualmente ou por meio de código. Neste exemplo, o serviço contém código para verificar a existência da fila e criar a fila se ela não existe. O nome da fila é lida do arquivo de configuração. O endereço base é usado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar o proxy para o serviço.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get the MSMQ queue name from appSettings in configuration.  
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
  
        // Close the ServiceHost to shut down the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração, conforme mostrado no exemplo de configuração.  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  O nome da fila usa um ponto (.) para o computador local e separadores de barra invertida em seu caminho ao criar a fila usando <xref:System.Messaging>. O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ponto de extremidade usa o endereço da fila com o esquema NET. MSMQ, usa 'localhost' para denotar o computador local, e usa barras em seu caminho.  
  
 O cliente cria um escopo de transação. Comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica, onde todas as mensagens são enviadas para a fila ou nenhuma das mensagens são enviadas para a fila. A transação é confirmada chamando <xref:System.Transactions.TransactionScope.Complete%2A> no escopo de transação.  
  
```  
// Create a client.  
OrderProcessorClient client = new OrderProcessorClient();  
  
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
  
// Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Make a queued call to submit the purchase order.  
    client.SubmitPurchaseOrder(po);  
    // Complete the transaction.  
    scope.Complete();  
}  
  
// Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Para verificar se as transações estão funcionando, modificar o cliente, os comentários do escopo da transação, conforme mostrado no código de exemplo a seguir, recompile a solução e execute o cliente.  
  
```  
//scope.Complete();  
```  
  
 Porque a transação não for concluída, as mensagens não são enviadas para a fila.  
  
 Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente. Você pode ver as mensagens de recebimento de serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente. Observe que como enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Execute o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receber as mensagens.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
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
  
 Por padrão, com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada. Há duas propriedades relevantes para a segurança de transporte MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>. Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do Active Directory para o MSMQ deve ser instalada. Se você executar esse exemplo em um computador que não atendam a esses critérios, você receberá um erro.  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do Active Directory  
  
1.  Se o computador não faz parte de um domínio ou não tem integração do Active Directory instalada, desativar a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no código de configuração de exemplo a seguir.  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
                 behaviorConfiguration="OrderProcessorServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint. -->  
          <endpoint  
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderProcessorServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.  
  
    > [!NOTE]
    >  Configuração `security``mode` para `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, e `Message` segurança `None`.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a>Consulte também

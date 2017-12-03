---
title: Envio em lote transacionado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc04f0ce1d303a32cbf2232c76bfc4ef1143c9ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-batching"></a>Envio em lote transacionado
Este exemplo demonstra como lote transacionadas leituras usando o serviço de enfileiramento de mensagens (MSMQ). Envio em lote transacionado é um recurso de otimização de desempenho para leituras transacionadas na comunicação em fila.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 Este exemplo demonstra o lote transacionado. O lote transacionado é um comportamento que permite o uso de uma única transação ao ler muitas mensagens na fila e processá-las.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ. Siga estas etapas para criar uma fila no Windows 2008.  
  
    1.  Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Expanda o **recursos** guia.  
  
    3.  Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.  
  
    4.  Verifique o **transacional** caixa.  
  
    5.  Digite `ServiceModelSamplesTransacted` como o nome da nova fila.  
  
    > [!NOTE]
    >  Neste exemplo o cliente envia centenas de mensagens como parte do lote. É normal para o aplicativo de serviço para levar algum tempo para processar esses.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a>Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do active directory  
  
1.  Por padrão, com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada. Há duas propriedades relevantes para a segurança de transporte MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do active directory para o MSMQ deve ser instalada. Se você executar esse exemplo em um computador que não atendam a esses critérios, você receberá um erro.  
  
2.  Se o computador não faz parte de um domínio ou não tem integração do active directory instalada, desativar a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no exemplo de configuração:  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
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
  
    </system.serviceModel>  
    ```  
  
3.  Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.  
  
    > [!NOTE]
    >  Configuração `security``mode` para `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, e `Message` segurança `None`.  
  
4.  Para executar o banco de dados em um computador remoto, altere a cadeia de conexão para apontar para o computador no qual reside o banco de dados.  
  
## <a name="requirements"></a>Requisitos  
 Para executar este exemplo, o MSMQ deve estar instalado e SQL ou SQL Express é necessária.  
  
## <a name="demonstrates"></a>Demonstra  
 O exemplo demonstra o comportamento do lote transacionado. O lote transacionado é um recurso de otimização de desempenho fornecido com o MSMQ de transporte em fila.  
  
 Quando transações são usadas para enviar e receber mensagens, há realmente 2 separar transações. Quando o cliente envia mensagens dentro do escopo de uma transação, a transação é local para o cliente e o Gerenciador de filas do cliente. Quando o serviço recebe mensagens dentro do escopo da transação, a transação é local para o serviço e o Gerenciador de fila de recebimento. É muito importante lembrar-se de que o cliente e o serviço não estão participando na mesma transação; em vez disso, eles estão usando transações diferentes ao executar as operações (como enviar e receber) com a fila.  
  
 No exemplo, usamos uma única transação para a execução de várias operações de serviço. Isso é usado apenas como um recurso de otimização de desempenho e não afeta a semântica do aplicativo. O exemplo é baseado em [transacionado associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).  
  
## <a name="comments"></a>Comentários  
 Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação. Para mostrar a otimização de desempenho, podemos enviar um grande número de mensagens. Nesse caso, até 2500 mensagens.  
  
 As mensagens enviadas para a fila, em seguida, são recebidas pelo serviço de dentro do escopo de transação definido pelo serviço. Sem o envio em lote, isso resulta em transações 2500 para cada invocação da operação de serviço. Isso afeta o desempenho do sistema. Como dois gerenciadores de recursos são envolvidos - fila do MSMQ e `Orders` banco de dados-cada essa transação é uma transação de DTC. Isso é otimizar usando um muito menor número de transações, garantindo que um lote de mensagens e chamadas de operação de serviço ocorrem em uma única transação.  
  
 Podemos usar o recurso de envio em lote por:  
  
-   Especificar o comportamento do lote transacionado na configuração.  
  
-   Especificar um tamanho de lote em termos de número de mensagens a serem lidos usando uma única transação.  
  
-   Especifica o número máximo de lotes simultâneos para executar.  
  
 Neste exemplo, mostramos ganhos de desempenho, reduzindo o número de transações, garantindo que os 100 operações de serviço são chamadas em uma única transação antes de confirmar a transação.  
  
 O comportamento de serviço define um comportamento de operação com `TransactionScopeRequired` definido como `true`. Isso garante que o mesmo escopo de transação que é usado para recuperar a mensagem da fila é usado por qualquer gerenciadores de recursos acessados pelo método. Neste exemplo, usamos um banco de dados básico para armazenar as informações de ordem de compra contidas na mensagem. O escopo da transação também garante que, se o método gera uma exceção, a mensagem é retornada para a fila. Sem configurar esse comportamento de operação, um canal em fila cria uma transação para ler a mensagem da fila e é confirmada automaticamente antes que ele é enviado para que se a operação falhar, a mensagem será perdida. O cenário mais comum é para operações de serviço para se inscrever na transação que é usada para ler a mensagem da fila, conforme demonstrado no código a seguir.  
  
 Observe que `ReleaseServiceInstanceOnTransactionComplete` é definido como `false`. Esse é um requisito importante para envio em lote. A propriedade `ReleaseServiceInstanceOnTransactionComplete` em `ServiceBehaviorAttribute` indica o que fazer com a instância do serviço depois que a transação é concluída. Por padrão, a instância do serviço é liberada após a conclusão da transação. A proporção de núcleo para envio em lote é o uso de uma única transação para leitura e expedir muitas mensagens na fila. Liberar, portanto, a instância do serviço acaba de completar a transação prematuramente, eliminando o uso muito do envio em lote. Se essa propriedade é definida como `true` e o comportamento do lote transacionado é adicionado ao ponto de extremidade, o comportamento de validação de envio em lote gera uma exceção.  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 O `Orders` classe encapsula o processamento do pedido. No exemplo, ele atualiza o banco de dados com informações de ordem de compra.  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 O comportamento de envio em lote e suas configurações são especificadas na configuração do aplicativo de serviço.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  O tamanho do lote é uma dica para o sistema. Por exemplo, se você especificar um tamanho de lote de 20, em seguida, 20 mensagens seriam lido e distribuída usando uma única transação e, em seguida, a transação é confirmada. Mas há casos em que a transação pode confirmar o lote antes de atingir o tamanho do lote.  
>   
>  Associada a cada transação é um tempo limite que inicia o acionamento depois que a transação é criada. Quando esse tempo limite expira, a transação será anulada. É possível para esse tempo limite expirar antes mesmo que o tamanho do lote for atingido. Para evitar funcionando novamente o lote devido a anulação de `TransactedBatchingBehavior` verifica para ver quanto tempo é deixado na transação. Se a 80% do tempo limite de transação estiver cheio, em seguida, a transação será confirmada.  
>   
>  Se não existem mais mensagens na fila e, em vez de esperar o cumprimento do tamanho do lote a <xref:System.ServiceModel.Description.TransactedBatchingBehavior> confirma a transação.  
>   
>  A escolha do tamanho do lote é dependente de seu aplicativo. Se o tamanho do lote for muito pequeno, você não pode obter o desempenho desejado. Por outro lado se o tamanho do lote for muito grande, ele pode diminuir o desempenho. Por exemplo, a transação pode durar mais e mantenha os bloqueios em seu banco de dados ou a transação foi dead bloqueada, que poderia fazer com que o lote para obter revertida e o trabalho de restauração.  
  
 O cliente cria um escopo de transação. Comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica, onde todas as mensagens são enviadas para a fila ou nenhuma das mensagens são enviadas para a fila. A transação é confirmada chamando <xref:System.Transactions.TransactionScope.Complete%2A> no escopo de transação.  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
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
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 Quando você executar o exemplo, as atividades do cliente e de serviço são exibidas em janelas do console de serviço e o cliente. Você pode ver as mensagens de recebimento de serviço do cliente. Pressione ENTER em cada janela de console para desligar o serviço e o cliente. Observe que como enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo. Execute o cliente, desligá-lo e, em seguida, inicie o serviço e ainda receber suas mensagens. Você pode ver uma saída sem interrupção, como as mensagens são lidas em um lote e processadas.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a>Consulte também

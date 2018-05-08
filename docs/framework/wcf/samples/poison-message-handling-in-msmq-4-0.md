---
title: Tratamento de mensagens suspeitas no MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 25d99e6864b967b498fc53a6f6d78f476f4d938f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="poison-message-handling-in-msmq-40"></a>Tratamento de mensagens suspeitas no MSMQ 4.0
Este exemplo demonstra como executar manipulação em um serviço de mensagens suspeitas. Este exemplo se baseia o [transacionado associação de MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) exemplo. Este exemplo usa `netMsmqBinding`. O serviço é um aplicativo de console auto-hospedado para que você possa observar o serviço de recebimento de mensagens na fila.  
  
 Comunicação em fila, o cliente se comunica com o serviço usando uma fila. Mais precisamente, o cliente envia mensagens a uma fila. O serviço recebe mensagens da fila. O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.  
  
 Uma mensagem suspeita é uma mensagem que repetidamente ler de uma fila quando o serviço de ler a mensagem não é possível processar a mensagem e, portanto, encerra a transação sob a qual a mensagem é lida. Nesses casos, a mensagem é repetida novamente. Isso pode, teoricamente, vá para sempre se há um problema com a mensagem. Observe que isso só pode ocorrer ao usar transações para ler da fila e chamar a operação de serviço.  
  
 Com base na versão do MSMQ, NetMsmqBinding dá suporte à detecção limitada para detecção total de mensagens suspeitas. Depois que a mensagem foi detectada como adulterados, podem ser tratado de várias maneiras. Novamente, com base na versão do MSMQ, NetMsmqBinding dá suporte à manipulação limitada para tratamento de total de mensagens suspeitas.  
  
 Este exemplo ilustra as funcionalidades de suspeitas limitadas fornecidas em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] e [!INCLUDE[wxp](../../../../includes/wxp-md.md)] plataforma e as funcionalidades de completo suspeitas fornecidas em [!INCLUDE[wv](../../../../includes/wv-md.md)]. Em ambos os exemplos, o objetivo é mover a mensagem suspeita a da fila para outra fila que pode ser atendida por um serviço de mensagens suspeitas.  
  
## <a name="msmq-v40-poison-handling-sample"></a>MSMQ v 4.0 suspeitas exemplo de tratamento  
 Em [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ fornece um recurso de fila de subseção suspeita que pode ser usado para armazenar mensagens suspeitas. Este exemplo demonstra a prática recomendada de lidar com mensagens suspeitas usando [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 A detecção de mensagens suspeitas em [!INCLUDE[wv](../../../../includes/wv-md.md)] é bastante sofisticado. Há 3 propriedades que ajudam a detecção. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é expedida para o aplicativo para processamento e número de vezes que uma determinada mensagem é novamente leitura da fila. Uma mensagem é lida novamente na fila quando ela é colocada de volta na fila porque a mensagem não pode ser distribuída para o aplicativo ou o aplicativo reverterá a transação na operação de serviço. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> é o número de vezes que a mensagem será movida para a fila de repetição. Quando <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é atingido, a mensagem será movida para a fila de repetição. A propriedade <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> é o atraso de tempo após o qual a mensagem é movida da fila de repetição para a fila principal. O <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> é redefinido para 0. A mensagem é tentada novamente. Se todas as tentativas de ler a mensagem de falha, a mensagem é marcada como adulterados.  
  
 Depois que a mensagem é marcada como adulterados, a mensagem é tratada de acordo com as configurações de <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeração. Para repetir os valores possíveis:  
  
-   Falha (padrão): A falha do ouvinte e também o host de serviço.  
  
-   Soltar: Para remover a mensagem.  
  
-   Mover: Mover a mensagem para a fila de mensagens suspeitas sub. Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   Rejeitar: Para rejeitar a mensagem, enviar a mensagem de volta ao remetente de mensagens mortas fila. Esse valor só está disponível na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 O exemplo demonstra como usar o `Move` disposição para a mensagem suspeita. `Move` faz com que a mensagem Mover para a fila sub suspeita.  
  
 O contrato de serviço é `IOrderProcessor`, que define um serviço unidirecional que é adequado para uso com filas.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 A operação de serviço exibe uma mensagem informando que a ordem de processamento. Para demonstrar a funcionalidade de mensagens suspeitas, o `SubmitPurchaseOrder` operação de serviço gera uma exceção ao reverter a transação em uma invocação aleatória do serviço. Isso faz com que a mensagem a ser colocado de volta na fila. Eventualmente, a mensagem é marcada como suspeitas. A configuração é definida para mover a mensagem suspeita para a fila de subseção suspeita.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
public class OrderProcessorService : IOrderProcessor  
{  
    static Random r = new Random(137);  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
  
        int randomNumber = r.Next(10);  
  
        if (randomNumber % 2 == 0)  
        {  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
        else  
        {  
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);  
            Console.WriteLine();  
            throw new Exception("Cannot process purchase order: " + po.PONumber);  
        }  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted");  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Get MSMQ queue name from app settings in configuration.  
        string queueName = ConfigurationManager.AppSettings["queueName"];  
  
        // Create the transacted MSMQ queue if necessary.  
        if (!System.Messaging.MessageQueue.Exists(queueName))  
            System.Messaging.MessageQueue.Create(queueName, true);  
  
        // Get the base address that is used to listen for WS-MetaDataExchange requests.  
        // This is useful to generate a proxy for the client.  
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        if(serviceHost.State != CommunicationState.Faulted) {  
            serviceHost.Close();  
        }  
  
    }  
}  
```

 A configuração de serviço inclui as seguintes propriedades de mensagem suspeita: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, e `receiveErrorHandling` conforme mostrado no seguinte arquivo de configuração.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />  
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>  
  </appSettings>  
  <system.serviceModel>  
    <services>  
      <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="PoisonBinding"   
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  
    <bindings>  
      <netMsmqBinding>  
        <binding name="PoisonBinding"   
                 receiveRetryCount="0"  
                 maxRetryCycles="1"  
                 retryCycleDelay="00:00:05"                        
                 receiveErrorHandling="Move">  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="processing-messages-from-the-poison-message-queue"></a>Processamento de mensagens da fila de mensagens suspeitas  
 O serviço de mensagens suspeitas lê mensagens da fila de mensagens suspeitas final e processá-las.  
  
 Mensagens na fila de mensagens suspeitas são mensagens que são endereçadas para o serviço que está processando a mensagem, o que pode ser diferente do ponto de extremidade de serviço de mensagens suspeitas. Portanto, quando o serviço de mensagens suspeitas lê mensagens da fila, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] camada do canal localiza a incompatibilidade nos pontos de extremidade e não enviar a mensagem. Nesse caso, a mensagem é endereçada ao serviço de processamento de pedidos, mas está sendo recebida pelo serviço de mensagens suspeitas. Para continuar a receber a mensagem, mesmo se a mensagem é resolvida para um ponto de extremidade diferente, devemos adicionar um `ServiceBehavior` para endereços de filtro em que o critério de correspondência é para corresponder a qualquer ponto de extremidade de serviço a mensagem está endereçada. Isso é necessário para processar mensagens ler da fila de mensagens suspeitas.  
  
 A implementação do serviço de mensagens suspeitas em si é muito semelhante para a implementação do serviço. Ele implementa o contrato e processa os pedidos. O exemplo de código é o seguinte.  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
  
    public static void OnServiceFaulted(object sender, EventArgs e)   
    {  
        Console.WriteLine("Service Faulted...exiting app");  
        Environment.Exit(1);  
    }  
  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
  
        // Create a ServiceHost for the OrderProcessorService type.  
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));  
  
        // Hook on to the service host faulted events.  
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);  
  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The poison message service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHostBase to shutdown the service.  
        if(serviceHost.State != CommunicationState.Faulted)  
        {  
            serviceHost.Close();  
        }  
    }  
```

 Ao contrário do serviço que lê mensagens da fila de ordem de processamento de pedidos, o serviço de mensagens suspeitas lê mensagens da fila sub suspeita. A fila de suspeita é uma subtipo fila da fila principal, chamada "suspeitas" e é automaticamente gerada pelo MSMQ. Para acessá-lo, forneça o nome de fila principal, seguido por um ";" e o subtipo nome da fila, nesse caso-"suspeita", conforme mostrado no exemplo de configuração.  
  
> [!NOTE]
>  No exemplo de v 3.0 do MSMQ, o nome da fila suspeita não é uma fila sub, em vez disso, a fila que mudamos a mensagem.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >  
        </endpoint>  
      </service>  
    </services>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 Quando você executar o exemplo, o cliente, serviço e atividades de serviço de mensagens suspeitas são exibidas em janelas do console. Você pode ver as mensagens de recebimento de serviço do cliente. Pressione ENTER em cada janela de console para interromper os serviços.  
  
 O serviço é iniciado em execução, o processamento de pedidos e inicia aleatoriamente encerrar o processamento. Se a mensagem indicar que ele processou a ordem, você pode executar o cliente novamente para enviar outra mensagem até que você veja que o serviço foi finalizado, na verdade, uma mensagem. Com base nas configurações de suspeitas configuradas, a mensagem a tentativa de uma vez para o processamento antes de movê-lo para a fila de suspeita final.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
```  
  
 Inicie o serviço de mensagens suspeitas para ler a mensagem inviabilizada da fila de suspeitas. Neste exemplo, o serviço de mensagens suspeitas lê a mensagem e processa-os. Você pode ver que a ordem de compra que foi encerrada e adulterada é lido pelo serviço de mensagens suspeitas.  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente. Se a fila não estiver presente, o serviço criará um. Você pode executar o serviço primeiro para criar a fila, ou você pode criar um por meio do Gerenciador de fila do MSMQ. Siga estas etapas para criar uma fila no Windows 2008.  
  
    1.  Abra o Gerenciador do servidor em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
    2.  Expanda o **recursos** guia.  
  
    3.  Clique com botão direito **filas de mensagens privadas**e selecione **novo**, **fila particular**.  
  
    4.  Verifique o **transacional** caixa.  
  
    5.  Digite `ServiceModelSamplesTransacted` como o nome da nova fila.  
  
3.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, alterar os nomes de fila para refletir o nome de host real em vez de localhost e siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
 Por padrão, com o `netMsmqBinding` transporte de associação de segurança está habilitada. Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinar o tipo de segurança de transporte. Por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio. Se você executar esse exemplo em um computador que não faz parte de um domínio, você receberá o seguinte erro: "Mensagem interna do usuário certificado do enfileiramento de mensagens não existe".  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar o exemplo em um computador associado a um grupo de trabalho  
  
1.  Se seu computador não fizer parte de um domínio, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no exemplo de configuração:  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     Certifique-se de que o ponto de extremidade está associado com a associação, definindo o atributo de bindingConfiguration do ponto de extremidade.  
  
2.  Certifique-se de que você altera a configuração no PoisonMessageServer, o cliente e servidor antes de executar o exemplo.  
  
    > [!NOTE]
    >  Configuração `security mode` para `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel`, e `Message` segurança `None`.  
  
3.  Em ordem para troca de dados de metadados trabalhar, é registrar uma URL com associação http. Isso requer que o serviço é executado em uma janela de comando com privilégios elevados. Caso contrário, você receberá uma exceção, como: exceção sem tratamento: System.ServiceModel.AddressAccessDeniedException: HTTP não pôde registrar a URL http://+:8000/ServiceModelSamples/service/. O processo não tem direitos de acesso a este namespace (consulte http://go.microsoft.com/fwlink/?LinkId=70353 para obter detalhes). ---> System.NET. HttpListenerException: acesso negado.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a>Consulte também

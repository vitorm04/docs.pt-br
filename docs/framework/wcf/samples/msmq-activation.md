---
title: Ativação de MSMQ
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 0b3d90ed756b2bb2b9bebc0ac9e36789a80df1d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745435"
---
# <a name="msmq-activation"></a>Ativação de MSMQ
Este exemplo demonstra como hospedar aplicativos no serviço de ativação de processos para Windows (WAS) que são lidos a partir de uma fila de mensagens. Este exemplo usa o `netMsmqBinding` e se baseia o [comunicação bidirecional](../../../../docs/framework/wcf/samples/two-way-communication.md) exemplo. Nesse caso, o serviço é um aplicativo hospedado na Web e o cliente é auto-hospedado e gera como saída para o console para observar o status das ordens de compra enviado.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
> [!NOTE]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os WCF e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows processo de ativação do WAS (serviço), o novo mecanismo de ativação de processo para [!INCLUDE[lserver](../../../../includes/lserver-md.md)], fornece recursos semelhantes de IIS que estavam disponíveis somente para aplicativos baseados em HTTP para aplicativos que usam protocolos não HTTP. Windows Communication Foundation (WCF) usa a interface do adaptador de escuta para comunicar as solicitações de ativação recebidas pelos protocolos não HTTP com suporte do WCF, como TCP, Pipes nomeados e MSMQ. A funcionalidade para o recebimento de solicitações por meio de protocolos não HTTP é hospedada por serviços gerenciados do Windows em execução no SMSvcHost.exe.  
  
 O serviço de adaptador de escuta NET. MSMQ (NetMsmqActivator) ativa na fila de aplicativos com base em mensagens na fila.  
  
 O cliente envia ordens de compra para o serviço de dentro do escopo de uma transação. O serviço recebe os pedidos em uma transação e o processa. O serviço, em seguida, chama de volta o cliente com o status do pedido. Para facilitar a comunicação bidirecional o cliente e o serviço usam filas para enfileirar as ordens de compra e o status do pedido.  
  
 O contrato de serviço `IOrderProcessor` define as operações de serviço unidirecional que funcionam com o enfileiramento de mensagens. A operação de serviço usa o ponto de extremidade de resposta para enviar o status da ordem para o cliente. Endereço do ponto de extremidade de resposta é o URI da fila usado para enviar o status do pedido para o cliente. Aplicativo de processamento de pedidos implementa esse contrato.  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 O contrato de resposta para enviar o status do pedido é especificado pelo cliente. O cliente implementa o contrato de status do pedido. O serviço usa o cliente gerado deste contrato para enviar o status da ordem de volta ao cliente.  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 A operação de serviço processa a ordem de compra enviado. O <xref:System.ServiceModel.OperationBehaviorAttribute> é aplicada à operação de serviço para especificar a inscrição automática na transação que é usada para receber a mensagem da fila e o preenchimento automático da transação após a conclusão da operação de serviço. O `Orders` classe encapsula a funcionalidade de ordem de processamento. Nesse caso, ele adiciona a ordem de compra em um dicionário. A transação que a operação de serviço inscrita em está disponível para operações no `Orders` classe.  
  
 A operação de serviço, além de processamento de ordem de compra enviado, respostas de volta para o cliente sobre o status do pedido.  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }
}
```  
  
 O cliente de associação a ser usado é especificado usando um arquivo de configuração.  
  
 O nome da fila MSMQ é especificado em uma seção appSettings do arquivo de configuração. O ponto de extremidade para o serviço é definido na seção System. ServiceModel do arquivo de configuração.  
  
> [!NOTE]
>  O endereço de ponto de extremidade e o nome da fila MSMQ usar convenções de endereçamento ligeiramente diferentes. O nome da fila MSMQ usa um ponto (.) para o computador local e os separadores de barra invertida em seu caminho. O endereço do ponto de extremidade WCF Especifica um NET. MSMQ: esquema, usa "localhost" para o computador local e usa barras "/" em seu caminho. Para ler de uma fila que está hospedada no computador remoto, substitua o "." e "localhost" para o nome do computador remoto.  
  
 Um arquivo. svc com o nome da classe é usado para hospedar o código de serviço no WAS.  
  
 O próprio arquivo SVC contém uma diretiva para criar o `OrderProcessorService`.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 O arquivo Service SVC também contém uma diretiva de assembly para garantir que Transactions é carregado.  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 O cliente cria um escopo de transação. A comunicação com o serviço ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica em que todas as mensagens de êxito ou falha. A transação é confirmada chamando `Complete` no escopo da transação.  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
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
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
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
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 A fila de status do pedido é criada no `Main` método. A configuração do cliente inclui a configuração de serviço de status do pedido para hospedar o serviço de status do pedido, conforme mostrado no seguinte exemplo de configuração.  
  
```xml  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas no servidor e cliente windows do console. Você pode ver o servidor receber mensagens do cliente. Pressione ENTER em cada janela de console para desligar o servidor e cliente.  
  
 O cliente exibe as informações de status do pedido enviadas pelo servidor:  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que [!INCLUDE[iisver](../../../../includes/iisver-md.md)] estiver instalado, pois ele é necessário para a ativação do WAS.  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md). Além disso, você deve instalar os componentes de ativação não HTTP do WCF:  
  
    1.  No menu **Iniciar**, selecione **Painel de Controle**.  
  
    2.  Selecione **programas e recursos**.  
  
    3.  Clique em **ativar ou desativar recursos do Windows**.  
  
    4.  Sob **resumo de recursos**, clique em **adicionar recursos**.  
  
    5.  Expanda o **Microsoft .NET Framework 3.0** nó e verifique se o **ativação não HTTP do Windows Communication Foundation** recurso.  
  
3.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Execute o cliente executando client.exe em uma janela de comando. Isso cria a fila e envia uma mensagem a ele. Sair do cliente em execução para ver o resultado do serviço de ler a mensagem  
  
5.  O serviço de ativação MSMQ é executado como serviço de rede por padrão. Portanto, a fila que é usada para ativar o aplicativo deve ter receber e inspecionar permissões para serviço de rede. Isso pode ser adicionado usando o MMC de enfileiramento de mensagens:  
  
    1.  Do **inicie** menu, clique em **executar**, em seguida, digite `Compmgmt.msc` e pressione ENTER.  
  
    2.  Sob **aplicativos e serviços**, expanda **enfileiramento**.  
  
    3.  Clique em **privativas**.  
  
    4.  A fila (servicemodelsamples/Service.svc) com o botão direito e escolha **propriedades**.  
  
    5.  Sobre o **segurança** , clique em **Add** e dar a inspeção e receber permissões para serviço de rede.  
  
6.  Configure o Windows processo Activation Service (WAS) para dar suporte à ativação de MSMQ.  
  
     Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado AddMsmqSiteBinding.cmd localizado no diretório de exemplo.  
  
    1.  Para dar suporte à ativação de NET. MSMQ, site da Web padrão primeiro deve ser associado ao protocolo NET. MSMQ. Isso pode ser feito usando appcmd.exe, que é instalado com o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] conjunto de ferramentas de gerenciamento. Em um prompt de comando com privilégios elevados (administrador), execute o comando a seguir.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
         Este comando adiciona uma associação de site do NET. MSMQ ao site da Web padrão.  
  
    2.  Embora todos os aplicativos dentro de um site compartilham uma associação de NET. MSMQ comuns, cada aplicativo pode habilitar o suporte do NET. MSMQ individualmente. Para habilitar o NET. MSMQ para o aplicativo /servicemodelsamples, execute o seguinte comando em um prompt de comando elevado.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
         Este comando habilita o aplicativo /servicemodelsamples sejam acessados usando `http://localhost/servicemodelsamples` e `net.msmq://localhost/servicemodelsamples`.
  
7.  Se você ainda não feito isso anteriormente, certifique-se de que o serviço de ativação MSMQ está habilitado. Do **inicie** menu, clique em **execute**e o tipo `Services.msc`. Pesquise a lista de serviços para o **adaptador de escuta NET. MSMQ**. Clique com botão direito e selecione **propriedades**. Defina a **tipo de inicialização** para **automáticas**, clique em **aplicar** e clique no **iniciar** botão. Esta etapa deve ser feita apenas uma vez antes do primeiro uso do serviço de adaptador de escuta NET. MSMQ.  
  
8.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Além disso, altere o código no cliente que envia a ordem de compra para refletir o nome do computador no URI da fila ao enviar o pedido de compra. Use o código a seguir:  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. Remova a associação de site do NET. MSMQ que você adicionou para este exemplo.  
  
     Como uma conveniência, as etapas a seguir são implementadas em um arquivo em lotes chamado RemoveMsmqSiteBinding.cmd localizado no diretório de exemplo:  
  
    1.  Remova o NET. MSMQ da lista de protocolos habilitados, executando o seguinte comando em um prompt de comando elevado.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
    2.  Remova a associação de site do NET. MSMQ, executando o seguinte comando em um prompt de comando elevado.  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
    > [!WARNING]
    >  Executar o arquivo em lotes redefinirá o DefaultAppPool para ser executado usando o .NET Framework versão 2.0.  
  
 Por padrão com o `netMsmqBinding` transporte de associação de segurança está habilitada. Duas propriedades, `MsmqAuthenticationMode` e `MsmqProtectionLevel`, juntos determinam o tipo de segurança de transporte. Por padrão, o modo de autenticação está definido como `Windows` e o nível de proteção é definido como `Sign`. Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio. Se você executar esse exemplo em um computador que não faz parte de um domínio, o seguinte erro foi recebido: "Mensagem do usuário interna certificado do enfileiramento de mensagens não existe".  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>Para executar o exemplo em um computador associado a um grupo de trabalho  
  
1.  Se o computador não fizer parte de um domínio, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação como none, conforme mostrado no seguinte exemplo de configuração.  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  Altere a configuração no servidor e o cliente antes de executar o exemplo.  
  
    > [!NOTE]
    >  Definindo `security mode` à `None` é equivalente à configuração `MsmqAuthenticationMode`, `MsmqProtectionLevel` e `Message` security `None`.  
  
3.  Para habilitar a ativação em um computador associado a um grupo de trabalho, o serviço de ativação e o processo de trabalho devem ser executados com uma conta de usuário específica (deve ser o mesmo para ambos) e a fila deve ter as ACLs para a conta de usuário específico.  
  
     Para alterar a identidade que o processo de trabalho é executado:  
  
    1.  Run Inetmgr.exe.  
  
    2.  Sob **Pools de aplicativos**, clique com botão direito do **AppPool** (normalmente **DefaultAppPool**) e escolha **definir padrões do Pool de aplicativos...** .  
  
    3.  Altere as propriedades de identidade para usar a conta de usuário específico.  
  
     Para alterar a identidade que o serviço de ativação é executado:  
  
    1.  Execute Services. msc.  
  
    2.  Clique com botão direito do **Net.MsmqListener adaptador**e escolha **propriedades**.  
  
4.  Alterar a conta de **LogOn** guia.  
  
5.  No grupo de trabalho, o serviço também deve executar usando um token sem restrições. Para fazer isso, execute o seguinte em uma janela de comando:  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)

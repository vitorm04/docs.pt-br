---
title: "Transporte: transações personalizadas através de exemplo de UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e26d0c25879b3b1b6ed873543f051de989ddd92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transporte: transações personalizadas através de exemplo de UDP
Este exemplo se baseia o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [extensibilidade de transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md). Ele estende o exemplo de transporte UDP para oferecer suporte ao fluxo de transação personalizado e demonstra o uso de <xref:System.ServiceModel.Channels.TransactionMessageProperty> propriedade.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Alterações de código no exemplo de transporte UDP  
 Para demonstrar o fluxo de transações, o exemplo altera o contrato de serviço para `ICalculatorContract` para exigir um escopo de transação para `CalculatorService.Add()`. O exemplo também adiciona um extra `System.Guid` parâmetro para o contrato do `Add` operação. Esse parâmetro é usado para passar o identificador da transação do cliente para o serviço.  
  
```  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);              
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 O [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo usa pacotes UDP para passar mensagens entre um cliente e um serviço. O [transporte: exemplo de transporte personalizado](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) usa o mesmo mecanismo de transporte de mensagens, mas quando o fluxo de uma transação, é inserido no pacote UDP junto com a mensagem codificada.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém a nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.  
  
 Para o transporte de fluxo de transação personalizado, a implementação de cliente precisa saber quais operações de serviço requerem o fluxo de transações e passar essas informações para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Deve haver também um mecanismo para transmitir a transação do usuário para a camada de transporte. Este exemplo usa "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inspetores de mensagem" para obter essas informações. O Inspetor de mensagens do cliente implementado aqui, que é chamado de `TransactionFlowInspector`, executa as seguintes tarefas:  
  
-   Determina se uma transação deve fluir para uma ação de mensagem determinada (Isso ocorre `IsTxFlowRequiredForThisOperation()`).  
  
-   Anexa a transação de ambiente atual para a mensagem usando `TransactionFlowProperty`, se uma transação é necessária para fluir (Isso é feito no `BeforeSendRequest()`).  
  
```  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;             
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;              
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 O `TransactionFlowInspector` em si é passado para o framework usando um comportamento personalizado: o `TransactionFlowBehavior`.  
  
```  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 Com o mecanismo anterior em vigor, o código de usuário cria um `TransactionScope` antes de chamar a operação de serviço. O Inspetor de mensagem garante que a transação é passada para o transporte, caso seja necessária para fluir para a operação de serviço.  
  
```  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());               
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }               
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 Ao receber um pacote UDP do cliente, o serviço desserializa-o para extrair a mensagem e, possivelmente, uma transação.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que reverte o processo de serialização executado pelo `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Se uma transação foi recebida no fluxo, ele é adicionado para a mensagem de `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Isso garante que o dispatcher pega a transação em tempo de expedição e utiliza ao chamar a operação de serviço resolvida pela mensagem.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  O exemplo atual deve ser executado da mesma forma que o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo. Para executá-lo, inicie o serviço com UdpTestService.exe. Se você estiver executando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve iniciar o serviço com privilégios elevados. Para fazer isso, clique com botão direito UdpTestService.exe em [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e clique em **executar como administrador**.  
  
3.  Isso produz a saída a seguir.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  Neste momento, você pode iniciar o cliente executando UdpTestClient.exe. A saída produzida pelo cliente é da seguinte maneira.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  A saída do serviço é da seguinte maneira.  
  
    ```  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6.  O aplicativo de serviço exibe a mensagem `The client transaction has flowed to the service` se ela pode corresponder ao identificador de transação enviado pelo cliente, no `clientTransactionId` parâmetro o `CalculatorService.Add()` operação, como o identificador da transação de serviço. Uma correspondência é obtida somente se a transação de cliente passou para o serviço.  
  
7.  Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e, em seguida, execute novamente o cliente de teste. Você verá a seguinte saída no serviço.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  Executando o cliente em relação ao serviço agora produz saída semelhante como antes.  
  
9. Para gerar novamente o código de cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e, em seguida, execute o seguinte comando Svcutil.exe do diretório raiz do exemplo.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Observe que o Svcutil.exe não gerar a configuração de extensão de associação para o `sampleProfileUdpBinding`; você deve adicioná-lo manualmente.  
  
    ```xml  
    <configuration>  
        <system.serviceModel>      
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Consulte também  
 [Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)

---
title: 'Transporte: Transações personalizadas sobre o exemplo de UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: aeab56c122cff4c8a1ee87cb067f03ee0c2f3227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044696"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transporte: Transações personalizadas sobre o exemplo de UDP
Este exemplo é baseado no [transporte: Exemplo](../../../../docs/framework/wcf/samples/transport-udp.md) de UDP na[extensibilidade de transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md)do Windows Communication Foundation (WCF). Ele estende o exemplo de transporte UDP para dar suporte ao fluxo de transações personalizadas e demonstra <xref:System.ServiceModel.Channels.TransactionMessageProperty> o uso da propriedade.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Alterações de código no exemplo de transporte UDP  
 Para demonstrar o fluxo de transações, o exemplo altera o contrato `ICalculatorContract` de serviço para para exigir um `CalculatorService.Add()`escopo de transação para. O exemplo também adiciona um parâmetro `System.Guid` extra ao contrato `Add` da operação. Esse parâmetro é usado para passar o identificador da transação do cliente para o serviço.  
  
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
  
 O [transporte: O](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo de UDP usa pacotes UDP para passar mensagens entre um cliente e um serviço. O [transporte: O exemplo](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) de transporte personalizado usa o mesmo mecanismo para transportar mensagens, mas quando uma transação flui, ela é inserida no pacote UDP junto com a mensagem codificada.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.  
  
 Para o transporte de fluxo de transações personalizado, a implementação do cliente deve saber quais operações de serviço exigem o fluxo de transações e passar essas informações para o WCF. Também deve haver um mecanismo para transmitir a transação do usuário para a camada de transporte. Este exemplo usa "inspetores de mensagem do WCF" para obter essas informações. O Inspetor de mensagem do cliente implementado aqui, que `TransactionFlowInspector`é chamado, executa as seguintes tarefas:  
  
- Determina se uma transação deve ser fluída para uma determinada ação de mensagem (isso ocorre em `IsTxFlowRequiredForThisOperation()`).  
  
- Anexa a transação de ambiente atual à mensagem usando `TransactionFlowProperty`, se uma transação for necessária para fluir (isso é feito em `BeforeSendRequest()`).  
  
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
  
 O `TransactionFlowInspector` próprio é passado para a estrutura usando um comportamento personalizado: o `TransactionFlowBehavior`.  
  
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
  
 Com o mecanismo anterior em vigor, o código do usuário cria `TransactionScope` um antes de chamar a operação de serviço. O Inspetor de mensagem garante que a transação seja passada para o transporte, caso seja necessário fluir para a operação de serviço.  
  
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
  
 Após receber um pacote UDP do cliente, o serviço o desserializa para extrair a mensagem e possivelmente uma transação.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que reverte o processo de serialização executado pelo `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Se uma transação tiver sido transformada em fluxo, ela será anexada à mensagem `TransactionMessageProperty`no.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Isso garante que o Dispatcher pegue a transação no momento da expedição e a use ao chamar a operação de serviço endereçada pela mensagem.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. O exemplo atual deve ser executado de forma semelhante [ao transporte: Exemplo](../../../../docs/framework/wcf/samples/transport-udp.md) de UDP. Para executá-lo, inicie o serviço com UdpTestService. exe. Se você estiver executando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]o, deverá iniciar o serviço com privilégios elevados. Para fazer isso, clique com o botão direito do mouse em UdpTestService. exe no explorador de arquivos e clique em **Executar como administrador**.  
  
3. Isso produz a saída a seguir.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. Neste momento, você pode iniciar o cliente executando UdpTestClient. exe. A saída produzida pelo cliente é a seguinte.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. A saída do serviço é a seguinte:  
  
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
  
6. O aplicativo de serviço exibirá `The client transaction has flowed to the service` a mensagem se ele puder corresponder ao identificador de transação enviado pelo cliente, `clientTransactionId` no parâmetro da `CalculatorService.Add()` operação, para o identificador da transação de serviço. Uma correspondência será obtida somente se a transação do cliente tiver fluído para o serviço.  
  
7. Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e execute o cliente de teste novamente. Você deverá ver a seguinte saída no serviço.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Executar o cliente em relação ao serviço agora produz uma saída semelhante como antes.  
  
9. Para regenerar o código do cliente e a configuração usando svcutil. exe, inicie o aplicativo de serviço e execute o comando svcutil. exe a seguir do diretório raiz do exemplo.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Observe que svcutil. exe não gera a configuração de extensão de associação para `sampleProfileUdpBinding`o; você deve adicioná-lo manualmente.  
  
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
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Consulte também

- [Porta UDP](../../../../docs/framework/wcf/samples/transport-udp.md)

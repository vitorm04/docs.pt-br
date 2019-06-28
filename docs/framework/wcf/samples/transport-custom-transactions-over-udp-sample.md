---
title: 'Transporte: Transações personalizadas através de exemplo de UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ec6499a8e69c8512c33297ac4477eaafc397d78f
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425520"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transporte: Transações personalizadas através de exemplo de UDP
Este exemplo se baseia o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) amostra no Windows Communication Foundation (WCF)[extensibilidade de transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md). Ele estende o exemplo de transporte UDP para dar suporte a fluxo de transação personalizada e demonstra o uso do <xref:System.ServiceModel.Channels.TransactionMessageProperty> propriedade.  
  
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
  
 O [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo usa pacotes UDP para passar mensagens entre um cliente e um serviço. O [transporte: Amostra de transporte personalizado](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) usa o mesmo mecanismo de transporte de mensagens, mas quando uma transação é colocada em fluxo, ele é inserido no pacote UDP juntamente com a mensagem codificada.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` é um método auxiliar que contém a nova funcionalidade para mesclar o token de propagação da transação atual com a entidade de mensagens e colocá-lo em um buffer.  
  
 Para o transporte de fluxo de transação personalizada, a implementação do cliente deve saber quais operações de serviço exigem o fluxo de transações e passar essas informações para o WCF. Também deve haver um mecanismo para transmitir a transação do usuário para a camada de transporte. Este exemplo usa "Inspetores de mensagem do WCF" para obter essas informações. O Inspetor de mensagens do cliente implementado aqui, que é chamado `TransactionFlowInspector`, executa as seguintes tarefas:  
  
- Determina se uma transação deve fluir para uma ação de mensagem determinada (Isso ocorre em `IsTxFlowRequiredForThisOperation()`).  
  
- Anexa a transação de ambiente atual para a mensagem usando `TransactionFlowProperty`, se uma transação é necessária para ser colocada em fluxo (Isso é feito no `BeforeSendRequest()`).  
  
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
  
 O `TransactionFlowInspector` em si é passada para o framework usando um comportamento personalizado: o `TransactionFlowBehavior`.  
  
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
  
 Com o mecanismo anterior em vigor, o código do usuário cria um `TransactionScope` antes de chamar a operação de serviço. O Inspetor de mensagens garante que a transação é passada para o transporte, caso seja necessária para fluir para a operação de serviço.  
  
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
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` é o método auxiliar que reverte o processo de serialização executado pelo `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Se uma transação foi colocada em fluxo no, ele é acrescentado à mensagem no `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Isso garante que o dispatcher pega a transação em tempo de expedição e usa-o ao chamar a operação de serviço resolvida com a mensagem.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. A amostra atual deve ser executada da mesma forma que o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo. Para executá-lo, inicie o serviço com UdpTestService.exe. Se você estiver executando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve iniciar o serviço com privilégios elevados. Para fazer isso, clique com botão direito UdpTestService.exe no Explorador de arquivos e clique em **executar como administrador**.  
  
3. Isso produz a saída a seguir.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. Neste momento, você pode iniciar o cliente executando UdpTestClient.exe. A saída produzida pelo cliente é da seguinte maneira.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. A saída do serviço é da seguinte maneira.  
  
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
  
6. O aplicativo de serviço exibe a mensagem `The client transaction has flowed to the service` se ele pode corresponder ao identificador de transação enviado pelo cliente, além de `clientTransactionId` parâmetro do `CalculatorService.Add()` operação, como o identificador da transação de serviço. Uma correspondência é obtida somente se a transação do cliente tem fluir para o serviço.  
  
7. Para executar o aplicativo cliente para pontos de extremidade publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e, em seguida, execute novamente o cliente de teste. Você deve ver a saída a seguir no serviço.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Executando o cliente no serviço agora produz saída semelhante como antes.  
  
9. Para regenerar o código do cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e, em seguida, execute o seguinte comando de Svcutil.exe do diretório raiz do exemplo.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Observe que Svcutil.exe não gerar a configuração de extensão de associação para o `sampleProfileUdpBinding`; você deve adicioná-lo manualmente.  
  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Consulte também

- [Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)

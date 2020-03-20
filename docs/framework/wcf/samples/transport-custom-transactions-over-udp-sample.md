---
title: 'Transporte: transações personalizadas através de exemplo de UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ba9fb91623606d3aaba5ba56784b20bb92d343a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143792"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transporte: transações personalizadas através de exemplo de UDP
Esta amostra é baseada na amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) na[Extensibilidade de Transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md)da Windows Communication Foundation (WCF). Ele estende a amostra udp transport para suportar o <xref:System.ServiceModel.Channels.TransactionMessageProperty> fluxo de transações personalizadas e demonstra o uso da propriedade.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Alterações de código na amostra de transporte UDP  
 Para demonstrar o fluxo de transação, a amostra altera o contrato de serviço para `ICalculatorContract` exigir um escopo de transação para `CalculatorService.Add()`. A amostra também `System.Guid` adiciona um parâmetro extra `Add` ao contrato da operação. Este parâmetro é usado para passar o identificador da transação do cliente para o serviço.  
  
```csharp  
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
  
 A [amostra Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) usa pacotes UDP para passar mensagens entre um cliente e um serviço. A [Amostra de Transporte Personalizado](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) usa o mesmo mecanismo para transportar mensagens, mas quando uma transação é fluída, ela é inserida no pacote UDP juntamente com a mensagem codificada.  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém uma nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.  
  
 Para o transporte de fluxo de transações personalizadas, a implementação do cliente deve saber quais operações de serviço requerem fluxo de transação e passar essas informações para o WCF. Deve haver também um mecanismo para transmitir a transação do usuário para a camada de transporte. Esta amostra usa "Inspetores de mensagens WCF" para obter essas informações. O inspetor de mensagens do `TransactionFlowInspector`cliente implementado aqui, que é chamado, executa as seguintes tarefas:  
  
- Determina se uma transação deve ser fluída para `IsTxFlowRequiredForThisOperation()`uma determinada ação de mensagem (isso ocorre em ).  
  
- Anexa a transação ambiente atual `TransactionFlowProperty`à mensagem usando , se uma transação for necessária para ser fluída (isso é feito em `BeforeSendRequest()`).  
  
```csharp  
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
  
 O `TransactionFlowInspector` próprio é passado para a estrutura `TransactionFlowBehavior`usando um comportamento personalizado: o .  
  
```csharp  
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
  
 Com o mecanismo anterior em vigor, `TransactionScope` o código do usuário cria um antes de chamar a operação do serviço. O inspetor de mensagens garante que a transação seja passada para o transporte caso seja necessária para ser fluída para a operação do serviço.  
  
```csharp  
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
  
 Ao receber um pacote UDP do cliente, o serviço o desserializa para extrair a mensagem e possivelmente uma transação.  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que inverte o `TransactionMessageBuffer.WriteTransactionMessageBuffer()`processo de serialização realizado por .  
  
 Se uma transação foi fluída, ela é `TransactionMessageProperty`anexada à mensagem no .  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Isso garante que o despachante pegue a transação no momento da expedição e a use ao ligar para a operação de serviço endereçada pela mensagem.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. A amostra atual deve ser executada de forma semelhante à amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md) Para executá-lo, inicie o serviço com UdpTestService.exe. Se você estiver executando o Windows Vista, você deve iniciar o serviço com privilégios elevados. Para isso, clique com o botão direito do mouse UdpTestService.exe no File Explorer e clique em **Executar como administrador**.  
  
3. Isso produz a seguinte saída.  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. Neste momento, você pode iniciar o cliente executando UdpTestClient.exe. A saída produzida pelo cliente é a seguinte.  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. A saída de serviço é a seguinte.  
  
    ```console
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
  
6. O aplicativo de `The client transaction has flowed to the service` serviço exibe a mensagem se puder corresponder `clientTransactionId` ao identificador `CalculatorService.Add()` de transação enviado pelo cliente, no parâmetro da operação, ao identificador da transação de serviço. Uma correspondência só é obtida se a transação do cliente tiver fluído para o serviço.  
  
7. Para executar o aplicativo cliente contra pontos finais publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e, em seguida, execute o cliente de teste novamente. Você deve ver a seguinte saída no serviço.  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Executar o cliente contra o serviço agora produz uma saída semelhante à de antes.  
  
9. Para regenerar o código e a configuração do cliente usando o Svcutil.exe, inicie o aplicativo de serviço e execute o seguinte comando Svcutil.exe a partir do diretório raiz da amostra.  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Observe que o Svcutil.exe não gera `sampleProfileUdpBinding`a configuração de extensão de vinculação para o ; você deve adicioná-lo manualmente.  
  
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
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Confira também

- [Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)

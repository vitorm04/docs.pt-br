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
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="95490-102">Transporte: transações personalizadas através de exemplo de UDP</span><span class="sxs-lookup"><span data-stu-id="95490-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="95490-103">Esta amostra é baseada na amostra [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) na[Extensibilidade de Transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md)da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95490-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="95490-104">Ele estende a amostra udp transport para suportar o <xref:System.ServiceModel.Channels.TransactionMessageProperty> fluxo de transações personalizadas e demonstra o uso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="95490-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="95490-105">Alterações de código na amostra de transporte UDP</span><span class="sxs-lookup"><span data-stu-id="95490-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="95490-106">Para demonstrar o fluxo de transação, a amostra altera o contrato de serviço para `ICalculatorContract` exigir um escopo de transação para `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="95490-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="95490-107">A amostra também `System.Guid` adiciona um parâmetro extra `Add` ao contrato da operação.</span><span class="sxs-lookup"><span data-stu-id="95490-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="95490-108">Este parâmetro é usado para passar o identificador da transação do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="95490-109">A [amostra Transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) usa pacotes UDP para passar mensagens entre um cliente e um serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="95490-110">A [Amostra de Transporte Personalizado](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) usa o mesmo mecanismo para transportar mensagens, mas quando uma transação é fluída, ela é inserida no pacote UDP juntamente com a mensagem codificada.</span><span class="sxs-lookup"><span data-stu-id="95490-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="95490-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém uma nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.</span><span class="sxs-lookup"><span data-stu-id="95490-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="95490-112">Para o transporte de fluxo de transações personalizadas, a implementação do cliente deve saber quais operações de serviço requerem fluxo de transação e passar essas informações para o WCF.</span><span class="sxs-lookup"><span data-stu-id="95490-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="95490-113">Deve haver também um mecanismo para transmitir a transação do usuário para a camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="95490-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="95490-114">Esta amostra usa "Inspetores de mensagens WCF" para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="95490-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="95490-115">O inspetor de mensagens do `TransactionFlowInspector`cliente implementado aqui, que é chamado, executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="95490-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="95490-116">Determina se uma transação deve ser fluída para `IsTxFlowRequiredForThisOperation()`uma determinada ação de mensagem (isso ocorre em ).</span><span class="sxs-lookup"><span data-stu-id="95490-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="95490-117">Anexa a transação ambiente atual `TransactionFlowProperty`à mensagem usando , se uma transação for necessária para ser fluída (isso é feito em `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="95490-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="95490-118">O `TransactionFlowInspector` próprio é passado para a estrutura `TransactionFlowBehavior`usando um comportamento personalizado: o .</span><span class="sxs-lookup"><span data-stu-id="95490-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="95490-119">Com o mecanismo anterior em vigor, `TransactionScope` o código do usuário cria um antes de chamar a operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="95490-120">O inspetor de mensagens garante que a transação seja passada para o transporte caso seja necessária para ser fluída para a operação do serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="95490-121">Ao receber um pacote UDP do cliente, o serviço o desserializa para extrair a mensagem e possivelmente uma transação.</span><span class="sxs-lookup"><span data-stu-id="95490-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="95490-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que inverte o `TransactionMessageBuffer.WriteTransactionMessageBuffer()`processo de serialização realizado por .</span><span class="sxs-lookup"><span data-stu-id="95490-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="95490-123">Se uma transação foi fluída, ela é `TransactionMessageProperty`anexada à mensagem no .</span><span class="sxs-lookup"><span data-stu-id="95490-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="95490-124">Isso garante que o despachante pegue a transação no momento da expedição e a use ao ligar para a operação de serviço endereçada pela mensagem.</span><span class="sxs-lookup"><span data-stu-id="95490-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95490-125">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="95490-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="95490-126">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95490-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="95490-127">A amostra atual deve ser executada de forma semelhante à amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="95490-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="95490-128">Para executá-lo, inicie o serviço com UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="95490-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="95490-129">Se você estiver executando o Windows Vista, você deve iniciar o serviço com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="95490-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="95490-130">Para isso, clique com o botão direito do mouse UdpTestService.exe no File Explorer e clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="95490-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="95490-131">Isso produz a seguinte saída.</span><span class="sxs-lookup"><span data-stu-id="95490-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="95490-132">Neste momento, você pode iniciar o cliente executando UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="95490-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="95490-133">A saída produzida pelo cliente é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="95490-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="95490-134">A saída de serviço é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="95490-134">The service output is as follows.</span></span>  
  
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
  
6. <span data-ttu-id="95490-135">O aplicativo de `The client transaction has flowed to the service` serviço exibe a mensagem se puder corresponder `clientTransactionId` ao identificador `CalculatorService.Add()` de transação enviado pelo cliente, no parâmetro da operação, ao identificador da transação de serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="95490-136">Uma correspondência só é obtida se a transação do cliente tiver fluído para o serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="95490-137">Para executar o aplicativo cliente contra pontos finais publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e, em seguida, execute o cliente de teste novamente.</span><span class="sxs-lookup"><span data-stu-id="95490-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="95490-138">Você deve ver a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="95490-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="95490-139">Executar o cliente contra o serviço agora produz uma saída semelhante à de antes.</span><span class="sxs-lookup"><span data-stu-id="95490-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="95490-140">Para regenerar o código e a configuração do cliente usando o Svcutil.exe, inicie o aplicativo de serviço e execute o seguinte comando Svcutil.exe a partir do diretório raiz da amostra.</span><span class="sxs-lookup"><span data-stu-id="95490-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="95490-141">Observe que o Svcutil.exe não gera `sampleProfileUdpBinding`a configuração de extensão de vinculação para o ; você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="95490-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="95490-142">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="95490-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95490-143">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="95490-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="95490-144">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="95490-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95490-145">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="95490-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="95490-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="95490-146">See also</span></span>

- [<span data-ttu-id="95490-147">Transporte: UDP</span><span class="sxs-lookup"><span data-stu-id="95490-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)

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
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="a89f3-102">Transporte: Transações personalizadas sobre o exemplo de UDP</span><span class="sxs-lookup"><span data-stu-id="a89f3-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="a89f3-103">Este exemplo é baseado no [transporte: Exemplo](../../../../docs/framework/wcf/samples/transport-udp.md) de UDP na[extensibilidade de transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md)do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a89f3-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="a89f3-104">Ele estende o exemplo de transporte UDP para dar suporte ao fluxo de transações personalizadas e demonstra <xref:System.ServiceModel.Channels.TransactionMessageProperty> o uso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a89f3-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="a89f3-105">Alterações de código no exemplo de transporte UDP</span><span class="sxs-lookup"><span data-stu-id="a89f3-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="a89f3-106">Para demonstrar o fluxo de transações, o exemplo altera o contrato `ICalculatorContract` de serviço para para exigir um `CalculatorService.Add()`escopo de transação para.</span><span class="sxs-lookup"><span data-stu-id="a89f3-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="a89f3-107">O exemplo também adiciona um parâmetro `System.Guid` extra ao contrato `Add` da operação.</span><span class="sxs-lookup"><span data-stu-id="a89f3-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="a89f3-108">Esse parâmetro é usado para passar o identificador da transação do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="a89f3-109">O [transporte: O](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo de UDP usa pacotes UDP para passar mensagens entre um cliente e um serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="a89f3-110">O [transporte: O exemplo](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) de transporte personalizado usa o mesmo mecanismo para transportar mensagens, mas quando uma transação flui, ela é inserida no pacote UDP junto com a mensagem codificada.</span><span class="sxs-lookup"><span data-stu-id="a89f3-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="a89f3-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.</span><span class="sxs-lookup"><span data-stu-id="a89f3-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="a89f3-112">Para o transporte de fluxo de transações personalizado, a implementação do cliente deve saber quais operações de serviço exigem o fluxo de transações e passar essas informações para o WCF.</span><span class="sxs-lookup"><span data-stu-id="a89f3-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="a89f3-113">Também deve haver um mecanismo para transmitir a transação do usuário para a camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="a89f3-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="a89f3-114">Este exemplo usa "inspetores de mensagem do WCF" para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="a89f3-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="a89f3-115">O Inspetor de mensagem do cliente implementado aqui, que `TransactionFlowInspector`é chamado, executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="a89f3-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="a89f3-116">Determina se uma transação deve ser fluída para uma determinada ação de mensagem (isso ocorre em `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="a89f3-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="a89f3-117">Anexa a transação de ambiente atual à mensagem usando `TransactionFlowProperty`, se uma transação for necessária para fluir (isso é feito em `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="a89f3-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="a89f3-118">O `TransactionFlowInspector` próprio é passado para a estrutura usando um comportamento personalizado: o `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="a89f3-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="a89f3-119">Com o mecanismo anterior em vigor, o código do usuário cria `TransactionScope` um antes de chamar a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="a89f3-120">O Inspetor de mensagem garante que a transação seja passada para o transporte, caso seja necessário fluir para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="a89f3-121">Após receber um pacote UDP do cliente, o serviço o desserializa para extrair a mensagem e possivelmente uma transação.</span><span class="sxs-lookup"><span data-stu-id="a89f3-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="a89f3-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que reverte o processo de serialização executado pelo `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="a89f3-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="a89f3-123">Se uma transação tiver sido transformada em fluxo, ela será anexada à mensagem `TransactionMessageProperty`no.</span><span class="sxs-lookup"><span data-stu-id="a89f3-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="a89f3-124">Isso garante que o Dispatcher pegue a transação no momento da expedição e a use ao chamar a operação de serviço endereçada pela mensagem.</span><span class="sxs-lookup"><span data-stu-id="a89f3-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a89f3-125">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a89f3-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a89f3-126">Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a89f3-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="a89f3-127">O exemplo atual deve ser executado de forma semelhante [ao transporte: Exemplo](../../../../docs/framework/wcf/samples/transport-udp.md) de UDP.</span><span class="sxs-lookup"><span data-stu-id="a89f3-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="a89f3-128">Para executá-lo, inicie o serviço com UdpTestService. exe.</span><span class="sxs-lookup"><span data-stu-id="a89f3-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="a89f3-129">Se você estiver executando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]o, deverá iniciar o serviço com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="a89f3-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="a89f3-130">Para fazer isso, clique com o botão direito do mouse em UdpTestService. exe no explorador de arquivos e clique em **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="a89f3-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="a89f3-131">Isso produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="a89f3-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="a89f3-132">Neste momento, você pode iniciar o cliente executando UdpTestClient. exe.</span><span class="sxs-lookup"><span data-stu-id="a89f3-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="a89f3-133">A saída produzida pelo cliente é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="a89f3-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="a89f3-134">A saída do serviço é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="a89f3-134">The service output is as follows.</span></span>  
  
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
  
6. <span data-ttu-id="a89f3-135">O aplicativo de serviço exibirá `The client transaction has flowed to the service` a mensagem se ele puder corresponder ao identificador de transação enviado pelo cliente, `clientTransactionId` no parâmetro da `CalculatorService.Add()` operação, para o identificador da transação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="a89f3-136">Uma correspondência será obtida somente se a transação do cliente tiver fluído para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="a89f3-137">Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e execute o cliente de teste novamente.</span><span class="sxs-lookup"><span data-stu-id="a89f3-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="a89f3-138">Você deverá ver a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="a89f3-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="a89f3-139">Executar o cliente em relação ao serviço agora produz uma saída semelhante como antes.</span><span class="sxs-lookup"><span data-stu-id="a89f3-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="a89f3-140">Para regenerar o código do cliente e a configuração usando svcutil. exe, inicie o aplicativo de serviço e execute o comando svcutil. exe a seguir do diretório raiz do exemplo.</span><span class="sxs-lookup"><span data-stu-id="a89f3-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="a89f3-141">Observe que svcutil. exe não gera a configuração de extensão de associação para `sampleProfileUdpBinding`o; você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="a89f3-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="a89f3-142">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a89f3-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a89f3-143">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a89f3-143">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a89f3-144">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="a89f3-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a89f3-145">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a89f3-145">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="a89f3-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89f3-146">See also</span></span>

- [<span data-ttu-id="a89f3-147">Porta UDP</span><span class="sxs-lookup"><span data-stu-id="a89f3-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)

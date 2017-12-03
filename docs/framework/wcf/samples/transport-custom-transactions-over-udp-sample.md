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
ms.openlocfilehash: b17cb737533f1542b5f702097da4592df8e17eac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="f4581-102">Transporte: transações personalizadas através de exemplo de UDP</span><span class="sxs-lookup"><span data-stu-id="f4581-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="f4581-103">Este exemplo se baseia o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [extensibilidade de transporte](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="f4581-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="f4581-104">Ele estende o exemplo de transporte UDP para oferecer suporte ao fluxo de transação personalizado e demonstra o uso de <xref:System.ServiceModel.Channels.TransactionMessageProperty> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f4581-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="f4581-105">Alterações de código no exemplo de transporte UDP</span><span class="sxs-lookup"><span data-stu-id="f4581-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="f4581-106">Para demonstrar o fluxo de transações, o exemplo altera o contrato de serviço para `ICalculatorContract` para exigir um escopo de transação para `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="f4581-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="f4581-107">O exemplo também adiciona um extra `System.Guid` parâmetro para o contrato do `Add` operação.</span><span class="sxs-lookup"><span data-stu-id="f4581-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="f4581-108">Esse parâmetro é usado para passar o identificador da transação do cliente para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="f4581-109">O [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo usa pacotes UDP para passar mensagens entre um cliente e um serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="f4581-110">O [transporte: exemplo de transporte personalizado](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) usa o mesmo mecanismo de transporte de mensagens, mas quando o fluxo de uma transação, é inserido no pacote UDP junto com a mensagem codificada.</span><span class="sxs-lookup"><span data-stu-id="f4581-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="f4581-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`é um método auxiliar que contém a nova funcionalidade para mesclar o token de propagação para a transação atual com a entidade de mensagem e colocá-lo em um buffer.</span><span class="sxs-lookup"><span data-stu-id="f4581-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="f4581-112">Para o transporte de fluxo de transação personalizado, a implementação de cliente precisa saber quais operações de serviço requerem o fluxo de transações e passar essas informações para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4581-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f4581-113">Deve haver também um mecanismo para transmitir a transação do usuário para a camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="f4581-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="f4581-114">Este exemplo usa "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inspetores de mensagem" para obter essas informações.</span><span class="sxs-lookup"><span data-stu-id="f4581-114">This sample uses "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message inspectors" to obtain this information.</span></span> <span data-ttu-id="f4581-115">O Inspetor de mensagens do cliente implementado aqui, que é chamado de `TransactionFlowInspector`, executa as seguintes tarefas:</span><span class="sxs-lookup"><span data-stu-id="f4581-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="f4581-116">Determina se uma transação deve fluir para uma ação de mensagem determinada (Isso ocorre `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="f4581-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="f4581-117">Anexa a transação de ambiente atual para a mensagem usando `TransactionFlowProperty`, se uma transação é necessária para fluir (Isso é feito no `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="f4581-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="f4581-118">O `TransactionFlowInspector` em si é passado para o framework usando um comportamento personalizado: o `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="f4581-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="f4581-119">Com o mecanismo anterior em vigor, o código de usuário cria um `TransactionScope` antes de chamar a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="f4581-120">O Inspetor de mensagem garante que a transação é passada para o transporte, caso seja necessária para fluir para a operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="f4581-121">Ao receber um pacote UDP do cliente, o serviço desserializa-o para extrair a mensagem e, possivelmente, uma transação.</span><span class="sxs-lookup"><span data-stu-id="f4581-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="f4581-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`é o método auxiliar que reverte o processo de serialização executado pelo `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="f4581-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="f4581-123">Se uma transação foi recebida no fluxo, ele é adicionado para a mensagem de `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="f4581-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="f4581-124">Isso garante que o dispatcher pega a transação em tempo de expedição e utiliza ao chamar a operação de serviço resolvida pela mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4581-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f4581-125">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f4581-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f4581-126">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f4581-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="f4581-127">O exemplo atual deve ser executado da mesma forma que o [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="f4581-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="f4581-128">Para executá-lo, inicie o serviço com UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="f4581-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="f4581-129">Se você estiver executando [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], você deve iniciar o serviço com privilégios elevados.</span><span class="sxs-lookup"><span data-stu-id="f4581-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="f4581-130">Para fazer isso, clique com botão direito UdpTestService.exe em [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e clique em **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="f4581-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="f4581-131">Isso produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4581-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="f4581-132">Neste momento, você pode iniciar o cliente executando UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="f4581-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="f4581-133">A saída produzida pelo cliente é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f4581-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="f4581-134">A saída do serviço é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f4581-134">The service output is as follows.</span></span>  
  
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
  
6.  <span data-ttu-id="f4581-135">O aplicativo de serviço exibe a mensagem `The client transaction has flowed to the service` se ela pode corresponder ao identificador de transação enviado pelo cliente, no `clientTransactionId` parâmetro o `CalculatorService.Add()` operação, como o identificador da transação de serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="f4581-136">Uma correspondência é obtida somente se a transação de cliente passou para o serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="f4581-137">Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione ENTER na janela do aplicativo de serviço e, em seguida, execute novamente o cliente de teste.</span><span class="sxs-lookup"><span data-stu-id="f4581-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="f4581-138">Você verá a seguinte saída no serviço.</span><span class="sxs-lookup"><span data-stu-id="f4581-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="f4581-139">Executando o cliente em relação ao serviço agora produz saída semelhante como antes.</span><span class="sxs-lookup"><span data-stu-id="f4581-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="f4581-140">Para gerar novamente o código de cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e, em seguida, execute o seguinte comando Svcutil.exe do diretório raiz do exemplo.</span><span class="sxs-lookup"><span data-stu-id="f4581-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="f4581-141">Observe que o Svcutil.exe não gerar a configuração de extensão de associação para o `sampleProfileUdpBinding`; você deve adicioná-lo manualmente.</span><span class="sxs-lookup"><span data-stu-id="f4581-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
>  <span data-ttu-id="f4581-142">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f4581-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f4581-143">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f4581-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f4581-144">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f4581-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f4581-145">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f4581-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="f4581-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4581-146">See Also</span></span>  
 [<span data-ttu-id="f4581-147">Transporte: UDP</span><span class="sxs-lookup"><span data-stu-id="f4581-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)

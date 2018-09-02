---
title: Envio em lote transacionado
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: abada9aaf5fac8f05599467f385e708e1898832f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416642"
---
# <a name="transacted-batching"></a><span data-ttu-id="2e808-102">Envio em lote transacionado</span><span class="sxs-lookup"><span data-stu-id="2e808-102">Transacted Batching</span></span>
<span data-ttu-id="2e808-103">Este exemplo demonstra como enviar em lote transacionadas leituras usando o serviço de enfileiramento de mensagens (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="2e808-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="2e808-104">Envio em lote transacionado é um recurso de otimização de desempenho para leituras transacionadas em comunicação em fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e808-105">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2e808-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2e808-106">Comunicação em fila, o cliente se comunica com o serviço usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="2e808-107">Mais precisamente, o cliente envia mensagens a uma fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="2e808-108">O serviço recebe mensagens da fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-108">The service receives messages from the queue.</span></span> <span data-ttu-id="2e808-109">O serviço e o cliente, portanto, não precisa estar em execução ao mesmo tempo para se comunicar usando uma fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="2e808-110">Este exemplo demonstra o envio em lote transacionado.</span><span class="sxs-lookup"><span data-stu-id="2e808-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="2e808-111">O lote transacionado é um comportamento que permite o uso de uma única transação durante a leitura de muitas mensagens na fila e processá-las.</span><span class="sxs-lookup"><span data-stu-id="2e808-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e808-112">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2e808-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2e808-113">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e808-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2e808-114">Se o serviço é executado primeiro, ele verificará para garantir que a fila está presente.</span><span class="sxs-lookup"><span data-stu-id="2e808-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="2e808-115">Se a fila não estiver presente, o serviço criará um.</span><span class="sxs-lookup"><span data-stu-id="2e808-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="2e808-116">Você pode executar o serviço pela primeira vez para criar a fila, ou você pode criar um por meio do Gerenciador de fila MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2e808-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="2e808-117">Siga estas etapas para criar uma fila no Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="2e808-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="2e808-118">Abra o Gerenciador do servidor no [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e808-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="2e808-119">Expanda o **recursos** guia.</span><span class="sxs-lookup"><span data-stu-id="2e808-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="2e808-120">Clique com botão direito **filas de mensagens privadas**e selecione **New**, **fila particular**.</span><span class="sxs-lookup"><span data-stu-id="2e808-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="2e808-121">Verifique as **transacional** caixa.</span><span class="sxs-lookup"><span data-stu-id="2e808-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="2e808-122">Insira `ServiceModelSamplesTransacted` como o nome da nova fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e808-123">Neste exemplo o cliente envia centenas de mensagens como parte do lote.</span><span class="sxs-lookup"><span data-stu-id="2e808-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="2e808-124">É normal para o aplicativo de serviço levar algum tempo para processar esses.</span><span class="sxs-lookup"><span data-stu-id="2e808-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="2e808-125">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e808-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="2e808-126">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2e808-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="2e808-127">Para executar o exemplo em um computador associado a um grupo de trabalho ou sem a integração do Active Directory</span><span class="sxs-lookup"><span data-stu-id="2e808-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="2e808-128">Por padrão com o <xref:System.ServiceModel.NetMsmqBinding>, segurança de transporte está habilitada.</span><span class="sxs-lookup"><span data-stu-id="2e808-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="2e808-129">Há duas propriedades relevantes para a segurança do transporte MSMQ <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> e <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` por padrão, o modo de autenticação é definido como `Windows` e o nível de proteção é definido como `Sign`.</span><span class="sxs-lookup"><span data-stu-id="2e808-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="2e808-130">Para o MSMQ fornecer a autenticação e o recurso de assinatura, ele deve ser parte de um domínio e a opção de integração do active directory para o MSMQ deve estar instalada.</span><span class="sxs-lookup"><span data-stu-id="2e808-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="2e808-131">Se você executar esse exemplo em um computador que não atendem a esses critérios, você receberá um erro.</span><span class="sxs-lookup"><span data-stu-id="2e808-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="2e808-132">Se o computador não fizer parte de um domínio ou não tem integração do Active Directory instalada, desative a segurança de transporte, definindo o nível de proteção e o modo de autenticação para `None` conforme mostrado no seguinte exemplo de configuração:</span><span class="sxs-lookup"><span data-stu-id="2e808-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
3.  <span data-ttu-id="2e808-133">Certifique-se de que você altera a configuração no servidor e o cliente antes de executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2e808-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e808-134">Definindo `security``mode` à `None` é equivalente à configuração <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, e `Message` security `None`.</span><span class="sxs-lookup"><span data-stu-id="2e808-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="2e808-135">Para executar o banco de dados em um computador remoto, altere a cadeia de conexão para apontar para o computador no qual reside o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="2e808-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e808-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e808-136">Requirements</span></span>  
 <span data-ttu-id="2e808-137">Para executar este exemplo, o MSMQ deve estar instalado e SQL ou SQL Express é necessária.</span><span class="sxs-lookup"><span data-stu-id="2e808-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2e808-138">Demonstra</span><span class="sxs-lookup"><span data-stu-id="2e808-138">Demonstrates</span></span>  
 <span data-ttu-id="2e808-139">O exemplo demonstra o comportamento de envio em lote transacionado.</span><span class="sxs-lookup"><span data-stu-id="2e808-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="2e808-140">O lote transacionado é um recurso de otimização de desempenho fornecido com o MSMQ em fila de transporte.</span><span class="sxs-lookup"><span data-stu-id="2e808-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="2e808-141">Na verdade, quando as transações são usadas para enviar e receber mensagens, existem 2 separar transações.</span><span class="sxs-lookup"><span data-stu-id="2e808-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="2e808-142">Quando o cliente envia mensagens dentro do escopo de uma transação, a transação é local para o cliente e o Gerenciador de fila do cliente.</span><span class="sxs-lookup"><span data-stu-id="2e808-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="2e808-143">Quando o serviço recebe mensagens dentro do escopo da transação, a transação é local para o serviço e o Gerenciador de fila de recebimento.</span><span class="sxs-lookup"><span data-stu-id="2e808-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="2e808-144">É muito importante lembrar-se de que o cliente e o serviço não estão participando na mesma transação; em vez disso, eles estão usando transações diferentes ao executar suas operações (como enviar e receber) com a fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="2e808-145">No exemplo, usamos uma única transação para a execução de várias operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e808-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="2e808-146">Isso é usado apenas como um recurso de otimização do desempenho e não afeta a semântica do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e808-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="2e808-147">O exemplo é baseado no [associação de MSMQ transacionado](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="2e808-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="2e808-148">Comentários</span><span class="sxs-lookup"><span data-stu-id="2e808-148">Comments</span></span>  
 <span data-ttu-id="2e808-149">Neste exemplo, o cliente envia um lote de mensagens para o serviço de dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="2e808-150">Para mostrar a otimização de desempenho, podemos enviar um grande número de mensagens; Nesse caso, até 2500 mensagens.</span><span class="sxs-lookup"><span data-stu-id="2e808-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="2e808-151">As mensagens enviadas para a fila, em seguida, são recebidas pelo serviço de dentro do escopo de transação definido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="2e808-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="2e808-152">Sem o envio em lote, isso resulta em transações 2500 para cada invocação da operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="2e808-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="2e808-153">Isso afeta o desempenho do sistema.</span><span class="sxs-lookup"><span data-stu-id="2e808-153">This impacts performance of the system.</span></span> <span data-ttu-id="2e808-154">Como dois gerenciadores de recursos são envolvidos - fila MSMQ e a `Orders` banco de dados-cada tal transação é uma transação do DTC.</span><span class="sxs-lookup"><span data-stu-id="2e808-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="2e808-155">Podemos otimizar isso usando um número muito menor de transações, garantindo que um lote de mensagens e invocações de operação de serviço ocorrem em uma única transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="2e808-156">Podemos usar o recurso de envio em lote por:</span><span class="sxs-lookup"><span data-stu-id="2e808-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="2e808-157">Especificando o comportamento de envio em lote transacionado na configuração.</span><span class="sxs-lookup"><span data-stu-id="2e808-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="2e808-158">Especificando um tamanho de lote em termos de número de mensagens a serem lidos usando uma única transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="2e808-159">Especifica o número máximo de lotes simultâneos para ser executado.</span><span class="sxs-lookup"><span data-stu-id="2e808-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="2e808-160">Neste exemplo, vamos mostrar ganhos de desempenho, reduzindo o número de transações, garantindo que os 100 operações de serviço são chamadas em uma única transação antes de confirmar a transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="2e808-161">O comportamento de serviço define um comportamento de operação com `TransactionScopeRequired` definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="2e808-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="2e808-162">Isso garante que o mesmo escopo da transação que é usado para recuperar a mensagem da fila é usado por qualquer gerenciadores de recursos acessados pelo método.</span><span class="sxs-lookup"><span data-stu-id="2e808-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="2e808-163">Neste exemplo, usamos um banco de dados básico para armazenar as informações de ordem de compra contidas na mensagem.</span><span class="sxs-lookup"><span data-stu-id="2e808-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="2e808-164">O escopo da transação também garante que, se o método gera uma exceção, a mensagem é retornada para a fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="2e808-165">Sem definir esse comportamento de operação, um canal em fila cria uma transação para ler a mensagem da fila e confirma a ele automaticamente antes que ela seja expedida para que se a operação falhar, a mensagem será perdida.</span><span class="sxs-lookup"><span data-stu-id="2e808-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="2e808-166">O cenário mais comum é para operações de serviço para se inscrever na transação que é usada para ler a mensagem da fila conforme demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e808-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="2e808-167">Observe que `ReleaseServiceInstanceOnTransactionComplete` é definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="2e808-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="2e808-168">Esse é um requisito importante para envio em lote.</span><span class="sxs-lookup"><span data-stu-id="2e808-168">This is an important requirement for batching.</span></span> <span data-ttu-id="2e808-169">A propriedade `ReleaseServiceInstanceOnTransactionComplete` em `ServiceBehaviorAttribute` indica o que fazer com a instância do serviço depois que a transação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="2e808-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="2e808-170">Por padrão, a instância do serviço é liberada após a conclusão da transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="2e808-171">O aspecto principal para envio em lote é o uso de uma única transação para leitura e expedição muitas mensagens na fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="2e808-172">Liberar, portanto, a instância do serviço acaba de completar a transação prematuramente, eliminando o uso muito do envio em lote.</span><span class="sxs-lookup"><span data-stu-id="2e808-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="2e808-173">Se essa propriedade é definida como `true` e comportamento de envio em lote transacionado é adicionado ao ponto de extremidade, o comportamento de validação de envio em lote gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="2e808-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  

```csharp
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

 <span data-ttu-id="2e808-174">O `Orders` classe encapsula o processamento do pedido.</span><span class="sxs-lookup"><span data-stu-id="2e808-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="2e808-175">No exemplo, ele atualiza o banco de dados com informações de ordem de compra.</span><span class="sxs-lookup"><span data-stu-id="2e808-175">In the sample, it updates the database with purchase order information.</span></span>  

```csharp
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

 <span data-ttu-id="2e808-176">O comportamento de envio em lote e sua configuração são especificadas na configuração do serviço de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e808-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
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
>  <span data-ttu-id="2e808-177">O tamanho do lote é uma dica para o sistema.</span><span class="sxs-lookup"><span data-stu-id="2e808-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="2e808-178">Por exemplo, se você especificar um tamanho de lote de 20, em seguida, 20 mensagens seriam lido e expedidas pelo uso de uma única transação e, em seguida, a transação é confirmada.</span><span class="sxs-lookup"><span data-stu-id="2e808-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="2e808-179">Mas há casos em que a transação pode confirmar o lote antes de atingir o tamanho do lote.</span><span class="sxs-lookup"><span data-stu-id="2e808-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="2e808-180">Associado a cada transação é um tempo limite que inicia o tique depois que a transação é criada.</span><span class="sxs-lookup"><span data-stu-id="2e808-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="2e808-181">Quando esse tempo limite expira, a transação é anulada.</span><span class="sxs-lookup"><span data-stu-id="2e808-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="2e808-182">É possível que esse tempo limite expirar antes mesmo que o tamanho do lote for atingido.</span><span class="sxs-lookup"><span data-stu-id="2e808-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="2e808-183">Para evitar a trabalhar novamente o lote por causa a anulação de `TransactedBatchingBehavior` verifica para ver quanto tempo resta na transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="2e808-184">Se acabar a 80% do tempo limite de transação, a transação é confirmada.</span><span class="sxs-lookup"><span data-stu-id="2e808-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="2e808-185">Se não houver mais nenhuma mensagem na fila e, em vez de aguardar o cumprimento do tamanho do lote a <xref:System.ServiceModel.Description.TransactedBatchingBehavior> confirma a transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="2e808-186">A escolha do tamanho do lote é dependente de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e808-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="2e808-187">Se o tamanho do lote for muito pequeno, você não pode obter o desempenho desejado.</span><span class="sxs-lookup"><span data-stu-id="2e808-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="2e808-188">Por outro lado se o tamanho do lote é muito grande, ele pode diminuir o desempenho.</span><span class="sxs-lookup"><span data-stu-id="2e808-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="2e808-189">Por exemplo, sua transação pode durar mais e mantêm bloqueios em seu banco de dados ou sua transação foi morta bloqueada, que poderia fazer com que o lote para obter revertida e refazer o trabalho.</span><span class="sxs-lookup"><span data-stu-id="2e808-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="2e808-190">O cliente cria um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-190">The client creates a transaction scope.</span></span> <span data-ttu-id="2e808-191">A comunicação com a fila ocorre dentro do escopo da transação, fazendo com que ele será tratado como uma unidade atômica em que todas as mensagens são enviadas para a fila ou nenhuma das mensagens são enviadas para a fila.</span><span class="sxs-lookup"><span data-stu-id="2e808-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="2e808-192">A transação é confirmada chamando <xref:System.Transactions.TransactionScope.Complete%2A> no escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="2e808-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
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

 <span data-ttu-id="2e808-193">Quando você executar o exemplo, as atividades do cliente e o serviço são exibidas nas janelas do console de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="2e808-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="2e808-194">Você pode ver as mensagens de recebimento do serviço do cliente.</span><span class="sxs-lookup"><span data-stu-id="2e808-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="2e808-195">Pressione ENTER em cada janela de console para desligar o serviço e o cliente.</span><span class="sxs-lookup"><span data-stu-id="2e808-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="2e808-196">Observe que porque o enfileiramento de mensagens está em uso, o cliente e o serviço não precisa estar em execução ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="2e808-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="2e808-197">Executar o cliente, desligá-lo e, em seguida, inicie o serviço e ainda recebe suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="2e808-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="2e808-198">Você pode ver uma saída sem interrupção como as mensagens são lidos em um lote e processadas.</span><span class="sxs-lookup"><span data-stu-id="2e808-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
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
>  <span data-ttu-id="2e808-199">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2e808-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2e808-200">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2e808-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e808-201">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2e808-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e808-202">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2e808-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="2e808-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e808-203">See Also</span></span>

---
title: "Comportamento de transação de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d881e7727c002cc9cc5322881a67dcb9a780efa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="a9289-102">Comportamento de transação de serviço</span><span class="sxs-lookup"><span data-stu-id="a9289-102">Service Transaction Behavior</span></span>
<span data-ttu-id="a9289-103">Este exemplo demonstra o uso de uma transação de coordenada de cliente e as configurações de ServiceBehaviorAttribute e OperationBehaviorAttribute para controlar o comportamento de transação de serviço.</span><span class="sxs-lookup"><span data-stu-id="a9289-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="a9289-104">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de cálculo, mas é estendido para manter um log das operações executadas em uma tabela de banco de dados e uma total para as operações de cálculo acumulado com monitoração de estado do servidor.</span><span class="sxs-lookup"><span data-stu-id="a9289-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="a9289-105">Gravações persistentes para a tabela de log do servidor são dependentes após o resultado de uma transação de cliente coordenada - se a transação do cliente não for concluída, a transação de serviço da Web garante que as atualizações para o banco de dados não são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="a9289-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9289-106">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a9289-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a9289-107">O contrato para o serviço define que todas as operações requerem que uma transação flua com solicitações:</span><span class="sxs-lookup"><span data-stu-id="a9289-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 <span data-ttu-id="a9289-108">Para habilitar o fluxo de transações de entrada, o serviço está configurado com o wsHttpBinding fornecido pelo sistema com o atributo transactionFlow para `true`.</span><span class="sxs-lookup"><span data-stu-id="a9289-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="a9289-109">Esta associação usa o protocolo WSAtomicTransactionOctober2004 interoperável:</span><span class="sxs-lookup"><span data-stu-id="a9289-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="a9289-110">Depois de iniciar as duas uma conexão para o serviço e uma transação, o cliente acessa várias operações de serviço dentro do escopo de transação e, em seguida, conclui a transação e fecha a conexão:</span><span class="sxs-lookup"><span data-stu-id="a9289-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="a9289-111">Sobre o serviço, há três atributos que afetam o comportamento de transação de serviço e eles fazem isso das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="a9289-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="a9289-112">Sobre o `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="a9289-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="a9289-113">O `TransactionTimeout` propriedade especifica o período de tempo no qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="a9289-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="a9289-114">Neste exemplo, ele é definido como 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="a9289-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="a9289-115">O `TransactionIsolationLevel` propriedade especifica o nível de isolamento com suporte do serviço.</span><span class="sxs-lookup"><span data-stu-id="a9289-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="a9289-116">Isso é necessário para coincidir com o nível de isolamento do cliente.</span><span class="sxs-lookup"><span data-stu-id="a9289-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="a9289-117">O `ReleaseServiceInstanceOnTransactionComplete` propriedade especifica se a instância do serviço será reciclada quando uma transação seja concluída.</span><span class="sxs-lookup"><span data-stu-id="a9289-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="a9289-118">Definindo-a como `false`, o serviço mantém a mesma instância de serviço entre as solicitações de operação.</span><span class="sxs-lookup"><span data-stu-id="a9289-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="a9289-119">Isso é necessário para manter a execução total.</span><span class="sxs-lookup"><span data-stu-id="a9289-119">This is required to maintain the running total.</span></span> <span data-ttu-id="a9289-120">Se definido como `true`, uma nova instância é gerada após a conclusão de cada ação.</span><span class="sxs-lookup"><span data-stu-id="a9289-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="a9289-121">O `TransactionAutoCompleteOnSessionClose` propriedade especifica se transações pendentes serão concluídas quando a sessão for fechada.</span><span class="sxs-lookup"><span data-stu-id="a9289-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="a9289-122">Definindo-a como `false`, as operações individuais são necessárias para definir o `OperationBehaviorAttribute``TransactionAutoComplete` propriedade `true` ou para solicitar explicitamente uma chamada para o `SetTransactionComplete` método para concluir as transações.</span><span class="sxs-lookup"><span data-stu-id="a9289-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="a9289-123">Este exemplo demonstra as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="a9289-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="a9289-124">Sobre o `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="a9289-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="a9289-125">O `SessionMode` propriedade especifica se o serviço correlaciona as solicitações adequadas para uma sessão lógica.</span><span class="sxs-lookup"><span data-stu-id="a9289-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="a9289-126">Como esse serviço inclui operações em que a propriedade OperationBehaviorAttribute TransactionAutoComplete é definida como `false` (multiplicar e dividir), `SessionMode.Required` deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="a9289-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="a9289-127">Por exemplo, a multiplicação operação não concluir a sua transação e se baseia em vez disso, uma chamada posterior a divisão para ser concluída com o `SetTransactionComplete` método; o serviço deve ser capaz de determinar que essas operações estão ocorrendo na mesma sessão.</span><span class="sxs-lookup"><span data-stu-id="a9289-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="a9289-128">Sobre o `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="a9289-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="a9289-129">O `TransactionScopeRequired` propriedade especifica se as ações da operação devem ser executadas em um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="a9289-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="a9289-130">Isso é definido como `true` para todas as operações neste exemplo e, porque o cliente flui sua transação para todas as operações, as ações ocorrem dentro do escopo de transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="a9289-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="a9289-131">O `TransactionAutoComplete` propriedade especifica se a transação na qual o método é executado é preenchida automaticamente se nenhuma exceção não tratada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="a9289-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="a9289-132">Conforme descrito anteriormente, isso é definido como `true` para as operações de adicionar e subtrair mas `false` para as operações de divisão e multiplicação.</span><span class="sxs-lookup"><span data-stu-id="a9289-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="a9289-133">As operações de adicionar e subtrair concluir suas ações automaticamente, a divisão conclua suas ações por meio de uma chamada explícita para o `SetTransactionComplete` método e a multiplicação não concluir suas ações, mas em vez disso, se baseia e requer uma chamada posterior, como a Divida, para concluir as ações.</span><span class="sxs-lookup"><span data-stu-id="a9289-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="a9289-134">A implementação de serviço atribuída é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a9289-134">The attributed service implementation is as follows:</span></span>  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 <span data-ttu-id="a9289-135">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="a9289-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a9289-136">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a9289-136">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="a9289-137">O registro em log as solicitações de operação de serviço são exibidos na janela do console do serviço.</span><span class="sxs-lookup"><span data-stu-id="a9289-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="a9289-138">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="a9289-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="a9289-139">Observe que, além de manter a execução total dos cálculos, o serviço de relatórios a criação de instâncias (uma instância para este exemplo) e registra as solicitações de operação em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a9289-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="a9289-140">Como todas as solicitações de fluem de transação do cliente, qualquer falha ao concluir a transação resulta em todas as operações de banco de dados que está sendo revertidas.</span><span class="sxs-lookup"><span data-stu-id="a9289-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="a9289-141">Isso pode ser demonstrado de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="a9289-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="a9289-142">Comente a chamada do cliente para `tx.Complete`() e execute - o resultado é o cliente sair do escopo da transação sem concluir a sua transação.</span><span class="sxs-lookup"><span data-stu-id="a9289-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="a9289-143">Comentar out a chamada para a operação de serviço de divisão - este resultados impedem que a ação iniciada pela conclusão da operação de multiplicação e, portanto, a transação do cliente, por fim, também não for concluída.</span><span class="sxs-lookup"><span data-stu-id="a9289-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="a9289-144">Lançar uma exceção sem tratamento em qualquer lugar no escopo da transação do cliente - isso da mesma forma impede que o cliente concluir sua transação.</span><span class="sxs-lookup"><span data-stu-id="a9289-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="a9289-145">O resultado de qualquer um desses é que nenhuma das operações executadas no escopo são confirmadas e a contagem de linhas persistentes no banco de dados não incrementam.</span><span class="sxs-lookup"><span data-stu-id="a9289-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9289-146">Como parte do processo de compilação, o arquivo de banco de dados é copiado para a pasta bin.</span><span class="sxs-lookup"><span data-stu-id="a9289-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="a9289-147">Você deve examinar essa cópia do arquivo de banco de dados para observar as linhas que são mantidas no log, em vez do arquivo que está incluído no projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9289-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9289-148">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a9289-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a9289-149">Certifique-se de que você tenha instalado o SQL Server 2005 Express Edition ou SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="a9289-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="a9289-150">No arquivo de App. config do serviço, o banco de dados `connectionString` pode ser definidas ou o banco de dados interações podem ser desabilitadas, definindo o appSettings `usingSql` valor `false`.</span><span class="sxs-lookup"><span data-stu-id="a9289-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="a9289-151">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9289-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a9289-152">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9289-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="a9289-153">Se você executar o exemplo em computadores, você deve configurar o Microsoft Distributed Transaction MSDTC (coordenador) para habilitar o fluxo de transações de rede e use a ferramenta WsatConfig.exe para habilitar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporte de transações de rede.</span><span class="sxs-lookup"><span data-stu-id="a9289-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="a9289-154">Para configurar o Microsoft Distributed transação MSDTC (coordenador) para dar suporte à execução do exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="a9289-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="a9289-155">No computador do serviço, configure o MSDTC para permitir transações de rede de entrada.</span><span class="sxs-lookup"><span data-stu-id="a9289-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="a9289-156">Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="a9289-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="a9289-157">Clique com botão direito **meu computador** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a9289-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="a9289-158">Sobre o **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="a9289-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="a9289-159">Verificar **acesso DTC de rede** e **permitir entrada**.</span><span class="sxs-lookup"><span data-stu-id="a9289-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="a9289-160">Clique em **Sim** para reiniciar o serviço MS DTC e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="a9289-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="a9289-161">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a9289-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="a9289-162">No computador do serviço e o computador cliente, configure o Firewall do Windows para incluir o Microsoft Distributed Transaction MSDTC (coordenador) à lista de aplicativos de exceção:</span><span class="sxs-lookup"><span data-stu-id="a9289-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="a9289-163">Execute o aplicativo de Firewall do Windows no painel de controle.</span><span class="sxs-lookup"><span data-stu-id="a9289-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="a9289-164">Do **exceções** , clique em **adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="a9289-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="a9289-165">Navegue até a pasta C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="a9289-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="a9289-166">Selecione Msdtc.exe e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="a9289-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="a9289-167">Clique em **Okey** para fechar o **adicionar programa** caixa de diálogo e clique em **Okey** novamente para fechar o miniaplicativo de Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="a9289-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="a9289-168">No computador cliente, configure o MSDTC para permitir transações de rede de saída:</span><span class="sxs-lookup"><span data-stu-id="a9289-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="a9289-169">Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="a9289-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="a9289-170">Clique com botão direito **meu computador** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a9289-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="a9289-171">Sobre o **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="a9289-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="a9289-172">Verificar **acesso DTC de rede** e **permitir saída**.</span><span class="sxs-lookup"><span data-stu-id="a9289-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="a9289-173">Clique em **Sim** para reiniciar o serviço MS DTC e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="a9289-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="a9289-174">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="a9289-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9289-175">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a9289-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9289-176">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a9289-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9289-177">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a9289-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9289-178">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a9289-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="a9289-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9289-179">See Also</span></span>

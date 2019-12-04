---
title: Comportamento de transação de serviço
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 38ad03d64d95e0653fba8018c59c62db9a698096
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715105"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="3e29b-102">Comportamento de transação de serviço</span><span class="sxs-lookup"><span data-stu-id="3e29b-102">Service Transaction Behavior</span></span>

<span data-ttu-id="3e29b-103">Este exemplo demonstra o uso de uma transação coordenada pelo cliente e as configurações de ServiceBehaviorAttribute e OperationBehaviorAttribute para controlar o comportamento da transação de serviço.</span><span class="sxs-lookup"><span data-stu-id="3e29b-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="3e29b-104">Este exemplo é baseado no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora, mas é estendido para manter um log de servidor das operações realizadas em uma tabela de banco de dados e um total de execução com estado para as operações de calculadora.</span><span class="sxs-lookup"><span data-stu-id="3e29b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="3e29b-105">As gravações persistentes na tabela de log do servidor dependem do resultado de uma transação coordenada do cliente – se a transação do cliente não for concluída, a transação do serviço Web garantirá que as atualizações do banco de dados não sejam confirmadas.</span><span class="sxs-lookup"><span data-stu-id="3e29b-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="3e29b-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3e29b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3e29b-107">O contrato para o serviço define que todas as operações exigem que uma transação flua com solicitações:</span><span class="sxs-lookup"><span data-stu-id="3e29b-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
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

<span data-ttu-id="3e29b-108">Para habilitar o fluxo de transações de entrada, o serviço é configurado com o wsHttpBinding fornecido pelo sistema com o atributo transactionFlow definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="3e29b-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="3e29b-109">Essa associação usa o protocolo interoperável WSAtomicTransactionOctober2004:</span><span class="sxs-lookup"><span data-stu-id="3e29b-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="3e29b-110">Depois de iniciar uma conexão com o serviço e uma transação, o cliente acessa várias operações de serviço dentro do escopo dessa transação e, em seguida, conclui a transação e fecha a conexão:</span><span class="sxs-lookup"><span data-stu-id="3e29b-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
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

<span data-ttu-id="3e29b-111">No serviço, há três atributos que afetam o comportamento da transação de serviço e fazem isso das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="3e29b-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="3e29b-112">Na `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3e29b-112">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="3e29b-113">A propriedade `TransactionTimeout` especifica o período de tempo no qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="3e29b-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="3e29b-114">Neste exemplo, ele é definido como 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="3e29b-114">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="3e29b-115">A propriedade `TransactionIsolationLevel` especifica o nível de isolamento ao qual o serviço dá suporte.</span><span class="sxs-lookup"><span data-stu-id="3e29b-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="3e29b-116">Isso é necessário para corresponder ao nível de isolamento do cliente.</span><span class="sxs-lookup"><span data-stu-id="3e29b-116">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="3e29b-117">A propriedade `ReleaseServiceInstanceOnTransactionComplete` especifica se a instância do serviço é reciclada quando uma transação é concluída.</span><span class="sxs-lookup"><span data-stu-id="3e29b-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="3e29b-118">Ao defini-lo como `false`, o serviço mantém a mesma instância de serviço nas solicitações de operação.</span><span class="sxs-lookup"><span data-stu-id="3e29b-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="3e29b-119">Isso é necessário para manter o total acumulado.</span><span class="sxs-lookup"><span data-stu-id="3e29b-119">This is required to maintain the running total.</span></span> <span data-ttu-id="3e29b-120">Se definido como `true`, uma nova instância será gerada após cada ação concluída.</span><span class="sxs-lookup"><span data-stu-id="3e29b-120">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="3e29b-121">A propriedade `TransactionAutoCompleteOnSessionClose` especifica se as transações pendentes são concluídas quando a sessão é fechada.</span><span class="sxs-lookup"><span data-stu-id="3e29b-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="3e29b-122">Ao defini-lo como `false`, as operações individuais são necessárias para definir a propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> como `true` ou para exigir explicitamente uma chamada para o método <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> para concluir as transações.</span><span class="sxs-lookup"><span data-stu-id="3e29b-122">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="3e29b-123">Este exemplo demonstra as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="3e29b-123">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="3e29b-124">Na `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3e29b-124">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="3e29b-125">A propriedade `SessionMode` especifica se o serviço correlaciona as solicitações apropriadas em uma sessão lógica.</span><span class="sxs-lookup"><span data-stu-id="3e29b-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="3e29b-126">Como esse serviço inclui operações em que a Propriedade OperationBehaviorAttribute TransactionAutoComplete está definida como `false` (multiplicar e dividir), `SessionMode.Required` deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="3e29b-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="3e29b-127">Por exemplo, a operação de multiplicação não conclui sua transação e, em vez disso, depende de uma chamada posterior para ser concluída usando o método `SetTransactionComplete`; o serviço deve ser capaz de determinar se essas operações estão ocorrendo dentro da mesma sessão.</span><span class="sxs-lookup"><span data-stu-id="3e29b-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="3e29b-128">Na `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="3e29b-128">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="3e29b-129">A propriedade `TransactionScopeRequired` especifica se as ações da operação devem ser executadas em um escopo de transação.</span><span class="sxs-lookup"><span data-stu-id="3e29b-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="3e29b-130">Isso é definido como `true` para todas as operações neste exemplo e, como o cliente flui sua transação para todas as operações, as ações ocorrem dentro do escopo dessa transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="3e29b-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="3e29b-131">A propriedade `TransactionAutoComplete` especifica se a transação na qual o método é executado será concluída automaticamente se nenhuma exceção não tratada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="3e29b-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="3e29b-132">Conforme descrito anteriormente, isso é definido como `true` para as operações adicionar e subtrair, mas `false` para as operações de multiplicar e dividir.</span><span class="sxs-lookup"><span data-stu-id="3e29b-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="3e29b-133">As operações adicionar e subtrair concluem suas ações automaticamente, a divisão conclui suas ações por meio de uma chamada explícita para o método `SetTransactionComplete`, e a multiplicação não conclui suas ações, mas, em vez disso, se baseia e requer uma chamada posterior, como a divisão, para concluir as ações.</span><span class="sxs-lookup"><span data-stu-id="3e29b-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="3e29b-134">A implementação do serviço atribuído é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="3e29b-134">The attributed service implementation is as follows:</span></span>

```csharp
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

    // Logging method omitted for brevity
}
```

<span data-ttu-id="3e29b-135">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="3e29b-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3e29b-136">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3e29b-136">Press ENTER in the client window to shut down the client.</span></span>

```console
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

<span data-ttu-id="3e29b-137">O registro em log das solicitações de operação de serviço é exibido na janela do console do serviço.</span><span class="sxs-lookup"><span data-stu-id="3e29b-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="3e29b-138">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3e29b-138">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="3e29b-139">Observe que, além de manter o total em execução dos cálculos, o serviço relata a criação de instâncias (uma instância para este exemplo) e registra as solicitações de operação em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3e29b-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="3e29b-140">Como todas as solicitações fluem a transação do cliente, qualquer falha ao concluir a transação resulta em todas as operações de banco de dados que estão sendo revertidas.</span><span class="sxs-lookup"><span data-stu-id="3e29b-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="3e29b-141">Isso pode ser demonstrado de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="3e29b-141">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="3e29b-142">Comente a chamada do cliente para `tx.Complete`() e execute novamente-isso resulta no cliente que sai do escopo da transação sem concluir sua transação.</span><span class="sxs-lookup"><span data-stu-id="3e29b-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="3e29b-143">Comente a chamada para a operação de serviço de divisão – esses resultados impedem que a ação iniciada pela operação de multiplicação seja concluída e, portanto, a transação do cliente também não seja concluída.</span><span class="sxs-lookup"><span data-stu-id="3e29b-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="3e29b-144">Lance uma exceção sem tratamento em qualquer lugar no escopo da transação do cliente-isso, de maneira semelhante, impede que o cliente conclua sua transação.</span><span class="sxs-lookup"><span data-stu-id="3e29b-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="3e29b-145">O resultado de qualquer um deles é que nenhuma das operações executadas nesse escopo é confirmada e a contagem de linhas mantidas no banco de dados não é incrementada.</span><span class="sxs-lookup"><span data-stu-id="3e29b-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="3e29b-146">Como parte do processo de compilação, o arquivo de banco de dados é copiado para a pasta bin.</span><span class="sxs-lookup"><span data-stu-id="3e29b-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="3e29b-147">Você deve examinar essa cópia do arquivo de banco de dados para observar as linhas que são persistidas no log, em vez do arquivo que está incluído no projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e29b-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e29b-148">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3e29b-148">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3e29b-149">Verifique se você instalou o SQL Server 2005 Express Edition ou o SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="3e29b-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="3e29b-150">No arquivo app. config do serviço, o `connectionString` do banco de dados pode ser definido ou as interações de banco de dados podem ser desabilitadas definindo o valor de `usingSql` appSettings como `false`.</span><span class="sxs-lookup"><span data-stu-id="3e29b-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="3e29b-151">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e29b-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="3e29b-152">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e29b-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="3e29b-153">Se você executar o exemplo entre computadores, deverá configurar o Microsoft Coordenador de Transações Distribuídas (MSDTC) para habilitar o fluxo de transações de rede e usar a ferramenta WsatConfig. exe para habilitar a rede de transações Windows Communication Foundation (WCF) support.</span><span class="sxs-lookup"><span data-stu-id="3e29b-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="3e29b-154">Para configurar o Microsoft Coordenador de Transações Distribuídas (MSDTC) para dar suporte à execução do exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="3e29b-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="3e29b-155">No computador de serviço, configure o MSDTC para permitir transações de rede de entrada.</span><span class="sxs-lookup"><span data-stu-id="3e29b-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="3e29b-156">No menu **Iniciar** , navegue até **painel de controle**, **Ferramentas administrativas**e serviços de **componentes**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="3e29b-157">Clique com o botão direito do mouse em **meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-157">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="3e29b-158">Na guia **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="3e29b-159">Verifique o **acesso ao DTC de rede** e permita a **entrada**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="3e29b-160">Clique em **Sim** para reiniciar o serviço MS DTC e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="3e29b-161">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3e29b-161">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="3e29b-162">Na máquina do serviço e no computador cliente, configure o Firewall do Windows para incluir o Microsoft Coordenador de Transações Distribuídas (MSDTC) na lista de aplicativos isentos:</span><span class="sxs-lookup"><span data-stu-id="3e29b-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="3e29b-163">Execute o aplicativo Firewall do Windows no painel de controle.</span><span class="sxs-lookup"><span data-stu-id="3e29b-163">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="3e29b-164">Na guia **exceções** , clique em **Adicionar programa**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-164">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="3e29b-165">Navegue até a pasta C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="3e29b-165">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="3e29b-166">Selecione MSDTC. exe e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-166">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="3e29b-167">Clique em **OK** para fechar a caixa de diálogo **Adicionar programa** e clique em **OK** novamente para fechar o miniaplicativo Firewall do Windows.</span><span class="sxs-lookup"><span data-stu-id="3e29b-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="3e29b-168">No computador cliente, configure o MSDTC para permitir transações de rede de saída:</span><span class="sxs-lookup"><span data-stu-id="3e29b-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="3e29b-169">No menu **Iniciar** , navegue até **painel de controle**, **Ferramentas administrativas**e serviços de **componentes**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="3e29b-170">Clique com o botão direito do mouse em **meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-170">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="3e29b-171">Na guia **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="3e29b-172">Verifique o **acesso ao DTC de rede** e permita a **saída**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="3e29b-173">Clique em **Sim** para reiniciar o serviço MS DTC e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="3e29b-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="3e29b-174">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3e29b-174">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e29b-175">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3e29b-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3e29b-176">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3e29b-176">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3e29b-177">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="3e29b-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e29b-178">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3e29b-178">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`

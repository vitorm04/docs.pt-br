---
title: Fluxo de transação WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: cde5599734dbeb450e10b2b74cf035b41129d653
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007468"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="3a9e2-102">Fluxo de transação WS</span><span class="sxs-lookup"><span data-stu-id="3a9e2-102">WS Transaction Flow</span></span>
<span data-ttu-id="3a9e2-103">Este exemplo demonstra o uso de uma transação de coordenadas de cliente e as opções de cliente e servidor para transações de fluxo usando o protocolo WS-AT ou OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="3a9e2-104">Este exemplo é baseado na [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de Calculadora, mas as operações são atribuídas para demonstrar o uso da `TransactionFlowAttribute` com o **TransactionFlowOption** enumeração para determinar para qual transação grau fluxo está habilitado.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="3a9e2-105">Dentro do escopo da transação fluída, um log das operações solicitados é escrito para um banco de dados e persiste até que a transação de coordenadas de cliente seja concluída - se a transação do cliente não for concluída, a transação de serviço Web garante que o as atualizações adequadas no banco de dados não são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a9e2-106">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3a9e2-107">Depois de iniciar uma conexão ao serviço e uma transação, o cliente acessa várias operações do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="3a9e2-108">O contrato para o serviço é definido da seguinte maneira com cada uma das operações que demonstra uma configuração diferente para o `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 <span data-ttu-id="3a9e2-109">Isso define as operações na ordem em que eles devem ser processadas:</span><span class="sxs-lookup"><span data-stu-id="3a9e2-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="3a9e2-110">Um `Add` solicitação de operação deve incluir uma transação fluída.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="3a9e2-111">Um `Subtract` solicitação de operação pode incluir uma transação fluída.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="3a9e2-112">Um `Multiply` solicitação de operação não deve incluir uma transação fluída por meio da configuração explícita de NotAllowed.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="3a9e2-113">Um `Divide` solicitação de operação não deve incluir uma transação fluída por meio da omissão de um `TransactionFlow` atributo.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="3a9e2-114">Para habilitar o fluxo de transações, associações com o [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada deve ser usada além dos atributos operação apropriada.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="3a9e2-115">Neste exemplo, a configuração do serviço expõe um ponto de extremidade TCP e um ponto de extremidade HTTP, além de um ponto de extremidade de troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="3a9e2-116">O ponto de extremidade TCP e o ponto de extremidade HTTP usam as seguintes associações, ambos com o [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="3a9e2-117">A netTcpBinding fornecido pelo sistema permite a especificação da transactionProtocol enquanto o wsHttpBinding fornecido pelo sistema usa apenas o protocolo WSAtomicTransactionOctober2004 mais interoperável.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="3a9e2-118">Use os OleTransactions protocolo só está disponível para pelos clientes do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3a9e2-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="3a9e2-119">Para a classe que implementa o `ICalculator` interface, todos os métodos são atribuídos com <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="3a9e2-120">Essa configuração declara que todas as ações tomadas dentro do método ocorrem dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="3a9e2-121">Nesse caso, as ações tomadas incluem a gravação no banco de dados de log.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="3a9e2-122">Se a solicitação de operação inclui uma transação fluída, em seguida, ocorrem as ações dentro do escopo de transação de entrada ou um novo escopo de transação é gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a9e2-123">O <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade define o comportamento local para as implementações de método de serviço e não define a capacidade do cliente ou o requisito para o fluxo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="3a9e2-124">No cliente, o serviço `TransactionFlowOption` configurações nas operações são refletidas na definição gerada do cliente a `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="3a9e2-125">Do Além disso, o serviço `transactionFlow` as configurações de propriedade são refletidas na configuração de aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="3a9e2-126">O cliente pode selecionar o transporte e protocolo selecionando apropriado `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  <span data-ttu-id="3a9e2-127">O comportamento observado deste exemplo é o mesmo, não importa qual transporte ou protocolo é escolhido.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="3a9e2-128">Que você iniciou a conexão ao serviço, o cliente cria um novo `TransactionScope` em torno de chamadas para as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="3a9e2-129">As chamadas para as operações são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3a9e2-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="3a9e2-130">O `Add` solicitação flui a transação necessária para o serviço e ações do serviço ocorrerem dentro do escopo de transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="3a9e2-131">A primeira `Subtract` solicitação também flui a transação permitida para o serviço e novamente as ações do serviço ocorrem dentro do escopo de transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="3a9e2-132">A segunda `Subtract` solicitação é executada dentro de um novo escopo de transação declarado com o `TransactionScopeOption.Suppress` opção.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="3a9e2-133">Isso elimina a transação do cliente inicial externa e a solicitação não fluir uma transação para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="3a9e2-134">Essa abordagem permite que um cliente explicitamente recusar e proteger contra o fluxo de uma transação para um serviço quando não é necessária.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="3a9e2-135">Ações do serviço ocorrem dentro do escopo de uma transação nova e desconectada.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="3a9e2-136">O `Multiply` solicitação não fluir uma transação para o serviço porque a definição de gerada do cliente do `ICalculator` interface inclui um <xref:System.ServiceModel.TransactionFlowAttribute> definido como <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="3a9e2-137">O `Divide` solicitação não fluir uma transação para o serviço porque novamente o cliente gerada pelo definição do `ICalculator` interface não incluir um `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="3a9e2-138">Ações de serviço novamente ocorrem dentro do escopo de outra transação nova e desconectada.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="3a9e2-139">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3a9e2-140">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="3a9e2-141">O registro em log as solicitações de operação de serviço são exibidos na janela do console do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="3a9e2-142">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="3a9e2-143">Após a execução bem-sucedida, o escopo de transação do cliente é concluída e todas as ações tomadas dentro do escopo são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="3a9e2-144">Especificamente, os registros de 5 observados são persistidos no banco de dados do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="3a9e2-145">O primeiro 2 deles ter ocorrido dentro do escopo de transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="3a9e2-146">Se ocorreu uma exceção em qualquer lugar dentro do cliente `TransactionScope` e em seguida, a transação não pode concluir.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="3a9e2-147">Isso faz com que os registros feitos no log dentro do escopo não ser confirmado no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="3a9e2-148">Esse efeito pode ser observado, repetindo o exemplo de execução após comentar a chamada para concluir o externo `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="3a9e2-149">Em tal uma execução, somente as ações últimos 3 (da segunda `Subtract`, o `Multiply` e o `Divide` solicitações) são registrados porque a transação do cliente não fluir para aqueles.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a9e2-150">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3a9e2-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a9e2-151">Para compilar a versão c# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="3a9e2-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="3a9e2-152">Certifique-se de que você tenha instalado o SQL Server Express Edition ou SQL Server e que a cadeia de caracteres de conexão foi definida corretamente no arquivo de configuração de aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="3a9e2-153">Para executar o exemplo sem usar um banco de dados, defina o `usingSql` valor no arquivo de configuração de aplicativo do serviço para `false`</span><span class="sxs-lookup"><span data-stu-id="3a9e2-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="3a9e2-154">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a9e2-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a9e2-155">Para configuração entre computadores, habilite o coordenador de transações distribuídas usando as instruções abaixo e usar a ferramenta de WsatConfig.exe do SDK do Windows para habilitar o suporte de rede de transações do WCF.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="3a9e2-156">Ver [Configurando o suporte a transações WS-Atomic](https://go.microsoft.com/fwlink/?LinkId=190370) para obter informações sobre como configurar WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="3a9e2-157">Se você executar o exemplo no mesmo computador ou em computadores diferentes, você deve configurar o Microsoft Distributed Transaction coordenador (MSDTC) para habilitar o fluxo de transações de rede e usar a ferramenta de WsatConfig.exe para habilitar o suporte de rede de transações do WCF.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="3a9e2-158">Para configurar o Microsoft Distributed Transaction coordenador (MSDTC) para dar suporte à execução do exemplo</span><span class="sxs-lookup"><span data-stu-id="3a9e2-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="3a9e2-159">Em um computador de serviço que executam o Windows Server 2003 ou Windows XP, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="3a9e2-160">Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="3a9e2-161">Expandir **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-161">Expand **Component Services**.</span></span> <span data-ttu-id="3a9e2-162">Abra o **computadores** pasta.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="3a9e2-163">Clique com botão direito **meu computador** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="3a9e2-164">Sobre o **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="3a9e2-165">Verifique **acesso DTC de rede** e **permitir entrada**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="3a9e2-166">Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="3a9e2-167">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="3a9e2-168">Em um computador de serviço que executam o Windows Server 2008 ou Windows Vista, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="3a9e2-169">Do **iniciar** menu, navegue até **painel de controle**, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="3a9e2-170">Expandir **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-170">Expand **Component Services**.</span></span> <span data-ttu-id="3a9e2-171">Abra o **computadores** pasta.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-171">Open the **Computers** folder.</span></span> <span data-ttu-id="3a9e2-172">Selecione **coordenador de transações distribuídas**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="3a9e2-173">Clique com botão direito **DTC coordenador** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="3a9e2-174">Sobre o **segurança** guia, seleção **acesso DTC de rede** e **permitir entrada**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="3a9e2-175">Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="3a9e2-176">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="3a9e2-177">O computador cliente, configure o MSDTC para permitir transações de rede de saída:</span><span class="sxs-lookup"><span data-stu-id="3a9e2-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="3a9e2-178">Do **iniciar** menu, navegue até `Control Panel`, em seguida, **ferramentas administrativas**e, em seguida, **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="3a9e2-179">Clique com botão direito **meu computador** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="3a9e2-180">Sobre o **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="3a9e2-181">Verifique **acesso DTC de rede** e **permitir saída**.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="3a9e2-182">Clique em **Okey**, em seguida, clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="3a9e2-183">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a9e2-184">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a9e2-185">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3a9e2-186">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a9e2-187">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3a9e2-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`

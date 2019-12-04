---
title: Fluxo de transação WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: db23c250014006655fa51ee5a2e5b54e15e4f964
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714594"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="838df-102">Fluxo de transação WS</span><span class="sxs-lookup"><span data-stu-id="838df-102">WS Transaction Flow</span></span>
<span data-ttu-id="838df-103">Este exemplo demonstra o uso de uma transação coordenada pelo cliente e as opções de cliente e servidor para o fluxo de transações usando a transação WS-Atomic ou o protocolo OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="838df-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="838df-104">Este exemplo é baseado no [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md) que implementa um serviço de calculadora, mas as operações são atribuídas para demonstrar o uso do `TransactionFlowAttribute` com a enumeração **TransactionFlowOption** para determinar para qual grau o fluxo de transações está habilitado.</span><span class="sxs-lookup"><span data-stu-id="838df-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="838df-105">Dentro do escopo da transação fluida, um log das operações solicitadas é gravado em um banco de dados e persiste até que a transação coordenada do cliente seja concluída – se a transação do cliente não for concluída, a transação do serviço Web garantirá que o as atualizações apropriadas para o banco de dados não são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="838df-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="838df-106">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="838df-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="838df-107">Depois de iniciar uma conexão com o serviço e uma transação, o cliente acessa várias operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="838df-108">O contrato para o serviço é definido da seguinte maneira com cada uma das operações que demonstram uma configuração diferente para o `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="838df-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="838df-109">Isso define as operações na ordem em que elas devem ser processadas:</span><span class="sxs-lookup"><span data-stu-id="838df-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="838df-110">Uma solicitação de operação de `Add` deve incluir uma transação fluida.</span><span class="sxs-lookup"><span data-stu-id="838df-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="838df-111">Uma solicitação de operação de `Subtract` pode incluir uma transação fluida.</span><span class="sxs-lookup"><span data-stu-id="838df-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="838df-112">Uma solicitação de operação de `Multiply` não deve incluir uma transação fluida por meio da configuração não permitida explícita.</span><span class="sxs-lookup"><span data-stu-id="838df-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="838df-113">Uma solicitação de operação `Divide` não deve incluir uma transação fluida por meio da omissão de um atributo `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="838df-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="838df-114">Para habilitar o fluxo de transações, as associações com a propriedade [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) habilitada devem ser usadas além dos atributos de operação apropriados.</span><span class="sxs-lookup"><span data-stu-id="838df-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="838df-115">Neste exemplo, a configuração do serviço expõe um ponto de extremidade TCP e um ponto de extremidade HTTP, além de um ponto de extremidade de troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="838df-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="838df-116">O ponto de extremidade TCP e o ponto de extremidade HTTP usam as seguintes associações, ambas com a propriedade [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="838df-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="838df-117">O netTcpbinding fornecido pelo sistema permite a especificação do transactionProtocol, enquanto que o wsHttpBinding fornecido pelo sistema usa apenas o protocolo WSAtomicTransactionOctober2004 mais interoperável.</span><span class="sxs-lookup"><span data-stu-id="838df-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="838df-118">O protocolo OleTransactions só está disponível para uso por clientes Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="838df-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="838df-119">Para a classe que implementa a interface `ICalculator`, todos os métodos são atribuídos com <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="838df-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="838df-120">Essa configuração declara que todas as ações executadas dentro do método ocorrem dentro do escopo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="838df-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="838df-121">Nesse caso, as ações executadas incluem a gravação no banco de dados de log.</span><span class="sxs-lookup"><span data-stu-id="838df-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="838df-122">Se a solicitação de operação incluir uma transação fluida, as ações ocorrerão dentro do escopo da transação de entrada ou um novo escopo de transação será gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="838df-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="838df-123">A propriedade <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> define o comportamento local para as implementações do método de serviço e não define a capacidade do cliente ou o requisito para o fluxo de uma transação.</span><span class="sxs-lookup"><span data-stu-id="838df-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="838df-124">No cliente, as configurações de `TransactionFlowOption` do serviço nas operações são refletidas na definição gerada do cliente da interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="838df-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="838df-125">Além disso, as configurações de propriedade de `transactionFlow` do serviço são refletidas na configuração do aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="838df-126">O cliente pode selecionar o transporte e o protocolo selecionando o `endpointConfigurationName`apropriado.</span><span class="sxs-lookup"><span data-stu-id="838df-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="838df-127">O comportamento observado desse exemplo é o mesmo, independentemente de qual protocolo ou transporte é escolhido.</span><span class="sxs-lookup"><span data-stu-id="838df-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="838df-128">Depois de iniciar a conexão com o serviço, o cliente cria um novo `TransactionScope` em volta das chamadas para as operações de serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="838df-129">As chamadas para as operações são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="838df-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="838df-130">A solicitação de `Add` flui a transação necessária para o serviço e as ações do serviço ocorrem dentro do escopo da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="838df-131">A primeira `Subtract` solicitação também flui a transação permitida para o serviço e, novamente, as ações do serviço ocorrem dentro do escopo da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="838df-132">A segunda `Subtract` solicitação é executada em um novo escopo de transação declarado com a opção `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="838df-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="838df-133">Isso suprime a transação externa inicial do cliente e a solicitação não flui uma transação para o serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="838df-134">Essa abordagem permite que um cliente recuse explicitamente e proteja-se contra o fluxo de uma transação para um serviço quando isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="838df-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="838df-135">As ações do serviço ocorrem no escopo de uma transação nova e não conectada.</span><span class="sxs-lookup"><span data-stu-id="838df-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="838df-136">A solicitação de `Multiply` não flui uma transação para o serviço porque a definição gerada pelo cliente da interface `ICalculator` inclui um <xref:System.ServiceModel.TransactionFlowAttribute> definido como <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="838df-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="838df-137">A solicitação de `Divide` não flui uma transação para o serviço porque, novamente, a definição gerada do cliente da interface `ICalculator` não inclui uma `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="838df-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="838df-138">As ações do serviço ocorrem novamente dentro do escopo de outra transação nova e não conectada.</span><span class="sxs-lookup"><span data-stu-id="838df-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="838df-139">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="838df-140">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
 <span data-ttu-id="838df-141">O registro em log das solicitações de operação de serviço é exibido na janela do console do serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="838df-142">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="838df-143">Após uma execução bem-sucedida, o escopo da transação do cliente é concluído e todas as ações executadas nesse escopo são confirmadas.</span><span class="sxs-lookup"><span data-stu-id="838df-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="838df-144">Especificamente, os 5 registros anotados são persistidos no banco de dados do serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="838df-145">As duas primeiras delas ocorreram dentro do escopo da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="838df-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="838df-146">Se ocorrer uma exceção em qualquer lugar dentro do `TransactionScope` do cliente, a transação não poderá ser concluída.</span><span class="sxs-lookup"><span data-stu-id="838df-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="838df-147">Isso faz com que os registros registrados nesse escopo não sejam confirmados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="838df-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="838df-148">Esse efeito pode ser observado repetindo-se a execução de exemplo depois de comentar a chamada para concluir a `TransactionScope`externa.</span><span class="sxs-lookup"><span data-stu-id="838df-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="838df-149">Nessa execução, apenas as três últimas ações (da segunda `Subtract`, as solicitações `Multiply` e `Divide`) são registradas porque a transação do cliente não fluiu para elas.</span><span class="sxs-lookup"><span data-stu-id="838df-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="838df-150">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="838df-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="838df-151">Para criar a C# versão do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="838df-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="838df-152">Verifique se você instalou o SQL Server Express Edition ou o SQL Server e se a cadeia de conexão foi definida corretamente no arquivo de configuração do aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="838df-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="838df-153">Para executar o exemplo sem usar um banco de dados, defina o valor `usingSql` no arquivo de configuração de aplicativo do serviço como `false`</span><span class="sxs-lookup"><span data-stu-id="838df-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="838df-154">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="838df-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="838df-155">Para configuração entre computadores, habilite o Coordenador de Transações Distribuídas usando as instruções abaixo e use a ferramenta WsatConfig. exe da SDK do Windows para habilitar o suporte à rede de transações do WCF.</span><span class="sxs-lookup"><span data-stu-id="838df-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="838df-156">Consulte [Configurando o suporte à transação WS-Atomic](https://go.microsoft.com/fwlink/?LinkId=190370) para obter informações sobre como configurar o WsatConfig. exe.</span><span class="sxs-lookup"><span data-stu-id="838df-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="838df-157">Se você executar o exemplo no mesmo computador ou em computadores diferentes, deverá configurar o Microsoft Coordenador de Transações Distribuídas (MSDTC) para habilitar o fluxo de transações de rede e usar a ferramenta WsatConfig. exe para habilitar o suporte à rede de transações do WCF.</span><span class="sxs-lookup"><span data-stu-id="838df-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="838df-158">Para configurar o Microsoft Coordenador de Transações Distribuídas (MSDTC) para dar suporte à execução do exemplo</span><span class="sxs-lookup"><span data-stu-id="838df-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="838df-159">Em um computador de serviço executando o Windows Server 2003 ou o Windows XP, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="838df-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="838df-160">No menu **Iniciar** , navegue até **painel de controle**, **Ferramentas administrativas**e serviços de **componentes**.</span><span class="sxs-lookup"><span data-stu-id="838df-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="838df-161">Expanda **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="838df-161">Expand **Component Services**.</span></span> <span data-ttu-id="838df-162">Abra a pasta **computadores** .</span><span class="sxs-lookup"><span data-stu-id="838df-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="838df-163">Clique com o botão direito do mouse em **meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="838df-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="838df-164">Na guia **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="838df-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="838df-165">Verifique o **acesso ao DTC de rede** e permita a **entrada**.</span><span class="sxs-lookup"><span data-stu-id="838df-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="838df-166">Clique em **OK**e em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="838df-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="838df-167">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="838df-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="838df-168">Em um computador de serviço executando o Windows Server 2008 ou o Windows Vista, configure o MSDTC para permitir transações de rede de entrada seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="838df-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="838df-169">No menu **Iniciar** , navegue até **painel de controle**, **Ferramentas administrativas**e serviços de **componentes**.</span><span class="sxs-lookup"><span data-stu-id="838df-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="838df-170">Expanda **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="838df-170">Expand **Component Services**.</span></span> <span data-ttu-id="838df-171">Abra a pasta **computadores** .</span><span class="sxs-lookup"><span data-stu-id="838df-171">Open the **Computers** folder.</span></span> <span data-ttu-id="838df-172">Selecione **Coordenador de transações distribuídas**.</span><span class="sxs-lookup"><span data-stu-id="838df-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="838df-173">Clique com o botão direito do mouse em **Coordenador DTC** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="838df-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="838df-174">Na guia **segurança** , marque **acesso DTC de rede** e **permitir entrada**.</span><span class="sxs-lookup"><span data-stu-id="838df-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="838df-175">Clique em **OK**e em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="838df-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="838df-176">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="838df-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="838df-177">No computador cliente, configure o MSDTC para permitir transações de rede de saída:</span><span class="sxs-lookup"><span data-stu-id="838df-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="838df-178">No menu **Iniciar** , navegue até `Control Panel`, **Ferramentas administrativas**e **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="838df-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="838df-179">Clique com o botão direito do mouse em **meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="838df-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="838df-180">Na guia **MSDTC** , clique em **configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="838df-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="838df-181">Verifique o **acesso ao DTC de rede** e permita a **saída**.</span><span class="sxs-lookup"><span data-stu-id="838df-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="838df-182">Clique em **OK**e em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="838df-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="838df-183">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="838df-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="838df-184">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="838df-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="838df-185">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="838df-185">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="838df-186">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="838df-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="838df-187">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="838df-187">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`

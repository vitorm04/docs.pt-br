---
title: Fluxo de transação WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183165"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="bf7bc-102">Fluxo de transação WS</span><span class="sxs-lookup"><span data-stu-id="bf7bc-102">WS Transaction Flow</span></span>
<span data-ttu-id="bf7bc-103">Esta amostra demonstra o uso de uma transação coordenada pelo cliente e das opções de fluxo de transações e cliente e servidor usando o protocolo WS-Atomic Transaction ou OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="bf7bc-104">Esta amostra é baseada no Getting Started que [implementa](../../../../docs/framework/wcf/samples/getting-started-sample.md) um serviço de calculadora, `TransactionFlowAttribute` mas as operações são atribuídas para demonstrar o uso do com a enumeração **TransactionFlowOption** para determinar até que ponto o fluxo de transação está habilitado.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="bf7bc-105">No escopo da transação fluída, um registro das operações solicitadas é gravado em um banco de dados e persiste até que a transação coordenada pelo cliente seja concluída - se a transação do cliente não for concluída, a transação de serviço web garante que a transação de serviço web assegure que a transação de serviço web atualizações apropriadas para o banco de dados não são cometidas.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf7bc-106">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bf7bc-107">Após o início de uma conexão com o serviço e uma transação, o cliente acessa diversas operações de atendimento.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="bf7bc-108">O contrato para o serviço é definido da seguinte forma com `TransactionFlowOption`cada uma das operações demonstrando um cenário diferente para o .</span><span class="sxs-lookup"><span data-stu-id="bf7bc-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="bf7bc-109">Isso define as operações na ordem em que devem ser processadas:</span><span class="sxs-lookup"><span data-stu-id="bf7bc-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="bf7bc-110">Uma `Add` solicitação de operação deve incluir uma transação fluída.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="bf7bc-111">Uma `Subtract` solicitação de operação pode incluir uma transação fluída.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="bf7bc-112">Uma `Multiply` solicitação de operação não deve incluir uma transação fluída através da configuração não permitida explícita.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="bf7bc-113">Uma `Divide` solicitação de operação não deve incluir uma `TransactionFlow` transação fluída através da omissão de um atributo.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="bf7bc-114">Para habilitar o fluxo de transações, as vinculações com a [ \<transaçãoFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriedade habilitada devem ser usadas, além dos atributos de operação apropriados.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="bf7bc-115">Nesta amostra, a configuração do serviço expõe um ponto final TCP e um ponto final HTTP, além de um ponto final do Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="bf7bc-116">O ponto final do TCP e o ponto final HTTP usam as seguintes vinculações, ambas com a [ \<propriedade transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) habilitada.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="bf7bc-117">O netTcpBinding fornecido pelo sistema permite a especificação do transactionProtocol, enquanto o wsHttpBinding fornecido pelo sistema usa apenas o protocolo WSAtomicTransactionOctoberOctober2004 mais interoperável.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="bf7bc-118">O protocolo OleTransactions só está disponível para uso por clientes da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf7bc-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="bf7bc-119">Para a classe que `ICalculator` implementa a interface, todos <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> os métodos são atribuídos com a propriedade definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="bf7bc-120">Esta configuração declara que todas as ações tomadas dentro do método ocorrem no âmbito de uma transação.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="bf7bc-121">Neste caso, as ações tomadas incluem o registro no banco de dados de log.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="bf7bc-122">Se a solicitação de operação incluir uma transação fluída, as ações ocorrerão no escopo da transação recebida ou um novo escopo de transação será gerado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf7bc-123">A <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> propriedade define o comportamento local para as implementações do método de serviço e não define a capacidade ou exigência do cliente para fluir uma transação.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="bf7bc-124">No cliente, as configurações do `TransactionFlowOption` serviço sobre as operações são refletidas `ICalculator` na definição gerada pelo cliente da interface.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="bf7bc-125">Além disso, as `transactionFlow` configurações de propriedade do serviço são refletidas na configuração do aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="bf7bc-126">O cliente pode selecionar o transporte e `endpointConfigurationName`o protocolo selecionando o apropriado .</span><span class="sxs-lookup"><span data-stu-id="bf7bc-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="bf7bc-127">O comportamento observado desta amostra é o mesmo, não importa qual protocolo ou transporte seja escolhido.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="bf7bc-128">Tendo iniciado a conexão com o `TransactionScope` serviço, o cliente cria uma nova em torno das chamadas para as operações de atendimento.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="bf7bc-129">As chamadas para as operações são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="bf7bc-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="bf7bc-130">A `Add` solicitação flui a transação necessária para o serviço e as ações do serviço ocorrem no âmbito da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="bf7bc-131">A `Subtract` primeira solicitação também flui a transação permitida para o serviço e novamente as ações do serviço ocorrem no âmbito da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="bf7bc-132">A `Subtract` segunda solicitação é realizada dentro de `TransactionScopeOption.Suppress` um novo escopo de transação declarado com a opção.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="bf7bc-133">Isso suprime a transação externa inicial do cliente e a solicitação não flui uma transação para o serviço.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="bf7bc-134">Essa abordagem permite que um cliente opte explicitamente e proteja contra o fluxo de uma transação para um serviço quando isso não é necessário.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="bf7bc-135">As ações do serviço ocorrem no âmbito de uma transação nova e não conectada.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="bf7bc-136">A `Multiply` solicitação não flui uma transação para o serviço `ICalculator` porque a <xref:System.ServiceModel.TransactionFlowAttribute> definição <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`gerada pelo cliente da interface inclui um conjunto para .</span><span class="sxs-lookup"><span data-stu-id="bf7bc-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="bf7bc-137">A `Divide` solicitação não flui uma transação para o serviço porque `ICalculator` novamente a `TransactionFlowAttribute`definição gerada pelo cliente da interface não inclui um .</span><span class="sxs-lookup"><span data-stu-id="bf7bc-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="bf7bc-138">As ações do serviço voltam a ocorrer no âmbito de outra transação nova e não conectada.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="bf7bc-139">Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bf7bc-140">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="bf7bc-141">O registro das solicitações de operação do serviço é exibido na janela do console do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="bf7bc-142">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="bf7bc-143">Após uma execução bem-sucedida, o escopo de transação do cliente é concluído e todas as ações tomadas dentro desse escopo são cometidas.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="bf7bc-144">Especificamente, os 5 registros anotados são persistidos no banco de dados do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="bf7bc-145">As duas primeiras delas ocorreram no âmbito da transação do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="bf7bc-146">Se uma exceção ocorreu em `TransactionScope` qualquer lugar dentro do cliente, então a transação não poderá ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="bf7bc-147">Isso faz com que os registros registrados nesse escopo não sejam comprometidos no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="bf7bc-148">Este efeito pode ser observado repetindo a amostra executada após comentar `TransactionScope`a chamada para completar o exterior .</span><span class="sxs-lookup"><span data-stu-id="bf7bc-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="bf7bc-149">Nessa execução, apenas as 3 últimas `Subtract`ações `Multiply` (a partir da segunda , as e as `Divide` solicitações) são registradas porque a transação do cliente não fluiu para essas.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bf7bc-150">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bf7bc-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bf7bc-151">Para construir a versão C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="bf7bc-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="bf7bc-152">Certifique-se de que você instalou o SQL Server Express Edition ou o SQL Server e que a seqüência de conexões foi configurada corretamente no arquivo de configuração do aplicativo do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="bf7bc-153">Para executar a amostra sem `usingSql` usar um banco de dados, defina o valor no arquivo de configuração do aplicativo do serviço para`false`</span><span class="sxs-lookup"><span data-stu-id="bf7bc-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="bf7bc-154">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bf7bc-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf7bc-155">Para a configuração entre máquinas, habilite o Coordenador de Transações Distribuídas usando as instruções abaixo e use a ferramenta WsatConfig.exe do Windows SDK para permitir o suporte à rede de transações WCF.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="bf7bc-156">Para obter informações sobre a configuração do WsatConfig.exe, consulte [Configurando o suporte à transação WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="bf7bc-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="bf7bc-157">Se você executar a amostra no mesmo computador ou em computadores diferentes, você deve configurar o Microsoft Distributed Transaction Coordinator (MSDTC) para permitir o fluxo de transações de rede e usar a ferramenta WsatConfig.exe para habilitar o suporte à rede de transações WCF.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="bf7bc-158">Para configurar o Microsoft Distributed Transaction Coordinator (MSDTC) para suportar a execução da amostra</span><span class="sxs-lookup"><span data-stu-id="bf7bc-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="bf7bc-159">Em uma máquina de serviço executando o Windows Server 2003 ou o Windows XP, configure o MSDTC para permitir transações de rede recebidas seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="bf7bc-160">Do menu **Iniciar,** navegue até o **Painel de Controle,** depois **Ferramentas Administrativas**e, em seguida, **Serviços de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="bf7bc-161">Expandir **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-161">Expand **Component Services**.</span></span> <span data-ttu-id="bf7bc-162">Abra a pasta **Computadores.**</span><span class="sxs-lookup"><span data-stu-id="bf7bc-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="bf7bc-163">Clique com o botão direito do mouse **em Meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="bf7bc-164">Na guia **MSDTC,** clique **em Configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="bf7bc-165">Verifique **o acesso ao DTC da rede** e permita a **entrada**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="bf7bc-166">Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="bf7bc-167">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="bf7bc-168">Em uma máquina de serviço executando o Windows Server 2008 ou o Windows Vista, configure o MSDTC para permitir transações de rede recebidas seguindo estas instruções.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="bf7bc-169">Do menu **Iniciar,** navegue até o **Painel de Controle,** depois **Ferramentas Administrativas**e, em seguida, **Serviços de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="bf7bc-170">Expandir **serviços de componentes**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-170">Expand **Component Services**.</span></span> <span data-ttu-id="bf7bc-171">Abra a pasta **Computadores.**</span><span class="sxs-lookup"><span data-stu-id="bf7bc-171">Open the **Computers** folder.</span></span> <span data-ttu-id="bf7bc-172">Selecione **coordenador de transações distribuídas**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="bf7bc-173">Clique com o botão direito do mouse **no coordenador do DTC** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="bf7bc-174">Na guia **Segurança,** verifique o **acesso dtc da rede** e permita a **entrada**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="bf7bc-175">Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="bf7bc-176">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="bf7bc-177">Na máquina cliente, configure o MSDTC para permitir transações de rede de saída:</span><span class="sxs-lookup"><span data-stu-id="bf7bc-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="bf7bc-178">A partir do menu `Control Panel` **Iniciar,** navegue até, em seguida, Ferramentas **Administrativas**e, em seguida, **Serviços de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="bf7bc-179">Clique com o botão direito do mouse **em Meu computador** e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="bf7bc-180">Na guia **MSDTC,** clique **em Configuração de segurança**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="bf7bc-181">Verifique **o acesso ao DTC da rede** e permita a **saída**.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="bf7bc-182">Clique **em OK**e clique em **Sim** para reiniciar o serviço MSDTC.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="bf7bc-183">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf7bc-184">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bf7bc-185">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bf7bc-186">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="bf7bc-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf7bc-187">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bf7bc-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`

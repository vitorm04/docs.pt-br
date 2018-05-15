---
title: 'Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9305fd2a0e61a71f6875d6061f835e9cdae5dd1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="27a65-102">Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência</span><span class="sxs-lookup"><span data-stu-id="27a65-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="27a65-103">A Biblioteca de Fluxo de dados TPL fornece as classes <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> para que você possa receber e armazenar em buffer os dados de uma ou mais fontes e, depois, propagar esses dados armazenados em buffer como uma coleção.</span><span class="sxs-lookup"><span data-stu-id="27a65-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="27a65-104">Este mecanismo de envio em lote é útil quando você coleta dados de uma ou mais fontes e, em seguida, processa vários elementos de dados como um lote.</span><span class="sxs-lookup"><span data-stu-id="27a65-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="27a65-105">Por exemplo, considere um aplicativo que usa o fluxo de dados para inserir registros em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="27a65-106">Essa operação pode ser mais eficiente se vários itens forem inseridos ao mesmo tempo, em vez de um de cada vez sequencialmente.</span><span class="sxs-lookup"><span data-stu-id="27a65-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="27a65-107">Este documento descreve como usar a classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> para melhorar a eficiência dessas operações de inserção de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="27a65-108">Também descreve como usar a classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> para capturar os resultados e todas as exceções que ocorrem quando o programa lê de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="27a65-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="27a65-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="27a65-110">Leia a seção Blocos de ingresso no documento [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) antes de começar este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="27a65-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="27a65-111">Certifique-se de que você tenha uma cópia do banco de dados Northwind, Northwind.sdf, disponível em seu computador.</span><span class="sxs-lookup"><span data-stu-id="27a65-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="27a65-112">Normalmente, esse arquivo está localizado na pasta %Arquivos de Programas%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span><span class="sxs-lookup"><span data-stu-id="27a65-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="27a65-113">Em algumas versões do Windows, não é possível se conectar ao Northwind.sdf quando o Visual Studio está em execução em um modo não administrador.</span><span class="sxs-lookup"><span data-stu-id="27a65-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="27a65-114">Para se conectar ao Northwind.sdf, inicie o Visual Studio ou um prompt de comando deste programa no modo **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="27a65-114">To connect to Northwind.sdf, start Visual Studio or a Visual Studio command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="27a65-115">Este passo a passo contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="27a65-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="27a65-116">Criar o Aplicativo de Console</span><span class="sxs-lookup"><span data-stu-id="27a65-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="27a65-117">Definir a classe do funcionário</span><span class="sxs-lookup"><span data-stu-id="27a65-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="27a65-118">Definir as operações de banco de dados do funcionário</span><span class="sxs-lookup"><span data-stu-id="27a65-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="27a65-119">Adicionar dados de funcionário ao banco de dados sem o uso de buffer</span><span class="sxs-lookup"><span data-stu-id="27a65-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="27a65-120">Usar o armazenamento em buffer para adicionar dados de funcionário ao banco de dados</span><span class="sxs-lookup"><span data-stu-id="27a65-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="27a65-121">Usar o ingresso em buffer para ler dados de funcionário do banco de dados</span><span class="sxs-lookup"><span data-stu-id="27a65-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="27a65-122">O exemplo completo</span><span class="sxs-lookup"><span data-stu-id="27a65-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="27a65-123">Criando o Aplicativo de Console</span><span class="sxs-lookup"><span data-stu-id="27a65-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="27a65-124">No Visual Studio, crie um projeto de **aplicativo de console** do Visual Basic ou do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="27a65-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="27a65-125">Neste documento, o projeto é chamado `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="27a65-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="27a65-126">Em seu projeto, adicione uma referência ao System.Data.SqlServerCe.dll e uma referência a System.Threading.Tasks.Dataflow.dll.</span><span class="sxs-lookup"><span data-stu-id="27a65-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="27a65-127">Verifique se o Form1.cs (Form1.vb para Visual Basic) contém as seguintes instruções `using` (`Imports` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="27a65-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="27a65-128">Adicione os membros de dados a seguir à classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="27a65-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="27a65-129">Definir a classe do funcionário</span><span class="sxs-lookup"><span data-stu-id="27a65-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="27a65-130">Adicione a classe `Program` à classe `Employee`.</span><span class="sxs-lookup"><span data-stu-id="27a65-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="27a65-131">A classe `Employee` contém três propriedades: `EmployeeID`, `LastName` e `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="27a65-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="27a65-132">Essas propriedades correspondem às colunas `Employee ID`, `Last Name` e `First Name` na tabela `Employees` no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="27a65-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="27a65-133">Para esta demonstração, a classe `Employee` também define o método `Random`, que cria um objeto `Employee` com valores aleatórios para suas propriedades.</span><span class="sxs-lookup"><span data-stu-id="27a65-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="27a65-134">Definir as operações de banco de dados do funcionário</span><span class="sxs-lookup"><span data-stu-id="27a65-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="27a65-135">Adicione à classe `Program` os métodos `InsertEmployees`, `GetEmployeeCount` e `GetEmployeeID`.</span><span class="sxs-lookup"><span data-stu-id="27a65-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="27a65-136">O método `InsertEmployees` adiciona novos registros de funcionário ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="27a65-137">O método `GetEmployeeCount` recupera o número de entradas na tabela `Employees`.</span><span class="sxs-lookup"><span data-stu-id="27a65-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="27a65-138">O método `GetEmployeeID` recupera o identificador do primeiro funcionário que tem o nome fornecido.</span><span class="sxs-lookup"><span data-stu-id="27a65-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="27a65-139">Cada um desses métodos usa uma cadeia de caracteres de conexão para o banco de dados Northwind e usa a funcionalidade no namespace `System.Data.SqlServerCe` para se comunicar com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="27a65-140">Adicionar dados de funcionário ao banco de dados sem o uso de buffer</span><span class="sxs-lookup"><span data-stu-id="27a65-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="27a65-141">Adicione à classe `Program` os métodos `AddEmployees` e `PostRandomEmployees`.</span><span class="sxs-lookup"><span data-stu-id="27a65-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="27a65-142">O método `AddEmployees` adiciona dados aleatórios de funcionários ao banco de dados usando o fluxo de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="27a65-143">Ele cria um objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> que chama o método `InsertEmployees` para adicionar uma entrada de funcionário ao banco de dados.</span><span class="sxs-lookup"><span data-stu-id="27a65-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="27a65-144">Em seguida, o método `AddEmployees` chama o método `PostRandomEmployees` para postar vários objetos `Employee` para o objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="27a65-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="27a65-145">Depois, o método `AddEmployees` espera a conclusão de todas as operações de inserção.</span><span class="sxs-lookup"><span data-stu-id="27a65-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="27a65-146">Usar o armazenamento em buffer para adicionar dados de funcionário ao banco de dados</span><span class="sxs-lookup"><span data-stu-id="27a65-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="27a65-147">Adicione à classe `Program` o método `AddEmployeesBatched`.</span><span class="sxs-lookup"><span data-stu-id="27a65-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="27a65-148">Esse método é semelhante a `AddEmployees`, exceto que ele também usa a classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> para armazenar em buffer vários objetos `Employee` antes de enviar esses objetos ao objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="27a65-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="27a65-149">Como a classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propaga vários elementos como uma coleção, o objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> é modificado a fim de funcionar em uma matriz de objetos `Employee`.</span><span class="sxs-lookup"><span data-stu-id="27a65-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="27a65-150">Assim como no método `AddEmployees`, `AddEmployeesBatched` chama o método `PostRandomEmployees` para postar vários objetos `Employee`; no entanto, `AddEmployeesBatched`posta esses objetos no objeto <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>.</span><span class="sxs-lookup"><span data-stu-id="27a65-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="27a65-151">O método `AddEmployeesBatched` também espera a conclusão de todas as operações de inserção.</span><span class="sxs-lookup"><span data-stu-id="27a65-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="27a65-152">Usar o ingresso em buffer para ler dados de funcionário do banco de dados</span><span class="sxs-lookup"><span data-stu-id="27a65-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="27a65-153">Adicione à classe `Program` o método `GetRandomEmployees`.</span><span class="sxs-lookup"><span data-stu-id="27a65-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="27a65-154">Esse método imprime as informações sobre funcionários aleatórios no console.</span><span class="sxs-lookup"><span data-stu-id="27a65-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="27a65-155">Ele cria vários objetos `Employee` aleatórios e chama o método `GetEmployeeID` para recuperar o identificador exclusivo de cada objeto.</span><span class="sxs-lookup"><span data-stu-id="27a65-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="27a65-156">Como o método `GetEmployeeID` lança uma exceção se nenhum funcionário corresponder aos nomes e sobrenomes indicados, o método `GetRandomEmployees` usa a classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> para armazenar objetos `Employee` para chamada bem-sucedida a `GetEmployeeID`, e objetos <xref:System.Exception?displayProperty=nameWithType> para chamadas com falha.</span><span class="sxs-lookup"><span data-stu-id="27a65-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="27a65-157">O objeto <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> neste exemplo age em um objeto <xref:System.Tuple%602> que contém uma lista de objetos `Employee` e uma lista de objetos <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="27a65-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="27a65-158">O objeto <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propaga esse dados quando a soma dos objetos `Employee` e <xref:System.Exception> recebidos for igual ao tamanho do lote.</span><span class="sxs-lookup"><span data-stu-id="27a65-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="27a65-159">O Exemplo Completo</span><span class="sxs-lookup"><span data-stu-id="27a65-159">The Complete Example</span></span>  
 <span data-ttu-id="27a65-160">O exemplo a seguir mostra todo o código.</span><span class="sxs-lookup"><span data-stu-id="27a65-160">The following example shows the complete code.</span></span> <span data-ttu-id="27a65-161">O método `Main` compara o tempo necessário para executar inserções em lotes do banco de dados em comparação com o tempo para executar as inserções do banco de dados sem lote.</span><span class="sxs-lookup"><span data-stu-id="27a65-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="27a65-162">Ele também demonstra o uso do ingresso em buffer para ler dados de funcionário do banco de dados e também informar erros.</span><span class="sxs-lookup"><span data-stu-id="27a65-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="27a65-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a65-163">See Also</span></span>  
 [<span data-ttu-id="27a65-164">Fluxo de dados</span><span class="sxs-lookup"><span data-stu-id="27a65-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

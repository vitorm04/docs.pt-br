---
title: "Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Explicação passo a passo: Usando BatchBlock e BatchedJoinBlock para aumentar a eficiência
A biblioteca de fluxo de dados TPL fornece o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> para que possa receber e buffer de dados de uma ou mais fontes e propagadas esses dados em buffer como uma coleção de classes. Este mecanismo de envio em lote é útil quando você coleta dados de uma ou mais fontes e, em seguida, processar vários elementos de dados como um lote. Por exemplo, considere um aplicativo que usa o fluxo de dados para inserir registros em um banco de dados. Essa operação pode ser mais eficiente se vários itens são inseridos sequencialmente ao mesmo tempo, em vez de um de cada vez. Este documento descreve como usar o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> operações de inserção de classe para melhorar a eficiência desse banco de dados. Ele também descreve como usar o <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe para capturar os resultados e todas as exceções que ocorrem quando o programa lê de um banco de dados.  
  
> [!TIP]
>  A biblioteca de fluxo de dados TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) não é distribuído com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para instalar o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o `Microsoft.Tpl.Dataflow` pacote.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
1.  Ler a seção blocos ingressar o [fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) documento antes de começar este passo a passo.  
  
2.  Certifique-se de que você tenha uma cópia do banco de dados Northwind, Northwind. sdf, disponível em seu computador. Normalmente, esse arquivo está localizado na pasta % programa Files%\Microsoft SQL Server Compact Edition\v3.5\Samples.\\.  
  
    > [!IMPORTANT]
    >  Em algumas versões do Windows, você não pode se conectar a Northwind. sdf se [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] está em execução em um modo não administrador. Para se conectar a Northwind. sdf, iniciar [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou um [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] prompt de comando no **executar como administrador** modo.  
  
 Este passo a passo contém as seguintes seções:  
  
-   [Criando o aplicativo de Console](#creating)  
  
-   [Definição da classe do funcionário](#employeeClass)  
  
-   [Definindo as operações de banco de dados de funcionário](#operations)  
  
-   [Adicionando dados de funcionário no banco de dados sem o uso de buffer](#nonBuffering)  
  
-   [Usando o armazenamento em buffer para adicionar dados de funcionário no banco de dados](#buffering)  
  
-   [Usando a associação em buffer para ler dados de funcionário do banco de dados](#bufferedJoin)  
  
-   [O exemplo completo](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Criando o Aplicativo de Console  
  
<a name="consoleApp"></a>   
1.  Em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], criar um Visual c# ou Visual Basic **aplicativo de Console** projeto. Neste documento, o projeto é denominado `DataflowBatchDatabase`.  
  
2.  No seu projeto, adicione uma referência ao SqlServerCe e uma referência a System.Threading.Tasks.Dataflow.dll.  
  
3.  Certifique-se de que Form1 (Form1. vb para [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contém o seguinte `using` (`Imports` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) instruções.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Adicionar os seguintes membros de dados para o `Program` classe.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Definição da classe do funcionário  
 Adicionar ao `Program` classe o `Employee` classe.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 O `Employee` classe contém três propriedades, `EmployeeID`, `LastName`, e `FirstName`. Essas propriedades correspondem ao `Employee ID`, `Last Name`, e `First Name` colunas o `Employees` tabela no banco de dados Northwind. Para esta demonstração, o `Employee` classe também define o `Random` método, que cria um `Employee` objeto que tem valores aleatórios para suas propriedades.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Definindo as operações de banco de dados de funcionário  
 Adicionar ao `Program` classe o `InsertEmployees`, `GetEmployeeCount`, e `GetEmployeeID` métodos.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 O `InsertEmployees` método adiciona novos registros de funcionário no banco de dados. O `GetEmployeeCount` método recupera o número de entradas na `Employees` tabela. O `GetEmployeeID` método recupera o identificador do primeiro funcionário que tem o nome fornecido. Cada um desses métodos usa uma cadeia de caracteres de conexão para o banco de dados Northwind e usa a funcionalidade de `System.Data.SqlServerCe` namespace para se comunicar com o banco de dados.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Adicionando dados de funcionário no banco de dados sem o uso de buffer  
 Adicionar ao `Program` classe o `AddEmployees` e `PostRandomEmployees` métodos.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 O `AddEmployees` método adiciona dados de funcionário aleatória para o banco de dados usando o fluxo de dados. Ele cria um <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto que chama o `InsertEmployees` método para adicionar uma entrada de funcionário no banco de dados. O `AddEmployees` , em seguida, chama um método de `PostRandomEmployees` método para postar vários `Employee` objetos para o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto. O `AddEmployees` método espera para todas as operações para terminar de inserção.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>Usando o armazenamento em buffer para adicionar dados de funcionário no banco de dados  
 Adicionar ao `Program` classe o `AddEmployeesBatched` método.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Esse método é semelhante `AddEmployees`, exceto que ele também usa o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe para armazenar em buffer vários `Employee` objetos antes de enviar esses objetos para o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto. Porque o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe propaga vários elementos em uma coleção, o <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto é modificado para funcionar em uma matriz de `Employee` objetos. Como no `AddEmployees` método, `AddEmployeesBatched` chamadas a `PostRandomEmployees` método para postar vários `Employee` objetos; no entanto, `AddEmployeesBatched` envia esses objetos para o <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objeto. O `AddEmployeesBatched` método também aguarda para todas as operações para terminar de inserção.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>Usando a associação em buffer para ler dados de funcionário do banco de dados  
 Adicionar ao `Program` classe o `GetRandomEmployees` método.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Esse método imprime as informações sobre funcionários aleatórios para o console. Ele cria vários aleatório `Employee` objetos e chama o `GetEmployeeID` método para recuperar o identificador exclusivo para cada objeto. Porque o `GetEmployeeID` método lançará uma exceção se não houver nenhum funcionário correspondência com nomes e sobrenomes determinados, o `GetRandomEmployees` método usa o <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe para armazenar `Employee` objetos para chamada bem-sucedida a `GetEmployeeID` e <xref:System.Exception?displayProperty=nameWithType> objetos para chamadas com falha. O <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objeto neste exemplo age em uma <xref:System.Tuple%602> objeto que contém uma lista de `Employee` objetos e uma lista de <xref:System.Exception> objetos. O <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objeto propaga esse dados quando a soma de recebido `Employee` e <xref:System.Exception> contagens de objeto é igual ao tamanho de lote.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>O Exemplo Completo  
 O exemplo a seguir mostra o código completo. O `Main` método compara a hora em que é necessário para executar inserções em lotes do banco de dados em comparação com o tempo para executar as inserções do banco de dados sem lote. Ele também demonstra o uso de junção em buffer para ler dados de funcionário do banco de dados e também informar erros.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Consulte também  
 [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)

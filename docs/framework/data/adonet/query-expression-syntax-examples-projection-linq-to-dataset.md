---
title: 'Exemplos de sintaxe de expressão de consulta: Projeção (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 64d8454a9eacca81e93677c2b63dc5afdcc27d64
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091689"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="f44c4-102">Exemplos de sintaxe de expressão de consulta: Projeção (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f44c4-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="f44c4-103">Os exemplos neste tópico demonstram como usar os métodos <xref:System.Linq.Enumerable.Select%2A> e <xref:System.Linq.Enumerable.SelectMany%2A> para consultar um <xref:System.Data.DataSet> usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="f44c4-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="f44c4-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f44c4-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f44c4-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f44c4-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f44c4-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="f44c4-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f44c4-107">Para obter mais informações, confira [Como: Criar um projeto LINQ to DataSet no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f44c4-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="f44c4-108">Selecionar</span><span class="sxs-lookup"><span data-stu-id="f44c4-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="f44c4-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f44c4-109">Example</span></span>  
 <span data-ttu-id="f44c4-110">Este exemplo usa o método <xref:System.Linq.Enumerable.Select%2A> para retornar todas as linhas da tabela de `Product` e exibir os nomes de produto.</span><span class="sxs-lookup"><span data-stu-id="f44c4-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="f44c4-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f44c4-111">Example</span></span>  
 <span data-ttu-id="f44c4-112">Este exemplo usa <xref:System.Linq.Enumerable.Select%2A> para retornar somente uma sequência de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="f44c4-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="f44c4-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="f44c4-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="f44c4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f44c4-114">Example</span></span>  
 <span data-ttu-id="f44c4-115">Este exemplo usa `From …, …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde `TotalDue` é menor que 500,00.</span><span class="sxs-lookup"><span data-stu-id="f44c4-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="f44c4-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f44c4-116">Example</span></span>  
 <span data-ttu-id="f44c4-117">Este exemplo usa `From …, …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos feitos em 1º de outubro de 2002 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f44c4-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="f44c4-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f44c4-118">Example</span></span>  
 <span data-ttu-id="f44c4-119">Este exemplo usa `From …, …` (o equivalente do método <xref:System.Linq.Enumerable.SelectMany%2A>) para selecionar todos os pedidos onde o total do pedido é maior que 10000,00 e usa a atribuição `From` para evitar solicitar o total duas vezes.</span><span class="sxs-lookup"><span data-stu-id="f44c4-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="f44c4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f44c4-120">See also</span></span>
- [<span data-ttu-id="f44c4-121">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="f44c4-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="f44c4-122">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f44c4-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="f44c4-123">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="f44c4-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f44c4-124">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f44c4-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

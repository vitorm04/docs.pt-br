---
title: 'Exemplos de sintaxe de expressão de consulta: Operadores agregados (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: e7151fd85c7e3988051ed87a60acc2b53a8af646
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878690"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="d5cbb-102">Exemplos de sintaxe de expressão de consulta: Operadores agregados (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d5cbb-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="d5cbb-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, e métodos de <xref:System.Linq.Enumerable.Sum%2A> para ver <xref:System.Data.DataSet> e os dados agregados usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="d5cbb-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="d5cbb-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d5cbb-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d5cbb-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="d5cbb-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d5cbb-107">Para obter mais informações, confira [Como: Criar um projeto LINQ to DataSet no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="d5cbb-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="d5cbb-108">Média</span><span class="sxs-lookup"><span data-stu-id="d5cbb-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5cbb-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-109">Example</span></span>  
 <span data-ttu-id="d5cbb-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para localizar o preço médio da tabela de produtos de cada estilo.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="d5cbb-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-111">Example</span></span>  
 <span data-ttu-id="d5cbb-112">Este exemplo usa <xref:System.Linq.Enumerable.Average%2A> para obter o total vencido médio para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="d5cbb-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d5cbb-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-113">Example</span></span>  
 <span data-ttu-id="d5cbb-114">Este exemplo usa <xref:System.Linq.Enumerable.Average%2A> para obter os pedidos com `TotalDue` médio para cada contato.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="d5cbb-115">Contagem</span><span class="sxs-lookup"><span data-stu-id="d5cbb-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5cbb-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-116">Example</span></span>  
 <span data-ttu-id="d5cbb-117">Este exemplo usa <xref:System.Linq.Enumerable.Count%2A> para retornar uma lista de IDs de contato e quantos pedidos cada um possui.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="d5cbb-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-118">Example</span></span>  
 <span data-ttu-id="d5cbb-119">Este exemplo agrupa produtos pela cor e usa <xref:System.Linq.Enumerable.Count%2A> para retornar o número de produtos em cada grupo de cor.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="d5cbb-120">Máx.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5cbb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-121">Example</span></span>  
 <span data-ttu-id="d5cbb-122">Este exemplo usa o método de <xref:System.Linq.Enumerable.Max%2A> para obter o total vencido o maior para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="d5cbb-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d5cbb-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-123">Example</span></span>  
 <span data-ttu-id="d5cbb-124">Este exemplo usa o método de <xref:System.Linq.Enumerable.Max%2A> para obter os pedidos com `TotalDue` o maior para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="d5cbb-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="d5cbb-125">Mín.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5cbb-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-126">Example</span></span>  
 <span data-ttu-id="d5cbb-127">Este exemplo usa o método de <xref:System.Linq.Enumerable.Min%2A> para obter o total vencido o menor para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="d5cbb-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d5cbb-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-128">Example</span></span>  
 <span data-ttu-id="d5cbb-129">Este exemplo usa o método de <xref:System.Linq.Enumerable.Min%2A> para obter os pedidos com o total vencido o menor para cada contato.</span><span class="sxs-lookup"><span data-stu-id="d5cbb-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="d5cbb-130">Sum</span><span class="sxs-lookup"><span data-stu-id="d5cbb-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="d5cbb-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5cbb-131">Example</span></span>  
 <span data-ttu-id="d5cbb-132">Este exemplo usa o método de <xref:System.Linq.Enumerable.Sum%2A> para obter o total vencido para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="d5cbb-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d5cbb-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5cbb-133">See also</span></span>

- [<span data-ttu-id="d5cbb-134">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="d5cbb-134">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="d5cbb-135">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d5cbb-135">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="d5cbb-136">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="d5cbb-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d5cbb-137">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5cbb-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

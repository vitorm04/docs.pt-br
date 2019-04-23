---
title: 'Exemplos de sintaxe de consulta baseada em método: Operadores agregados (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 88d9c7299c9dbf024a07f223ef7ec7d03f8066d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215125"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="4d24e-102">Exemplos de sintaxe de consulta baseada em método: Operadores agregados (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4d24e-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="4d24e-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, e operadores de <xref:System.Linq.Enumerable.Sum%2A> para ver <xref:System.Data.DataSet> e os dados agregados usando a sintaxe da consulta de método.</span><span class="sxs-lookup"><span data-stu-id="4d24e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="4d24e-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="4d24e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4d24e-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4d24e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4d24e-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="4d24e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="4d24e-107">Para obter mais informações, confira [Como: Criar um projeto LINQ to DataSet no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="4d24e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="4d24e-108">Agregado</span><span class="sxs-lookup"><span data-stu-id="4d24e-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-109">Example</span></span>  
 <span data-ttu-id="4d24e-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Aggregate%2A> para obter os primeiros 5 contatos da tabela de `Contact` e criar uma lista delimitada por vírgulas dos sobrenomes.</span><span class="sxs-lookup"><span data-stu-id="4d24e-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="4d24e-111">Média</span><span class="sxs-lookup"><span data-stu-id="4d24e-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-112">Example</span></span>  
 <span data-ttu-id="4d24e-113">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para localizar o preço médio da tabela de produtos.</span><span class="sxs-lookup"><span data-stu-id="4d24e-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-114">Example</span></span>  
 <span data-ttu-id="4d24e-115">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para localizar o preço médio da tabela de produtos de cada estilo.</span><span class="sxs-lookup"><span data-stu-id="4d24e-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-116">Example</span></span>  
 <span data-ttu-id="4d24e-117">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para localizar o total vencido médio.</span><span class="sxs-lookup"><span data-stu-id="4d24e-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-118">Example</span></span>  
 <span data-ttu-id="4d24e-119">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para obter o total vencido médio para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="4d24e-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-120">Example</span></span>  
 <span data-ttu-id="4d24e-121">Este exemplo usa o método de <xref:System.Linq.Enumerable.Average%2A> para obter os pedidos com `TotalDue` médio para cada contato.</span><span class="sxs-lookup"><span data-stu-id="4d24e-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="4d24e-122">Contagem</span><span class="sxs-lookup"><span data-stu-id="4d24e-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-123">Example</span></span>  
 <span data-ttu-id="4d24e-124">Este exemplo usa o método de <xref:System.Linq.Enumerable.Count%2A> para retornar o número de produtos na tabela de `Product` .</span><span class="sxs-lookup"><span data-stu-id="4d24e-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-125">Example</span></span>  
 <span data-ttu-id="4d24e-126">Este exemplo usa o método de <xref:System.Linq.Enumerable.Count%2A> para retornar uma lista de IDs de contato e quantos pedidos cada um possui.</span><span class="sxs-lookup"><span data-stu-id="4d24e-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-127">Example</span></span>  
 <span data-ttu-id="4d24e-128">Este exemplo agrupa produtos pela cor e usa o método de <xref:System.Linq.Enumerable.Count%2A> para retornar o número de produtos em cada grupo de cor.</span><span class="sxs-lookup"><span data-stu-id="4d24e-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="4d24e-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="4d24e-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-130">Example</span></span>  
 <span data-ttu-id="4d24e-131">Este exemplo obtém a contagem de contatos como um inteiro long.</span><span class="sxs-lookup"><span data-stu-id="4d24e-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="4d24e-132">Máx.</span><span class="sxs-lookup"><span data-stu-id="4d24e-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-133">Example</span></span>  
 <span data-ttu-id="4d24e-134">Este exemplo usa o método de <xref:System.Linq.Enumerable.Max%2A> para obter o total vencido maior.</span><span class="sxs-lookup"><span data-stu-id="4d24e-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-135">Example</span></span>  
 <span data-ttu-id="4d24e-136">Este exemplo usa o método de <xref:System.Linq.Enumerable.Max%2A> para obter o total vencido o maior para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="4d24e-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-137">Example</span></span>  
 <span data-ttu-id="4d24e-138">Este exemplo usa o método de <xref:System.Linq.Enumerable.Max%2A> para obter os pedidos com `TotalDue` o maior para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="4d24e-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="4d24e-139">Mín.</span><span class="sxs-lookup"><span data-stu-id="4d24e-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-140">Example</span></span>  
 <span data-ttu-id="4d24e-141">Este exemplo usa o método de <xref:System.Linq.Enumerable.Min%2A> para obter o total vencido o menor.</span><span class="sxs-lookup"><span data-stu-id="4d24e-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-142">Example</span></span>  
 <span data-ttu-id="4d24e-143">Este exemplo usa o método de <xref:System.Linq.Enumerable.Min%2A> para obter o total vencido o menor para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="4d24e-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-144">Example</span></span>  
 <span data-ttu-id="4d24e-145">Este exemplo usa o método de <xref:System.Linq.Enumerable.Min%2A> para obter os pedidos com o total vencido o menor para cada contato.</span><span class="sxs-lookup"><span data-stu-id="4d24e-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="4d24e-146">Sum</span><span class="sxs-lookup"><span data-stu-id="4d24e-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="4d24e-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-147">Example</span></span>  
 <span data-ttu-id="4d24e-148">Este exemplo usa o método de <xref:System.Linq.Enumerable.Sum%2A> para obter o número total de quantidades de ordem na tabela de `SalesOrderDetail` .</span><span class="sxs-lookup"><span data-stu-id="4d24e-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="4d24e-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d24e-149">Example</span></span>  
 <span data-ttu-id="4d24e-150">Este exemplo usa o método de <xref:System.Linq.Enumerable.Sum%2A> para obter o total vencido para cada identificação de contatos</span><span class="sxs-lookup"><span data-stu-id="4d24e-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4d24e-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d24e-151">See also</span></span>

- [<span data-ttu-id="4d24e-152">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="4d24e-152">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="4d24e-153">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="4d24e-153">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="4d24e-154">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="4d24e-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4d24e-155">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d24e-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

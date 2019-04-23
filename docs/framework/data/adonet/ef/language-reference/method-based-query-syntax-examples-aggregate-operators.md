---
title: 'Exemplos de sintaxe de consulta baseada em método: Operadores de agregação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: 06609ce14edeb7e9306816b8a8d58d2212b61751
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207767"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="07540-102">Exemplos de sintaxe de consulta baseada em método: Operadores de agregação</span><span class="sxs-lookup"><span data-stu-id="07540-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="07540-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, e <xref:System.Linq.Enumerable.Sum%2A> métodos para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de consulta com base em método.</span><span class="sxs-lookup"><span data-stu-id="07540-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="07540-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="07540-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="07540-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="07540-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="07540-106">Média</span><span class="sxs-lookup"><span data-stu-id="07540-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-107">Example</span></span>  
 <span data-ttu-id="07540-108">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Average%2A> para localizar o preço médio da lista de produtos.</span><span class="sxs-lookup"><span data-stu-id="07540-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-109">Example</span></span>  
 <span data-ttu-id="07540-110">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Average%2A> para localizar o preço médio da lista de produtos de cada estilo.</span><span class="sxs-lookup"><span data-stu-id="07540-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-111">Example</span></span>  
 <span data-ttu-id="07540-112">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Average%2A> para localizar o valor total médio.</span><span class="sxs-lookup"><span data-stu-id="07540-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-113">Example</span></span>  
 <span data-ttu-id="07540-114">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Average%2A> para obter o valor total médio para cada ID de contato.</span><span class="sxs-lookup"><span data-stu-id="07540-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-115">Example</span></span>  
 <span data-ttu-id="07540-116">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Average%2A> para obter os pedidos com o valor total médio para cada contato.</span><span class="sxs-lookup"><span data-stu-id="07540-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="07540-117">Contagem</span><span class="sxs-lookup"><span data-stu-id="07540-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-118">Example</span></span>  
 <span data-ttu-id="07540-119">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Count%2A> para retornar o número de produtos na tabela de produtos.</span><span class="sxs-lookup"><span data-stu-id="07540-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="07540-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-120">Example</span></span>  
 <span data-ttu-id="07540-121">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Count%2A> para retornar uma lista de IDs de contato e quantos pedidos cada um tem.</span><span class="sxs-lookup"><span data-stu-id="07540-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="07540-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-122">Example</span></span>  
 <span data-ttu-id="07540-123">O exemplo a seguir agrupa produtos pela cor e usa o método <xref:System.Linq.Enumerable.Count%2A> para retornar o número de produtos em cada grupo de cor.</span><span class="sxs-lookup"><span data-stu-id="07540-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="07540-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="07540-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-125">Example</span></span>  
 <span data-ttu-id="07540-126">O exemplo a seguir obtém a contagem de contatos como um inteiro longo.</span><span class="sxs-lookup"><span data-stu-id="07540-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="07540-127">Máx.</span><span class="sxs-lookup"><span data-stu-id="07540-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-128">Example</span></span>  
 <span data-ttu-id="07540-129">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Max%2A> para obter o maior valor total.</span><span class="sxs-lookup"><span data-stu-id="07540-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-130">Example</span></span>  
 <span data-ttu-id="07540-131">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Max%2A> para obter o maior valor total para cada ID de contato.</span><span class="sxs-lookup"><span data-stu-id="07540-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-132">Example</span></span>  
 <span data-ttu-id="07540-133">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Max%2A> para obter os pedidos com o maior valor total para cada ID de contato.</span><span class="sxs-lookup"><span data-stu-id="07540-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="07540-134">Mín.</span><span class="sxs-lookup"><span data-stu-id="07540-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-135">Example</span></span>  
 <span data-ttu-id="07540-136">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Min%2A> para obter o menor valor total.</span><span class="sxs-lookup"><span data-stu-id="07540-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-137">Example</span></span>  
 <span data-ttu-id="07540-138">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Min%2A> para obter o menor valor total para cada ID de contato.</span><span class="sxs-lookup"><span data-stu-id="07540-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-139">Example</span></span>  
 <span data-ttu-id="07540-140">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Min%2A> para obter os pedidos com o menor valor total para cada contato.</span><span class="sxs-lookup"><span data-stu-id="07540-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="07540-141">Sum</span><span class="sxs-lookup"><span data-stu-id="07540-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="07540-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-142">Example</span></span>  
 <span data-ttu-id="07540-143">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Sum%2A> para obter o número total de quantidades do pedido na tabela SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="07540-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="07540-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07540-144">Example</span></span>  
 <span data-ttu-id="07540-145">O exemplo a seguir usa o método <xref:System.Linq.Enumerable.Sum%2A> para obter o valor total para cada ID de contato.</span><span class="sxs-lookup"><span data-stu-id="07540-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="07540-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07540-146">See also</span></span>

- [<span data-ttu-id="07540-147">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="07540-147">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

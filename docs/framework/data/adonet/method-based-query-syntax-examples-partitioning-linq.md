---
title: 'Exemplos de sintaxe da consulta com base em método: Divisão (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: d517b09ac921001ab16216e4950df66dfabda13d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766160"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="676b8-102">Exemplos de sintaxe da consulta com base em método: Divisão (LINQ</span><span class="sxs-lookup"><span data-stu-id="676b8-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="676b8-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, e métodos de <xref:System.Linq.Enumerable.TakeWhile%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="676b8-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="676b8-104">O `FillDataSet` método usado nesses exemplos é especificado em [carregar dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="676b8-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="676b8-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="676b8-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="676b8-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="676b8-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="676b8-107">Para obter mais informações, consulte [como: criar um LINQ to DataSet de projeto no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="676b8-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="676b8-108">Skip</span><span class="sxs-lookup"><span data-stu-id="676b8-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="676b8-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-109">Example</span></span>  
 <span data-ttu-id="676b8-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter mas todos os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="676b8-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="676b8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-111">Example</span></span>  
 <span data-ttu-id="676b8-112">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="676b8-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="676b8-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="676b8-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="676b8-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-114">Example</span></span>  
 <span data-ttu-id="676b8-115">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e métodos de <xref:System.Linq.Enumerable.SkipWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela maior que 300,00.</span><span class="sxs-lookup"><span data-stu-id="676b8-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="676b8-116">Take</span><span class="sxs-lookup"><span data-stu-id="676b8-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="676b8-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-117">Example</span></span>  
 <span data-ttu-id="676b8-118">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter apenas os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="676b8-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="676b8-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-119">Example</span></span>  
 <span data-ttu-id="676b8-120">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="676b8-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="676b8-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="676b8-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="676b8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="676b8-122">Example</span></span>  
 <span data-ttu-id="676b8-123">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e <xref:System.Linq.Enumerable.TakeWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela menor que 300,00.</span><span class="sxs-lookup"><span data-stu-id="676b8-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="676b8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="676b8-124">See Also</span></span>  
 [<span data-ttu-id="676b8-125">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="676b8-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="676b8-126">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="676b8-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="676b8-127">Visão Geral de Operadores de Consulta Padrão</span><span class="sxs-lookup"><span data-stu-id="676b8-127">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)

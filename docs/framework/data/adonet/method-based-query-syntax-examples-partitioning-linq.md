---
title: 'Exemplos de sintaxe de consulta baseada em método: Divisão (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: bfc26835258606ff20dd066ecb6e4c874d0be2f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116708"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="aa41d-102">Exemplos de sintaxe de consulta baseada em método: Divisão (LINQ</span><span class="sxs-lookup"><span data-stu-id="aa41d-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>
<span data-ttu-id="aa41d-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, e métodos de <xref:System.Linq.Enumerable.TakeWhile%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="aa41d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="aa41d-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto de dados](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="aa41d-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="aa41d-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="aa41d-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="aa41d-106">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="aa41d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="aa41d-107">Para obter mais informações, confira [Como: Criar um projeto LINQ to DataSet no Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="aa41d-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="aa41d-108">Skip</span><span class="sxs-lookup"><span data-stu-id="aa41d-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa41d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-109">Example</span></span>  
 <span data-ttu-id="aa41d-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter mas todos os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="aa41d-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="aa41d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-111">Example</span></span>  
 <span data-ttu-id="aa41d-112">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="aa41d-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="aa41d-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="aa41d-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa41d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-114">Example</span></span>  
 <span data-ttu-id="aa41d-115">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e métodos de <xref:System.Linq.Enumerable.SkipWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela maior que 300,00.</span><span class="sxs-lookup"><span data-stu-id="aa41d-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="aa41d-116">Take</span><span class="sxs-lookup"><span data-stu-id="aa41d-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa41d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-117">Example</span></span>  
 <span data-ttu-id="aa41d-118">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter apenas os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="aa41d-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="aa41d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-119">Example</span></span>  
 <span data-ttu-id="aa41d-120">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="aa41d-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="aa41d-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="aa41d-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="aa41d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa41d-122">Example</span></span>  
 <span data-ttu-id="aa41d-123">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e <xref:System.Linq.Enumerable.TakeWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela menor que 300,00.</span><span class="sxs-lookup"><span data-stu-id="aa41d-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="aa41d-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa41d-124">See also</span></span>

- [<span data-ttu-id="aa41d-125">Carregar dados para um conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="aa41d-125">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="aa41d-126">Exemplos de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="aa41d-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="aa41d-127">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="aa41d-127">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="aa41d-128">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa41d-128">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

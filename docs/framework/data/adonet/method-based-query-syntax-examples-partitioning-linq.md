---
title: 'Exemplos de sintaxe da consulta com base em método: Divisão (LINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a582c53f-f203-44ae-a797-d7f169a4fbb5
ms.openlocfilehash: 0ef7176ccffb7037a7d4496cc7d4da7991741d38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147925"
---
# <a name="method-based-query-syntax-examples-partitioning-linq"></a><span data-ttu-id="ece7d-102">Exemplos de sintaxe da consulta com base em método: Divisão (LINQ</span><span class="sxs-lookup"><span data-stu-id="ece7d-102">Method-Based Query Syntax Examples: Partitioning (LINQ</span></span>

<span data-ttu-id="ece7d-103">Os exemplos neste tópico demonstram como usar <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, e métodos de <xref:System.Linq.Enumerable.TakeWhile%2A> para ver <xref:System.Data.DataSet> usando a sintaxe da expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="ece7d-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>, <xref:System.Linq.Enumerable.Take%2A>, and <xref:System.Linq.Enumerable.TakeWhile%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="ece7d-104">O `FillDataSet` método usado nesses exemplos é especificado no [carregamento de dados em um conjunto](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ece7d-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="ece7d-105">Os exemplos neste tópico usam as tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ece7d-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ece7d-106">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="ece7d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="ece7d-107">Para obter mais informações, consulte [como: criar um projeto de LINQ to DataSet no Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="ece7d-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="skip"></a><span data-ttu-id="ece7d-108">Ignorar</span><span class="sxs-lookup"><span data-stu-id="ece7d-108">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="ece7d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-109">Example</span></span>  

 <span data-ttu-id="ece7d-110">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter mas todos os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="ece7d-110">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first five contacts of the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipsimple)]
 [!code-vb[DP LINQ to DataSet Examples#SkipSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipsimple)]  
  
### <a name="example"></a><span data-ttu-id="ece7d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-111">Example</span></span>  

 <span data-ttu-id="ece7d-112">Este exemplo usa o método de <xref:System.Linq.Enumerable.Skip%2A> para obter todos mas os dois primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="ece7d-112">This example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP LINQ to DataSet Examples#SkipNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipnested)]  
  
## <a name="skipwhile"></a><span data-ttu-id="ece7d-113">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="ece7d-113">SkipWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="ece7d-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-114">Example</span></span>  

 <span data-ttu-id="ece7d-115">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e métodos de <xref:System.Linq.Enumerable.SkipWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela maior que 300,00.</span><span class="sxs-lookup"><span data-stu-id="ece7d-115">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.SkipWhile%2A> methods to return products from the `Product` table with a list price greater than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#skipwhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SkipWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#skipwhilesimple_mq)]  
  
## <a name="take"></a><span data-ttu-id="ece7d-116">Take</span><span class="sxs-lookup"><span data-stu-id="ece7d-116">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="ece7d-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-117">Example</span></span>  

 <span data-ttu-id="ece7d-118">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter apenas os cinco primeiros contatos da tabela de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="ece7d-118">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get only the first five contacts from the `Contact` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takesimple)]
 [!code-vb[DP LINQ to DataSet Examples#TakeSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takesimple)]  
  
### <a name="example"></a><span data-ttu-id="ece7d-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-119">Example</span></span>  

 <span data-ttu-id="ece7d-120">Este exemplo usa o método de <xref:System.Linq.Enumerable.Take%2A> para obter os três primeiros endereços em Seattle.</span><span class="sxs-lookup"><span data-stu-id="ece7d-120">This example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takenested)]
 [!code-vb[DP LINQ to DataSet Examples#TakeNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takenested)]  
  
## <a name="takewhile"></a><span data-ttu-id="ece7d-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="ece7d-121">TakeWhile</span></span>  
  
### <a name="example"></a><span data-ttu-id="ece7d-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ece7d-122">Example</span></span>  

 <span data-ttu-id="ece7d-123">Este exemplo usa <xref:System.Linq.Enumerable.OrderBy%2A> e <xref:System.Linq.Enumerable.TakeWhile%2A> para retornar produtos da tabela de `Product` com um custo de tabela menor que 300,00.</span><span class="sxs-lookup"><span data-stu-id="ece7d-123">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.TakeWhile%2A> to return products from the `Product` table with a list price less than 300.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#takewhilesimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#TakeWhileSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#takewhilesimple_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ece7d-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="ece7d-124">See also</span></span>

- [<span data-ttu-id="ece7d-125">Carregando dados em um DataSet</span><span class="sxs-lookup"><span data-stu-id="ece7d-125">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="ece7d-126">LINQ para exemplos de DataSet</span><span class="sxs-lookup"><span data-stu-id="ece7d-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="ece7d-127">Visão geral de operadores de consulta padrão (C#)</span><span class="sxs-lookup"><span data-stu-id="ece7d-127">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ece7d-128">Visão geral de operadores de consulta padrão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ece7d-128">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

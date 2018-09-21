---
title: 'Exemplos de sintaxe da expressão de consulta: Classificação'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: bc8bfaabb9e90e66e4ec81e551fd66319a78ca7e
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493421"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="012d2-102">Exemplos de sintaxe da expressão de consulta: Classificação</span><span class="sxs-lookup"><span data-stu-id="012d2-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="012d2-103">Os exemplos neste tópico demonstram como usar o `OrderBy` e `OrderByDescending` métodos para consultar o [modelo de vendas AdventureWorks](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="012d2-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="012d2-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="012d2-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="012d2-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="012d2-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="012d2-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="012d2-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="012d2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012d2-107">Example</span></span>  
 <span data-ttu-id="012d2-108">O exemplo a seguir usa <xref:System.Linq.Enumerable.OrderBy%2A> para retornar uma lista de contatos ordenados por sobrenome.</span><span class="sxs-lookup"><span data-stu-id="012d2-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="012d2-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012d2-109">Example</span></span>  
 <span data-ttu-id="012d2-110">O exemplo a seguir usa <xref:System.Linq.Enumerable.OrderBy%2A> para classificar uma lista de contatos pelo comprimento do sobrenome.</span><span class="sxs-lookup"><span data-stu-id="012d2-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="012d2-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="012d2-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="012d2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012d2-112">Example</span></span>  
 <span data-ttu-id="012d2-113">O exemplo a seguir usa `orderby… descending` (`Order By … Descending` no Visual Basic), que é equivalente ao método de <xref:System.Linq.Enumerable.OrderByDescending%2A> , para classificar a tabela de preços de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="012d2-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="012d2-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="012d2-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="012d2-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012d2-115">Example</span></span>  
 <span data-ttu-id="012d2-116">O exemplo a seguir usa <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenBy%2A> para retornar uma lista de contatos ordenados por sobrenome e em seguida pelo nome.</span><span class="sxs-lookup"><span data-stu-id="012d2-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="012d2-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="012d2-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="012d2-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="012d2-118">Example</span></span>  
 <span data-ttu-id="012d2-119">O exemplo a seguir usa `OrderBy… Descending`, que é equivalente ao método de <xref:System.Linq.Enumerable.ThenByDescending%2A> , para classificar uma lista de produtos, principalmente por nome e em seguida pelo custo da tabela de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="012d2-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="012d2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="012d2-120">See Also</span></span>  
 [<span data-ttu-id="012d2-121">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="012d2-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

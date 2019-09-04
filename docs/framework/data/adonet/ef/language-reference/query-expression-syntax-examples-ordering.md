---
title: 'Exemplos de sintaxe de expressão de consulta: Ordenando'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcbc9625-7cf7-476e-85d2-058f12682f54
ms.openlocfilehash: fbcb6ffe27234beb120e71ebc71c782abd4be24a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249463"
---
# <a name="query-expression-syntax-examples-ordering"></a><span data-ttu-id="89a19-102">Exemplos de sintaxe de expressão de consulta: Ordenando</span><span class="sxs-lookup"><span data-stu-id="89a19-102">Query Expression Syntax Examples: Ordering</span></span>
<span data-ttu-id="89a19-103">Os exemplos neste tópico demonstram como usar os métodos `OrderBy` e `OrderByDescending` para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="89a19-103">The examples in this topic demonstrate how to use the `OrderBy` and `OrderByDescending` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="89a19-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="89a19-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="89a19-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="89a19-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="orderby"></a><span data-ttu-id="89a19-106">OrderBy</span><span class="sxs-lookup"><span data-stu-id="89a19-106">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="89a19-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a19-107">Example</span></span>  
 <span data-ttu-id="89a19-108">O exemplo a seguir usa <xref:System.Linq.Enumerable.OrderBy%2A> para retornar uma lista de contatos ordenados por sobrenome.</span><span class="sxs-lookup"><span data-stu-id="89a19-108">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP L2E Examples#OrderBySimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="89a19-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a19-109">Example</span></span>  
 <span data-ttu-id="89a19-110">O exemplo a seguir usa <xref:System.Linq.Enumerable.OrderBy%2A> para classificar uma lista de contatos pelo comprimento do sobrenome.</span><span class="sxs-lookup"><span data-stu-id="89a19-110">The following example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP L2E Examples#OrderBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="89a19-111">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="89a19-111">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="89a19-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a19-112">Example</span></span>  
 <span data-ttu-id="89a19-113">O exemplo a seguir usa `orderby… descending` (`Order By … Descending` no Visual Basic), que é equivalente ao método de <xref:System.Linq.Enumerable.OrderByDescending%2A> , para classificar a tabela de preços de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="89a19-113">The following example uses `orderby… descending` (`Order By … Descending` in Visual Basic), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP L2E Examples#OrderByDescendingSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="thenby"></a><span data-ttu-id="89a19-114">ThenBy</span><span class="sxs-lookup"><span data-stu-id="89a19-114">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="89a19-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a19-115">Example</span></span>  
 <span data-ttu-id="89a19-116">O exemplo a seguir usa <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenBy%2A> para retornar uma lista de contatos ordenados por sobrenome e em seguida pelo nome.</span><span class="sxs-lookup"><span data-stu-id="89a19-116">The following example uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby)]
 [!code-vb[DP L2E Examples#OrderByThenBy](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="89a19-117">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="89a19-117">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="89a19-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="89a19-118">Example</span></span>  
 <span data-ttu-id="89a19-119">O exemplo a seguir usa `OrderBy… Descending`, que é equivalente ao método de <xref:System.Linq.Enumerable.ThenByDescending%2A> , para classificar uma lista de produtos, principalmente por nome e em seguida pelo custo da tabela de mais alto para o menor.</span><span class="sxs-lookup"><span data-stu-id="89a19-119">The following example uses `OrderBy… Descending`, which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price from highest to lowest.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP L2E Examples#ThenByDescendingSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="89a19-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89a19-120">See also</span></span>

- [<span data-ttu-id="89a19-121">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="89a19-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

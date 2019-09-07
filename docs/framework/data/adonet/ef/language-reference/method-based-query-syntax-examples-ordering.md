---
title: 'Exemplos de sintaxe de consulta baseada em método: Ordenando'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5d21b178-d731-471a-8534-1f8184a2ef06
ms.openlocfilehash: e10101e2a3534d981b2126884a2a61b411254477
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397325"
---
# <a name="method-based-query-syntax-examples-ordering"></a><span data-ttu-id="e5ba1-102">Exemplos de sintaxe de consulta baseada em método: Ordenando</span><span class="sxs-lookup"><span data-stu-id="e5ba1-102">Method-Based Query Syntax Examples: Ordering</span></span>
<span data-ttu-id="e5ba1-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.ThenBy%2A> método para consultar o modelo de [vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando a sintaxe de consulta baseada em método.</span><span class="sxs-lookup"><span data-stu-id="e5ba1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ThenBy%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="e5ba1-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e5ba1-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e5ba1-105">Os exemplos neste tópico usam as seguintes `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="e5ba1-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="thenby"></a><span data-ttu-id="e5ba1-106">ThenBy</span><span class="sxs-lookup"><span data-stu-id="e5ba1-106">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="e5ba1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5ba1-107">Example</span></span>  
 <span data-ttu-id="e5ba1-108">O exemplo a seguir na sintaxe da consulta com base em método usa <xref:System.Linq.Queryable.OrderBy%2A> e <xref:System.Linq.Queryable.ThenBy%2A> para retornar uma lista de contatos ordenados por sobrenome e em seguida pelo nome.</span><span class="sxs-lookup"><span data-stu-id="e5ba1-108">The following example in method-based query syntax uses <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenBy%2A> to return a list of contacts ordered by last name and then by first name.</span></span>  
  
 [!code-csharp[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#orderbythenby_mq)]
 [!code-vb[DP L2E Examples#OrderByThenBy_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#orderbythenby_mq)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="e5ba1-109">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="e5ba1-109">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="e5ba1-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5ba1-110">Example</span></span>  
 <span data-ttu-id="e5ba1-111">O seguinte exemplo usa os métodos de <xref:System.Linq.Queryable.OrderBy%2A> e de <xref:System.Linq.Queryable.ThenByDescending%2A> para o primeiro tipo pelo custo da tabela e em seguida, executar uma descida meio de nomes do produto.</span><span class="sxs-lookup"><span data-stu-id="e5ba1-111">The following example uses the <xref:System.Linq.Queryable.OrderBy%2A> and <xref:System.Linq.Queryable.ThenByDescending%2A> methods to first sort by list price, and then perform a descending sort of the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#thenbydescending_mq)]
 [!code-vb[DP L2E Examples#ThenByDescending_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#thenbydescending_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="e5ba1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5ba1-112">See also</span></span>

- [<span data-ttu-id="e5ba1-113">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e5ba1-113">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

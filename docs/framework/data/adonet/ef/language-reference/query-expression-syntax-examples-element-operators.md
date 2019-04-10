---
title: 'Exemplos de sintaxe de expressão de consulta: Operadores de elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 1b73e22e79c665763390561a1e48b2583ec6cd27
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215502"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="f0cb6-102">Exemplos de sintaxe de expressão de consulta: Operadores de elemento</span><span class="sxs-lookup"><span data-stu-id="f0cb6-102">Query Expression Syntax Examples: Element Operators</span></span>
<span data-ttu-id="f0cb6-103">Os exemplos neste tópico demonstram como usar o <xref:System.Linq.Enumerable.First%2A> método para consultar o [modelo de vendas AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples) usando a sintaxe de expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="f0cb6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using the query expression syntax.</span></span> <span data-ttu-id="f0cb6-104">O Modelo de vendas AdventureWorks usado nesses exemplos é criado a partir das tabelas Contact, Address, Product, SalesOrderHeader e SalesOrderDetail no banco de dados de exemplo AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f0cb6-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f0cb6-105">Os exemplos neste tópico usam o seguinte `using` / `Imports` instruções:</span><span class="sxs-lookup"><span data-stu-id="f0cb6-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="f0cb6-106">Primeiro</span><span class="sxs-lookup"><span data-stu-id="f0cb6-106">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="f0cb6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0cb6-107">Example</span></span>  
 <span data-ttu-id="f0cb6-108">O exemplo a seguir usa o método de <xref:System.Linq.Enumerable.First%2A> para retornar o primeiro contato cujo nome é “Brooke”.</span><span class="sxs-lookup"><span data-stu-id="f0cb6-108">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="f0cb6-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0cb6-109">See also</span></span>

- [<span data-ttu-id="f0cb6-110">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f0cb6-110">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)

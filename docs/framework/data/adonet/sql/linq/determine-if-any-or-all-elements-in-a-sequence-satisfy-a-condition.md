---
title: Determinar se alguns ou todos os elementos em uma sequência satisfazem uma condição
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877364"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="b937b-102">Determinar se alguns ou todos os elementos em uma sequência satisfazem uma condição</span><span class="sxs-lookup"><span data-stu-id="b937b-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="b937b-103">O operador de <xref:System.Linq.Enumerable.All%2A> retorna `true` se todos os elementos em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="b937b-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="b937b-104">O operador de <xref:System.Linq.Queryable.Any%2A> retorna `true` se qualquer elemento em uma sequência satisfazem uma condição.</span><span class="sxs-lookup"><span data-stu-id="b937b-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b937b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b937b-105">Example</span></span>  
 <span data-ttu-id="b937b-106">O exemplo a seguir retorna uma sequência de clientes que possuem pelo menos um pedido.</span><span class="sxs-lookup"><span data-stu-id="b937b-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="b937b-107">O `Where` / `where` cláusula é avaliada como `true` se o determinado `Customer` tem algum `Order`.</span><span class="sxs-lookup"><span data-stu-id="b937b-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="b937b-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b937b-108">Example</span></span>  
 <span data-ttu-id="b937b-109">O seguinte código de Visual Basic determina a lista de clientes que não colocaram pedidos, e assegura que para cada cliente na lista, um nome de contato é fornecido.</span><span class="sxs-lookup"><span data-stu-id="b937b-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="b937b-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b937b-110">Example</span></span>  
 <span data-ttu-id="b937b-111">O exemplo de C# retorna uma sequência de clientes cujos pedidos têm `ShipCity` que começa com “C 2.0”.</span><span class="sxs-lookup"><span data-stu-id="b937b-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="b937b-112">Também são incluídos no retorno clientes que não têm nenhum pedido.</span><span class="sxs-lookup"><span data-stu-id="b937b-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="b937b-113">(Por design, o operador de <xref:System.Linq.Queryable.All%2A> retorna `true` para uma sequência vazia.) Os clientes sem pedidos são cortadas na saída de console usando o operador de `Count` .</span><span class="sxs-lookup"><span data-stu-id="b937b-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="b937b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b937b-114">See also</span></span>

- [<span data-ttu-id="b937b-115">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="b937b-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)

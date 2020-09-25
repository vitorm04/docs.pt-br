---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 0fe32d8c3c37e99a50ca03262dc6184337b4450e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200193"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="dffa8-102">Retornar a união de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="dffa8-102">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="dffa8-103">Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="dffa8-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dffa8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dffa8-104">Example</span></span>  

 <span data-ttu-id="dffa8-105">Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países/regiões em que há `Customers` ou `Employees` .</span><span class="sxs-lookup"><span data-stu-id="dffa8-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="dffa8-106">No [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , o <xref:System.Linq.Queryable.Union%2A> operador é definido para conjuntos de valores como a concatenação não ordenada dos conjuntos de multiconjuntos (efetivamente o resultado da [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) cláusula em SQL).</span><span class="sxs-lookup"><span data-stu-id="dffa8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="dffa8-107">Para obter mais informações e exemplos, consulte <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dffa8-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dffa8-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="dffa8-108">See also</span></span>

- [<span data-ttu-id="dffa8-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="dffa8-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="dffa8-110">Conversão padrão de operador de consulta</span><span class="sxs-lookup"><span data-stu-id="dffa8-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

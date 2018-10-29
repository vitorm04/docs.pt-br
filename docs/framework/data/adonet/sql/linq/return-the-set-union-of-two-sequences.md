---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: ffdc1dc0f9b5c2ed3b9898d0c71c9b384723fe05
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200543"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="a744d-102">Retornar a união de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="a744d-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="a744d-103">Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="a744d-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a744d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a744d-104">Example</span></span>  
 <span data-ttu-id="a744d-105">Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países em que há `Customers` ou `Employees`.</span><span class="sxs-lookup"><span data-stu-id="a744d-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="a744d-106">Na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o <xref:System.Linq.Queryable.Union%2A> operador está definido para multisets como concatenação não ordenada de multisets (efetivamente o resultado das [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) cláusula no SQL).</span><span class="sxs-lookup"><span data-stu-id="a744d-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause in SQL).</span></span>

<span data-ttu-id="a744d-107">Para obter mais informações e exemplos, consulte <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a744d-107">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a744d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a744d-108">See Also</span></span>  
 [<span data-ttu-id="a744d-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="a744d-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="a744d-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="a744d-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

---
title: Retornar a união de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5aa05384cba826f9cdd7a948a31b2860eaad7f18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358071"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="4d01d-102">Retornar a união de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="4d01d-102">Return the Set Union of Two Sequences</span></span>
<span data-ttu-id="4d01d-103">Use o operador de <xref:System.Linq.Queryable.Union%2A> para retornar a união ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="4d01d-103">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d01d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d01d-104">Example</span></span>  
 <span data-ttu-id="4d01d-105">Este exemplo usa <xref:System.Linq.Queryable.Union%2A> para retornar uma sequência de todos os países em que há `Customers` ou `Employees`.</span><span class="sxs-lookup"><span data-stu-id="4d01d-105">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="4d01d-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], o <xref:System.Linq.Queryable.Union%2A> operador está definido para multisets como a concatenação não ordenada de multisets (efetivamente o resultado da `UNION ALL` cláusula no SQL).</span><span class="sxs-lookup"><span data-stu-id="4d01d-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the `UNION ALL` clause in SQL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d01d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d01d-107">See Also</span></span>  
 [<span data-ttu-id="4d01d-108">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="4d01d-108">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="4d01d-109">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="4d01d-109">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

---
title: Retornar a interseção de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 3458ebf8f5708496eef6246fa55cf528e8a32bc4
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380066"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="59b9c-102">Retornar a interseção de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="59b9c-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="59b9c-103">Use o operador de <xref:System.Linq.Queryable.Intersect%2A> para retornar a interseção ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="59b9c-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b9c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59b9c-104">Example</span></span>  
 <span data-ttu-id="59b9c-105">Este exemplo usa <xref:System.Linq.Queryable.Intersect%2A> para retornar uma sequência de todos os países/regiões em que tanto `Customers` e `Employees` ao vivo.</span><span class="sxs-lookup"><span data-stu-id="59b9c-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="59b9c-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Intersect%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="59b9c-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="59b9c-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="59b9c-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b9c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59b9c-108">See also</span></span>

- [<span data-ttu-id="59b9c-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="59b9c-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="59b9c-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="59b9c-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

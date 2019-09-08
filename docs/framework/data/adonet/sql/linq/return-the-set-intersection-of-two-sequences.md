---
title: Retornar a interseção de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 944d0b2efe1e74f901a493d1c3202d0f180d599d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792710"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="066b8-102">Retornar a interseção de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="066b8-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="066b8-103">Use o operador de <xref:System.Linq.Queryable.Intersect%2A> para retornar a interseção ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="066b8-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="066b8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="066b8-104">Example</span></span>  
 <span data-ttu-id="066b8-105">Este exemplo usa <xref:System.Linq.Queryable.Intersect%2A> para retornar uma sequência de todos os países/regiões nos quais `Customers` o `Employees` e o dinâmico.</span><span class="sxs-lookup"><span data-stu-id="066b8-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="066b8-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Intersect%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="066b8-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="066b8-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="066b8-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="066b8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="066b8-108">See also</span></span>

- [<span data-ttu-id="066b8-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="066b8-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="066b8-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="066b8-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

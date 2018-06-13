---
title: Retornar a interseção de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 9fd2a5dc435829d08594ea3c2f1c129328386250
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358778"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="793b5-102">Retornar a interseção de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="793b5-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="793b5-103">Use o operador de <xref:System.Linq.Queryable.Intersect%2A> para retornar a interseção ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="793b5-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="793b5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="793b5-104">Example</span></span>  
 <span data-ttu-id="793b5-105">Este exemplo usa <xref:System.Linq.Queryable.Intersect%2A> para retornar uma sequência de todos os países em que `Customers` e `Employees` ativa.</span><span class="sxs-lookup"><span data-stu-id="793b5-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="793b5-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Intersect%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="793b5-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="793b5-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="793b5-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793b5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="793b5-108">See Also</span></span>  
 [<span data-ttu-id="793b5-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="793b5-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="793b5-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="793b5-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

---
title: Retornar a interseção de sequências de duas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205896"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="f85df-102">Retornar a interseção de sequências de duas</span><span class="sxs-lookup"><span data-stu-id="f85df-102">Return the Set Intersection of Two Sequences</span></span>
<span data-ttu-id="f85df-103">Use o operador de <xref:System.Linq.Queryable.Intersect%2A> para retornar a interseção ajustada de duas sequências.</span><span class="sxs-lookup"><span data-stu-id="f85df-103">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f85df-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f85df-104">Example</span></span>  
 <span data-ttu-id="f85df-105">Este exemplo usa <xref:System.Linq.Queryable.Intersect%2A> para retornar uma sequência de todos os países em que `Customers` e `Employees` ativa.</span><span class="sxs-lookup"><span data-stu-id="f85df-105">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="f85df-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Intersect%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="f85df-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="f85df-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="f85df-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85df-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f85df-108">See also</span></span>

- [<span data-ttu-id="f85df-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="f85df-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="f85df-110">Conversão padrão de operador de consulta</span><span class="sxs-lookup"><span data-stu-id="f85df-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

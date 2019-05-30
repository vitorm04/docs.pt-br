---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 5bb7d797ad2adc4374f7a10c11d66be69feeb7a1
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380044"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="55932-102">Retornar a diferença entre duas sequências ajustada</span><span class="sxs-lookup"><span data-stu-id="55932-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="55932-103">Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.</span><span class="sxs-lookup"><span data-stu-id="55932-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55932-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55932-104">Example</span></span>  
 <span data-ttu-id="55932-105">Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países/regiões em que `Customers` ativo, mas no qual nenhum `Employees` ao vivo.</span><span class="sxs-lookup"><span data-stu-id="55932-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="55932-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="55932-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="55932-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="55932-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55932-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55932-108">See also</span></span>

- [<span data-ttu-id="55932-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="55932-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="55932-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="55932-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

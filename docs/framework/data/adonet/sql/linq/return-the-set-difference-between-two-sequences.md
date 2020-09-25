---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200323"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="a85c0-102">Retornar a diferença entre duas sequências ajustada</span><span class="sxs-lookup"><span data-stu-id="a85c0-102">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="a85c0-103">Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.</span><span class="sxs-lookup"><span data-stu-id="a85c0-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a85c0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a85c0-104">Example</span></span>  

 <span data-ttu-id="a85c0-105">Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países/regiões nos quais o `Customers` Live, mas no qual não há `Employees` tempo.</span><span class="sxs-lookup"><span data-stu-id="a85c0-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="a85c0-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="a85c0-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="a85c0-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="a85c0-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85c0-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="a85c0-108">See also</span></span>

- [<span data-ttu-id="a85c0-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="a85c0-109">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="a85c0-110">Conversão padrão de operador de consulta</span><span class="sxs-lookup"><span data-stu-id="a85c0-110">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)

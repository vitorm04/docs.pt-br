---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 80348961d2848e9664e6978789ceb2441ea2f89a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356212"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="6bcfb-102">Retornar a diferença entre duas sequências ajustada</span><span class="sxs-lookup"><span data-stu-id="6bcfb-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="6bcfb-103">Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.</span><span class="sxs-lookup"><span data-stu-id="6bcfb-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bcfb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bcfb-104">Example</span></span>  
 <span data-ttu-id="6bcfb-105">Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países em que `Customers` ativa mas em que nenhum `Employees` ativa.</span><span class="sxs-lookup"><span data-stu-id="6bcfb-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="6bcfb-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="6bcfb-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="6bcfb-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="6bcfb-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcfb-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bcfb-108">See Also</span></span>  
 [<span data-ttu-id="6bcfb-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="6bcfb-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="6bcfb-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="6bcfb-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

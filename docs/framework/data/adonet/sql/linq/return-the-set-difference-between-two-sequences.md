---
title: Retornar a diferença entre duas sequências ajustada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037525"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="6c371-102">Retornar a diferença entre duas sequências ajustada</span><span class="sxs-lookup"><span data-stu-id="6c371-102">Return the Set Difference Between Two Sequences</span></span>
<span data-ttu-id="6c371-103">Use o operador de <xref:System.Linq.Queryable.Except%2A> para retornar a diferença entre duas ajustada sequências.</span><span class="sxs-lookup"><span data-stu-id="6c371-103">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c371-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6c371-104">Example</span></span>  
 <span data-ttu-id="6c371-105">Este exemplo usa <xref:System.Linq.Queryable.Except%2A> para retornar uma sequência de todos os países em que `Customers` ativa mas em que nenhum `Employees` ativa.</span><span class="sxs-lookup"><span data-stu-id="6c371-105">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="6c371-106">Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a operação de <xref:System.Linq.Queryable.Except%2A> é bem definido somente em conjuntos.</span><span class="sxs-lookup"><span data-stu-id="6c371-106">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="6c371-107">A semântica de multisets é indefinida.</span><span class="sxs-lookup"><span data-stu-id="6c371-107">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c371-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c371-108">See also</span></span>

- [<span data-ttu-id="6c371-109">Exemplos de consulta</span><span class="sxs-lookup"><span data-stu-id="6c371-109">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="6c371-110">Conversão de operador de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="6c371-110">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)

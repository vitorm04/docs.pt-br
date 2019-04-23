---
title: 'Como: filtrar no nível de DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: 343cffa9b1c034068e5abcc652e936f89ee6a992
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084577"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="bd3f1-102">Como: filtrar no nível de DataContext</span><span class="sxs-lookup"><span data-stu-id="bd3f1-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="bd3f1-103">Você pode filtrar `EntitySets` em `DataContext` nível.</span><span class="sxs-lookup"><span data-stu-id="bd3f1-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="bd3f1-104">Como filtros se aplicam a todas as consultas feitas com essa instância de <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="bd3f1-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd3f1-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd3f1-105">Example</span></span>  
 <span data-ttu-id="bd3f1-106">No exemplo a seguir, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> é usado para filtrar os pedidos pré-compilação para clientes carregados por `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="bd3f1-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="bd3f1-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd3f1-107">See also</span></span>

- [<span data-ttu-id="bd3f1-108">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="bd3f1-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)

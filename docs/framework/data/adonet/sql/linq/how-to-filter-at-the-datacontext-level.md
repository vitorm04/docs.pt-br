---
title: 'Como: Filtrar a nível de DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: c04be0bb955cff4bf796d14d45b39cac7ce4352d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354927"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="f9dac-102">Como: Filtrar a nível de DataContext</span><span class="sxs-lookup"><span data-stu-id="f9dac-102">How to: Filter at the DataContext Level</span></span>
<span data-ttu-id="f9dac-103">Você pode filtrar `EntitySets` em `DataContext` nível.</span><span class="sxs-lookup"><span data-stu-id="f9dac-103">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="f9dac-104">Como filtros se aplicam a todas as consultas feitas com essa instância de <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="f9dac-104">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dac-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f9dac-105">Example</span></span>  
 <span data-ttu-id="f9dac-106">No exemplo a seguir, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> é usado para filtrar os pedidos pré-compilação para clientes carregados por `ShippedDate`.</span><span class="sxs-lookup"><span data-stu-id="f9dac-106">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dac-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9dac-107">See Also</span></span>  
 [<span data-ttu-id="f9dac-108">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="f9dac-108">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)

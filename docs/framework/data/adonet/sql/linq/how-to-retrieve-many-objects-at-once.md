---
title: 'Como: Recuperar vários objetos ao mesmo tempo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 31091b6634c9d95c008929680620fb66d95d473c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653782"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="17f17-102">Como: Recuperar vários objetos ao mesmo tempo</span><span class="sxs-lookup"><span data-stu-id="17f17-102">How to: Retrieve Many Objects At Once</span></span>
<span data-ttu-id="17f17-103">Você pode recuperar vários objetos em uma consulta usando <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="17f17-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f17-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17f17-104">Example</span></span>  
 <span data-ttu-id="17f17-105">O código a seguir usa o método de <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> para recuperar `Customer` e objetos de `Order` .</span><span class="sxs-lookup"><span data-stu-id="17f17-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="17f17-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17f17-106">See also</span></span>
- [<span data-ttu-id="17f17-107">Conceitos de consulta</span><span class="sxs-lookup"><span data-stu-id="17f17-107">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)

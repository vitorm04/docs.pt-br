---
title: 'Como: Recuperar informações de conflito de entidade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 1c2f9a5f822d8783f997c9c5c09ef508c2d8dca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629027"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="b95d2-102">Como: Recuperar informações de conflito de entidade</span><span class="sxs-lookup"><span data-stu-id="b95d2-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="b95d2-103">Você pode usar objetos de classe de <xref:System.Data.Linq.ObjectChangeConflict> para fornecer informações sobre os conflitos revelados por exceções de <xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="b95d2-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="b95d2-104">Para obter mais informações, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b95d2-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b95d2-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b95d2-105">Example</span></span>  
 <span data-ttu-id="b95d2-106">O exemplo a seguir efetua iterações através de uma lista de conflitos acumulados.</span><span class="sxs-lookup"><span data-stu-id="b95d2-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b95d2-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b95d2-107">See also</span></span>
- [<span data-ttu-id="b95d2-108">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="b95d2-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

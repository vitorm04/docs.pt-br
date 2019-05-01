---
title: 'Como: recuperar informações de conflito de membro'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: fae1513e7a7ead98318d907b220b7510758c9ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037596"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="ae910-102">Como: recuperar informações de conflito de membro</span><span class="sxs-lookup"><span data-stu-id="ae910-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="ae910-103">Você pode usar a classe de <xref:System.Data.Linq.MemberChangeConflict> para recuperar informações sobre membros individuais em conflito.</span><span class="sxs-lookup"><span data-stu-id="ae910-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="ae910-104">Nesse mesmo contexto você pode prever manipulação personalizada de conflito para qualquer membro.</span><span class="sxs-lookup"><span data-stu-id="ae910-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="ae910-105">Para obter mais informações, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ae910-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae910-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae910-106">Example</span></span>  
 <span data-ttu-id="ae910-107">O código a seguir efetua iterações através de objetos de <xref:System.Data.Linq.ObjectChangeConflict> .</span><span class="sxs-lookup"><span data-stu-id="ae910-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="ae910-108">Para cada objeto, então itera através de objetos de <xref:System.Data.Linq.MemberChangeConflict> .</span><span class="sxs-lookup"><span data-stu-id="ae910-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae910-109">Inclua <xref:System.Reflection> para fornecer informações de <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae910-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ae910-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae910-110">See also</span></span>

- [<span data-ttu-id="ae910-111">Como: Gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="ae910-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

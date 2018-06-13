---
title: 'Como: Recuperar informações de conflito de membro'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 5d0788daac6c1be8dd7670c330d1efc36b074c2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354375"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Como: Recuperar informações de conflito de membro
Você pode usar a classe de <xref:System.Data.Linq.MemberChangeConflict> para recuperar informações sobre membros individuais em conflito. Nesse mesmo contexto você pode prever manipulação personalizada de conflito para qualquer membro. Para obter mais informações, consulte [simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir efetua iterações através de objetos de <xref:System.Data.Linq.ObjectChangeConflict> . Para cada objeto, então itera através de objetos de <xref:System.Data.Linq.MemberChangeConflict> .  
  
> [!NOTE]
>  Inclua <xref:System.Reflection> para fornecer informações de <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Como gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

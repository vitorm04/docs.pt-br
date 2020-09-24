---
title: 'Como: recuperar informações de conflito de membro'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 4848ef69914f0520d2365538faea7fa064c1a15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155803"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Como: recuperar informações de conflito de membro

Você pode usar a classe de <xref:System.Data.Linq.MemberChangeConflict> para recuperar informações sobre membros individuais em conflito. Nesse mesmo contexto você pode prever manipulação personalizada de conflito para qualquer membro. Para obter mais informações, consulte [simultaneidade otimista: visão geral](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Exemplo  

 O código a seguir efetua iterações através de objetos de <xref:System.Data.Linq.ObjectChangeConflict> . Para cada objeto, então itera através de objetos de <xref:System.Data.Linq.MemberChangeConflict> .  
  
> [!NOTE]
> Inclua <xref:System.Reflection> para fornecer informações de <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Confira também

- [Como: gerenciar conflitos de alteração](how-to-manage-change-conflicts.md)

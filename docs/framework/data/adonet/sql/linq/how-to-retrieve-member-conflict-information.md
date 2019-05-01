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
# <a name="how-to-retrieve-member-conflict-information"></a>Como: recuperar informações de conflito de membro
Você pode usar a classe de <xref:System.Data.Linq.MemberChangeConflict> para recuperar informações sobre membros individuais em conflito. Nesse mesmo contexto você pode prever manipulação personalizada de conflito para qualquer membro. Para obter mais informações, consulte [a simultaneidade otimista: Visão geral do](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir efetua iterações através de objetos de <xref:System.Data.Linq.ObjectChangeConflict> . Para cada objeto, então itera através de objetos de <xref:System.Data.Linq.MemberChangeConflict> .  
  
> [!NOTE]
>  Inclua <xref:System.Reflection> para fornecer informações de <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

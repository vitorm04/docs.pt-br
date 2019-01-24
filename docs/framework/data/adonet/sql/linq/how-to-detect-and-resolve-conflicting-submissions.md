---
title: 'Como: Detectar e resolver submissões conflitantes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ab1b56d409a3b185be15ebc8dc119a57038d55bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510501"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Como: Detectar e resolver submissões conflitantes
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece vários recursos para detectar e resolver conflitos que provêm de alterações do usuário a base de dados. Para obter mais informações, confira [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra uma `try` / `catch` bloco que captura um <xref:System.Data.Linq.ChangeConflictException> exceção. Informações de entidade e de membros para cada conflito for exibida na janela do console.  
  
> [!NOTE]
>  Você deve incluir a política de `using System.Reflection` (`Imports System.Reflection` no Visual Basic) para oferecer suporte à pesquisa documental. Para obter mais informações, consulte <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também
- [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

---
title: "Como: Detectar e resolver conflitos submissões"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28dba94262002f863a750a83493ba98b3714fabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Como: Detectar e resolver conflitos submissões
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fornece vários recursos para detectar e resolver conflitos que provêm de alterações do usuário a base de dados. Para obter mais informações, consulte [como: gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra um `try` / `catch` bloco captura um <xref:System.Data.Linq.ChangeConflictException> exceção. Informações de entidade e de membros para cada conflito for exibida na janela do console.  
  
> [!NOTE]
>  Você deve incluir a política de `using System.Reflection` (`Imports System.Reflection` no Visual Basic) para oferecer suporte à pesquisa documental. Para obter mais informações, consulte <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Realizando e enviando alterações de dados](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Como gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

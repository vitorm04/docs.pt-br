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
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="2b5ff-102">Como: Detectar e resolver conflitos submissões</span><span class="sxs-lookup"><span data-stu-id="2b5ff-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="2b5ff-103"> fornece vários recursos para detectar e resolver conflitos que provêm de alterações do usuário a base de dados.</span><span class="sxs-lookup"><span data-stu-id="2b5ff-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="2b5ff-104">Para obter mais informações, consulte [como: gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="2b5ff-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b5ff-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b5ff-105">Example</span></span>  
 <span data-ttu-id="2b5ff-106">A exemplo a seguir mostra um `try` / `catch` bloco captura um <xref:System.Data.Linq.ChangeConflictException> exceção.</span><span class="sxs-lookup"><span data-stu-id="2b5ff-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="2b5ff-107">Informações de entidade e de membros para cada conflito for exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="2b5ff-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b5ff-108">Você deve incluir a política de `using System.Reflection` (`Imports System.Reflection` no Visual Basic) para oferecer suporte à pesquisa documental.</span><span class="sxs-lookup"><span data-stu-id="2b5ff-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="2b5ff-109">Para obter mais informações, consulte <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="2b5ff-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2b5ff-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b5ff-110">See Also</span></span>  
 [<span data-ttu-id="2b5ff-111">Realizando e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="2b5ff-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="2b5ff-112">Como gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="2b5ff-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

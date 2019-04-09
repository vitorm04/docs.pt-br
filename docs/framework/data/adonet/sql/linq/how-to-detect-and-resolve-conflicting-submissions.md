---
title: 'Como: detectar e resolver submissões com conflito'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 606231449263f1c26596ca8606a88053c6aded8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138119"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="f43ab-102">Como: detectar e resolver submissões com conflito</span><span class="sxs-lookup"><span data-stu-id="f43ab-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f43ab-103">fornece muitos recursos para detectar e resolver conflitos que provêm de alterações do usuário no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f43ab-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="f43ab-104">Para obter mais informações, confira [Como: Gerenciar conflitos de alteração](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="f43ab-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f43ab-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f43ab-105">Example</span></span>  
 <span data-ttu-id="f43ab-106">A exemplo a seguir mostra uma `try` / `catch` bloco que captura um <xref:System.Data.Linq.ChangeConflictException> exceção.</span><span class="sxs-lookup"><span data-stu-id="f43ab-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="f43ab-107">Informações de entidade e de membros para cada conflito for exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f43ab-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f43ab-108">Você deve incluir a política de `using System.Reflection` (`Imports System.Reflection` no Visual Basic) para oferecer suporte à pesquisa documental.</span><span class="sxs-lookup"><span data-stu-id="f43ab-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="f43ab-109">Para obter mais informações, consulte <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="f43ab-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f43ab-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f43ab-110">See also</span></span>

- [<span data-ttu-id="f43ab-111">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="f43ab-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="f43ab-112">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="f43ab-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)

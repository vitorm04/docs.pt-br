---
title: 'Como: detectar e resolver submissões com conflito'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147717"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="02f8b-102">Como: detectar e resolver submissões com conflito</span><span class="sxs-lookup"><span data-stu-id="02f8b-102">How to: Detect and Resolve Conflicting Submissions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="02f8b-103">fornece vários recursos para detectar e resolver conflitos que provêm de alterações do usuário a base de dados.</span><span class="sxs-lookup"><span data-stu-id="02f8b-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="02f8b-104">Para obter mais informações, consulte [como: gerenciar conflitos de alteração](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="02f8b-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02f8b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02f8b-105">Example</span></span>  

 <span data-ttu-id="02f8b-106">O exemplo a seguir mostra um `try` / `catch` bloco que captura uma <xref:System.Data.Linq.ChangeConflictException> exceção.</span><span class="sxs-lookup"><span data-stu-id="02f8b-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="02f8b-107">Informações de entidade e de membros para cada conflito for exibida na janela do console.</span><span class="sxs-lookup"><span data-stu-id="02f8b-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02f8b-108">Você deve incluir a política de `using System.Reflection` (`Imports System.Reflection` no Visual Basic) para oferecer suporte à pesquisa documental.</span><span class="sxs-lookup"><span data-stu-id="02f8b-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="02f8b-109">Para obter mais informações, consulte <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="02f8b-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="02f8b-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="02f8b-110">See also</span></span>

- [<span data-ttu-id="02f8b-111">Fazendo e enviando alterações de dados</span><span class="sxs-lookup"><span data-stu-id="02f8b-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="02f8b-112">Como: gerenciar conflitos de alteração</span><span class="sxs-lookup"><span data-stu-id="02f8b-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)

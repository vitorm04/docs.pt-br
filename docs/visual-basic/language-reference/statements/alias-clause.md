---
title: "Cláusula alias (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Alias
dev_langs:
- VB
helpviewer_keywords:
- Alias keyword
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a4d96de71b03449349553198b2277310d69b19e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="d6da5-102">Cláusula Alias (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6da5-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="d6da5-103">Indica que um procedimento externo tem outro nome em sua DLL.</span><span class="sxs-lookup"><span data-stu-id="d6da5-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6da5-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d6da5-104">Remarks</span></span>  
 <span data-ttu-id="d6da5-105">O `Alias` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="d6da5-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="d6da5-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="d6da5-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="d6da5-107">No exemplo a seguir, o `Alias` palavra-chave é usada para fornecer o nome da função em Advapi32. dll, `GetUserNameA`, que `getUserName` é usado no lugar de neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d6da5-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="d6da5-108">Função `getUserName` é chamado na sub-rotina `getUser`, que exibe o nome do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="d6da5-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 <span data-ttu-id="d6da5-109">[!code-vb[VbVbalrStatements&#15;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d6da5-109">[!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6da5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6da5-110">See Also</span></span>  
 [<span data-ttu-id="d6da5-111">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d6da5-111">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

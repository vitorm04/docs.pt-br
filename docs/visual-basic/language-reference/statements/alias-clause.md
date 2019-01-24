---
title: Cláusula Alias (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 9cf97402d0b0a6cd16dd75a970c1d29a2fcc30a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498564"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="fd6d9-102">Cláusula Alias (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd6d9-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="fd6d9-103">Indica que um procedimento externo tem outro nome em sua DLL.</span><span class="sxs-lookup"><span data-stu-id="fd6d9-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd6d9-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd6d9-104">Remarks</span></span>  
 <span data-ttu-id="fd6d9-105">O `Alias` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="fd6d9-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="fd6d9-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="fd6d9-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="fd6d9-107">No exemplo a seguir, o `Alias` palavra-chave é usada para fornecer o nome da função em advapi32.dll, `GetUserNameA`, que `getUserName` é usado no lugar de neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="fd6d9-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="fd6d9-108">Função `getUserName` é chamado no sub `getUser`, que exibe o nome do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="fd6d9-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fd6d9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd6d9-109">See also</span></span>
- [<span data-ttu-id="fd6d9-110">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="fd6d9-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)

---
title: Cláusula Alias
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 77d4685f242864842e5a84b3a3de3ba1793e9aa4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866681"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="b8a1d-102">Cláusula Alias (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8a1d-102">Alias Clause (Visual Basic)</span></span>

<span data-ttu-id="b8a1d-103">Indica que um procedimento externo tem outro nome em sua DLL.</span><span class="sxs-lookup"><span data-stu-id="b8a1d-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8a1d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8a1d-104">Remarks</span></span>  

 <span data-ttu-id="b8a1d-105">A `Alias` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="b8a1d-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="b8a1d-106">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="b8a1d-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="b8a1d-107">No exemplo a seguir, a `Alias` palavra-chave é usada para fornecer o nome da função em advapi32.dll, `GetUserNameA` que `getUserName` é usada no lugar deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="b8a1d-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="b8a1d-108">A função `getUserName` é chamada em sub `getUser` , que exibe o nome do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="b8a1d-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="b8a1d-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8a1d-109">See also</span></span>

- [<span data-ttu-id="b8a1d-110">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="b8a1d-110">Keywords</span></span>](../keywords/index.md)

---
title: Cláusula Alias (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 62b34f5860b35104b6a8caa82c359383999dd61b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599168"
---
# <a name="alias-clause-visual-basic"></a>Cláusula Alias (Visual Basic)
Indica que um procedimento externo tem outro nome em sua DLL.  
  
## <a name="remarks"></a>Comentários  
 O `Alias` palavra-chave pode ser usado neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 No exemplo a seguir, o `Alias` palavra-chave é usada para fornecer o nome da função Advapi32, `GetUserNameA`, que `getUserName` é usado no lugar de neste exemplo. Função `getUserName` é chamado em sub `getUser`, que exibe o nome do usuário atual.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)

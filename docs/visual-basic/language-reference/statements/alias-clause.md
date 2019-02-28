---
title: Cláusula Alias (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: 3b1a66ecfd3c023a12ac62191ca3671a195b45a6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978217"
---
# <a name="alias-clause-visual-basic"></a>Cláusula Alias (Visual Basic)
Indica que um procedimento externo tem outro nome em sua DLL.  
  
## <a name="remarks"></a>Comentários  
 O `Alias` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 No exemplo a seguir, o `Alias` palavra-chave é usada para fornecer o nome da função em advapi32.dll, `GetUserNameA`, que `getUserName` é usado no lugar de neste exemplo. Função `getUserName` é chamado no sub `getUser`, que exibe o nome do usuário atual.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Consulte também
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)

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
# <a name="alias-clause-visual-basic"></a>Cláusula Alias (Visual Basic)

Indica que um procedimento externo tem outro nome em sua DLL.  
  
## <a name="remarks"></a>Comentários  

 A `Alias` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Declare](declare-statement.md)  
  
 No exemplo a seguir, a `Alias` palavra-chave é usada para fornecer o nome da função em advapi32.dll, `GetUserNameA` que `getUserName` é usada no lugar deste exemplo. A função `getUserName` é chamada em sub `getUser` , que exibe o nome do usuário atual.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Confira também

- [Palavras-chave](../keywords/index.md)

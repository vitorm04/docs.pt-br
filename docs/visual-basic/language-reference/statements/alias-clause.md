---
title: Cláusula Alias
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: a7f67224c5d26816bdc1974dc4aa82d796c41284
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349141"
---
# <a name="alias-clause-visual-basic"></a>Cláusula Alias (Visual Basic)
Indica que um procedimento externo tem outro nome em sua DLL.  
  
## <a name="remarks"></a>Comentários  
 A palavra-chave `Alias` pode ser usada neste contexto:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 No exemplo a seguir, a palavra-chave `Alias` é usada para fornecer o nome da função em advapi32. dll, `GetUserNameA`, que `getUserName` é usado no lugar deste exemplo. A função `getUserName` é chamada em sub `getUser`, que exibe o nome do usuário atual.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Consulte também

- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)

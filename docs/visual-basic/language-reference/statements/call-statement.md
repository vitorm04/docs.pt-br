---
title: Instrução Call (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 6d8fd8060789c4035fd38e41c5de7e43f6330e64
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977013"
---
# <a name="call-statement-visual-basic"></a>Instrução Call (Visual Basic)
Transfere o controle para um `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a>Partes  
|||
|---|---|
|`procedureName`|Necessário. Nome do procedimento de chamada.|
|`argumentList`|Opcional. Lista de variáveis ou expressões que representam os argumentos são passados para o procedimento quando ele é chamado. Vários argumentos são separados por vírgulas. Se você incluir `argumentList`, você deve colocá-la entre parênteses.|
|||
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `Call` palavra-chave quando você chama um procedimento. Para a maioria das chamadas de procedimento, não é necessário usar essa palavra-chave.  
  
 Normalmente, você usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador. Usar o `Call` palavra-chave para outros usos não é recomendado.  
  
 Se o procedimento retorna um valor, o `Call` instrução descarta-lo.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra dois exemplos em que o `Call` palavra-chave é necessária para chamar um procedimento. Nos dois exemplos, a expressão de chamada não começa com um identificador.  
  
 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

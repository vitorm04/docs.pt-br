---
title: Instrução Continue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638240"
---
# <a name="continue-statement-visual-basic"></a>Instrução Continue (Visual Basic)
Transfere o controle imediatamente para a próxima iteração de um loop.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode transferir de dentro de um `Do`, `For`, ou `While` loop para a próxima iteração do loop. Controle passa imediatamente para o teste de condição de loop, que é equivalente a transferir para o `For` ou `While` instrução, ou para o `Do` ou `Loop` instrução que contém o `Until` ou `While` cláusula.  
  
 Você pode usar `Continue` em qualquer local no loop que permite transferências. As regras que permite a transferência de controle são o mesmo que o [instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).  
  
 Por exemplo, se um loop está totalmente contido dentro de um `Try` bloco, um `Catch` bloco, ou um `Finally` bloco, você pode usar `Continue` para transferir o loop. Se, por outro lado, o `Try`... `End Try` estrutura está contida dentro do loop, você não pode usar `Continue` para transferir o controle da `Finally` bloco e você pode usá-lo para transferir de uma `Try` ou `Catch` bloquear somente se você transferir completamente fora do `Try`... `End Try` estrutura.  
  
 Se você tem loops aninhados do mesmo tipo, por exemplo uma `Do` loop dentro de outra `Do` loop, um `Continue Do` ignora a instrução para a próxima iteração de mais interna `Do` loop que o contém. Não é possível usar `Continue` para ignorar a próxima iteração de um loop que contém o mesmo tipo.  
  
 Se você tem loops aninhados de diferentes tipos, por exemplo uma `Do` loop dentro de uma `For` loop, pule para a próxima iteração de qualquer um loop usando a `Continue Do` ou `Continue For`.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo de código usa o `Continue While` instrução para ignorar a próxima coluna de uma matriz se o divisor é zero. O `Continue While` está dentro de um `For` loop. Ele transfere para o `While col < lastcol` instrução, que é a próxima iteração do mais interna `While` loop que contém o `For` loop.  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Consulte também

- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

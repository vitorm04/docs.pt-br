---
title: Instrução Exit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 63bcc5d5205681917ba30bdb73bc496307a6322a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672507"
---
# <a name="exit-statement-visual-basic"></a>Instrução Exit (Visual Basic)
Sai de um procedimento ou bloco e transfere o controle imediatamente para a instrução após a chamada de procedimento ou a definição de bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Instruções  
 `Exit Do`  
 Sai imediatamente o `Do` loop no qual ele aparece. A execução continua com a instrução após a `Loop` instrução. `Exit Do` pode ser usado somente dentro de um `Do` loop. Quando usado dentro aninhados `Do` loops, `Exit Do` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit For`  
 Sai imediatamente o `For` loop no qual ele aparece. A execução continua com a instrução após a `Next` instrução. `Exit For` pode ser usado somente dentro de um `For`... `Next` ou `For Each`... `Next` loop. Quando usado dentro aninhados `For` loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit Function`  
 Sai imediatamente o `Function` procedimento no qual ele aparece. A execução continua com a instrução após a instrução que chamou o `Function` procedimento. `Exit Function` pode ser usado somente dentro de um `Function` procedimento.  
  
 Para especificar um valor de retorno, você pode atribuir o valor para o nome da função em uma linha antes do `Exit Function` instrução. Para atribuir o valor de retorno e a função em uma instrução de saída, em vez disso, você pode usar o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Sai imediatamente o `Property` procedimento no qual ele aparece. A execução continua com a instrução que chamou o `Property` procedimento, ou seja, com a instrução solicitando ou definindo o valor da propriedade. `Exit Property` pode ser usado somente dentro de uma propriedade `Get` ou `Set` procedimento.  
  
 Para especificar um valor de retorno em uma `Get` procedimento, você pode atribuir o valor para o nome da função em uma linha antes do `Exit Property` instrução. Para atribuir o valor de retorno e a saída a `Get` procedimento em uma instrução, você pode usar o `Return` instrução.  
  
 Em um `Set` procedimento, o `Exit Property` instrução é equivalente ao `Return` instrução.  
  
 `Exit Select`  
 Sai imediatamente o `Select Case` bloco no qual ele aparece. A execução continua com a instrução após a `End Select` instrução. `Exit Select` pode ser usado somente dentro de um `Select Case` instrução.  
  
 `Exit Sub`  
 Sai imediatamente o `Sub` procedimento no qual ele aparece. A execução continua com a instrução após a instrução que chamou o `Sub` procedimento. `Exit Sub` pode ser usado somente dentro de um `Sub` procedimento.  
  
 Em um `Sub` procedimento, o `Exit Sub` instrução é equivalente ao `Return` instrução.  
  
 `Exit Try`  
 Sai imediatamente a `Try` ou `Catch` bloco no qual ele aparece. A execução continua com o `Finally` bloquear se houver um, ou com a instrução após a `End Try` instrução caso contrário. `Exit Try` pode ser usado somente dentro de um `Try` ou `Catch` bloco e não estão dentro um `Finally` bloco.  
  
 `Exit While`  
 Sai imediatamente o `While` loop no qual ele aparece. A execução continua com a instrução após a `End While` instrução. `Exit While` pode ser usado somente dentro de um `While` loop. Quando usados aninhados dentro `While` loops `Exit While` transfere o controle para o loop que está um nível acima do loop onde `Exit While` ocorre.  
  
## <a name="remarks"></a>Comentários  
 Não confunda `Exit` instruções com `End` instruções. `Exit` não defina o final de uma instrução.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a condição de loop para o loop quando a `index` variável é maior que 100. O `If` instrução no loop, no entanto, faz com que o `Exit Do` instrução para interromper o loop quando a variável de índice é maior que 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atribui o valor de retorno para o nome da função `myFunction`e, em seguida, usa `Exit Function` para retornar da função.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) para atribuir o valor de retorno e a função de saída.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md)
- [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

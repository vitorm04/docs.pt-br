---
title: "Instrução Exit (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Exit
dev_langs:
- VB
helpviewer_keywords:
- execution, ending
- files, closing
- programs, quitting
- code, exiting
- Exit statement
- program termination
- execution, stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 38fb1ad5c00fa3be9850292f737ab24a392a446b
ms.lasthandoff: 03/13/2017

---
# <a name="exit-statement-visual-basic"></a>Instrução Exit (Visual Basic)
Sai de um procedimento ou bloco e transfere o controle imediatamente para a instrução após a chamada de procedimento ou a definição de bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a>Instruções  
 `Exit Do`  
 Sai imediatamente o `Do` um loop no qual ele aparece. A execução continua com a declaração que segue a `Loop` instrução. `Exit Do`pode ser usado somente dentro de um `Do` loop. Quando usado dentro aninhados `Do` loops, `Exit Do` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit For`  
 Sai imediatamente o `For` um loop no qual ele aparece. A execução continua com a declaração que segue a `Next` instrução. `Exit For`pode ser usado somente dentro de um `For`... `Next` or `For Each`... `Next` loop. Quando usado dentro aninhados `For` loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit Function`  
 Sai imediatamente o `Function` procedimento no qual ele aparece. A execução continua com a instrução após a declaração que chamou o `Function` procedimento. `Exit Function`pode ser usado somente dentro de uma `Function` procedimento.  
  
 Para especificar um valor de retorno, você pode atribuir o valor ao nome da função em uma linha antes do `Exit Function` instrução. Para atribuir o valor de retorno e a função em uma instrução exit, você pode usar o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Sai imediatamente o `Property` procedimento no qual ele aparece. A execução continua com a declaração que chamou o `Property` procedimento, ou seja, com a declaração requisitando ou configurando o valor da propriedade. `Exit Property`pode ser usado somente dentro de uma propriedade `Get` ou `Set` procedimento.  
  
 Para especificar um valor de retorno em uma `Get` procedimento, você pode atribuir o valor ao nome da função em uma linha antes do `Exit Property` instrução. Para atribuir o valor de retorno e saia do `Get` procedimento em uma instrução, você pode usar o `Return` instrução.  
  
 Em um `Set` procedimento, o `Exit Property` declaração equivale a `Return` instrução.  
  
 `Exit Select`  
 Sai imediatamente o `Select Case` bloco no qual ele aparece. A execução continua com a declaração que segue a `End Select` instrução. `Exit Select`pode ser usado somente dentro de um `Select Case` instrução.  
  
 `Exit Sub`  
 Sai imediatamente o `Sub` procedimento no qual ele aparece. A execução continua com a instrução após a declaração que chamou o `Sub` procedimento. `Exit Sub`pode ser usado somente dentro de uma `Sub` procedimento.  
  
 Em um `Sub` procedimento, o `Exit Sub` declaração equivale a `Return` instrução.  
  
 `Exit Try`  
 Sai imediatamente o `Try` ou `Catch` bloco no qual ele aparece. A execução continua com a `Finally` bloquear se houver um, ou com o seguinte instrução de `End Try` instrução caso contrário. `Exit Try`pode ser usado somente dentro de um `Try` ou `Catch` bloco e não dentro um `Finally` bloco.  
  
 `Exit While`  
 Sai imediatamente o `While` um loop no qual ele aparece. A execução continua com a declaração que segue a `End While` instrução. `Exit While`pode ser usado somente dentro de um `While` loop. Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle ao loop que está um nível acima do loop onde `Exit While` ocorre.  
  
## <a name="remarks"></a>Comentários  
 Não confunda `Exit` instruções com `End` instruções. `Exit`define o fim de uma instrução.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, a condição de loop para o loop quando o `index` variável é maior que 100. O `If` instrução loop, no entanto, faz o `Exit Do` instrução para interromper o loop quando a variável de índice for maior que 10.  
  
 [!code-vb[VbVbalrStatements&#133;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction`e, em seguida, usa `Exit Function` para retornar da função.  
  
 [!code-vb[VbVbalrStatements&#23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) para atribuir o valor de retorno e a função exit.  
  
 [!code-vb[VbVbalrStatements&#24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução continue](../../../visual-basic/language-reference/statements/continue-statement.md)   
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md)   
 [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)

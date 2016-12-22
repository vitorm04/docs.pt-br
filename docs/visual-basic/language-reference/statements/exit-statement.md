---
title: "Instru&#231;&#227;o Exit (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Exit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "código, saindo"
  - "execução, terminando"
  - "execução, parando"
  - "instrução Exit"
  - "arquivos, fechamento"
  - "encerramento do programa"
  - "programas, saindo"
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Exit (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Sai de um procedimento ou bloco e tranfere controle imediatamente à declaração após o procedimento ou à definição do bloco.  
  
## Sintaxe  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## Instruções  
 `Exit Do`  
 Sai imediatamente do loop `Do` no qual ele aparece.  Execução continua com a seguinte instrução de `Loop` instrução.  `Exit Do`pode ser usado somente dentro de um `Do` loop.  Quando usado dentro de loops `Do` aninhados, `Exit Do` sai do loop mais interno e transfere controle ao segundo maior nível de aninhamento.  
  
 `Exit For`  
 Sai imediatamente do loop `For` no qual ele aparece.  Execução continua com a seguinte instrução de `Next` instrução.  `Exit For`pode ser usado somente dentro de um `For`...`Next` or `For Each`...`Next` loop.  Quando usado dentro de loops `For` aninhados, `Exit For` sai do loop mais interno e transfere controle ao segundo maior nível de aninhamento.  
  
 `Exit Function`  
 Sai imediatamente do procedimento `Function` no qual ele aparece.  Execução continua com a instrução após a instrução que chamou o `Function` procedimento.  `Exit Function`pode ser usado somente dentro de um `Function` procedimento.  
  
 Para especificar um valor de retorno, você pode atribuir o valor ao nome da função em uma linha antes do `Exit Function` instrução.  Para atribuir o valor de retorno e a função em uma instrução de sair, você pode usar o [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Exit Property`  
 Sai imediatamente do procedimento `Property` no qual ele aparece.  Execução continua com a instrução que chamou o `Property` procedimento, ou seja, com a instrução solicitando ou definir o valor da propriedade.  `Exit Property`pode ser usado somente dentro de uma propriedade `Get` ou `Set` procedimento.  
  
 Para especificar um valor de retorno em um `Get` procedimento, você pode atribuir o valor ao nome da função em uma linha antes do `Exit Property` instrução.  Para atribuir o valor de retorno e sair do `Get` procedimento em uma instrução, você pode usar o `Return` instrução.  
  
 Em um `Set` procedimento, o `Exit Property` declaração equivale a `Return` instrução.  
  
 `Exit Select`  
 Sai imediatamento do bloco `Select Case` no qual ele aparece.  Execução continua com a seguinte instrução de `End Select` instrução.  `Exit Select`pode ser usado somente dentro de um `Select Case` instrução.  
  
 `Exit Sub`  
 Sai imediatamente do procedimento `Sub` no qual ele aparece.  Execução continua com a instrução após a instrução que chamou o `Sub` procedimento.  `Exit Sub`pode ser usado somente dentro de um `Sub` procedimento.  
  
 Em um `Sub` procedimento, o `Exit Sub` declaração equivale a `Return` instrução.  
  
 `Exit Try`  
 Sai imediatamente do bloco `Try` ou `Catch` no qual ele aparece.  Execução continua com o `Finally` bloquear se houver um, ou com a seguinte instrução de `End Try` outro tipo de instrução.  `Exit Try`pode ser usado somente dentro de um `Try` ou `Catch` bloco e não entre um `Finally` bloco.  
  
 `Exit While`  
 Sai imediatamente do loop `While` no qual ele aparece.  Execução continua com a seguinte instrução de `End While` instrução.  `Exit While`pode ser usado somente dentro de um `While` loop.  Quando usado dentro de loops `While` aninhados, `Exit While` transfere controle ao loop que está um nível acima do loop onde `Exit While` ocorre.  
  
## Comentários  
 Não confunda `Exit` instruções com `End` instruções.  `Exit`não define o final de uma instrução.  
  
## Exemplo  
 No exemplo a seguir, a condição de loop interrompe o loop quando o `index` variável é maior do que 100.  O `If` instrução no loop, no entanto, faz com que o `Exit Do` a instrução para interromper o loop quando a variável de índice é maior que 10.  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## Exemplo  
 O exemplo a seguir atribui o valor de retorno para o nome da função `myFunction`e, em seguida, usa `Exit Function` para retornar da função.  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## Exemplo  
 O exemplo a seguir usa a [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) para atribuir o valor de retorno e a função de sair.  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## Consulte também  
 [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)   
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md)   
 [Instrução Stop](../../../visual-basic/language-reference/statements/stop-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
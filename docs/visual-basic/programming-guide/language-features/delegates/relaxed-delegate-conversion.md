---
title: "Convers&#227;o de delegado reduzida (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversões, delegado relaxado"
  - "delegados [Visual Basic], conversão relaxada"
  - "conversão de delegado relaxada [Visual Basic]"
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Convers&#227;o de delegado reduzida (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Conversão de delegado relaxados permite que você atribuir sub\-rotinas e funções a delegados ou manipuladores, mesmo quando suas assinaturas não são idênticas. Dessa forma, a ligação a delegados é consistente com a ligação já permitida para invocações do método.  
  
## Os parâmetros e o tipo de retorno  
 No lugar da assinatura de correspondência exata, a conversão reduzida requer que as seguintes condições ser atendidas quando `Option Strict` for definido como `On`:  
  
-   Uma conversão de expansão deve existir do tipo de dados de cada parâmetro do delegado ao tipo de dados do parâmetro correspondente da função atribuída ou `Sub`.  No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer`.  O parâmetro `m` nas expressões lambda atribuídas deve ter um tipo de dados para o qual há uma conversão de ampliação de `Integer`,como `Long` ou `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Conversões de restrição são permitidas somente quando `Option Strict` é definida como `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Uma conversão de expansão deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` para o tipo de retorno do delegado.  Nos exemplos a seguir, o corpo de cada expressão lambda atribuído deve ser avaliada como um tipo de dados que amplia a `Integer` porque o tipo de retorno de `del1` é `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Se `Option Strict` é definida como `Off`, a restrição de ampliaçao será removida em ambas as direções.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## Omitindo especificações de parâmetros  
 Delegados reduzidos também permitem que você omita completamente especificações de parâmetro no método atribuído:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Observe que não é possível especificar alguns parâmetros e omitir outros.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 A capacidade para omitir os parâmetros é útil em uma situação como definir um manipulador de eventos, onde vários parâmetros complexos estão envolvidos.  Os argumentos para alguns manipuladores de eventos não são usados.  Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento está registrado e ignora os argumentos.  Delegados reduzidos permitem que você omita os argumentos em tais declarações quando não há ambiguidades nos resultados.  No exemplo a seguir, o método totalmente especificado `OnClick`pode ser regravado como `RelaxedOnClick`.  
  
```vb#  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## Exemplos AddressOf  
 Expressões Lambda são usadas nos exemplos anteriores para deixar as relações de tipo fáceis de usar.  No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf`, `Handles`,ou `AddHandler`.  
  
 No exemplo a seguir, as funções `f1`,`f2`,`f3`,e `f4` podem ser todas atribuídas a `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 O exemplo a seguir é válido somente quando `Option Strict` for definido como `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## Descartando função de retorno  
 Representante reduzida de Conversão permite que você atribuir uma função a um `Sub` representante, ignorando efetivamente o valor de retorno da função.  No entanto, não é possível atribuir uma `Sub` a uma função delegada.  No exemplo a seguir, o endereço da função `doubler` é atribuído a `Sub` delegado `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## Consulte também  
 [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Como passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
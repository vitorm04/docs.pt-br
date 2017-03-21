---
title: "Conversão de delegado (Visual Basic) reduzida | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
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
ms.openlocfilehash: c0160165d3df9755481b89570b4cd135b3a990a2
ms.lasthandoff: 03/13/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Conversão de delegado reduzida (Visual Basic)
Conversão de delegado reduzida permite que você atribua sub-rotinas e funções a delegados ou manipuladores mesmo quando as assinaturas não são idênticas. Portanto, a ligação a delegados fica consistente com a associação já permitida para invocações de método.  
  
## <a name="parameters-and-return-type"></a>Parâmetros e tipo de retorno  
 Em vez de correspondência exata de assinatura, a conversão reduzida requer que as seguintes condições ser atendidas quando `Option Strict` é definido como `On`:  
  
-   Uma conversão de ampliação deve existir do tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro correspondente da função atribuída ou `Sub`. No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer`. Parâmetro `m` lambda atribuídas expressões devem ter um tipo de dados para o qual há uma conversão de ampliação de `Integer`, como `Long` ou `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates n º&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates n º&2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Conversões de restrição são permitidas somente quando `Option Strict` é definido como `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates n º&8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Uma conversão de ampliação deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` para o tipo de retorno do delegado. Nos exemplos a seguir, o corpo de cada expressão lambda atribuída deve ser avaliada como um tipo de dados que amplia a `Integer` porque o tipo de retorno de `del1` é `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates n º&3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Se `Option Strict` é definido como `Off`, a restrição de ampliação será removida em ambas as direções.  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>Omitindo especificações de parâmetros  
 Delegados relaxados também permitem que você omita completamente especificações de parâmetro no método atribuído:  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Observe que não é possível especificar alguns parâmetros e omitir outros.  
  
 [!code-vb[VbVbalrRelaxedDelegates&#15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 A capacidade para omitir os parâmetros é útil em uma situação como definir um manipulador de eventos, onde vários parâmetros complexos estão envolvidos. Os argumentos para alguns manipuladores de eventos não são usados. Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento está registrado e ignora os argumentos. Delegados relaxados permitem que você omita os argumentos em tais declarações quando não há ambiguidades nos resultados. No exemplo a seguir, o método totalmente especificado `OnClick` pode ser reescrito como `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Exemplos de AddressOf  
 Expressões lambda são usadas nos exemplos anteriores para facilitar ver os relacionamentos de tipo. No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf`, `Handles`, ou `AddHandler`.  
  
 No exemplo a seguir, as funções `f1`, `f2`, `f3`, e `f4` podem ser atribuídos a `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates&#7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 O exemplo a seguir é válido somente quando `Option Strict` é definido como `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates&#14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Descartando função de retorno  
 Conversão de delegado reduzida permite atribuir uma função a um `Sub` representante, ignorando efetivamente o valor de retorno da função. No entanto, você não pode atribuir um `Sub` a uma função delegada. No exemplo a seguir, o endereço da função `doubler` é atribuído a `Sub` delegar `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates n º&11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Como: passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

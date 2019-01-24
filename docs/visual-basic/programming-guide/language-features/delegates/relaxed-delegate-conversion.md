---
title: Conversão de delegado reduzida (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: e2838b6473b8c00927073a530b4b49870fcfa9c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600369"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>Conversão de delegado reduzida (Visual Basic)
Conversão de delegado reduzida permite que você atribua sub-rotinas e funções a delegados ou manipuladores mesmo quando as assinaturas não são idênticas. Dessa forma, a ligação a delegados é consistente com a associação já permitida para invocações de método.  
  
## <a name="parameters-and-return-type"></a>Parâmetros e tipo de retorno  
 Em vez de correspondência exata de assinatura, a conversão reduzida requer que as seguintes condições ser atendidas quando `Option Strict` é definido como `On`:  
  
-   Uma conversão de ampliação deve existir do tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro correspondente da função atribuída ou `Sub`. No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer`. Parâmetro `m` lambda atribuídas expressões devem ter um tipo de dados para o qual há uma conversão de ampliação de `Integer`, como `Long` ou `Double`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     Conversões de estreitamento são permitidas somente quando `Option Strict` é definido como `Off`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   Uma conversão de ampliação deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` para o tipo de retorno do delegado. Nos exemplos a seguir, o corpo de cada expressão lambda atribuída deve ser avaliada como um tipo de dados é ampliado para `Integer` porque o tipo de retorno de `del1` é `Integer`.  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 Se `Option Strict` é definido como `Off`, a restrição de ampliação é removido em ambas as direções.  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a>A omissão de especificações de parâmetro  
 Delegados relaxados também permitem que você omita completamente especificações de parâmetro no método atribuído:  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 Observe que você não pode especificar alguns parâmetros e omitir outras pessoas.  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 A capacidade de omitir parâmetros é útil em uma situação como a definição de um manipulador de eventos, onde vários parâmetros complexos estão envolvidos. Os argumentos para alguns manipuladores de eventos não são usados. Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento é registrado e ignora os argumentos. Delegados relaxados permitem que você omita os argumentos em tais declarações quando nenhum resultado ambiguidades. No exemplo a seguir, o método totalmente especificado `OnClick` pode ser reescrita como `RelaxedOnClick`.  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>Exemplos de AddressOf  
 Expressões lambda são usadas nos exemplos anteriores para facilitar as relações de tipo ver. No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf`, `Handles`, ou `AddHandler`.  
  
 No exemplo a seguir, funções `f1`, `f2`, `f3`, e `f4` podem ser atribuídos a `Del1`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 O exemplo a seguir é válido somente quando `Option Strict` é definido como `Off`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a>Descartando função de retorno  
 Conversão de delegado reduzida permite que você atribua uma função a um `Sub` representante, ignorando efetivamente o valor de retorno da função. No entanto, não é possível atribuir um `Sub` para um delegado de função. No exemplo a seguir, o endereço da função `doubler` for atribuído a `Sub` delegar `Del3`.  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Expressões Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Como: Passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)

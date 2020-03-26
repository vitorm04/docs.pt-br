---
title: O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249520"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência
Uma `If` expressão pode ter dois ou três argumentos. Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo de valor anulado. Se o primeiro argumento avaliar `Nothing`qualquer outra coisa que não, seu valor é devolvido. Se o primeiro argumento `Nothing`avaliar, o segundo argumento é avaliado e devolvido.  
  
 Por exemplo, o código `If` a seguir contém duas expressões, uma com três argumentos e outra com dois argumentos. As expressões calculam e retornam o mesmo valor.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 As seguintes expressões causam este erro:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **ID de erro:** BC33107  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se você não puder alterar o código para que o primeiro argumento seja um tipo `If` de valor ou `If...Then...Else` tipo de referência anulado, considere converter-se para uma expressão de três argumentos ou para uma declaração.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Confira também

- [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Tipos de valor anulados](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

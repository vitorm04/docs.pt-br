---
title: O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 32ff0adca9d35e6b5439ae06be85414924dac2e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838611"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>O primeiro operando em uma expressão 'If' binária deve ser um tipo que permite valor nulo ou um de referência
Um `If` expressão pode levar dois ou três argumentos. Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo anulável. Se o primeiro argumento for avaliado como algo diferente de `Nothing`, seu valor será retornado. Se o primeiro argumento é avaliado como `Nothing`, o segundo argumento é avaliado e retornado.  
  
 Por exemplo, o código a seguir contém duas `If` expressões, uma com três argumentos e outra com dois argumentos. As expressões de calculam e retornam o mesmo valor.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 As expressões a seguir causam esse erro:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **ID do erro:** BC33107  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você não pode alterar o código para que o primeiro argumento é um tipo anulável ou tipo de referência, considere a conversão para um argumento de três `If` expressão, ou como um `If...Then...Else` instrução.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Consulte também

- [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)
- [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

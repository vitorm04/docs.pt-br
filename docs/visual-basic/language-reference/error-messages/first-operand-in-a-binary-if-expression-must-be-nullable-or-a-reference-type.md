---
title: "O primeiro operando em um binário &quot;If&quot; expressão deve ser anulável ou um tipo de referência | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
dev_langs:
- VB
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: f8a761909902075347470e3703d9604839781f21
ms.lasthandoff: 03/13/2017

---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>O primeiro operando em um binário 'If' expressão deve ser anulável ou um tipo de referência
Um `If` expressão pode levar dois ou três argumentos. Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo anulável. Se o primeiro argumento for avaliado como algo diferente de `Nothing`, seu valor será retornado. Se o primeiro argumento for avaliado como `Nothing`, o segundo argumento é avaliado e retornado.  
  
 Por exemplo, o código a seguir contém duas `If` expressões, uma com três argumentos e outra com dois argumentos. As expressões calculam e retornam o mesmo valor.  
  
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
  
-   Se você não pode alterar o código para que o primeiro argumento é um tipo anulável ou tipo de referência, considere a conversão para um argumento de três `If` expressão, ou um `If...Then...Else` instrução.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Consulte também  
 [Se operador](../../../visual-basic/language-reference/operators/if-operator.md)   
 [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)

---
title: "O primeiro operando em uma express&#227;o &#39;If&#39; bin&#225;ria deve ser um tipo que permite valor nulo ou um de refer&#234;ncia | Microsoft Docs"
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
  - "bc33107"
  - "vbc33107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33107"
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O primeiro operando em uma express&#227;o &#39;If&#39; bin&#225;ria deve ser um tipo que permite valor nulo ou um de refer&#234;ncia
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma expressão `If` pode receber ou dois ou três argumentos.  Quando você envia apenas dois argumentos, o primeiro argumento deve ser um tipo de referência ou um tipo anulável.  Se o primeiro argumento for avaliado como algo diferente de `Nothing`, seu valor será retornado.  Se o primeiro argumento é avaliado como `Nothing`, o segundo argumento é avaliado e retornado.  
  
 Por exemplo, o código a seguir contém duas expressões `If` uma com três argumentos e outra com dois argumentos.  As expressões calculam e retornam o mesmo valor.  
  
```vb#  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 As expressões a seguir causam este erro:  
  
```vb#  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Identificação do erro:**  BC33107  
  
### Para corrigir este erro  
  
-   Se você não pode alterar o código para que o primeiro argumento é um tipo anulável ou um tipo de referência, considere a conversão de um argumento de três `If` a expressão, ou para um `If...Then...Else` instrução.  
  
    ```vb#  
    Console.WriteLine(If(choice1 < choice2, 1, 2))  
    Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
    ```  
  
## Consulte também  
 [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Tipos de valor que permitem valor nulo](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
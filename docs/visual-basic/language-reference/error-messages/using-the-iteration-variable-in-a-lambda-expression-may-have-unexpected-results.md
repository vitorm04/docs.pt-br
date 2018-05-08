---
title: O uso de uma variável de iteração em uma expressão lambda pode ter resultados inesperados
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 7144a5fd4a197fddaf1ac4132df0ff70995ad067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>O uso de uma variável de iteração em uma expressão lambda pode ter resultados inesperados
Uso da variável de iteração em uma expressão lambda pode ter resultados inesperados. Em vez disso, crie uma variável local no loop e atribua o valor da variável de iteração.  
  
 Esse aviso aparece quando você usa uma variável de iteração de loop em uma expressão lambda que é declarada dentro do loop. Por exemplo, o exemplo a seguir faz com que o aviso apareça.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 O exemplo a seguir mostra os resultados inesperados podem ocorrer.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 O `For` loop cria uma matriz de expressões lambda, cada um deles retorna o valor da variável de iteração de loop `i`. Quando as expressões lambda são avaliadas no `For Each` loop, você pode esperar ver 0, 1, 2, 3 e 4 exibido, os valores sucessivos `i` no `For` loop. Em vez disso, você pode ver o valor final do `i` exibidos cinco vezes:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42324  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribuir o valor da variável de iteração a uma variável local e use a variável local na expressão lambda.  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>Consulte também  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)

---
title: "O uso de uma vari&#225;vel de itera&#231;&#227;o em uma express&#227;o lambda pode ter resultados inesperados | Microsoft Docs"
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
  - "vbc42324"
  - "bc42324"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42324"
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O uso de uma vari&#225;vel de itera&#231;&#227;o em uma express&#227;o lambda pode ter resultados inesperados
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uso da variável de iteração em uma expressão lambda pode ter resultados inesperados.Em vez disso, crie uma variável local dentro do loop e atribua o valor da variável de iteração.  
  
 Esse aviso aparece quando você usa uma variável de iteração do loop em uma expressão lambda que é declarada dentro do loop.  Por exemplo, o exemplo a seguir faz com que o aviso apareça.  
  
```vb#  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 O exemplo a seguir mostra os resultados inesperados que possam ocorrer.  
  
```vb#  
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
  
 O `For` loop cria uma matriz de expressões lambda, cada um deles retorna o valor da variável de iteração do loop `i`.  Quando as expressões lambda são avaliadas na `For Each` loop, você pode esperar ver 0, 1, 2, 3 e 4 exibido, os valores de sucessivos de `i` na `For` loop.  Em vez disso, você pode ver o valor final da `i` exibidas cinco vezes:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Por padrão, essa é uma mensagem de aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC42324  
  
### Para corrigir este erro  
  
-   Atribuir o valor da variável de iteração a uma variável local e use a variável local na expressão lambda.  
  
    ```vb#  
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
  
## Consulte também  
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
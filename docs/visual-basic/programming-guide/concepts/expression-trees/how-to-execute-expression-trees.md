---
title: "Como: executar &#225;rvores de express&#227;o (Visual Basic) | Microsoft Docs"
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
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: executar &#225;rvores de express&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como executar uma árvore de expressão. Executar uma árvore de expressão pode retornar um valor, ou ele pode executar apenas uma ação como chamar um método.  
  
 Somente as árvores de expressão que representam as expressões lambda podem ser executadas. Árvores de expressão que representam as expressões lambda são do tipo <xref:System.Linq.Expressions.LambdaExpression> ou <xref:System.Linq.Expressions.Expression%601>. Para executar essas árvores de expressão, chame o <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> método para criar um delegado executável e, em seguida, chamar o delegado.  
  
> [!NOTE]
>  Se o tipo do delegado não é conhecido, ou seja, a expressão lambda é do tipo <xref:System.Linq.Expressions.LambdaExpression> e não <xref:System.Linq.Expressions.Expression%601>, você deve chamar o <xref:System.Delegate.DynamicInvoke%2A> método no delegado em vez de chamá\-lo diretamente.  
  
 Se uma árvore de expressão não representa uma expressão lambda, você pode criar uma nova expressão lambda que tenha a árvore de expressão original como o corpo, chamando o <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> método. Em seguida, você pode executar a expressão lambda, conforme descrito anteriormente nesta seção.  
  
## Exemplo  
 O exemplo de código a seguir demonstra como executar uma árvore de expressão que representa a elevar um número a uma potência criando uma expressão lambda e executá\-lo. O resultado, que representa o número elevado à potência, é exibido.  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## Compilando o código  
  
-   Adicione uma referência a System.Core.dll se ele já não foi referenciado.  
  
-   Inclua o namespace System.Linq.Expressions.  
  
## Consulte também  
 [Árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Como: modificar árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
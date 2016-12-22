---
title: "&#193;rvores de express&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#193;rvores de express&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Árvores de expressão representam código em uma estrutura de dados de árvore, onde cada nó é uma expressão, por exemplo, uma chamada de método ou uma operação binária como `x < y`.  
  
 Você pode compilar e executar código representado por árvores de expressão. Isso permite a modificação dinâmica de código executável, a execução de consultas LINQ em vários bancos de dados e a criação de consultas dinâmicas. Para obter mais informações sobre árvores de expressão no LINQ, consulte [Como: usar árvores de expressão para compilar consultas dinâmicas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).  
  
 Árvores de expressão também são usados no tempo de execução de linguagem dinâmico \(DLR\) para fornecer interoperabilidade entre linguagens dinâmicas e o .NET Framework e permitem a gravadores compiladores emitam árvores de expressão em vez de Microsoft intermediate language \(MSIL\). Para obter mais informações sobre o DLR, consulte [Visão geral do Dynamic Language Runtime](../Topic/Dynamic%20Language%20Runtime%20Overview.md).  
  
 Você pode ter o compilador c\# ou Visual Basic criar uma árvore de expressão para você com base em uma expressão lambda anônima ou criar árvores de expressão manualmente usando o <xref:System.Linq.Expressions> namespace.  
  
## Criando árvores de expressão de expressões Lambda  
 Quando uma expressão lambda é atribuída a uma variável do tipo <xref:System.Linq.Expressions.Expression%601>, o compilador emite código para construir uma árvore de expressão que representa a expressão lambda.  
  
 O compilador do Visual Basic pode gerar árvores de expressão somente de expressões lambdas \(ou lambdas de linha única\). Ele não é possível analisar instruções lambdas \(ou lambdas de várias linhas\). Para obter mais informações sobre expressões lambda em Visual Basic, consulte [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Os exemplos de código a seguir demonstram como fazer com que o compilador do Visual Basic criar uma árvore de expressão que representa a expressão lambda `Function(num) num < 5`.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## Criando árvores de expressão usando a API  
 Para criar árvores de expressão usando a API, use o <xref:System.Linq.Expressions.Expression> classe. Essa classe contém métodos de fábrica estático que criar expressão de nós da árvore de tipos específicos, por exemplo, <xref:System.Linq.Expressions.ParameterExpression>, que representa uma variável ou parâmetro, ou <xref:System.Linq.Expressions.MethodCallExpression>, que representa uma chamada de método.<xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, e outros tipos específicos de expressão também são definidos no <xref:System.Linq.Expressions> namespace. Esses tipos derivam do tipo abstrato <xref:System.Linq.Expressions.Expression>.  
  
 O exemplo de código a seguir demonstra como criar uma árvore de expressão que representa a expressão lambda `Function(num) num < 5` usando a API.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 No .NET Framework 4 ou posterior, a API de árvores de expressão também suporta atribuições e expressões de fluxo de controle, como loops, blocos condicionais, e `try-catch` blocos. Usando a API, você pode criar árvores de expressão são mais complexas do que aquelas que podem ser criados a partir de expressões lambda pelo compilador do Visual Basic. O exemplo a seguir demonstra como criar uma árvore de expressão que calcula o fatorial de um número.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Para obter mais informações, consulte [Gerar métodos dinâmicos com árvores de expressão no Visual Studio 2010 \(ou posterior\)](http://go.microsoft.com/fwlink/?LinkId=169513).  
  
## Analisando árvores de expressão  
 O exemplo de código a seguir demonstra como a árvore de expressão que representa a expressão lambda `Function(num) num < 5` podem ser divididos em suas partes.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
## Imutabilidade das árvores de expressão  
 Árvores de expressão devem ser imutáveis. Isso significa que, se você quiser modificar uma árvore de expressão, você precisa construir uma nova árvore de expressão copiando um existente e substituindo seus nós. Você pode usar um visitante de árvore de expressão para percorrer a árvore de expressão existente. Para obter mais informações, consulte [Como: modificar árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).  
  
## Compilando árvores de expressão  
 O <xref:System.Linq.Expressions.Expression%601> tipo fornece o <xref:System.Linq.Expressions.Expression%601.Compile%2A> método que compila o código representado por uma árvore de expressão para um delegado executável.  
  
 O exemplo de código a seguir demonstra como compilar uma árvore de expressão e executar o código resultante.  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 Para obter mais informações, consulte [Como: executar árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).  
  
## Consulte também  
 <xref:System.Linq.Expressions>   
 [Como: executar árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [Como: modificar árvores de expressão \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)   
 [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Visão geral do Dynamic Language Runtime](../Topic/Dynamic%20Language%20Runtime%20Overview.md)   
 [Conceitos de programação \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/index.md)
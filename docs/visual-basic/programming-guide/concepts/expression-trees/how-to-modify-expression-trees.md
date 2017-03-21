---
title: "Como: modificar árvores de expressão (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fb4e818eed7d6547e091c914d40b3ce87af59512
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Como: modificar árvores de expressão (Visual Basic)
Este tópico mostra como modificar uma árvore de expressão. Árvores de expressão são imutáveis, o que significa que eles não podem ser modificados. Para alterar uma árvore de expressão, você deve criar uma cópia de uma árvore de expressão existente e quando você cria a cópia, faça as alterações necessárias. Você pode usar o <xref:System.Linq.Expressions.ExpressionVisitor>classe para percorrer uma árvore de expressão existente e copiar cada nó que ele entra.</xref:System.Linq.Expressions.ExpressionVisitor>  
  
### <a name="to-modify-an-expression-tree"></a>Para modificar uma árvore de expressão  
  
1.  Criar um novo **aplicativo de Console** projeto.  
  
2.  Adicionar uma `Imports` instrução ao arquivo para o `System.Linq.Expressions` namespace.  
  
3.  Adicionar o `AndAlsoModifier` classe ao seu projeto.  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     Essa classe herda o <xref:System.Linq.Expressions.ExpressionVisitor>da classe e é especializada para modificar as expressões que representam condicional `AND` operações.</xref:System.Linq.Expressions.ExpressionVisitor> Ele muda essas operações uma condicional `AND` para uma condicional `OR`. Para fazer isso, as substituições de classe de <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>método do tipo base, pois condicional `AND` expressões são representadas como expressões binárias.</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> No `VisitBinary` método, se a expressão que é passada para ele representa uma condicional `AND` operação, o código cria uma nova expressão que contém a condicional `OR` operador condicional em vez de `AND` operador. Se a expressão que é passada para `VisitBinary` não representa uma condicional `AND` adia a operação, o método para a implementação da classe base. Os métodos da classe base nós de construção que são semelhantes as árvores de expressão são passadas, mas os nós têm suas árvores sub substituídos com as árvores de expressão são produzidos recursivamente pelo visitante.  
  
4.  Adicionar uma `Imports` instrução ao arquivo para o `System.Linq.Expressions` namespace.  
  
5.  Adicione código para o `Main` método no arquivo Module1. vb para criar uma árvore de expressão e passá-lo para o método que modificá-la.  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     O código cria uma expressão que contém uma condicional `AND` operação. Ele cria uma instância do `AndAlsoModifier` classe e passa a expressão para o `Modify` método dessa classe. O original e as árvores de expressão modificados são enviadas para mostrar a alteração.  
  
6.  Compilar e executar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Como: executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)

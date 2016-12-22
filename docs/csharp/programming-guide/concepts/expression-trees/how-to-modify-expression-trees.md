---
title: "Como: modificar &#225;rvores de express&#227;o (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: modificar &#225;rvores de express&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como modificar uma árvore de expressão. Árvores de expressão são imutáveis, o que significa que eles não podem ser modificados. Para alterar uma árvore de expressão, você deve criar uma cópia de uma árvore de expressão existente e quando você cria a cópia, faça as alterações necessárias. Você pode usar o <xref:System.Linq.Expressions.ExpressionVisitor> classe para percorrer uma árvore de expressão existente e copiar cada nó que ele entra.  
  
### Para modificar uma árvore de expressão  
  
1.  Criar um novo **aplicativo de Console** projeto.  
  
2.  Adicione um `using` diretiva para o arquivo para o `System.Linq.Expressions` namespace.  
  
3.  Adicionar o `AndAlsoModifier` classe ao seu projeto.  
  
    ```c#  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     Essa classe herda o <xref:System.Linq.Expressions.ExpressionVisitor> da classe e é especializada para modificar as expressões que representam condicional `AND` operações. Ele muda essas operações uma condicional `AND` para uma condicional `OR`. Para fazer isso, as substituições de classe de <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> método do tipo base, pois condicional `AND` expressões são representadas como expressões binárias. No `VisitBinary` método, se a expressão que é passada para ele representa uma condicional `AND` operação, o código cria uma nova expressão que contém a condicional `OR` operador condicional em vez de `AND` operador. Se a expressão que é passada para `VisitBinary` não representa uma condicional `AND` adia a operação, o método para a implementação da classe base. Os métodos da classe base nós de construção que são semelhantes as árvores de expressão são passadas, mas os nós têm suas árvores sub substituídos com as árvores de expressão são produzidos recursivamente pelo visitante.  
  
4.  Adicione um `using` diretiva para o arquivo para o `System.Linq.Expressions` namespace.  
  
5.  Adicione código para o `Main` método no arquivo Program.cs para criar uma árvore de expressão e passá\-lo para o método que modificá\-la.  
  
    ```c#  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     O código cria uma expressão que contém uma condicional `AND` operação. Ele cria uma instância do `AndAlsoModifier` classe e passa a expressão para o `Modify` método dessa classe. O original e as árvores de expressão modificados são enviadas para mostrar a alteração.  
  
6.  Compilar e executar o aplicativo.  
  
## Consulte também  
 [Como: executar árvores de expressão \(c\#\)](../Topic/How%20to:%20Execute%20Expression%20Trees%20\(C%23\).md)   
 [Árvores de expressão \(c\#\)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
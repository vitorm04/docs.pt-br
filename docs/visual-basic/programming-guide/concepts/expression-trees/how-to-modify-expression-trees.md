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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2f0d383cbac639212519177fb1825875682f6233
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="1ce21-102">Como: modificar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce21-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="1ce21-103">Este tópico mostra como modificar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="1ce21-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="1ce21-104">Árvores de expressão são imutáveis, o que significa que eles não podem ser modificados.</span><span class="sxs-lookup"><span data-stu-id="1ce21-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="1ce21-105">Para alterar uma árvore de expressão, você deve criar uma cópia de uma árvore de expressão existente e quando você cria a cópia, faça as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="1ce21-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="1ce21-106">Você pode usar o <xref:System.Linq.Expressions.ExpressionVisitor>classe para percorrer uma árvore de expressão existente e copiar cada nó que ele entra.</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="1ce21-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="1ce21-107">Para modificar uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="1ce21-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="1ce21-108">Criar um novo **aplicativo de Console** projeto.</span><span class="sxs-lookup"><span data-stu-id="1ce21-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="1ce21-109">Adicionar uma `Imports` instrução ao arquivo para o `System.Linq.Expressions` namespace.</span><span class="sxs-lookup"><span data-stu-id="1ce21-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="1ce21-110">Adicionar o `AndAlsoModifier` classe ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1ce21-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="1ce21-111">Essa classe herda o <xref:System.Linq.Expressions.ExpressionVisitor>da classe e é especializada para modificar as expressões que representam condicional `AND` operações.</xref:System.Linq.Expressions.ExpressionVisitor></span><span class="sxs-lookup"><span data-stu-id="1ce21-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="1ce21-112">Ele muda essas operações uma condicional `AND` para uma condicional `OR`.</span><span class="sxs-lookup"><span data-stu-id="1ce21-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="1ce21-113">Para fazer isso, as substituições de classe de <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A>método do tipo base, pois condicional `AND` expressões são representadas como expressões binárias.</xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A></span><span class="sxs-lookup"><span data-stu-id="1ce21-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="1ce21-114">No `VisitBinary` método, se a expressão que é passada para ele representa uma condicional `AND` operação, o código cria uma nova expressão que contém a condicional `OR` operador condicional em vez de `AND` operador.</span><span class="sxs-lookup"><span data-stu-id="1ce21-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="1ce21-115">Se a expressão que é passada para `VisitBinary` não representa uma condicional `AND` adia a operação, o método para a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="1ce21-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="1ce21-116">Os métodos da classe base nós de construção que são semelhantes as árvores de expressão são passadas, mas os nós têm suas árvores sub substituídos com as árvores de expressão são produzidos recursivamente pelo visitante.</span><span class="sxs-lookup"><span data-stu-id="1ce21-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="1ce21-117">Adicionar uma `Imports` instrução ao arquivo para o `System.Linq.Expressions` namespace.</span><span class="sxs-lookup"><span data-stu-id="1ce21-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="1ce21-118">Adicione código para o `Main` método no arquivo Module1. vb para criar uma árvore de expressão e passá-lo para o método que modificá-la.</span><span class="sxs-lookup"><span data-stu-id="1ce21-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="1ce21-119">O código cria uma expressão que contém uma condicional `AND` operação.</span><span class="sxs-lookup"><span data-stu-id="1ce21-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="1ce21-120">Ele cria uma instância do `AndAlsoModifier` classe e passa a expressão para o `Modify` método dessa classe.</span><span class="sxs-lookup"><span data-stu-id="1ce21-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="1ce21-121">O original e as árvores de expressão modificados são enviadas para mostrar a alteração.</span><span class="sxs-lookup"><span data-stu-id="1ce21-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="1ce21-122">Compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ce21-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce21-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ce21-123">See Also</span></span>  
 <span data-ttu-id="1ce21-124">[Como: executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="1ce21-124">[How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
<span data-ttu-id="1ce21-125"> [Árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span><span class="sxs-lookup"><span data-stu-id="1ce21-125"> [Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)</span></span>

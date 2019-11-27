---
title: Como modificar árvores de expressão
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353753"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="ff7e0-102">Como: modificar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff7e0-102">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="ff7e0-103">Este tópico mostra como modificar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="ff7e0-104">As árvores de expressão são imutáveis, o que significa que elas não podem ser diretamente modificadas.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="ff7e0-105">Para alterar uma árvore de expressão, você deve criar uma cópia de uma árvore de expressão existente e, ao criar a cópia, faça as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="ff7e0-106">Você pode usar a classe <xref:System.Linq.Expressions.ExpressionVisitor> para percorrer uma árvore de expressão existente e copiar cada nó que ela visitar.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="ff7e0-107">Para modificar uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="ff7e0-107">To modify an expression tree</span></span>

1. <span data-ttu-id="ff7e0-108">Crie um novo projeto de **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-108">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="ff7e0-109">Adicione uma instrução `Imports` ao arquivo para o namespace `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="ff7e0-110">Adicione a classe `AndAlsoModifier` ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-110">Add the `AndAlsoModifier` class to your project.</span></span>

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

    <span data-ttu-id="ff7e0-111">Essa classe herda a classe <xref:System.Linq.Expressions.ExpressionVisitor> e é especializada para modificar expressões que representam operações `AND` condicionais.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="ff7e0-112">Ela muda essas operações de uma `AND` condicional para uma `OR` condicional.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="ff7e0-113">Para fazer isso, a classe substitui o método <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> do tipo base, pois as expressões `AND` condicionais são representadas como expressões binárias.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="ff7e0-114">No método `VisitBinary`, se a expressão que é passada a ele representa uma operação `AND` condicional, o código cria uma nova expressão que contém o operador `OR` condicional em vez do operador `AND` condicional.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="ff7e0-115">Se a expressão que é passada para o `VisitBinary` não representa uma operação `AND` condicional, o método adia para a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="ff7e0-116">Os métodos da classe base constroem nós que são semelhantes às árvores de expressão que são passadas, mas os nós têm suas subárvores substituídas pelas árvores de expressão que são produzidas recursivamente pelo visitante.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="ff7e0-117">Adicione uma instrução `Imports` ao arquivo para o namespace `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="ff7e0-118">Adicione código ao método `Main` no arquivo Module1. vb para criar uma árvore de expressão e passá-la para o método que irá modificá-la.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

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

    <span data-ttu-id="ff7e0-119">O código cria uma expressão que contém uma operação `AND` condicional.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="ff7e0-120">Em seguida, ele cria uma instância da classe `AndAlsoModifier` e passa a expressão ao método `Modify` dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="ff7e0-121">A árvore de expressão original e a modificada são geradas para mostrar a alteração.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-121">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="ff7e0-122">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ff7e0-122">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff7e0-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff7e0-123">See also</span></span>

- [<span data-ttu-id="ff7e0-124">Como: executar árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff7e0-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="ff7e0-125">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff7e0-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)

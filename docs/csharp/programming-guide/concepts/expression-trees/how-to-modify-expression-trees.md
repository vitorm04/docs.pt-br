---
title: Como modificar árvores de expressão (C#)
description: Saiba como modificar uma árvore de expressão criando uma cópia de uma árvore de expressão existente e fazendo as alterações necessárias.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 01176f489794a0f4ca29d229d29507fdba0fd5a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167685"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="a3c5e-103">Como modificar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c5e-103">How to modify expression trees (C#)</span></span>

<span data-ttu-id="a3c5e-104">Este tópico mostra como modificar uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="a3c5e-105">As árvores de expressão são imutáveis, o que significa que elas não podem ser diretamente modificadas.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="a3c5e-106">Para alterar uma árvore de expressão, você deve criar uma cópia de uma árvore de expressão existente e, ao criar a cópia, faça as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="a3c5e-107">Você pode usar a classe <xref:System.Linq.Expressions.ExpressionVisitor> para percorrer uma árvore de expressão existente e copiar cada nó que ela visitar.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="a3c5e-108">Para modificar uma árvore de expressão</span><span class="sxs-lookup"><span data-stu-id="a3c5e-108">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="a3c5e-109">Crie um novo projeto de **aplicativo de console** .</span><span class="sxs-lookup"><span data-stu-id="a3c5e-109">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="a3c5e-110">Adicione uma diretiva `using` ao arquivo para o namespace `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-110">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="a3c5e-111">Adicione a classe `AndAlsoModifier` ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-111">Add the `AndAlsoModifier` class to your project.</span></span>  
  
    ```csharp  
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
  
     <span data-ttu-id="a3c5e-112">Essa classe herda a classe <xref:System.Linq.Expressions.ExpressionVisitor> e é especializada para modificar expressões que representam operações `AND` condicionais.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="a3c5e-113">Ela muda essas operações de uma `AND` condicional para uma `OR` condicional.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="a3c5e-114">Para fazer isso, a classe substitui o método <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> do tipo base, pois as expressões `AND` condicionais são representadas como expressões binárias.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="a3c5e-115">No método `VisitBinary`, se a expressão que é passada a ele representa uma operação `AND` condicional, o código cria uma nova expressão que contém o operador `OR` condicional em vez do operador `AND` condicional.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="a3c5e-116">Se a expressão que é passada para o `VisitBinary` não representa uma operação `AND` condicional, o método adia para a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="a3c5e-117">Os métodos da classe base constroem nós que são semelhantes às árvores de expressão que são passadas, mas os nós têm suas subárvores substituídas pelas árvores de expressão que são produzidas recursivamente pelo visitante.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="a3c5e-118">Adicione uma diretiva `using` ao arquivo para o namespace `System.Linq.Expressions`.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-118">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="a3c5e-119">Adicione código para o método `Main` no arquivo Program.cs para criar uma árvore de expressão e passá-la ao método que a modificará.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-119">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
    ```csharp  
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
  
     <span data-ttu-id="a3c5e-120">O código cria uma expressão que contém uma operação `AND` condicional.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="a3c5e-121">Em seguida, ele cria uma instância da classe `AndAlsoModifier` e passa a expressão ao método `Modify` dessa classe.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="a3c5e-122">A árvore de expressão original e a modificada são geradas para mostrar a alteração.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-122">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="a3c5e-123">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a3c5e-123">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c5e-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a3c5e-124">See also</span></span>

- [<span data-ttu-id="a3c5e-125">Como executar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c5e-125">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="a3c5e-126">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="a3c5e-126">Expression Trees (C#)</span></span>](./index.md)

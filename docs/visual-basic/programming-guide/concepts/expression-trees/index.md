---
title: "Árvores de expressão (Visual Basic)"
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
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e67f6696ab6e41e9185c7d1356b98113e1473a87
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="17013-102">Árvores de expressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17013-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="17013-103">Árvores de expressão representam código em uma estrutura de dados de árvore, onde cada nó é, por exemplo, uma expressão, uma chamada de método ou uma operação binária como `x < y`.</span><span class="sxs-lookup"><span data-stu-id="17013-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="17013-104">Você pode compilar e executar código representado por árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="17013-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="17013-105">Isso permite a modificação dinâmica de código executável, a execução de consultas LINQ em vários bancos de dados e a criação de consultas dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="17013-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="17013-106">Para obter mais informações sobre árvores de expressão no LINQ, consulte [Como usar árvores de expressão para compilar consultas dinâmicas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="17013-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="17013-107">Árvores de expressão também são usadas no tempo de execução de linguagem dinâmica (DLR) para fornecer interoperabilidade entre linguagens dinâmicas e o .NET Framework e permitir que gravadores compiladores emitam árvores de expressão em vez de Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="17013-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="17013-108">Para obter mais informações sobre o DLR, consulte [Visão geral do Dynamic Language Runtime](https://msdn.microsoft.com/library/dd233052).</span><span class="sxs-lookup"><span data-stu-id="17013-108">For more information about the DLR, see [Dynamic Language Runtime Overview](https://msdn.microsoft.com/library/dd233052).</span></span>  
  
 <span data-ttu-id="17013-109">Você pode fazer o compilador C# ou do Visual Basic criar uma árvore de expressões para você com base em uma expressão lambda anônima ou criar árvores de expressão manualmente usando o namespace <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="17013-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="17013-110">Criando árvores de expressão de expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="17013-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="17013-111">Quando uma expressão lambda é atribuída a uma variável do tipo <xref:System.Linq.Expressions.Expression%601>, o compilador emite código para criar uma árvore de expressão que representa a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="17013-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="17013-112">Os compiladores do Visual Basic podem gerar árvores de expressão de expressões lambdas (ou lambdas de linha única).</span><span class="sxs-lookup"><span data-stu-id="17013-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="17013-113">Ele não é possível analisar instruções lambdas (ou lambdas de várias linhas).</span><span class="sxs-lookup"><span data-stu-id="17013-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="17013-114">Para obter mais informações sobre expressões lambda no Visual Basic, consulte [Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17013-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="17013-115">Os exemplos de código a seguir demonstram como fazer os compiladores do Visual Basic criarem uma árvore de expressão que representa a expressão lambda `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="17013-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="17013-116">Criando árvores de expressão usando a API</span><span class="sxs-lookup"><span data-stu-id="17013-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="17013-117">Para criar árvores de expressão usando a API, use a classe <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="17013-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="17013-118">Essa classe contém métodos de fábrica estáticos para criar nós de árvore de expressão de tipos específicos, por exemplo, <xref:System.Linq.Expressions.ParameterExpression>, que representa uma variável ou parâmetro, ou <xref:System.Linq.Expressions.MethodCallExpression>, que representa uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="17013-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="17013-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> e os outros tipos específicos de expressão também são definidos no namespace <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="17013-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="17013-120">Esses tipos derivam do tipo abstrato <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="17013-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="17013-121">O exemplo de código a seguir demonstra como criar uma árvore de expressão que representa a expressão lambda `Function(num) num < 5` usando a API.</span><span class="sxs-lookup"><span data-stu-id="17013-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="17013-122">No .NET Framework 4 ou posterior, a API de árvores de expressão também dá suporte a atribuições e expressões de fluxo de controle, como loops, blocos condicionais e blocos `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="17013-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="17013-123">Usando a API, você pode criar árvores de expressão mais complexas do que aquelas que podem ser criadas por meio de expressões lambda pelos compiladores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="17013-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="17013-124">O exemplo a seguir demonstra como criar uma árvore de expressão que calcula o fatorial de um número.</span><span class="sxs-lookup"><span data-stu-id="17013-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.   
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="17013-125">Para saber mais, confira [Gerar métodos dinâmicos com árvores de expressão no Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), que também se aplica a versões mais recentes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17013-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](http://go.microsoft.com/fwlink/p/?LinkId=169513), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="17013-126">Analisando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="17013-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="17013-127">O exemplo de código a seguir demonstra como a árvore de expressão que representa a expressão lambda `Function(num) num < 5` pode ser decomposta em suas partes.</span><span class="sxs-lookup"><span data-stu-id="17013-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="17013-128">Imutabilidade das árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="17013-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="17013-129">Árvores de expressão devem ser imutáveis.</span><span class="sxs-lookup"><span data-stu-id="17013-129">Expression trees should be immutable.</span></span> <span data-ttu-id="17013-130">Isso significa que se você deseja modificar uma árvore de expressão, deverá criar uma nova árvore de expressão, copiando a existente e substituindo seus nós.</span><span class="sxs-lookup"><span data-stu-id="17013-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="17013-131">Você pode usar um visitantes de árvore expressão para percorrer a árvore de expressão existente.</span><span class="sxs-lookup"><span data-stu-id="17013-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="17013-132">Para obter mais informações, consulte [Como modificar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="17013-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="17013-133">Compilando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="17013-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="17013-134">O tipo <xref:System.Linq.Expressions.Expression%601> fornece o método <xref:System.Linq.Expressions.Expression%601.Compile%2A> que compila o código representado por uma árvore de expressão para um delegado executável.</span><span class="sxs-lookup"><span data-stu-id="17013-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="17013-135">O exemplo de código a seguir demonstra como compilar uma árvore de expressão e executar o código resultante.</span><span class="sxs-lookup"><span data-stu-id="17013-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="17013-136">Para obter mais informações, consulte [Como executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="17013-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17013-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17013-137">See Also</span></span>  
 <span data-ttu-id="17013-138"><xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="17013-138"><xref:System.Linq.Expressions></span></span>   
 <span data-ttu-id="17013-139">[Como executar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="17013-139">[How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md) </span></span>  
 <span data-ttu-id="17013-140">[Como modificar árvores de expressão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md) </span><span class="sxs-lookup"><span data-stu-id="17013-140">[How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md) </span></span>  
 <span data-ttu-id="17013-141">[Expressões Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="17013-141">[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
 <span data-ttu-id="17013-142">[Visão geral do Dynamic Language Runtime](https://msdn.microsoft.com/library/dd233052) </span><span class="sxs-lookup"><span data-stu-id="17013-142">[Dynamic Language Runtime Overview](https://msdn.microsoft.com/library/dd233052) </span></span>  
 [<span data-ttu-id="17013-143">Conceitos de programação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17013-143">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)


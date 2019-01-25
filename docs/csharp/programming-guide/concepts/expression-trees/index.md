---
title: Árvores de expressão (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7744954d3a3f552d5765e6e7085950f08a5adf55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720922"
---
# <a name="expression-trees-c"></a><span data-ttu-id="22eec-102">Árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="22eec-102">Expression Trees (C#)</span></span>
<span data-ttu-id="22eec-103">Árvores de expressão representam código em uma estrutura de dados de árvore, onde cada nó é, por exemplo, uma expressão, uma chamada de método ou uma operação binária como `x < y`.</span><span class="sxs-lookup"><span data-stu-id="22eec-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="22eec-104">Você pode compilar e executar código representado por árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="22eec-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="22eec-105">Isso permite a modificação dinâmica de código executável, a execução de consultas LINQ em vários bancos de dados e a criação de consultas dinâmicas.</span><span class="sxs-lookup"><span data-stu-id="22eec-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="22eec-106">Confira mais informações sobre árvores de expressão no LINQ em [Como: usar árvores de expressão para compilar consultas dinâmicas (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="22eec-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="22eec-107">Árvores de expressão também são usadas no tempo de execução de linguagem dinâmica (DLR) para fornecer interoperabilidade entre linguagens dinâmicas e o .NET Framework e permitir que gravadores compiladores emitam árvores de expressão em vez de Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="22eec-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="22eec-108">Para obter mais informações sobre o DLR, consulte [Visão geral do Dynamic Language Runtime](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="22eec-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="22eec-109">Você pode fazer o compilador C# ou do Visual Basic criar uma árvore de expressões para você com base em uma expressão lambda anônima ou criar árvores de expressão manualmente usando o namespace <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="22eec-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="22eec-110">Criando árvores de expressão de expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="22eec-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="22eec-111">Quando uma expressão lambda é atribuída a uma variável do tipo <xref:System.Linq.Expressions.Expression%601>, o compilador emite código para criar uma árvore de expressão que representa a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="22eec-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="22eec-112">Os compiladores do C# podem gerar árvores de expressão apenas por meio de expressões lambda (ou lambdas de linha única).</span><span class="sxs-lookup"><span data-stu-id="22eec-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="22eec-113">Ele não é possível analisar instruções lambdas (ou lambdas de várias linhas).</span><span class="sxs-lookup"><span data-stu-id="22eec-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="22eec-114">Para obter mais informações sobre expressões lambda no C#, consulte [Expressões lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="22eec-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="22eec-115">Os exemplos de código a seguir demonstram como fazer os compiladores do C# criarem uma árvore de expressão que representa a expressão lambda `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="22eec-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="22eec-116">Criando árvores de expressão usando a API</span><span class="sxs-lookup"><span data-stu-id="22eec-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="22eec-117">Para criar árvores de expressão usando a API, use a classe <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="22eec-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="22eec-118">Essa classe contém métodos de fábrica estáticos para criar nós de árvore de expressão de tipos específicos, por exemplo, <xref:System.Linq.Expressions.ParameterExpression>, que representa uma variável ou parâmetro, ou <xref:System.Linq.Expressions.MethodCallExpression>, que representa uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="22eec-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="22eec-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression> e os outros tipos específicos de expressão também são definidos no namespace <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="22eec-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="22eec-120">Esses tipos derivam do tipo abstrato <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="22eec-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="22eec-121">O exemplo de código a seguir demonstra como criar uma árvore de expressão que representa a expressão lambda `num => num < 5` usando a API.</span><span class="sxs-lookup"><span data-stu-id="22eec-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for   
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="22eec-122">No .NET Framework 4 ou posterior, a API de árvores de expressão também dá suporte a atribuições e expressões de fluxo de controle, como loops, blocos condicionais e blocos `try-catch`.</span><span class="sxs-lookup"><span data-stu-id="22eec-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="22eec-123">Usando a API, você pode criar árvores de expressão mais complexas do que aquelas que podem ser criadas por meio de expressões lambda pelos compiladores do C#.</span><span class="sxs-lookup"><span data-stu-id="22eec-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="22eec-124">O exemplo a seguir demonstra como criar uma árvore de expressão que calcula o fatorial de um número.</span><span class="sxs-lookup"><span data-stu-id="22eec-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.   
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="22eec-125">Para saber mais, confira [Gerar métodos dinâmicos com árvores de expressão no Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), que também se aplica a versões mais recentes do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22eec-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="22eec-126">Analisando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="22eec-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="22eec-127">O exemplo de código a seguir demonstra como a árvore de expressão que representa a expressão lambda `num => num < 5` pode ser decomposta em suas partes.</span><span class="sxs-lookup"><span data-stu-id="22eec-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="22eec-128">Imutabilidade das árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="22eec-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="22eec-129">Árvores de expressão devem ser imutáveis.</span><span class="sxs-lookup"><span data-stu-id="22eec-129">Expression trees should be immutable.</span></span> <span data-ttu-id="22eec-130">Isso significa que se você deseja modificar uma árvore de expressão, deverá criar uma nova árvore de expressão, copiando a existente e substituindo seus nós.</span><span class="sxs-lookup"><span data-stu-id="22eec-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="22eec-131">Você pode usar um visitantes de árvore expressão para percorrer a árvore de expressão existente.</span><span class="sxs-lookup"><span data-stu-id="22eec-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="22eec-132">Para obter mais informações, confira [Como: modificar árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="22eec-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="22eec-133">Compilando árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="22eec-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="22eec-134">O tipo <xref:System.Linq.Expressions.Expression%601> fornece o método <xref:System.Linq.Expressions.Expression%601.Compile%2A> que compila o código representado por uma árvore de expressão para um delegado executável.</span><span class="sxs-lookup"><span data-stu-id="22eec-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="22eec-135">O exemplo de código a seguir demonstra como compilar uma árvore de expressão e executar o código resultante.</span><span class="sxs-lookup"><span data-stu-id="22eec-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="22eec-136">Para obter mais informações, confira [Como: executar árvores de expressão (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="22eec-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22eec-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22eec-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="22eec-138">Como: executar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="22eec-138">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="22eec-139">Como: modificar árvores de expressão (C#)</span><span class="sxs-lookup"><span data-stu-id="22eec-139">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="22eec-140">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="22eec-140">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="22eec-141">Visão geral do Dynamic Language Runtime</span><span class="sxs-lookup"><span data-stu-id="22eec-141">Dynamic Language Runtime Overview</span></span>](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="22eec-142">Conceitos de programação (C#)</span><span class="sxs-lookup"><span data-stu-id="22eec-142">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)

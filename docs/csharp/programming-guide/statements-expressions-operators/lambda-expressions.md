---
title: Expressões lambda – Guia de Programação em C#
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58125727"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="fb6af-102">Expressões lambda (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fb6af-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="fb6af-103">Uma *expressão lambda* é um bloco de código (uma expressão ou um bloco de instruções) que é tratado como um objeto.</span><span class="sxs-lookup"><span data-stu-id="fb6af-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="fb6af-104">Ela pode ser passada como um argumento para métodos e também pode ser retornada por chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="fb6af-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="fb6af-105">As expressões lambda são usadas amplamente para:</span><span class="sxs-lookup"><span data-stu-id="fb6af-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="fb6af-106">Passar o código que deve ser executado para métodos assíncronos, como <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="fb6af-107">Escrever [expressões de consulta LINQ](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="fb6af-108">Criar [árvores de expressão](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="fb6af-109">As expressões lambda são códigos que podem ser representados como um delegado ou como uma árvore de expressão que é compilada para um delegado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="fb6af-110">O tipo delegado específico de uma expressão lambda depende de seus parâmetros e do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="fb6af-111">As expressões lambda que não retornam um valor correspondem a um delegado `Action` específico, dependendo de seu número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fb6af-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="fb6af-112">As expressões lambda que retornam um valor correspondem a um delegado `Func` específico, dependendo de seu número de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fb6af-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="fb6af-113">Por exemplo, uma expressão lambda que tem dois parâmetros, mas não retorna nenhum valor, corresponde a um delegado <xref:System.Action%602>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="fb6af-114">Uma expressão lambda que tem um parâmetro e retorna um valor corresponde ao delegado <xref:System.Func%602>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="fb6af-115">Usa uma expressão lambda usa o `=>`, o [operador de declaração lambda](../../language-reference/operators/lambda-operator.md), para separar a lista de parâmetros de lambda de seu código executável.</span><span class="sxs-lookup"><span data-stu-id="fb6af-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="fb6af-116">Para criar uma expressão lambda, você especifica os parâmetros de entrada (se houver) no lado esquerdo do operador lambda e coloca a expressão ou o bloco de instruções do outro lado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="fb6af-117">Por exemplo, a expressão lambda de linha única `x => x * x` especifica um parâmetro chamado `x` e retorna o valor de `x` ao quadrado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="fb6af-118">Você pode atribuir essa expressão a um tipo delegado como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="fb6af-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="fb6af-119">Você também pode atribuir uma expressão lambda a um tipo de árvore de expressão:</span><span class="sxs-lookup"><span data-stu-id="fb6af-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="fb6af-120">Ou pode passá-la diretamente como um argumento de método:</span><span class="sxs-lookup"><span data-stu-id="fb6af-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="fb6af-121">Quando você usa a sintaxe baseada em método para chamar o método <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na classe <xref:System.Linq.Enumerable?displayProperty=nameWithType> (assim como faz em LINQ to Objects e LINQ to XML), o parâmetro é um tipo delegado <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb6af-122">Uma expressão lambda é a maneira mais conveniente de criar esse delegado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="fb6af-123">Quando você chama o método <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> na classe <xref:System.Linq.Queryable?displayProperty=nameWithType> (como faz no LINQ to SQL), o tipo de parâmetro é um tipo de árvore de expressão [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="fb6af-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="fb6af-124">Novamente, uma expressão lambda é apenas uma maneira muito concisa de construir essa árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="fb6af-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="fb6af-125">Os lambdas permitem que chamadas `Select` pareçam semelhantes embora, na verdade, o tipo de objeto criado do lambda seja diferente.</span><span class="sxs-lookup"><span data-stu-id="fb6af-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="fb6af-126">Todas as restrições que se aplicam a [métodos anônimos](anonymous-methods.md) também se aplicam às expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6af-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="fb6af-127">Lambdas de expressão</span><span class="sxs-lookup"><span data-stu-id="fb6af-127">Expression lambdas</span></span>

<span data-ttu-id="fb6af-128">Uma expressão lambda com uma expressão no lado direito do operador `=>` é chamada de *lambda de expressão*.</span><span class="sxs-lookup"><span data-stu-id="fb6af-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="fb6af-129">Os lambdas de expressão são usados amplamente na construção de [árvores de expressão](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="fb6af-130">Uma expressão lambda retorna o resultado da expressão e tem o seguinte formato básico:</span><span class="sxs-lookup"><span data-stu-id="fb6af-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="fb6af-131">Os parênteses serão opcionais somente se o lambda tiver um parâmetro de entrada; caso contrário, eles serão obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="fb6af-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="fb6af-132">Especifique parâmetros de entrada zero com parênteses vazios:</span><span class="sxs-lookup"><span data-stu-id="fb6af-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="fb6af-133">Dois ou mais parâmetros de entrada são separados por vírgulas e envolvidos por parênteses:</span><span class="sxs-lookup"><span data-stu-id="fb6af-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="fb6af-134">Às vezes, é difícil ou impossível para o compilador inferir os tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="fb6af-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="fb6af-135">Você pode especificar os tipos de maneira explícita conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="fb6af-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="fb6af-136">Os tipos de parâmetro de entrada devem ser todos explícitos ou implícitos; caso contrário, ocorrerá o erro [CS0748](../../misc/cs0748.md) de compilador.</span><span class="sxs-lookup"><span data-stu-id="fb6af-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="fb6af-137">O corpo de um lambda de expressão pode consistir em uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="fb6af-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="fb6af-138">No entanto, se você estiver criando árvores de expressão que serão avaliadas fora contexto do .NET Common Language Runtime, como no SQL Server, você não deverá usar chamadas de método em lambdas de expressão.</span><span class="sxs-lookup"><span data-stu-id="fb6af-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="fb6af-139">Os métodos não terão significado fora do contexto do .NET Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="fb6af-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="fb6af-140">Lambdas de instrução</span><span class="sxs-lookup"><span data-stu-id="fb6af-140">Statement lambdas</span></span>

<span data-ttu-id="fb6af-141">Um lambda de instrução lembra um lambda de expressão, exceto que as instruções estão incluídas entre chaves:</span><span class="sxs-lookup"><span data-stu-id="fb6af-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="fb6af-142">O corpo de uma instrução lambda pode consistir de qualquer número de instruções; no entanto, na prática, normalmente não há mais de duas ou três.</span><span class="sxs-lookup"><span data-stu-id="fb6af-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="fb6af-143">Lambdas de instrução, como métodos anônimos, não podem ser usados para criar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="fb6af-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="fb6af-144">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="fb6af-144">Async lambdas</span></span>

<span data-ttu-id="fb6af-145">Você pode facilmente criar expressões e instruções lambda que incorporem processamento assíncrono, ao usar as palavras-chaves [async](../../language-reference/keywords/async.md) e [await](../../language-reference/keywords/await.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="fb6af-146">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="fb6af-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="fb6af-147">Você pode adicionar o mesmo manipulador de eventos ao usar um lambda assíncrono.</span><span class="sxs-lookup"><span data-stu-id="fb6af-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="fb6af-148">Para adicionar esse manipulador, adicione um modificador `async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fb6af-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="fb6af-149">Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [Programação assíncrona com async e await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="fb6af-150">Expressões lambda e tuplas</span><span class="sxs-lookup"><span data-stu-id="fb6af-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="fb6af-151">A partir do C# 7.0, a linguagem C# fornece suporte interno para [tuplas](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="fb6af-152">Você pode fornecer uma tupla como um argumento para uma expressão lambda e a expressão lambda também pode retornar uma tupla.</span><span class="sxs-lookup"><span data-stu-id="fb6af-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="fb6af-153">Em alguns casos, o compilador do C# usa a inferência de tipos para determinar os tipos dos componentes da tupla.</span><span class="sxs-lookup"><span data-stu-id="fb6af-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="fb6af-154">Você pode definir uma tupla, colocando entre parênteses uma lista delimitada por vírgulas de seus componentes.</span><span class="sxs-lookup"><span data-stu-id="fb6af-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="fb6af-155">O exemplo a seguir usa a tupla com três componentes para passar uma sequência de números para uma expressão lambda, que dobra cada valor e retorna uma tupla com três componentes que contém o resultado das multiplicações.</span><span class="sxs-lookup"><span data-stu-id="fb6af-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="fb6af-156">Normalmente, os campos de uma tupla são chamados de `Item1`, `Item2`, etc. No entanto, você pode definir uma tupla com componentes nomeados, como é feito no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb6af-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="fb6af-157">Para saber mais sobre tuplas C#, confira o artigo sobre [tipos de tuplas C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="fb6af-158">Lambdas com os operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="fb6af-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="fb6af-159">O LINQ to Objects, entre outras implementações, tem um parâmetro de entrada cujo tipo faz parte da família de delegados genéricos <xref:System.Func%601>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="fb6af-160">Esses delegados usam parâmetros de tipo para definir o número e o tipo de parâmetros de entrada e o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="fb6af-161">delegados `Func` são muito úteis para encapsular expressões definidas pelo usuário aplicadas a cada elemento em um conjunto de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="fb6af-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="fb6af-162">Por exemplo, considere o seguinte tipo delegado <xref:System.Func%602>:</span><span class="sxs-lookup"><span data-stu-id="fb6af-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="fb6af-163">O delegado pode ser instanciado como um `Func<int, bool>`, em que `int` é um parâmetro de entrada e `bool` é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="fb6af-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="fb6af-164">O valor de retorno é sempre especificado no último parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="fb6af-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="fb6af-165">Por exemplo, `Func<int, string, bool>` define um delegado com dois parâmetros de entrada, `int` e `string`, e um tipo de retorno de `bool`.</span><span class="sxs-lookup"><span data-stu-id="fb6af-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="fb6af-166">O delegado `Func` a seguir, quando é invocado, retornará um valor booliano que indica se o parâmetro de entrada é ou não igual a cinco:</span><span class="sxs-lookup"><span data-stu-id="fb6af-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="fb6af-167">Você também pode fornecer uma expressão lambda quando o tipo de argumento é um <xref:System.Linq.Expressions.Expression%601>. Por exemplo, nos operadores de consulta padrão que são definidos no tipo <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="fb6af-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="fb6af-168">Quando você especifica um argumento <xref:System.Linq.Expressions.Expression%601>, o lambda é compilado em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="fb6af-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="fb6af-169">O exemplo a seguir usa o operador padrão de consulta <xref:System.Linq.Enumerable.Count%2A>:</span><span class="sxs-lookup"><span data-stu-id="fb6af-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="fb6af-170">O compilador pode inferir o tipo de parâmetro de entrada ou você também pode especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fb6af-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="fb6af-171">Essa expressão lambda em particular conta esses inteiros (`n`) que, quando dividida por dois, tem um resto 1.</span><span class="sxs-lookup"><span data-stu-id="fb6af-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="fb6af-172">O exemplo a seguir gera uma sequência que contém todos os elementos da matriz `numbers` que precedem o 9, porque esse é o primeiro número na sequência que não satisfaz a condição:</span><span class="sxs-lookup"><span data-stu-id="fb6af-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="fb6af-173">O exemplo a seguir especifica vários parâmetros de entrada, colocando-os entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="fb6af-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="fb6af-174">O método retorna todos os elementos na matriz `numbers` até encontrar um número cujo valor seja inferior à sua posição ordinal na matriz:</span><span class="sxs-lookup"><span data-stu-id="fb6af-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="fb6af-175">Inferência de tipos em expressões lambda</span><span class="sxs-lookup"><span data-stu-id="fb6af-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="fb6af-176">Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo do lambda, nos tipos de parâmetro e em outros fatores, conforme descrito na especificação da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="fb6af-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="fb6af-177">Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="fb6af-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="fb6af-178">Se você estiver consultando um `IEnumerable<Customer>`, a variável de entrada será inferida para ser um objeto `Customer`, o que significa que você terá acesso aos seus métodos e propriedades:</span><span class="sxs-lookup"><span data-stu-id="fb6af-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="fb6af-179">As regras gerais para a inferência de tipos para lambdas são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="fb6af-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="fb6af-180">O lambda deve conter o mesmo número de parâmetros do tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="fb6af-181">Cada parâmetro de entrada no lambda deve ser implicitamente conversível em seu parâmetro delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="fb6af-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="fb6af-182">O valor de retorno do lambda (se houver) deve ser implicitamente conversível para o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="fb6af-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="fb6af-183">Observe que as expressões lambda em si não têm um tipo porque o sistema de tipo comum não possui nenhum conceito intrínseco de "expressão lambda."</span><span class="sxs-lookup"><span data-stu-id="fb6af-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="fb6af-184">No entanto, às vezes é conveniente falar informalmente do "tipo" de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6af-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="fb6af-185">Nesses casos, o tipo se refere ao tipo delegado ou tipo <xref:System.Linq.Expressions.Expression> ao qual a expressão lambda é convertida.</span><span class="sxs-lookup"><span data-stu-id="fb6af-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="fb6af-186">Escopo variável em expressões lambda</span><span class="sxs-lookup"><span data-stu-id="fb6af-186">Variable scope in lambda expressions</span></span>

<span data-ttu-id="fb6af-187">Os lambdas podem se referir a *variáveis externas* (confira os [Métodos Anônimos](anonymous-methods.md)) que estão no escopo do método que define a expressão lambda ou no escopo do tipo que contém a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6af-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="fb6af-188">As variáveis que são capturadas dessa forma são armazenadas para uso na expressão lambda mesmo que de alguma outra forma elas saíssem do escopo e fossem coletadas como lixo.</span><span class="sxs-lookup"><span data-stu-id="fb6af-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="fb6af-189">Uma variável externa deve ser definitivamente atribuída para que possa ser consumida em uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6af-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="fb6af-190">O exemplo a seguir demonstra estas regras:</span><span class="sxs-lookup"><span data-stu-id="fb6af-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="fb6af-191">As seguintes regras se aplicam ao escopo variável em expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="fb6af-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="fb6af-192">Uma variável capturada não será coletada do lixo até que o delegado que faz referência a ela se qualifique para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="fb6af-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="fb6af-193">As variáveis introduzidas em uma expressão lambda não são visíveis no método delimitador.</span><span class="sxs-lookup"><span data-stu-id="fb6af-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="fb6af-194">Uma expressão lambda não pode capturar um parâmetro [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md) diretamente de um método delimitador.</span><span class="sxs-lookup"><span data-stu-id="fb6af-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="fb6af-195">Uma instrução [return](../../language-reference/keywords/return.md) em uma expressão lambda não faz com que o método delimitador retorne.</span><span class="sxs-lookup"><span data-stu-id="fb6af-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="fb6af-196">Uma expressão lambda não pode conter uma instrução [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md) ou [continue](../../language-reference/keywords/continue.md) se o destino daquela instrução de salto estiver fora do bloco da expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb6af-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="fb6af-197">Também será um erro ter uma instrução de salto fora do bloco da expressão lambda se o destino estiver dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="fb6af-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fb6af-198">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fb6af-198">C# language specification</span></span>

<span data-ttu-id="fb6af-199">Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="fb6af-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="fb6af-200">Capítulo do livro em destaque</span><span class="sxs-lookup"><span data-stu-id="fb6af-200">Featured book chapter</span></span>

<span data-ttu-id="fb6af-201">[Delegados, eventos e expressões lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) no [Manual de instruções C# 3.0, terceira edição: mais de 250 soluções para programadores do C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="fb6af-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb6af-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb6af-202">See also</span></span>

- [<span data-ttu-id="fb6af-203">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fb6af-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fb6af-204">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="fb6af-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="fb6af-205">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="fb6af-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="fb6af-206">Árvores de Expressão</span><span class="sxs-lookup"><span data-stu-id="fb6af-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="fb6af-207">Funções locais comparadas com expressões lambda</span><span class="sxs-lookup"><span data-stu-id="fb6af-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="fb6af-208">Expressões lambda tipadas implicitamente</span><span class="sxs-lookup"><span data-stu-id="fb6af-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="fb6af-209">Exemplos de C# do Visual Studio 2008 (veja os arquivos de exemplo de consultas LINQ e programa XQuery)</span><span class="sxs-lookup"><span data-stu-id="fb6af-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="fb6af-210">Expressões lambda recursivas</span><span class="sxs-lookup"><span data-stu-id="fb6af-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)

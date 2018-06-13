---
title: Executar árvores de expressão
description: Saiba mais sobre como executar árvores de expressão, convertendo-as em instruções de IL (linguagem intermediária) executáveis.
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 54706cd5d8ebe60bb893bc82f05aecddae370602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218157"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="764da-103">Executar árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="764da-103">Executing Expression Trees</span></span>

[<span data-ttu-id="764da-104">Anterior – Tipos de estruturas que dão suporte às árvores de expressão</span><span class="sxs-lookup"><span data-stu-id="764da-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="764da-105">Uma *árvore de expressão* é uma estrutura de dados que representa algum código.</span><span class="sxs-lookup"><span data-stu-id="764da-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="764da-106">Ela não é código compilado nem executável.</span><span class="sxs-lookup"><span data-stu-id="764da-106">It is not compiled and executable code.</span></span> <span data-ttu-id="764da-107">Se você quiser executar o código do .NET que é representado por uma árvore de expressão, é necessário convertê-lo em instruções IL executáveis.</span><span class="sxs-lookup"><span data-stu-id="764da-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="764da-108">Expressões lambda para funções</span><span class="sxs-lookup"><span data-stu-id="764da-108">Lambda Expressions to Functions</span></span>
<span data-ttu-id="764da-109">Você pode converter qualquer LambdaExpression ou qualquer tipo derivado de LambdaExpression em IL executável.</span><span class="sxs-lookup"><span data-stu-id="764da-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="764da-110">Outros tipos de expressão não podem ser convertidos diretamente em código.</span><span class="sxs-lookup"><span data-stu-id="764da-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="764da-111">Essa restrição tem pouco efeito na prática.</span><span class="sxs-lookup"><span data-stu-id="764da-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="764da-112">As expressões lambda são os únicos tipos de expressões que você gostaria de executar convertendo em IL (linguagem intermediária) executável.</span><span class="sxs-lookup"><span data-stu-id="764da-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="764da-113">(Pense no que significaria executar diretamente uma `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="764da-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="764da-114">Significaria alguma coisa útil?) Qualquer árvore de expressão que é uma `LamdbaExpression` ou um tipo derivado de `LambdaExpression`, pode ser convertido em IL.</span><span class="sxs-lookup"><span data-stu-id="764da-114">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="764da-115">O tipo de expressão `Expression<TDelegate>` é o único exemplo concreto nas bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="764da-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="764da-116">Ele é usado para representar uma expressão que mapeia para qualquer tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="764da-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="764da-117">Como esse tipo mapeia para um tipo delegado, o .NET pode examinar a expressão e gerar a IL para um delegado apropriado que corresponda à assinatura da expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="764da-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="764da-118">Na maioria dos casos, isso cria um mapeamento simples entre uma expressão e o delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="764da-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="764da-119">Por exemplo, uma árvore de expressão que é representada por `Expression<Func<int>>` seria convertida em um delegado do tipo `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="764da-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="764da-120">Para uma expressão lambda com qualquer tipo de retorno e lista de argumentos, existe um tipo delegado que é o tipo de destino para o código executável representado por essa expressão lamdba.</span><span class="sxs-lookup"><span data-stu-id="764da-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="764da-121">O tipo `LamdbaExpression` contém membros `Compile` e `CompileToMethod` que você usaria para converter uma árvore de expressão em código executável.</span><span class="sxs-lookup"><span data-stu-id="764da-121">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="764da-122">O método `Compile` cria um delegado.</span><span class="sxs-lookup"><span data-stu-id="764da-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="764da-123">O método `CompileToMethod` atualiza um objeto `MethodBuilder` com a IL que representa a saída compilada da árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="764da-124">Observe que `CompileToMethod` só está disponível na estrutura de área de trabalho completa e não na estrutura do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="764da-124">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="764da-125">Opcionalmente, você também pode fornecer um `DebugInfoGenerator` que receberá as informações de depuração de símbolo para o objeto delegado gerado.</span><span class="sxs-lookup"><span data-stu-id="764da-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="764da-126">Isso permite que você converta a árvore de expressão em um objeto delegado e tenha as informações de depuração completas sobre o delegado gerado.</span><span class="sxs-lookup"><span data-stu-id="764da-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="764da-127">Uma expressão seria convertida em um delegado usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="764da-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="764da-128">Observe que o tipo delegado se baseia no tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="764da-129">Você deve conhecer o tipo de retorno e a lista de argumentos se quiser usar o objeto delegado de maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="764da-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="764da-130">O método `LambdaExpression.Compile()` retorna o tipo `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="764da-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="764da-131">Você precisará convertê-lo para o tipo delegado correto para fazer com que as ferramentas de tempo de compilação verifiquem a lista de argumentos do tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="764da-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="764da-132">Execução e tempos de vida</span><span class="sxs-lookup"><span data-stu-id="764da-132">Execution and Lifetimes</span></span>

<span data-ttu-id="764da-133">O código é executado ao invocar o delegado que foi criado quando você chamou `LamdbaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="764da-133">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="764da-134">Você pode ver isso acima do local em que `add.Compile()` retorna um delegado.</span><span class="sxs-lookup"><span data-stu-id="764da-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="764da-135">Invocar o delegado, chamando `func()`, executa o código.</span><span class="sxs-lookup"><span data-stu-id="764da-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="764da-136">Esse delegado representa o código na árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="764da-137">Você pode reter o identificador para esse delegado e invocá-lo mais tarde.</span><span class="sxs-lookup"><span data-stu-id="764da-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="764da-138">Você não precisa compilar a árvore de expressão sempre que deseja executar o código que ela representa.</span><span class="sxs-lookup"><span data-stu-id="764da-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="764da-139">(Lembre-se que as árvores de expressão são imutáveis e compilar a mesma árvore de expressão mais tarde, criará um delegado que executa o mesmo código).</span><span class="sxs-lookup"><span data-stu-id="764da-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="764da-140">Eu alerto contra a tentativa de criar mecanismos de cache mais sofisticados para aumentar o desempenho ao evitar chamadas de compilação desnecessárias.</span><span class="sxs-lookup"><span data-stu-id="764da-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="764da-141">A comparação de duas árvores de expressão arbitrárias para determinar se elas representam o mesmo algoritmo também será algo demorado para executar.</span><span class="sxs-lookup"><span data-stu-id="764da-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="764da-142">Provavelmente você descobrirá que o tempo de computação economizado para evitar quaisquer chamadas extras à `LambdaExpression.Compile()` será mais demorado que o tempo da execução do código que determina se duas árvores de expressão diferentes resultam no mesmo código executável.</span><span class="sxs-lookup"><span data-stu-id="764da-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="764da-143">Advertências</span><span class="sxs-lookup"><span data-stu-id="764da-143">Caveats</span></span>

<span data-ttu-id="764da-144">A compilação de uma expressão lambda para um delegado e invocar esse delegado é uma das operações mais simples que você pode realizar com uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="764da-145">No entanto, mesmo com essa operação simples, há limitações que você deve estar ciente.</span><span class="sxs-lookup"><span data-stu-id="764da-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="764da-146">As expressões lambda criam fechamentos sobre todas as variáveis locais que são referenciadas na expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="764da-147">Você deve assegurar que todas as variáveis que farão parte do delegado são utilizáveis no local em que você chamar `Compile` e no momento em que você executar o delegado resultante.</span><span class="sxs-lookup"><span data-stu-id="764da-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="764da-148">Em geral, o compilador garantirá que isso seja verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="764da-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="764da-149">No entanto, se sua expressão acessa uma variável que implementa `IDisposable`, é possível que seu código descarte o objeto enquanto ele ainda é mantido pela árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="764da-150">Por exemplo, esse código funciona bem, porque `int` não implementa `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="764da-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="764da-151">O delegado capturou uma referência à variável local `constant`.</span><span class="sxs-lookup"><span data-stu-id="764da-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="764da-152">Essa variável é acessada a qualquer momento mais tarde, quando a função retornada por `CreateBoundFunc` for executada.</span><span class="sxs-lookup"><span data-stu-id="764da-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="764da-153">No entanto, considere essa classe (bastante artificial) que implementa `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="764da-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="764da-154">Ao usá-la em uma expressão, como mostrado abaixo, você obterá uma `ObjectDisposedException` ao executar o código referenciado pela propriedade `Resource.Argument`:</span><span class="sxs-lookup"><span data-stu-id="764da-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="764da-155">O delegado retornado desse método fechou sobre o objeto `constant`, que foi descartado.</span><span class="sxs-lookup"><span data-stu-id="764da-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="764da-156">(Foi descartado, porque foi declarado em uma instrução `using`).</span><span class="sxs-lookup"><span data-stu-id="764da-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="764da-157">Agora, ao executar o delegado retornado desse método, uma `ObjecctDisposedException` será lançada no ponto de execução.</span><span class="sxs-lookup"><span data-stu-id="764da-157">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="764da-158">Parece realmente estranho ter um erro de tempo de execução que representa um constructo de tempo de compilação, mas esse é o mundo em que entramos quando trabalhamos com árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="764da-159">Há muitas permutações desse problema, portanto é difícil oferecer diretrizes gerais para evitá-lo.</span><span class="sxs-lookup"><span data-stu-id="764da-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="764da-160">Tenha cuidado ao acessar variáveis locais quando estiver definindo expressões e tenha cuidado ao acessar o estado no objeto atual (representado por `this`) quando estiver criando uma árvore de expressão que pode ser retornada por uma API pública.</span><span class="sxs-lookup"><span data-stu-id="764da-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="764da-161">O código na sua expressão pode referenciar métodos ou propriedades em outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="764da-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="764da-162">Esse assembly deve estar acessível quando a expressão for definida, quando ela for compilada e quando o delegado resultante for chamado.</span><span class="sxs-lookup"><span data-stu-id="764da-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="764da-163">Você vai se deparar com uma `ReferencedAssemblyNotFoundException` nos casos em que ele não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="764da-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="764da-164">Resumo</span><span class="sxs-lookup"><span data-stu-id="764da-164">Summary</span></span>

<span data-ttu-id="764da-165">As árvores de expressão que representam expressões lambda podem ser compiladas para criar um delegado que pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="764da-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="764da-166">Isso fornece um mecanismo para executar o código representado por uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="764da-167">A árvore de expressão representa o código que seria executado para qualquer constructo específico que você criar.</span><span class="sxs-lookup"><span data-stu-id="764da-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="764da-168">Contanto que o ambiente em que você compilar e executar o código corresponda ao ambiente em que você criar a expressão, tudo funcionará conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="764da-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="764da-169">Quando isso não acontece, os erros são bastante previsíveis e serão capturados em seus primeiros testes de qualquer código usando as árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="764da-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="764da-170">Próximo – Interpretando expressões</span><span class="sxs-lookup"><span data-stu-id="764da-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

---
title: Expressões de computação
description: Aprenda a criar sintaxe conveniente para escrever cálculos em F# que podem ser seqüenciados e combinados usando construções de fluxo de controle e vinculações.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400228"
---
# <a name="computation-expressions"></a><span data-ttu-id="a5099-103">Expressões de computação</span><span class="sxs-lookup"><span data-stu-id="a5099-103">Computation Expressions</span></span>

<span data-ttu-id="a5099-104">As expressões de computação em F# fornecem uma sintaxe conveniente para escrever cálculos que podem ser seqüenciados e combinados usando construções de fluxo de controle e vinculações.</span><span class="sxs-lookup"><span data-stu-id="a5099-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="a5099-105">Dependendo do tipo de expressão computacional, eles podem ser pensados como uma maneira de expressar mônades, monóides, transformadores mônades e functores aplicados.</span><span class="sxs-lookup"><span data-stu-id="a5099-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="a5099-106">No entanto, ao contrário de outras línguas (como *a notação* em Haskell), elas não estão ligadas a uma única abstração, e não dependem de macros ou outras formas de metaprogramação para realizar uma sintaxe conveniente e sensível ao contexto.</span><span class="sxs-lookup"><span data-stu-id="a5099-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="a5099-107">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a5099-107">Overview</span></span>

<span data-ttu-id="a5099-108">Computações podem assumir muitas formas.</span><span class="sxs-lookup"><span data-stu-id="a5099-108">Computations can take many forms.</span></span> <span data-ttu-id="a5099-109">A forma mais comum de computação é a execução de um segmento único, que é fácil de entender e modificar.</span><span class="sxs-lookup"><span data-stu-id="a5099-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="a5099-110">No entanto, nem todas as formas de computação são tão simples quanto a execução de um único segmento.</span><span class="sxs-lookup"><span data-stu-id="a5099-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="a5099-111">Alguns exemplos incluem:</span><span class="sxs-lookup"><span data-stu-id="a5099-111">Some examples include:</span></span>

- <span data-ttu-id="a5099-112">Cálculos não determinísticos</span><span class="sxs-lookup"><span data-stu-id="a5099-112">Non-deterministic computations</span></span>
- <span data-ttu-id="a5099-113">Cálculos assíncronos</span><span class="sxs-lookup"><span data-stu-id="a5099-113">Asynchronous computations</span></span>
- <span data-ttu-id="a5099-114">Cálculos eficazes</span><span class="sxs-lookup"><span data-stu-id="a5099-114">Effectful computations</span></span>
- <span data-ttu-id="a5099-115">Computação generativa</span><span class="sxs-lookup"><span data-stu-id="a5099-115">Generative computations</span></span>

<span data-ttu-id="a5099-116">Em geral, existem cálculos sensíveis ao *contexto* que você deve executar em certas partes de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5099-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="a5099-117">Escrever código susceptino de um código sensível ao contexto pode ser desafiador, pois é fácil "vazar" cálculos fora de um determinado contexto sem abstrações para impedi-lo de fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="a5099-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="a5099-118">Essas abstrações são muitas vezes desafiadoras para escrever por si mesmo, e é por isso que F# tem uma maneira generalizada de fazer as chamadas **expressões computacionais.**</span><span class="sxs-lookup"><span data-stu-id="a5099-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="a5099-119">As expressões computacionais oferecem um modelo uniforme de sintaxe e abstração para codificação de computação sensível ao contexto.</span><span class="sxs-lookup"><span data-stu-id="a5099-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="a5099-120">Cada expressão de computação é apoiada por um tipo *de construtor.*</span><span class="sxs-lookup"><span data-stu-id="a5099-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="a5099-121">O tipo de construtor define as operações disponíveis para a expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="a5099-122">Consulte [Criando um novo tipo de expressão de computação,](computation-expressions.md#creating-a-new-type-of-computation-expression)que mostra como criar uma expressão de computação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a5099-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="a5099-123">Visão geral da sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5099-123">Syntax overview</span></span>

<span data-ttu-id="a5099-124">Todas as expressões de computação têm a seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a5099-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="a5099-125">onde `builder-expr` está o nome de um tipo de construtor `cexper` que define a expressão de computação, e é o corpo de expressão da expressão computacional.</span><span class="sxs-lookup"><span data-stu-id="a5099-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="a5099-126">Por exemplo, `async` o código de expressão de computação pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="a5099-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="a5099-127">Há uma sintaxe adicional especial disponível dentro de uma expressão de computação, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="a5099-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="a5099-128">As seguintes formas de expressão são possíveis com expressões de computação:</span><span class="sxs-lookup"><span data-stu-id="a5099-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="a5099-129">Cada uma dessas palavras-chave e outras palavras-chave Padrão F# só estão disponíveis em uma expressão de computação se tiverem sido definidas no tipo de construtor de backup.</span><span class="sxs-lookup"><span data-stu-id="a5099-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="a5099-130">A única exceção `match!`a isso é, que é `let!` o próprio açúcar sintático para o uso seguido de um padrão compatível com o resultado.</span><span class="sxs-lookup"><span data-stu-id="a5099-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="a5099-131">O tipo de construtor é um objeto que define métodos especiais que regem a forma como os fragmentos da expressão computacional são combinados; ou seja, seus métodos controlam como a expressão computacional se comporta.</span><span class="sxs-lookup"><span data-stu-id="a5099-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="a5099-132">Outra maneira de descrever uma classe de construtores é dizer que ele permite personalizar a operação de muitas construções F#, como loops e vinculações.</span><span class="sxs-lookup"><span data-stu-id="a5099-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="a5099-133">A `let!` palavra-chave liga o resultado de uma chamada a outra expressão de computação a um nome:</span><span class="sxs-lookup"><span data-stu-id="a5099-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="a5099-134">Se você vincular a chamada a `let`uma expressão de computação com , você não obterá o resultado da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="a5099-135">Em vez disso, você terá vinculado o valor da chamada *não realizada* a essa expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="a5099-136">Use `let!` para se ligar ao resultado.</span><span class="sxs-lookup"><span data-stu-id="a5099-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="a5099-137">`let!`é definido `Bind(x, f)` pelo membro no tipo de construtor.</span><span class="sxs-lookup"><span data-stu-id="a5099-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="a5099-138">A `do!` palavra-chave é para chamar uma `unit`expressão de computação `Zero` que retorna um tipo semelhante (definido pelo membro no construtor):</span><span class="sxs-lookup"><span data-stu-id="a5099-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="a5099-139">Para o fluxo de trabalho `Async<unit>` [assíncrono,](asynchronous-workflows.md)este tipo é .</span><span class="sxs-lookup"><span data-stu-id="a5099-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="a5099-140">Para outras expressões de computação, `CExpType<unit>`é provável que o tipo seja .</span><span class="sxs-lookup"><span data-stu-id="a5099-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="a5099-141">`do!`é definido `Bind(x, f)` pelo membro sobre o `f` tipo `unit`de construtor, onde produz um .</span><span class="sxs-lookup"><span data-stu-id="a5099-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="a5099-142">A `yield` palavra-chave é para devolver um valor da expressão computacional <xref:System.Collections.Generic.IEnumerable%601>para que ele possa ser consumido como um :</span><span class="sxs-lookup"><span data-stu-id="a5099-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="a5099-143">Na maioria dos casos, pode ser omitido por chamadores.</span><span class="sxs-lookup"><span data-stu-id="a5099-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="a5099-144">A maneira mais comum `yield` de `->` omitir é com o operador:</span><span class="sxs-lookup"><span data-stu-id="a5099-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="a5099-145">Para expressões mais complexas que podem render muitos valores diferentes, e talvez condicionalmente, simplesmente omitir a palavra-chave pode fazer:</span><span class="sxs-lookup"><span data-stu-id="a5099-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="a5099-146">Como com a [palavra-chave de rendimento em C#](../../csharp/language-reference/keywords/yield.md), cada elemento na expressão de computação é rendido de volta como é iterado.</span><span class="sxs-lookup"><span data-stu-id="a5099-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="a5099-147">`yield`é definido `Yield(x)` pelo membro no tipo `x` de construtor, onde está o item a render de volta.</span><span class="sxs-lookup"><span data-stu-id="a5099-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="a5099-148">A `yield!` palavra-chave é para achatar uma coleção de valores de uma expressão computacional:</span><span class="sxs-lookup"><span data-stu-id="a5099-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="a5099-149">Quando avaliada, a expressão de `yield!` computação chamada terá seus itens recolhidos um a um, achatando o resultado.</span><span class="sxs-lookup"><span data-stu-id="a5099-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="a5099-150">`yield!`é definido `YieldFrom(x)` pelo membro sobre o `x` tipo de construtor, onde está uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="a5099-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="a5099-151">Ao `yield` `yield!` contrário, deve ser explicitamente especificado.</span><span class="sxs-lookup"><span data-stu-id="a5099-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="a5099-152">Seu comportamento não está implícito nas expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="a5099-153">A `return` palavra-chave envolve um valor no tipo correspondente à expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="a5099-154">Além das expressões `yield`computacionais usando, é usado para "completar" uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="a5099-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="a5099-155">`return`é definido `Return(x)` pelo membro no tipo `x` de construtor, onde está o item para embrulhar.</span><span class="sxs-lookup"><span data-stu-id="a5099-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="a5099-156">A `return!` palavra-chave percebe o valor de uma expressão de computação e envoltórios que resultam no tipo correspondente à expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="a5099-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="a5099-157">`return!`é definido `ReturnFrom(x)` pelo membro sobre o `x` tipo de construtor, onde está outra expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="a5099-158">A `match!` palavra-chave permite que você inforre uma chamada para outra expressão de computação e correspondência de padrão em seu resultado:</span><span class="sxs-lookup"><span data-stu-id="a5099-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="a5099-159">Ao chamar uma expressão `match!`de computação com , `let!`ele vai perceber o resultado da chamada como .</span><span class="sxs-lookup"><span data-stu-id="a5099-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="a5099-160">Isso é frequentemente usado ao chamar uma expressão de computação onde o resultado é [opcional](options.md).</span><span class="sxs-lookup"><span data-stu-id="a5099-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="a5099-161">Expressões de computação incorporadas</span><span class="sxs-lookup"><span data-stu-id="a5099-161">Built-in computation expressions</span></span>

<span data-ttu-id="a5099-162">A biblioteca principal F# define três expressões de computação incorporadas: Expressões de [seqüência,](sequences.md) [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de consulta](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a5099-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="a5099-163">Criando um novo tipo de expressão de computação</span><span class="sxs-lookup"><span data-stu-id="a5099-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="a5099-164">Você pode definir as características de suas próprias expressões de computação criando uma classe de construtor e definindo certos métodos especiais na classe.</span><span class="sxs-lookup"><span data-stu-id="a5099-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="a5099-165">A classe construtora pode definir opcionalmente os métodos listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5099-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="a5099-166">A tabela a seguir descreve métodos que podem ser usados em uma classe de construtor de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a5099-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="a5099-167">**Método**</span><span class="sxs-lookup"><span data-stu-id="a5099-167">**Method**</span></span>|<span data-ttu-id="a5099-168">**Assinatura típica**</span><span class="sxs-lookup"><span data-stu-id="a5099-168">**Typical signature(s)**</span></span>|<span data-ttu-id="a5099-169">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="a5099-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="a5099-170">Chamado `let!` e `do!` em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="a5099-171">Envolve uma expressão de computação como função.</span><span class="sxs-lookup"><span data-stu-id="a5099-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="a5099-172">Chamado `return` em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="a5099-173">Chamado `return!` em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="a5099-174">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="a5099-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="a5099-175">Executa uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="a5099-176">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="a5099-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="a5099-177">Pediu sequenciamento em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="a5099-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="a5099-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="a5099-179">Pediu `for...do` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="a5099-180">Pediu `try...finally` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="a5099-181">Pediu `try...with` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="a5099-182">Pediu `use` vinculações nas expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="a5099-183">Pediu `while...do` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="a5099-184">Pediu `yield` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="a5099-185">Pediu `yield!` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="a5099-186">Pediu ramos `else` vazios de `if...then` expressões em expressões computacionais.</span><span class="sxs-lookup"><span data-stu-id="a5099-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="a5099-187">Indica que a expressão de `Run` computação é passada ao membro como uma citação.</span><span class="sxs-lookup"><span data-stu-id="a5099-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="a5099-188">Traduz todas as instâncias de um cálculo em uma citação.</span><span class="sxs-lookup"><span data-stu-id="a5099-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="a5099-189">Muitos dos métodos em uma classe `M<'T>` de construtor usam e retornam um construto, que é tipicamente um tipo `Async<'T>` definido separadamente que caracteriza `Seq<'T>` o tipo de computação sendo combinada, por exemplo, para fluxos de trabalho assíncronos e para fluxos de trabalho seqüenciais.</span><span class="sxs-lookup"><span data-stu-id="a5099-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="a5099-190">As assinaturas desses métodos permitem que eles sejam combinados e aninhados entre si, de modo que o objeto de fluxo de trabalho retornado de uma construção possa ser passado para o próximo.</span><span class="sxs-lookup"><span data-stu-id="a5099-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="a5099-191">O compilador, quando analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhadas usando os métodos na tabela anterior e o código na expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="a5099-192">A expressão aninhada é da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a5099-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="a5099-193">No código acima, as `Run` `Delay` chamadas são omitidas se não forem definidas na classe de construtor de expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="a5099-194">O corpo da expressão computacional, `{| cexpr |}`aqui denotado como , é traduzido em chamadas envolvendo os métodos da classe construtora pelas traduções descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a5099-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="a5099-195">A expressão `{| cexpr |}` de computação é definida recursivamente `expr` de acordo com `cexpr` essas traduções onde é uma expressão F# e é uma expressão computacional.</span><span class="sxs-lookup"><span data-stu-id="a5099-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="a5099-196">Expression</span><span class="sxs-lookup"><span data-stu-id="a5099-196">Expression</span></span>|<span data-ttu-id="a5099-197">Tradução</span><span class="sxs-lookup"><span data-stu-id="a5099-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="a5099-198">Na tabela anterior, `other-expr` descreve uma expressão que não está listada de outra forma na tabela.</span><span class="sxs-lookup"><span data-stu-id="a5099-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="a5099-199">Uma classe de construtor não precisa implementar todos os métodos e suportar todas as traduções listadas na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="a5099-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="a5099-200">Aqueles construtos que não são implementados não estão disponíveis em expressões computacionais desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a5099-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="a5099-201">Por exemplo, se você não `use` quiser apoiar a palavra-chave em suas expressões `Use` de computação, você pode omitir a definição de em sua classe de construtor.</span><span class="sxs-lookup"><span data-stu-id="a5099-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="a5099-202">O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação como uma série de etapas que podem ser avaliadas um passo de cada vez.</span><span class="sxs-lookup"><span data-stu-id="a5099-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="a5099-203">Um tipo de `OkOrException`união discriminada, codifica o estado de erro da expressão como avaliado até agora.</span><span class="sxs-lookup"><span data-stu-id="a5099-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="a5099-204">Este código demonstra vários padrões típicos que você pode usar em suas expressões de computação, como implementações de caldeiras de alguns dos métodos de construtor.</span><span class="sxs-lookup"><span data-stu-id="a5099-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="a5099-205">Uma expressão de computação tem um tipo subjacente, que a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="a5099-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="a5099-206">O tipo subjacente pode representar um resultado computado ou um cálculo atrasado que pode ser realizado, ou pode fornecer uma maneira de iterar através de algum tipo de coleta.</span><span class="sxs-lookup"><span data-stu-id="a5099-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="a5099-207">No exemplo anterior, o tipo subjacente era **Eventualmente**.</span><span class="sxs-lookup"><span data-stu-id="a5099-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="a5099-208">Para uma expressão de seqüência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5099-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a5099-209">Para uma expressão de consulta, <xref:System.Linq.IQueryable?displayProperty=nameWithType>o tipo subjacente é .</span><span class="sxs-lookup"><span data-stu-id="a5099-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a5099-210">Para um fluxo de trabalho assíncrono, o tipo subjacente é [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="a5099-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="a5099-211">O `Async` objeto representa o trabalho a ser realizado para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="a5099-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="a5099-212">Por exemplo, [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) você chama para executar um cálculo e retornar o resultado.</span><span class="sxs-lookup"><span data-stu-id="a5099-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="a5099-213">Operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a5099-213">Custom Operations</span></span>

<span data-ttu-id="a5099-214">Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como operador em uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="a5099-215">Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="a5099-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="a5099-216">Quando você define uma operação personalizada, você deve definir os métodos Rendimento e Para na expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="a5099-217">Para definir uma operação personalizada, coloque-a em uma classe de [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)construtor para a expressão de computação e, em seguida, aplique o .</span><span class="sxs-lookup"><span data-stu-id="a5099-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="a5099-218">Este atributo tem uma seqüência como argumento, que é o nome a ser usado em uma operação personalizada.</span><span class="sxs-lookup"><span data-stu-id="a5099-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="a5099-219">Este nome entra em escopo no início da cinta encaracolada de abertura da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="a5099-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="a5099-220">Portanto, você não deve usar identificadores que tenham o mesmo nome de uma operação personalizada neste bloco.</span><span class="sxs-lookup"><span data-stu-id="a5099-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="a5099-221">Por exemplo, evite o uso de `all` `last` identificadores como ou em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="a5099-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="a5099-222">Ampliação de construtores existentes com novas operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a5099-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="a5099-223">Se você já tem uma classe de construtor, suas operações personalizadas podem ser estendidas de fora desta classe de construtores.</span><span class="sxs-lookup"><span data-stu-id="a5099-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="a5099-224">As extensões devem ser declaradas em módulos.</span><span class="sxs-lookup"><span data-stu-id="a5099-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="a5099-225">Os namespaces não podem conter membros de extensão, exceto no mesmo arquivo e no mesmo grupo de declaração de namespace onde o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="a5099-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="a5099-226">O exemplo a seguir mostra `Microsoft.FSharp.Linq.QueryBuilder` a extensão da classe existente.</span><span class="sxs-lookup"><span data-stu-id="a5099-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="a5099-227">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5099-227">See also</span></span>

- [<span data-ttu-id="a5099-228">Referência de idioma F#</span><span class="sxs-lookup"><span data-stu-id="a5099-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a5099-229">Fluxos de Trabalho Assíncronos</span><span class="sxs-lookup"><span data-stu-id="a5099-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="a5099-230">Sequências</span><span class="sxs-lookup"><span data-stu-id="a5099-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="a5099-231">Expressões de consulta</span><span class="sxs-lookup"><span data-stu-id="a5099-231">Query Expressions</span></span>](query-expressions.md)

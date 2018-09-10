---
title: Expressões de computação (F#)
description: 'Saiba como criar uma sintaxe conveniente para criar cálculos em F # que podem ser sequenciados e combinados usando construções de fluxo de controle e associações.'
ms.date: 07/27/2018
ms.openlocfilehash: ce81af7966a436b3973de277fb2a78ec06f4c471
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273759"
---
# <a name="computation-expressions"></a><span data-ttu-id="863a8-103">Expressões de computação</span><span class="sxs-lookup"><span data-stu-id="863a8-103">Computation Expressions</span></span>

<span data-ttu-id="863a8-104">Expressões de computação no F # fornecem uma sintaxe conveniente para criar cálculos que podem ser sequenciados e combinados usando construções de fluxo de controle e associações.</span><span class="sxs-lookup"><span data-stu-id="863a8-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="863a8-105">Dependendo do tipo de expressão de computação, elas podem ser consideradas como uma maneira de expressar monads, monoids, transformadores monad e functors applicative.</span><span class="sxs-lookup"><span data-stu-id="863a8-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="863a8-106">No entanto, ao contrário de outras linguagens (como *notação* em Haskell), eles não estão vinculados a uma única abstração e não dependem de macros ou outras formas de metaprogramação para realizar uma sintaxe conveniente e sensível ao contexto.</span><span class="sxs-lookup"><span data-stu-id="863a8-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="863a8-107">Visão geral</span><span class="sxs-lookup"><span data-stu-id="863a8-107">Overview</span></span>

<span data-ttu-id="863a8-108">Computações podem assumir várias formas.</span><span class="sxs-lookup"><span data-stu-id="863a8-108">Computations can take many forms.</span></span> <span data-ttu-id="863a8-109">A forma mais comum de computação é execução single-threaded, que é fácil de entender e modificar.</span><span class="sxs-lookup"><span data-stu-id="863a8-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="863a8-110">No entanto, nem todos os formulários de computação são tão simples como execução single-threaded.</span><span class="sxs-lookup"><span data-stu-id="863a8-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="863a8-111">Eis alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="863a8-111">Some examples include:</span></span>

* <span data-ttu-id="863a8-112">Cálculos não determinísticas</span><span class="sxs-lookup"><span data-stu-id="863a8-112">Non-deterministic computations</span></span>
* <span data-ttu-id="863a8-113">Computações assíncronas</span><span class="sxs-lookup"><span data-stu-id="863a8-113">Asynchronous computations</span></span>
* <span data-ttu-id="863a8-114">Computações effectful</span><span class="sxs-lookup"><span data-stu-id="863a8-114">Effectful computations</span></span>
* <span data-ttu-id="863a8-115">Computações produtivas</span><span class="sxs-lookup"><span data-stu-id="863a8-115">Generative computations</span></span>

<span data-ttu-id="863a8-116">De modo geral, há *contextual* cálculos que você deve executar em determinadas partes de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="863a8-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="863a8-117">Escrever o código sensível ao contexto pode ser um desafio, pois é fácil de computações "vaze" fora de um determinado contexto sem abstrações para impedir que você fazer isso.</span><span class="sxs-lookup"><span data-stu-id="863a8-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="863a8-118">Essas abstrações geralmente são um desafio para escrever por conta própria, por isso, o F # tem uma maneira generalizada fazer chamados **expressões de computação**.</span><span class="sxs-lookup"><span data-stu-id="863a8-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="863a8-119">Expressões de computação oferecem um modelo uniforme de sintaxe e abstração para codificação de cálculos sensíveis ao contexto.</span><span class="sxs-lookup"><span data-stu-id="863a8-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="863a8-120">Cada expressão de computação é apoiado por um *construtor* tipo.</span><span class="sxs-lookup"><span data-stu-id="863a8-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="863a8-121">O tipo de construtor define as operações que estão disponíveis para a expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="863a8-122">Ver [criando uma nova expressão de tipo de computação](computation-expressions.md#creating-a-new-type-of-computation-expression), que mostra como criar uma expressão de cálculo personalizado.</span><span class="sxs-lookup"><span data-stu-id="863a8-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="863a8-123">Visão geral da sintaxe</span><span class="sxs-lookup"><span data-stu-id="863a8-123">Syntax overview</span></span>

<span data-ttu-id="863a8-124">Todas as expressões de computação têm o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="863a8-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="863a8-125">em que `builder-expr` é o nome de um tipo de construtor que define a expressão de computação, e `cexper` é o corpo de expressão da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="863a8-126">Por exemplo, `async` código de expressão de cálculo pode ter esta aparência:</span><span class="sxs-lookup"><span data-stu-id="863a8-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="863a8-127">Há uma sintaxe especial, adicional disponível dentro de uma expressão de computação, conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="863a8-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="863a8-128">Os formulários de expressão a seguir são possíveis com expressões de computação:</span><span class="sxs-lookup"><span data-stu-id="863a8-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="863a8-129">Cada uma dessas palavras-chave e outros F # palavras-chave padrão só estão disponíveis em uma expressão de computação se eles tiverem sido definidos no tipo de construtor de backup.</span><span class="sxs-lookup"><span data-stu-id="863a8-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="863a8-130">É a única exceção a isso `match!`, que é a própria açúcar sintático para o uso de `let!` seguido por uma correspondência de padrões no resultado.</span><span class="sxs-lookup"><span data-stu-id="863a8-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="863a8-131">O tipo de construtor é um objeto que define os métodos especiais que regem a forma como os fragmentos da expressão de computação são combinados; ou seja, a seus métodos controlam o comportamento da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="863a8-132">Outra maneira de descrever uma classe de construtor é dizer que ele permite que você personalize a operação de várias construções no F #, como loops e associações.</span><span class="sxs-lookup"><span data-stu-id="863a8-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="863a8-133">O `let!` palavra-chave associa o resultado de uma chamada para outra expressão de computação para um nome:</span><span class="sxs-lookup"><span data-stu-id="863a8-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="863a8-134">Se você associar a chamada para uma expressão de computação com `let`, você não obterá o resultado da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="863a8-135">Em vez disso, você será tiver associado o valor de *não realizado* chamada para essa expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="863a8-136">Use `let!` para associar ao resultado.</span><span class="sxs-lookup"><span data-stu-id="863a8-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="863a8-137">`let!` é definido pelo `Bind(x, f)` membro no tipo de construtor.</span><span class="sxs-lookup"><span data-stu-id="863a8-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="863a8-138">O `do!` palavra-chave é para chamar uma expressão de cálculo que retorna um `unit`-como o tipo (definido pelo `Zero` membro no construtor de):</span><span class="sxs-lookup"><span data-stu-id="863a8-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! sumbitData data url
        ...
    }
```

<span data-ttu-id="863a8-139">Para o [fluxo de trabalho assíncrono](asynchronous-workflows.md), esse tipo é `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="863a8-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="863a8-140">Para outras expressões de cálculo, o tipo é provavelmente será `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="863a8-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="863a8-141">`do!` é definido pela `Bind(x, f)` membro no tipo de construtor, onde `f` produz um `unit`.</span><span class="sxs-lookup"><span data-stu-id="863a8-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="863a8-142">O `yield` palavra-chave é para retornar um valor de expressão de computação para que ele possa ser consumido como um <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="863a8-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="863a8-143">Assim como acontece com o [palavra-chave na linguagem c# yield](../../csharp/language-reference/keywords/yield.md), cada elemento na expressão de cálculo é rendido de volta como ele é iterado.</span><span class="sxs-lookup"><span data-stu-id="863a8-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="863a8-144">`yield` é definido pela `Yield(x)` membro no tipo de construtor, onde `x` é o item para gerar novamente.</span><span class="sxs-lookup"><span data-stu-id="863a8-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="863a8-145">O `yield!` palavra-chave é para mesclar uma coleção de valores de uma expressão de cálculo:</span><span class="sxs-lookup"><span data-stu-id="863a8-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="863a8-146">Quando avaliada, a expressão de computação chamado pelo `yield!` serão seus itens produziram back---individualmente, simplificar o resultado.</span><span class="sxs-lookup"><span data-stu-id="863a8-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="863a8-147">`yield!` é definido pela `YieldFrom(x)` membro no tipo de construtor, onde `x` é uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="863a8-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="863a8-148">O `return` palavra-chave encapsula um valor no tipo correspondente à expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="863a8-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="863a8-149">Além das expressões de computação usando `yield`, ele é usado para "complete" uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="863a8-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="863a8-150">`return` é definido pela `Return(x)` membro no tipo de construtor, onde `x` é o item a ser encapsulado.</span><span class="sxs-lookup"><span data-stu-id="863a8-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="863a8-151">O `return!` palavra-chave percebe que o valor de uma expressão de computação e encapsula o resultado no tipo correspondente à expressão de cálculo:</span><span class="sxs-lookup"><span data-stu-id="863a8-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="863a8-152">`return!` é definido pela `ReturnFrom(x)` membro no tipo de construtor, onde `x` é outra expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="863a8-153">Começando com o F # 4.5, o `match!` palavra-chave permite que você embutir uma chamada para outra correspondência de expressão e o padrão de computação em seu resultado:</span><span class="sxs-lookup"><span data-stu-id="863a8-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="863a8-154">Ao chamar uma expressão de computação com `match!`, ele obterá o resultado da chamada, como `let!`.</span><span class="sxs-lookup"><span data-stu-id="863a8-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="863a8-155">Isso geralmente é usado ao chamar uma expressão de computação em que o resultado é um [opcional](options.md).</span><span class="sxs-lookup"><span data-stu-id="863a8-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="863a8-156">Expressões de computação interna</span><span class="sxs-lookup"><span data-stu-id="863a8-156">Built-in computation expressions</span></span>

<span data-ttu-id="863a8-157">A biblioteca principal F # define três expressões de computação interna: [expressões de sequência](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de consulta](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="863a8-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="863a8-158">Criar um novo tipo de expressão de computação</span><span class="sxs-lookup"><span data-stu-id="863a8-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="863a8-159">Você pode definir as características de suas próprias expressões de cálculo, criando uma classe de construtor e definindo determinados métodos especiais na classe.</span><span class="sxs-lookup"><span data-stu-id="863a8-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="863a8-160">A classe de construtor, opcionalmente, pode definir os métodos, conforme listado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="863a8-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="863a8-161">A tabela a seguir descreve os métodos que podem ser usados em uma classe de construtor do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="863a8-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="863a8-162">**Método**</span><span class="sxs-lookup"><span data-stu-id="863a8-162">**Method**</span></span>|<span data-ttu-id="863a8-163">**Típica assinatura (s)**</span><span class="sxs-lookup"><span data-stu-id="863a8-163">**Typical signature(s)**</span></span>|<span data-ttu-id="863a8-164">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="863a8-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="863a8-165">Chamado para `let!` e `do!` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="863a8-166">Encapsula uma expressão de computação como uma função.</span><span class="sxs-lookup"><span data-stu-id="863a8-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="863a8-167">Chamado para `return` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="863a8-168">Chamado para `return!` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="863a8-169">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="863a8-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="863a8-170">Executa uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="863a8-171">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="863a8-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="863a8-172">Chamado para o sequenciamento em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="863a8-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="863a8-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="863a8-174">Chamado para `for...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="863a8-175">Chamado para `try...finally` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="863a8-176">Chamado para `try...with` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="863a8-177">Chamado para `use` ligações em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="863a8-178">Chamado para `while...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="863a8-179">Chamado para `yield` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="863a8-180">Chamado para `yield!` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="863a8-181">Chamado para vazio `else` ramificações de `if...then` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|

<span data-ttu-id="863a8-182">Muitos dos métodos em uma classe de construtor usam e retornam um `M<'T>` constructo, que geralmente é um tipo definido separadamente que caracteriza o tipo de computações sendo combinados, por exemplo, `Async<'T>` para fluxos de trabalho assíncronos e `Seq<'T>` para fluxos de trabalho da sequência.</span><span class="sxs-lookup"><span data-stu-id="863a8-182">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="863a8-183">As assinaturas desses métodos habilitá-los a serem combinados e aninhados uns com os outros, para que o objeto de fluxo de trabalho retornado por uma construção que pode ser passado para o próximo.</span><span class="sxs-lookup"><span data-stu-id="863a8-183">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="863a8-184">O compilador, quando ele analisa uma expressão de computação, converte a expressão em uma série de chamadas de função aninhada usando os métodos na tabela anterior e o código na expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="863a8-184">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="863a8-185">A expressão aninhada é da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="863a8-185">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="863a8-186">No código acima, as chamadas para `Run` e `Delay` são omitidos se eles não estão definidos na classe de construtor de expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-186">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="863a8-187">O corpo da expressão de computação, aqui é denotado como `{| cexpr |}`, é convertida em chamadas envolvendo os métodos da classe de construtor pelas conversões descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="863a8-187">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="863a8-188">A expressão de cálculo `{| cexpr |}` é definido recursivamente acordo com essas traduções em que `expr` é uma expressão F # e `cexpr` é uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-188">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="863a8-189">Expressão</span><span class="sxs-lookup"><span data-stu-id="863a8-189">Expression</span></span>|<span data-ttu-id="863a8-190">Conversão</span><span class="sxs-lookup"><span data-stu-id="863a8-190">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="863a8-191">Na tabela anterior, `other-expr` descreve uma expressão que não esteja listada na tabela de caso contrário.</span><span class="sxs-lookup"><span data-stu-id="863a8-191">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="863a8-192">Uma classe de construtor não precisa implementar todos os métodos e dar suporte a todas as conversões listadas na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="863a8-192">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="863a8-193">Essas construções que não são implementadas não estão disponíveis em expressões de computação desse tipo.</span><span class="sxs-lookup"><span data-stu-id="863a8-193">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="863a8-194">Por exemplo, se você não deseja oferecer suporte a `use` palavra-chave em suas expressões de computação, você pode omitir a definição de `Use` em sua classe de construtor.</span><span class="sxs-lookup"><span data-stu-id="863a8-194">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="863a8-195">O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação de uma série de etapas que podem ser avaliadas uma etapa por vez.</span><span class="sxs-lookup"><span data-stu-id="863a8-195">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="863a8-196">Um tipo de união de discriminada `OkOrException`, codifica o estado de erro da expressão, conforme avaliado até o momento.</span><span class="sxs-lookup"><span data-stu-id="863a8-196">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="863a8-197">Esse código demonstra vários padrões típicos que você pode usar em suas expressões de computação, como as implementações de texto clichê de alguns dos métodos de construtor.</span><span class="sxs-lookup"><span data-stu-id="863a8-197">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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
        | Done value -> NotYetDone (fun () -> func value)
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
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="863a8-198">Uma expressão de computação tem um tipo subjacente, que retorna a expressão.</span><span class="sxs-lookup"><span data-stu-id="863a8-198">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="863a8-199">O tipo subjacente pode representar um resultado calculado ou uma computação atrasada que pode ser executada ou ela pode fornecer uma maneira para iterar por meio de algum tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="863a8-199">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="863a8-200">No exemplo anterior, o tipo subjacente foi **eventualmente**.</span><span class="sxs-lookup"><span data-stu-id="863a8-200">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="863a8-201">Uma expressão de sequência, o tipo subjacente é <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="863a8-201">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="863a8-202">Uma expressão de consulta, o tipo subjacente é <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="863a8-202">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="863a8-203">Para um fluxo de trabalho assíncrono, o tipo subjacente é [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="863a8-203">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="863a8-204">O `Async` objeto representa o trabalho seja realizado para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="863a8-204">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="863a8-205">Por exemplo, você chama [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar um cálculo e retornar o resultado.</span><span class="sxs-lookup"><span data-stu-id="863a8-205">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="863a8-206">Operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="863a8-206">Custom Operations</span></span>

<span data-ttu-id="863a8-207">Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como um operador em uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-207">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="863a8-208">Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="863a8-208">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="863a8-209">Quando você define uma operação personalizada, você deve definir o rendimento e métodos na expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="863a8-209">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="863a8-210">Para definir uma operação personalizada, coloque-o em uma classe de construtor para a expressão de cálculo e, em seguida, aplicar a [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="863a8-210">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="863a8-211">Esse atributo usa uma cadeia de caracteres como um argumento, que é o nome a ser usado em uma operação personalizada.</span><span class="sxs-lookup"><span data-stu-id="863a8-211">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="863a8-212">Esse nome entra em escopo no início da chave de abertura da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="863a8-212">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="863a8-213">Portanto, você não deve usar identificadores que têm o mesmo nome que uma operação personalizada neste bloco.</span><span class="sxs-lookup"><span data-stu-id="863a8-213">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="863a8-214">Por exemplo, evite o uso de identificadores como `all` ou `last` em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="863a8-214">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="863a8-215">Estendendo construtores existentes com novas operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="863a8-215">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="863a8-216">Se você já tiver uma classe de construtor, suas operações personalizadas podem ser estendidas de fora dessa classe de construtor.</span><span class="sxs-lookup"><span data-stu-id="863a8-216">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="863a8-217">As extensões devem ser declaradas em módulos.</span><span class="sxs-lookup"><span data-stu-id="863a8-217">Extensions must be declared in modules.</span></span> <span data-ttu-id="863a8-218">Namespaces não podem conter membros de extensão, exceto no mesmo arquivo e o mesmo grupo de declaração de namespace no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="863a8-218">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="863a8-219">O exemplo a seguir mostra a extensão da existente `Microsoft.FSharp.Linq.QueryBuilder` classe.</span><span class="sxs-lookup"><span data-stu-id="863a8-219">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="863a8-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="863a8-220">See also</span></span>

- [<span data-ttu-id="863a8-221">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="863a8-221">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="863a8-222">Fluxos de Trabalho Assíncronos</span><span class="sxs-lookup"><span data-stu-id="863a8-222">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="863a8-223">Sequências</span><span class="sxs-lookup"><span data-stu-id="863a8-223">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="863a8-224">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="863a8-224">Query Expressions</span></span>](query-expressions.md)

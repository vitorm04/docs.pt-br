---
title: Expressões de computação
description: Saiba como criar uma sintaxe conveniente para escrever cálculos no F# que pode ser sequenciada e combinada usando construções e associações de fluxo de controle.
ms.date: 03/15/2019
ms.openlocfilehash: bca328a09ff61fb76d30960221ee3350fcc25fc1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106577"
---
# <a name="computation-expressions"></a><span data-ttu-id="d4796-103">Expressões de computação</span><span class="sxs-lookup"><span data-stu-id="d4796-103">Computation Expressions</span></span>

<span data-ttu-id="d4796-104">As expressões de F# computação no fornecem uma sintaxe conveniente para escrever computações que podem ser sequenciadas e combinadas usando construções e associações de fluxo de controle.</span><span class="sxs-lookup"><span data-stu-id="d4796-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="d4796-105">Dependendo do tipo de expressão de computação, eles podem ser considerados como uma maneira de expressar monads, monoids, transformadores do Monad e Applicative transmissão functors.</span><span class="sxs-lookup"><span data-stu-id="d4796-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="d4796-106">No entanto, ao contrário de outras linguagens (como o *-Notation* no Haskell), elas não estão vinculadas a uma única abstração e não dependem de macros ou de outras formas de metaprogramação para realizar uma sintaxe conveniente e sensível ao contexto.</span><span class="sxs-lookup"><span data-stu-id="d4796-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="d4796-107">Visão geral</span><span class="sxs-lookup"><span data-stu-id="d4796-107">Overview</span></span>

<span data-ttu-id="d4796-108">As computações podem ter muitas formas.</span><span class="sxs-lookup"><span data-stu-id="d4796-108">Computations can take many forms.</span></span> <span data-ttu-id="d4796-109">A forma mais comum de computação é a execução de thread único, que é fácil de entender e modificar.</span><span class="sxs-lookup"><span data-stu-id="d4796-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="d4796-110">No entanto, nem todas as formas de computação são tão simples quanto a execução de thread único.</span><span class="sxs-lookup"><span data-stu-id="d4796-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="d4796-111">Eis alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="d4796-111">Some examples include:</span></span>

- <span data-ttu-id="d4796-112">Computações não determinísticas</span><span class="sxs-lookup"><span data-stu-id="d4796-112">Non-deterministic computations</span></span>
- <span data-ttu-id="d4796-113">Computações assíncronas</span><span class="sxs-lookup"><span data-stu-id="d4796-113">Asynchronous computations</span></span>
- <span data-ttu-id="d4796-114">Cálculos de efeito</span><span class="sxs-lookup"><span data-stu-id="d4796-114">Effectful computations</span></span>
- <span data-ttu-id="d4796-115">Computações de geração</span><span class="sxs-lookup"><span data-stu-id="d4796-115">Generative computations</span></span>

<span data-ttu-id="d4796-116">Em geral, há cálculos *sensíveis ao contexto* que você deve executar em determinadas partes de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4796-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="d4796-117">Escrever código sensível ao contexto pode ser desafiador, pois é fácil "vazar" cálculos fora de um determinado contexto sem abstrações para impedir que você faça isso.</span><span class="sxs-lookup"><span data-stu-id="d4796-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="d4796-118">Muitas vezes, essas abstrações são desafiadoras de escrever por conta própria F# , e é por isso que tem uma maneira generalizada de fazer isso, chamado de **expressões de computação**.</span><span class="sxs-lookup"><span data-stu-id="d4796-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="d4796-119">As expressões de computação oferecem uma sintaxe uniforme e um modelo de abstração para codificar cálculos sensíveis ao contexto.</span><span class="sxs-lookup"><span data-stu-id="d4796-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="d4796-120">Cada expressão de computação é apoiada por um tipo de *Construtor* .</span><span class="sxs-lookup"><span data-stu-id="d4796-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="d4796-121">O tipo de construtor define as operações que estão disponíveis para a expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="d4796-122">Consulte [criando um novo tipo de expressão de computação](computation-expressions.md#creating-a-new-type-of-computation-expression), que mostra como criar uma expressão de computação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d4796-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="d4796-123">Visão geral da sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4796-123">Syntax overview</span></span>

<span data-ttu-id="d4796-124">Todas as expressões de computação têm o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="d4796-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="d4796-125">em `builder-expr` que é o nome de um tipo de construtor que define a expressão de `cexper` computação e é o corpo da expressão da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="d4796-126">Por exemplo, `async` o código de expressão de computação pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="d4796-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="d4796-127">Há uma sintaxe adicional e especial disponível em uma expressão de computação, conforme mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d4796-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="d4796-128">Os formulários de expressão a seguir são possíveis com expressões de computação:</span><span class="sxs-lookup"><span data-stu-id="d4796-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="d4796-129">Cada uma dessas palavras-chave e outras palavras- F# chave padrão só estarão disponíveis em uma expressão de computação se elas tiverem sido definidas no tipo de construtor de backup.</span><span class="sxs-lookup"><span data-stu-id="d4796-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="d4796-130">A única exceção é `match!`, que é, por sua vez, uma simplificação sintática para o uso de `let!` seguido por um padrão de correspondência no resultado.</span><span class="sxs-lookup"><span data-stu-id="d4796-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="d4796-131">O tipo de construtor é um objeto que define métodos especiais que regem a maneira como os fragmentos da expressão de computação são combinados; ou seja, seus métodos controlam a forma como a expressão de computação se comporta.</span><span class="sxs-lookup"><span data-stu-id="d4796-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="d4796-132">Outra maneira de descrever uma classe de construtor é dizer que ela permite que você personalize a operação de muitas F# construções, como loops e associações.</span><span class="sxs-lookup"><span data-stu-id="d4796-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="d4796-133">A `let!` palavra-chave associa o resultado de uma chamada a outra expressão de computação a um nome:</span><span class="sxs-lookup"><span data-stu-id="d4796-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="d4796-134">Se você associar a chamada a uma expressão de computação `let`com, não obterá o resultado da expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="d4796-135">Em vez disso, você terá associado o valor da chamada não *realizada* a essa expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="d4796-136">Use `let!` para associar ao resultado.</span><span class="sxs-lookup"><span data-stu-id="d4796-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="d4796-137">`let!`é definido pelo `Bind(x, f)` membro no tipo de construtor.</span><span class="sxs-lookup"><span data-stu-id="d4796-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="d4796-138">A `do!` palavra-chave é para chamar uma expressão de computação `unit`que retorna um `Zero` tipo-like (definido pelo membro no Construtor):</span><span class="sxs-lookup"><span data-stu-id="d4796-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="d4796-139">Para o [fluxo de trabalho assíncrono](asynchronous-workflows.md), esse `Async<unit>`tipo é.</span><span class="sxs-lookup"><span data-stu-id="d4796-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="d4796-140">Para outras expressões de computação, é provável que o tipo `CExpType<unit>`seja.</span><span class="sxs-lookup"><span data-stu-id="d4796-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="d4796-141">`do!`é definido pelo `Bind(x, f)` membro no tipo de construtor, onde `f` produz um `unit`.</span><span class="sxs-lookup"><span data-stu-id="d4796-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="d4796-142">A `yield` palavra-chave é para retornar um valor da expressão de computação para que ela possa ser consumida como um <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="d4796-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="d4796-143">Assim como acontece com a [palavra C#-chave yield em ](../../csharp/language-reference/keywords/yield.md), cada elemento na expressão de computação é devolvido conforme é iterado.</span><span class="sxs-lookup"><span data-stu-id="d4796-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="d4796-144">`yield`é definido pelo `Yield(x)` membro no tipo de construtor, em que `x` é o item a ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="d4796-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="d4796-145">A `yield!` palavra-chave é para mesclar uma coleção de valores de uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="d4796-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="d4796-146">Quando avaliado, a expressão de computação chamada `yield!` por terá seus itens devolvidos um-por-um, mesclando o resultado.</span><span class="sxs-lookup"><span data-stu-id="d4796-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="d4796-147">`yield!`é definido pelo `YieldFrom(x)` membro no tipo de construtor, em que `x` é uma coleção de valores.</span><span class="sxs-lookup"><span data-stu-id="d4796-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="d4796-148">A `return` palavra-chave encapsula um valor no tipo correspondente à expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="d4796-149">Além das expressões de computação `yield`usando o, ele é usado para "Concluir" uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="d4796-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="d4796-150">`return`é definido pelo `Return(x)` membro no tipo de construtor, em que `x` é o item a ser quebrado.</span><span class="sxs-lookup"><span data-stu-id="d4796-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="d4796-151">A `return!` palavra-chave percebe o valor de uma expressão de computação e encapsulamentos que resultam no tipo correspondente à expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="d4796-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="d4796-152">`return!`é definido pelo `ReturnFrom(x)` membro no tipo de construtor, em que `x` é outra expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="d4796-153">A partir F# do 4,5, `match!` a palavra-chave permite embutir uma chamada para outra expressão de computação e correspondência de padrão em seu resultado:</span><span class="sxs-lookup"><span data-stu-id="d4796-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="d4796-154">Ao chamar uma expressão de computação `match!`com o, ele perceberá o resultado da chamada `let!`como.</span><span class="sxs-lookup"><span data-stu-id="d4796-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="d4796-155">Isso geralmente é usado ao chamar uma expressão de computação em que o resultado é um [opcional](options.md).</span><span class="sxs-lookup"><span data-stu-id="d4796-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="d4796-156">Expressões de computação internas</span><span class="sxs-lookup"><span data-stu-id="d4796-156">Built-in computation expressions</span></span>

<span data-ttu-id="d4796-157">A F# biblioteca principal define três expressões de computação internas: [Expressões de sequência](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e expressões de [consulta](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d4796-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="d4796-158">Criando um novo tipo de expressão de computação</span><span class="sxs-lookup"><span data-stu-id="d4796-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="d4796-159">Você pode definir as características de suas próprias expressões de computação criando uma classe de construtor e definindo determinados métodos especiais na classe.</span><span class="sxs-lookup"><span data-stu-id="d4796-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="d4796-160">A classe Builder pode, opcionalmente, definir os métodos conforme listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4796-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="d4796-161">A tabela a seguir descreve os métodos que podem ser usados em uma classe do construtor de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d4796-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="d4796-162">**Método**</span><span class="sxs-lookup"><span data-stu-id="d4796-162">**Method**</span></span>|<span data-ttu-id="d4796-163">**Assinaturas típicas**</span><span class="sxs-lookup"><span data-stu-id="d4796-163">**Typical signature(s)**</span></span>|<span data-ttu-id="d4796-164">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="d4796-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="d4796-165">Chamado para `let!` e `do!` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="d4796-166">Encapsula uma expressão de computação como uma função.</span><span class="sxs-lookup"><span data-stu-id="d4796-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="d4796-167">Chamado para `return` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="d4796-168">Chamado para `return!` em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="d4796-169">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="d4796-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="d4796-170">Executa uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="d4796-171">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="d4796-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="d4796-172">Chamado para sequenciamento em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="d4796-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="d4796-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="d4796-174">Chamado para `for...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="d4796-175">Chamado para `try...finally` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="d4796-176">Chamado para `try...with` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="d4796-177">Chamado para `use` associações em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="d4796-178">Chamado para `while...do` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="d4796-179">Chamado para `yield` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="d4796-180">Chamado para `yield!` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="d4796-181">Chamado para ramificações vazias `else` de `if...then` expressões em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="d4796-182">Indica que a expressão de computação é passada para `Run` o membro como uma cotação.</span><span class="sxs-lookup"><span data-stu-id="d4796-182">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="d4796-183">Ele traduz todas as instâncias de uma computação em uma cotação.</span><span class="sxs-lookup"><span data-stu-id="d4796-183">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="d4796-184">Muitos dos métodos em uma classe de Construtor usam e retornam `M<'T>` uma construção, que normalmente é um tipo definido separadamente que caracteriza o tipo de cálculo que está sendo combinado, por exemplo `Async<'T>` , para fluxos de trabalho `Seq<'T>` assíncronos e para fluxos de trabalho de sequência.</span><span class="sxs-lookup"><span data-stu-id="d4796-184">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="d4796-185">As assinaturas desses métodos permitem que eles sejam combinados e aninhados entre si, para que o objeto de fluxo de trabalho retornado de uma construção possa ser passado para o próximo.</span><span class="sxs-lookup"><span data-stu-id="d4796-185">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="d4796-186">O compilador, quando analisa uma expressão de cálculo, converte a expressão em uma série de chamadas de função aninhadas usando os métodos na tabela anterior e o código na expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-186">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="d4796-187">A expressão aninhada é do seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="d4796-187">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="d4796-188">No código acima, as chamadas para `Run` e `Delay` serão omitidas se não estiverem definidas na classe do construtor de expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-188">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="d4796-189">O corpo da expressão de computação, aqui indicado como, é `{| cexpr |}`traduzido em chamadas que envolvem os métodos da classe Builder pelas traduções descritas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4796-189">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="d4796-190">A `{| cexpr |}` expressão de computação é definida recursivamente de acordo com essas traduções F# em que `cexpr` `expr` é uma expressão e é uma expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="d4796-190">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="d4796-191">Expressão</span><span class="sxs-lookup"><span data-stu-id="d4796-191">Expression</span></span>|<span data-ttu-id="d4796-192">Conversão</span><span class="sxs-lookup"><span data-stu-id="d4796-192">Translation</span></span>|
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
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
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

<span data-ttu-id="d4796-193">Na tabela anterior, `other-expr` descreve uma expressão que não é listada de outra forma na tabela.</span><span class="sxs-lookup"><span data-stu-id="d4796-193">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="d4796-194">Uma classe de construtor não precisa implementar todos os métodos e dar suporte a todas as conversões listadas na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="d4796-194">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="d4796-195">As construções que não estão implementadas não estão disponíveis em expressões de computação desse tipo.</span><span class="sxs-lookup"><span data-stu-id="d4796-195">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="d4796-196">Por exemplo, se você não quiser dar suporte `use` à palavra-chave em suas expressões de computação, poderá omitir a definição de `Use` na classe do construtor.</span><span class="sxs-lookup"><span data-stu-id="d4796-196">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="d4796-197">O exemplo de código a seguir mostra uma expressão de computação que encapsula uma computação como uma série de etapas que podem ser avaliadas uma etapa por vez.</span><span class="sxs-lookup"><span data-stu-id="d4796-197">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="d4796-198">Um tipo de união discriminada `OkOrException`,, codifica o estado de erro da expressão como avaliado até agora.</span><span class="sxs-lookup"><span data-stu-id="d4796-198">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="d4796-199">Esse código demonstra vários padrões típicos que você pode usar em suas expressões de computação, como implementações padronizadas de alguns dos métodos do Builder.</span><span class="sxs-lookup"><span data-stu-id="d4796-199">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="d4796-200">Uma expressão de computação tem um tipo subjacente, que a expressão retorna.</span><span class="sxs-lookup"><span data-stu-id="d4796-200">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="d4796-201">O tipo subjacente pode representar um resultado calculado ou uma computação atrasada que pode ser executada ou pode fornecer uma maneira de iterar por meio de algum tipo de coleção.</span><span class="sxs-lookup"><span data-stu-id="d4796-201">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="d4796-202">No exemplo anterior, o tipo subjacente era **eventualmente**.</span><span class="sxs-lookup"><span data-stu-id="d4796-202">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="d4796-203">Para uma expressão de sequência, o tipo subjacente <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>é.</span><span class="sxs-lookup"><span data-stu-id="d4796-203">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d4796-204">Para uma expressão de consulta, o tipo subjacente <xref:System.Linq.IQueryable?displayProperty=nameWithType>é.</span><span class="sxs-lookup"><span data-stu-id="d4796-204">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d4796-205">Para um fluxo de trabalho assíncrono, o tipo [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)subjacente é.</span><span class="sxs-lookup"><span data-stu-id="d4796-205">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="d4796-206">O `Async` objeto representa o trabalho a ser executado para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="d4796-206">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="d4796-207">Por exemplo, você chama [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) para executar uma computação e retornar o resultado.</span><span class="sxs-lookup"><span data-stu-id="d4796-207">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="d4796-208">Operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d4796-208">Custom Operations</span></span>

<span data-ttu-id="d4796-209">Você pode definir uma operação personalizada em uma expressão de computação e usar uma operação personalizada como um operador em uma expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-209">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="d4796-210">Por exemplo, você pode incluir um operador de consulta em uma expressão de consulta.</span><span class="sxs-lookup"><span data-stu-id="d4796-210">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="d4796-211">Ao definir uma operação personalizada, você deve definir o yield e os métodos na expressão de computação.</span><span class="sxs-lookup"><span data-stu-id="d4796-211">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="d4796-212">Para definir uma operação personalizada, coloque-a em uma classe de construtor para a expressão de computação e aplique [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)o.</span><span class="sxs-lookup"><span data-stu-id="d4796-212">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="d4796-213">Esse atributo usa uma cadeia de caracteres como um argumento, que é o nome a ser usado em uma operação personalizada.</span><span class="sxs-lookup"><span data-stu-id="d4796-213">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="d4796-214">Esse nome entra no escopo no início da chave de computação da expressão de cálculo.</span><span class="sxs-lookup"><span data-stu-id="d4796-214">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="d4796-215">Portanto, você não deve usar identificadores que têm o mesmo nome que uma operação personalizada neste bloco.</span><span class="sxs-lookup"><span data-stu-id="d4796-215">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="d4796-216">Por exemplo, evite o uso de identificadores como `all` ou `last` em expressões de consulta.</span><span class="sxs-lookup"><span data-stu-id="d4796-216">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="d4796-217">Estendendo construtores existentes com novas operações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d4796-217">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="d4796-218">Se você já tiver uma classe de construtor, suas operações personalizadas poderão ser estendidas de fora dessa classe do construtor.</span><span class="sxs-lookup"><span data-stu-id="d4796-218">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="d4796-219">As extensões devem ser declaradas em módulos.</span><span class="sxs-lookup"><span data-stu-id="d4796-219">Extensions must be declared in modules.</span></span> <span data-ttu-id="d4796-220">Os namespaces não podem conter membros de extensão, exceto no mesmo arquivo e no mesmo grupo de declarações de namespace em que o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="d4796-220">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="d4796-221">O exemplo a seguir mostra a extensão da classe `Microsoft.FSharp.Linq.QueryBuilder` existente.</span><span class="sxs-lookup"><span data-stu-id="d4796-221">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="d4796-222">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4796-222">See also</span></span>

- [<span data-ttu-id="d4796-223">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="d4796-223">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d4796-224">Fluxos de Trabalho Assíncronos</span><span class="sxs-lookup"><span data-stu-id="d4796-224">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="d4796-225">Sequências</span><span class="sxs-lookup"><span data-stu-id="d4796-225">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="d4796-226">Expressões de Consulta</span><span class="sxs-lookup"><span data-stu-id="d4796-226">Query Expressions</span></span>](query-expressions.md)

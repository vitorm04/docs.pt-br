---
title: 'Funções recursivas: a palavra-chave rec'
description: "Saiba como a palavra-chave ' Rec ' do F # é usada com a palavra-chave ' Let ' para definir uma função recursiva."
ms.date: 08/12/2020
ms.openlocfilehash: 389357bd13cef39b1d07972c1a3167320b61612b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558706"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="9919d-103">Funções recursivas: a palavra-chave rec</span><span class="sxs-lookup"><span data-stu-id="9919d-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="9919d-104">A `rec` palavra-chave é usada junto com a `let` palavra-chave para definir uma função recursiva.</span><span class="sxs-lookup"><span data-stu-id="9919d-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="9919d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9919d-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="9919d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9919d-106">Remarks</span></span>

<span data-ttu-id="9919d-107">Funções recursivas – funções que chamam a si mesmas – são identificadas explicitamente na linguagem F # com a `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9919d-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="9919d-108">A `rec` palavra-chave torna o nome da `let` associação disponível em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="9919d-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="9919d-109">O exemplo a seguir mostra uma função recursiva que computa o número *n*<sup>th</sup> Fibonacci usando a definição matemática.</span><span class="sxs-lookup"><span data-stu-id="9919d-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="9919d-110">Na prática, um código como o exemplo anterior não é ideal porque ele unecessarily Recomputa os valores que já foram computados.</span><span class="sxs-lookup"><span data-stu-id="9919d-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="9919d-111">Isso ocorre porque não é a cauda recursiva, o que é explicado mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="9919d-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="9919d-112">Os métodos são recursivos implicitamente dentro do tipo em que são definidos, o que significa que não há necessidade de adicionar a `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9919d-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="9919d-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9919d-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="9919d-114">No entanto, permitir associações dentro de classes não é implicitamente recursivo.</span><span class="sxs-lookup"><span data-stu-id="9919d-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="9919d-115">Todas as `let` funções associadas exigem a `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9919d-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="9919d-116">Recursão final</span><span class="sxs-lookup"><span data-stu-id="9919d-116">Tail recursion</span></span>

<span data-ttu-id="9919d-117">Para algumas funções recursivas, é necessário refatorar uma definição mais "pura" para uma que seja a [cauda recursiva](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="9919d-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="9919d-118">Isso impede recálculos desnecessários.</span><span class="sxs-lookup"><span data-stu-id="9919d-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="9919d-119">Por exemplo, o gerador de número de Fibonacci anterior pode ser reescrito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9919d-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="9919d-120">Essa é uma implementação mais complicada.</span><span class="sxs-lookup"><span data-stu-id="9919d-120">This is a more complicated implementation.</span></span> <span data-ttu-id="9919d-121">Gerar um número Fibonacci é um ótimo exemplo de um algoritmo "simples", que é matematicamente puro, mas ineficiente na prática.</span><span class="sxs-lookup"><span data-stu-id="9919d-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="9919d-122">Vários aspectos o tornam eficiente em F # enquanto ainda restam definidos recursivamente:</span><span class="sxs-lookup"><span data-stu-id="9919d-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="9919d-123">Uma função interna recursiva chamada `loop` , que é um padrão idiomática F #.</span><span class="sxs-lookup"><span data-stu-id="9919d-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="9919d-124">Dois parâmetros de acumulador, que passam valores de acumulação para chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="9919d-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="9919d-125">Uma verificação no valor de `n` para retornar uma acumulação específica.</span><span class="sxs-lookup"><span data-stu-id="9919d-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="9919d-126">Se este exemplo tiver sido escrito iterativamente com um loop, o código seria semelhante com dois valores diferentes acumulando números até que uma determinada condição fosse atendida.</span><span class="sxs-lookup"><span data-stu-id="9919d-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="9919d-127">O motivo pelo qual isso é a cauda-recursiva é porque a chamada recursiva não precisa salvar nenhum valor na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="9919d-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="9919d-128">Todos os valores intermediários que estão sendo calculados são acumulados por meio de entradas para a função interna.</span><span class="sxs-lookup"><span data-stu-id="9919d-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="9919d-129">Isso também permite que o compilador F # Otimize o código para ser tão rápido quanto se você tivesse escrito algo como um `while` loop.</span><span class="sxs-lookup"><span data-stu-id="9919d-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="9919d-130">É comum escrever código F # que processa recursivamente algo com uma função interna e externa, como mostra o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="9919d-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="9919d-131">A função interna usa a recursão de cauda, enquanto a função externa tem uma interface melhor para chamadores.</span><span class="sxs-lookup"><span data-stu-id="9919d-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="9919d-132">Funções recursivas mutuamente</span><span class="sxs-lookup"><span data-stu-id="9919d-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="9919d-133">Às vezes, as funções são *recursivas mutuamente*, o que significa que as chamadas formam um círculo, em que uma função chama outra que, por sua vez, chama a primeira, com qualquer número de chamadas entre elas.</span><span class="sxs-lookup"><span data-stu-id="9919d-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="9919d-134">Você deve definir essas funções juntas em uma `let` associação, usando a `and` palavra-chave para vinculá-las.</span><span class="sxs-lookup"><span data-stu-id="9919d-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="9919d-135">O exemplo a seguir mostra duas funções recursivas mutuamente.</span><span class="sxs-lookup"><span data-stu-id="9919d-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="9919d-136">Valores recursivos</span><span class="sxs-lookup"><span data-stu-id="9919d-136">Recursive values</span></span>

<span data-ttu-id="9919d-137">Você também pode definir um `let` valor associado a ser recursivo.</span><span class="sxs-lookup"><span data-stu-id="9919d-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="9919d-138">Isso às vezes é feito para registro em log.</span><span class="sxs-lookup"><span data-stu-id="9919d-138">This is sometimes done for logging.</span></span> <span data-ttu-id="9919d-139">Com o F # 5 e a `nameof` função, você pode fazer isso:</span><span class="sxs-lookup"><span data-stu-id="9919d-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="9919d-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="9919d-140">See also</span></span>

- [<span data-ttu-id="9919d-141">Funções</span><span class="sxs-lookup"><span data-stu-id="9919d-141">Functions</span></span>](index.md)

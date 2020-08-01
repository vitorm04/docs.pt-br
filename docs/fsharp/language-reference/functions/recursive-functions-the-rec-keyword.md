---
title: 'Funções recursivas: a palavra-chave rec'
description: "Saiba como a palavra-chave ' Rec ' do F # é usada com a palavra-chave ' Let ' para definir uma função recursiva."
ms.date: 05/16/2016
ms.openlocfilehash: c2374f90b4585327c6f5208a3d6bca75a23d0cbb
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455651"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="1ea28-103">Funções recursivas: a palavra-chave rec</span><span class="sxs-lookup"><span data-stu-id="1ea28-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="1ea28-104">A `rec` palavra-chave é usada junto com a `let` palavra-chave para definir uma função recursiva.</span><span class="sxs-lookup"><span data-stu-id="1ea28-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ea28-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1ea28-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="1ea28-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1ea28-106">Remarks</span></span>

<span data-ttu-id="1ea28-107">Funções recursivas, funções que chamam a si mesmas, são identificadas explicitamente na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="1ea28-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="1ea28-108">Isso torna o identificador que está sendo definido disponível no escopo da função.</span><span class="sxs-lookup"><span data-stu-id="1ea28-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="1ea28-109">O código a seguir ilustra uma função recursiva que computa o número *n*<sup>th</sup> Fibonacci usando a definição matemática.</span><span class="sxs-lookup"><span data-stu-id="1ea28-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="1ea28-110">Na prática, um código como o exemplo anterior não é ideal porque ele unecessarily Recomputa os valores que já foram computados.</span><span class="sxs-lookup"><span data-stu-id="1ea28-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="1ea28-111">Isso ocorre porque não é a cauda recursiva, o que é explicado mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="1ea28-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="1ea28-112">Os métodos são recursivos implicitamente dentro do tipo; Não é necessário adicionar a `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1ea28-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="1ea28-113">Permitir que associações dentro de classes não sejam recursivas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="1ea28-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="1ea28-114">Recursão final</span><span class="sxs-lookup"><span data-stu-id="1ea28-114">Tail recursion</span></span>

<span data-ttu-id="1ea28-115">Para algumas funções recursivas, é necessário refatorar uma definição mais "pura" para uma que seja a [cauda recursiva](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="1ea28-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="1ea28-116">Isso impede recálculos desnecessários.</span><span class="sxs-lookup"><span data-stu-id="1ea28-116">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="1ea28-117">Por exemplo, o gerador de número de Fibonacci anterior pode ser reescrito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1ea28-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

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

<span data-ttu-id="1ea28-118">Essa é uma implementação mais complicada.</span><span class="sxs-lookup"><span data-stu-id="1ea28-118">This is a more complicated implementation.</span></span> <span data-ttu-id="1ea28-119">Gerar um número Fibonacci é um ótimo exemplo de um algoritmo "simples", que é matematicamente puro, mas ineficiente na prática.</span><span class="sxs-lookup"><span data-stu-id="1ea28-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="1ea28-120">Vários aspectos o tornam eficiente em F # enquanto ainda restam definidos recursivamente:</span><span class="sxs-lookup"><span data-stu-id="1ea28-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="1ea28-121">Uma função interna recursiva chamada `loop` , que é um padrão idiomática F #.</span><span class="sxs-lookup"><span data-stu-id="1ea28-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="1ea28-122">Dois parâmetros de acumulador, que passam valores de acumulação para chamadas recursivas.</span><span class="sxs-lookup"><span data-stu-id="1ea28-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="1ea28-123">Uma verificação no valor de `n` para retornar uma acumulação específica.</span><span class="sxs-lookup"><span data-stu-id="1ea28-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="1ea28-124">Se este exemplo tiver sido escrito iterativamente com um loop, o código seria semelhante com dois valores diferentes acumulando números até que uma determinada condição fosse atendida.</span><span class="sxs-lookup"><span data-stu-id="1ea28-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="1ea28-125">O motivo pelo qual isso é a cauda-recursiva é porque a chamada recursiva não precisa salvar nenhum valor na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="1ea28-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="1ea28-126">Todos os valores intermediários que estão sendo calculados são acumulados por meio de entradas para a função interna.</span><span class="sxs-lookup"><span data-stu-id="1ea28-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="1ea28-127">Isso também permite que o compilador F # Otimize o código para ser tão rápido quanto se você tivesse escrito algo como um `while` loop.</span><span class="sxs-lookup"><span data-stu-id="1ea28-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="1ea28-128">É comum escrever código F # que processa recursivamente algo com uma função interna e externa, como mostra o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1ea28-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="1ea28-129">A função interna usa a recursão de cauda, enquanto a função externa tem uma interface melhor para chamadores.</span><span class="sxs-lookup"><span data-stu-id="1ea28-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="1ea28-130">Funções recursivas mutuamente</span><span class="sxs-lookup"><span data-stu-id="1ea28-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="1ea28-131">Às vezes, as funções são *recursivas mutuamente*, o que significa que as chamadas formam um círculo, em que uma função chama outra que, por sua vez, chama a primeira, com qualquer número de chamadas entre elas.</span><span class="sxs-lookup"><span data-stu-id="1ea28-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="1ea28-132">Você deve definir essas funções juntas em uma `let` associação, usando a `and` palavra-chave para vinculá-las.</span><span class="sxs-lookup"><span data-stu-id="1ea28-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="1ea28-133">O exemplo a seguir mostra duas funções recursivas mutuamente.</span><span class="sxs-lookup"><span data-stu-id="1ea28-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="1ea28-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="1ea28-134">See also</span></span>

- [<span data-ttu-id="1ea28-135">Funções</span><span class="sxs-lookup"><span data-stu-id="1ea28-135">Functions</span></span>](index.md)

---
title: O que é F#
description: 'Saiba mais sobre o que é a linguagem de programação F # e qual é a programação em F #. Saiba mais sobre tipos de dados avançados, funções e como eles se encaixam juntos.'
ms.date: 08/03/2018
ms.openlocfilehash: 37dc2f472d65a046e4bf67e672e2a96f4d4afded
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439645"
---
# <a name="what-is-f"></a><span data-ttu-id="b6c70-104">O que é F\#</span><span class="sxs-lookup"><span data-stu-id="b6c70-104">What is F\#</span></span>

<span data-ttu-id="b6c70-105">O F # é uma linguagem de programação funcional que torna mais fácil escrever código correto e passível de manutenção.</span><span class="sxs-lookup"><span data-stu-id="b6c70-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="b6c70-106">A programação F # envolve principalmente a definição de tipos e funções que são de tipo inferido e generalizados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b6c70-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="b6c70-107">Isso permite que seu foco permaneça no domínio problemático e manipule seus dados, em vez dos detalhes da programação.</span><span class="sxs-lookup"><span data-stu-id="b6c70-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

<span data-ttu-id="b6c70-108">O F # tem vários recursos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="b6c70-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="b6c70-109">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="b6c70-109">Lightweight syntax</span></span>
* <span data-ttu-id="b6c70-110">Imutável por padrão</span><span class="sxs-lookup"><span data-stu-id="b6c70-110">Immutable by default</span></span>
* <span data-ttu-id="b6c70-111">Inferência de tipos e generalização automática</span><span class="sxs-lookup"><span data-stu-id="b6c70-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="b6c70-112">Funções de primeira classe</span><span class="sxs-lookup"><span data-stu-id="b6c70-112">First-class functions</span></span>
* <span data-ttu-id="b6c70-113">Tipos de dados avançados</span><span class="sxs-lookup"><span data-stu-id="b6c70-113">Powerful data types</span></span>
* <span data-ttu-id="b6c70-114">Correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="b6c70-114">Pattern matching</span></span>
* <span data-ttu-id="b6c70-115">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="b6c70-115">Async programming</span></span>

<span data-ttu-id="b6c70-116">Um conjunto completo de recursos está documentado na [referência de linguagem F #](./language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="b6c70-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="b6c70-117">Tipos de dados avançados</span><span class="sxs-lookup"><span data-stu-id="b6c70-117">Rich data types</span></span>

<span data-ttu-id="b6c70-118">Tipos de dados como [registros](./language-reference/records.md) e [uniões discriminadas](./language-reference/discriminated-unions.md) permitem que você represente domínios e dados complexos.</span><span class="sxs-lookup"><span data-stu-id="b6c70-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

<span data-ttu-id="b6c70-119">Os registros F # e as uniões discriminadas são não nulos, imutáveis e comparáveis por padrão, tornando-os muito fáceis de usar.</span><span class="sxs-lookup"><span data-stu-id="b6c70-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="b6c70-120">Correção imposta com funções e correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="b6c70-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="b6c70-121">As funções de F # são fáceis de declarar e poderosas na prática.</span><span class="sxs-lookup"><span data-stu-id="b6c70-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="b6c70-122">Quando combinado com [correspondência de padrões](./language-reference/pattern-matching.md), eles permitem que você defina o comportamento cuja exatidão é imposta pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="b6c70-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

<span data-ttu-id="b6c70-123">As funções F # também são de primeira classe, o que significa que elas podem ser passadas como parâmetros e retornadas de outras funções.</span><span class="sxs-lookup"><span data-stu-id="b6c70-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="b6c70-124">Funções para definir operações em objetos</span><span class="sxs-lookup"><span data-stu-id="b6c70-124">Functions to define operations on objects</span></span>

<span data-ttu-id="b6c70-125">O F # tem suporte total para objetos, que são tipos de dados úteis quando você precisa misturar dados e funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b6c70-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="b6c70-126">As funções F # são usadas para manipular objetos.</span><span class="sxs-lookup"><span data-stu-id="b6c70-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="b6c70-127">Em vez de escrever código orientado a objeto, em F #, você geralmente escreverá um código que trata os objetos como outro tipo de dados para funções a serem manipuladas.</span><span class="sxs-lookup"><span data-stu-id="b6c70-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="b6c70-128">Recursos como [interfaces genéricas](./language-reference/interfaces.md), [expressões de objeto](./language-reference/object-expressions.md)e uso criterioso de [Membros](./language-reference/members/index.md) são comuns em programas em F # maiores.</span><span class="sxs-lookup"><span data-stu-id="b6c70-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6c70-129">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b6c70-129">Next steps</span></span>

<span data-ttu-id="b6c70-130">Para saber mais sobre um conjunto maior de recursos do F #, confira o [Tour em f #](tour.md).</span><span class="sxs-lookup"><span data-stu-id="b6c70-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>

---
title: 'O que é o F #'
description: 'Saiba mais sobre o que o F # é linguagem de programação e o que é a programação em F # como. Saiba mais sobre tipos de dados avançados, funções e como elas se encaixam.'
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564558"
---
# <a name="what-is-f"></a><span data-ttu-id="ec691-104">O que é o F #</span><span class="sxs-lookup"><span data-stu-id="ec691-104">What is F#</span></span> #

<span data-ttu-id="ec691-105">F # é uma linguagem de programação funcional que torna mais fácil escrever código correto e sustentável.</span><span class="sxs-lookup"><span data-stu-id="ec691-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="ec691-106">Programação em F # envolve principalmente a definição de tipos e funções que são de tipo inferido e generalizadas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ec691-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="ec691-107">Isso permite que o foco permaneça no domínio do problema e manipular seus dados, em vez dos detalhes de programação.</span><span class="sxs-lookup"><span data-stu-id="ec691-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

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

<span data-ttu-id="ec691-108">F # tem inúmeros recursos, incluindo:</span><span class="sxs-lookup"><span data-stu-id="ec691-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="ec691-109">Sintaxe leve</span><span class="sxs-lookup"><span data-stu-id="ec691-109">Lightweight syntax</span></span>
* <span data-ttu-id="ec691-110">Imutável por padrão</span><span class="sxs-lookup"><span data-stu-id="ec691-110">Immutable by default</span></span>
* <span data-ttu-id="ec691-111">Inferência de tipo e a generalização automática</span><span class="sxs-lookup"><span data-stu-id="ec691-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="ec691-112">Funções de primeira classe</span><span class="sxs-lookup"><span data-stu-id="ec691-112">First-class functions</span></span>
* <span data-ttu-id="ec691-113">Tipos de dados avançados</span><span class="sxs-lookup"><span data-stu-id="ec691-113">Powerful data types</span></span>
* <span data-ttu-id="ec691-114">Correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="ec691-114">Pattern matching</span></span>
* <span data-ttu-id="ec691-115">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="ec691-115">Async programming</span></span>

<span data-ttu-id="ec691-116">Um conjunto completo de recursos estão documentados a [referência da linguagem F #](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec691-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="ec691-117">Tipos de dados avançados</span><span class="sxs-lookup"><span data-stu-id="ec691-117">Rich data types</span></span>

<span data-ttu-id="ec691-118">Tipos de dados, como [registros](language-reference/records.md) e [uniões discriminadas](language-reference/discriminated-unions.md) permitem que você representar dados complexos e domínios.</span><span class="sxs-lookup"><span data-stu-id="ec691-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="ec691-119">Registros do F # e uniões discriminadas são não-nulo, imutável e comparável por padrão, o que torna muito fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="ec691-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="ec691-120">Correção de imposto com correspondência de padrões e funções</span><span class="sxs-lookup"><span data-stu-id="ec691-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="ec691-121">Funções de F # são fácil de declarar e avançadas na prática.</span><span class="sxs-lookup"><span data-stu-id="ec691-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="ec691-122">Quando combinado com [correspondência de padrões](language-reference/pattern-matching.md), eles permitem que você defina o comportamento cuja correção é imposta pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="ec691-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="ec691-123">Funções de F # também são de primeira classe, que significa que eles podem ser passados como parâmetros e retornados de outras funções.</span><span class="sxs-lookup"><span data-stu-id="ec691-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="ec691-124">Funções para definir as operações em objetos</span><span class="sxs-lookup"><span data-stu-id="ec691-124">Functions to define operations on objects</span></span>

<span data-ttu-id="ec691-125">F # tem suporte completo para objetos que são tipos de dados úteis quando você precisa combinar dados e funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="ec691-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="ec691-126">Funções de F # são usadas para manipular objetos.</span><span class="sxs-lookup"><span data-stu-id="ec691-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="ec691-127">Em vez de escrever código que é orientada a objeto, em F #, você irá geralmente escrever código que trata objetos como outro tipo de dados para as funções para manipular.</span><span class="sxs-lookup"><span data-stu-id="ec691-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="ec691-128">Recursos como [interfaces genéricas](language-reference/interfaces.md), [expressões de objeto](language-reference/object-expressions.md)e uso criterioso de [membros](language-reference/members/index.md) são comuns em F # programas maiores.</span><span class="sxs-lookup"><span data-stu-id="ec691-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec691-129">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ec691-129">Next steps</span></span>

<span data-ttu-id="ec691-130">Para saber mais sobre um conjunto maior de recursos do F #, confira a [Tour do F #](tour.md).</span><span class="sxs-lookup"><span data-stu-id="ec691-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
---
title: O que é o F#
description: Saiba mais sobre o que o F# é linguagem de programação e o que é a programação em F# como. Saiba mais sobre tipos de dados avançados, funções e como elas se encaixam.
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863290"
---
# <a name="what-is-f"></a>O que é o F# #

F# é uma linguagem de programação funcional que torna mais fácil escrever código correto e sustentável.

Programação em F# envolve principalmente a definição de tipos e funções que são de tipo inferido e generalizadas automaticamente. Isso permite que o foco permaneça no domínio do problema e manipular seus dados, em vez dos detalhes de programação.

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

F# tem inúmeros recursos, incluindo:

* Sintaxe leve
* Imutável por padrão
* Inferência de tipo e a generalização automática
* Funções de primeira classe
* Tipos de dados avançados
* Correspondência de padrões
* Programação assíncrona

Um conjunto completo de recursos estão documentados a [referência da linguagem F#](language-reference/index.md).

## <a name="rich-data-types"></a>Tipos de dados avançados

Tipos de dados, como [registros](language-reference/records.md) e [uniões discriminadas](language-reference/discriminated-unions.md) permitem que você representar dados complexos e domínios.

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

Registros do F# e uniões discriminadas são não-nulo, imutável e comparável por padrão, o que torna muito fácil de usar.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Correção de imposto com correspondência de padrões e funções

Funções de F# são fácil de declarar e avançadas na prática. Quando combinado com [correspondência de padrões](language-reference/pattern-matching.md), eles permitem que você defina o comportamento cuja correção é imposta pelo compilador.

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

Funções de F# também são de primeira classe, que significa que eles podem ser passados como parâmetros e retornados de outras funções.

## <a name="functions-to-define-operations-on-objects"></a>Funções para definir as operações em objetos

F# tem suporte completo para objetos que são tipos de dados úteis quando você precisa combinar dados e funcionalidade. Funções de F# são usadas para manipular objetos.

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

Em vez de escrever código que é orientada a objeto, em F#, você irá geralmente escrever código que trata objetos como outro tipo de dados para as funções para manipular. Recursos como [interfaces genéricas](language-reference/interfaces.md), [expressões de objeto](language-reference/object-expressions.md)e uso criterioso de [membros](language-reference/members/index.md) são comuns em F# programas maiores.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre um conjunto maior de recursos do F#, confira a [Tour do F#](tour.md).
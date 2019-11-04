---
title: Resultados
description: Saiba como usar o F# tipo ' Result ' para ajudá-lo a escrever código tolerante a erros.
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424848"
---
# <a name="results"></a>Resultados

A partir F# do 4,1, há um tipo de `Result<'T,'TFailure>` que você pode usar para escrever código tolerante a erros que pode ser composto.

## <a name="syntax"></a>Sintaxe

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Comentários

Observe que o tipo de resultado é uma [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions), que é outro recurso F# introduzido em 4,1.  A semântica de igualdade estrutural se aplica aqui.

O tipo de `Result` normalmente é usado no tratamento de erros monadic, que é geralmente chamado de [programação orientada por ferrovia](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) na F# comunidade.  O exemplo trivial a seguir demonstra essa abordagem.

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

Como você pode ver, é muito fácil encadear várias funções de validação se você forçá-las a retornar um `Result`.  Isso permite que você divida a funcionalidade como esta em pequenas partes, que são tão combináveis quanto você precisa delas.  Isso também tem o valor agregado de *impor* o uso da [correspondência de padrões](pattern-matching.md) no final de uma rodada de validação, o que, por sua vez, impõe um grau mais alto de exatidão do programa.

## <a name="see-also"></a>Consulte também

- [Uniões Discriminadas](discriminated-unions.md)
- [Correspondência Padrão](pattern-matching.md)

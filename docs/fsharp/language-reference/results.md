---
title: 'Resultados (F #)'
description: "Saiba como usar o tipo F # 'Resultado' para ajudá-lo a escrever código tolerante a erros."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: 26478ccfbf88d43c0b194e77d9aacc313515283f
ms.sourcegitcommit: 8d14e8c1b15009330c9880f8523686158924e1a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2017
---
# <a name="results"></a><span data-ttu-id="b0be8-104">Resultados</span><span class="sxs-lookup"><span data-stu-id="b0be8-104">Results</span></span>

<span data-ttu-id="b0be8-105">A partir do F # 4.1, há um `Result<'T,'TFailure>` tipo que você pode usar para escrever código tolerante a erros que pode ser composto.</span><span class="sxs-lookup"><span data-stu-id="b0be8-105">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0be8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0be8-106">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="b0be8-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0be8-107">Remarks</span></span>

<span data-ttu-id="b0be8-108">Observe que o tipo de resultado é um [struct discriminada union](discriminated-unions.md#struct-discriminated-unions), que é outro recurso introduzido no F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="b0be8-108">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="b0be8-109">Semântica de igualdade estrutural se aplicam aqui.</span><span class="sxs-lookup"><span data-stu-id="b0be8-109">Structural equality semantics apply here.</span></span>

<span data-ttu-id="b0be8-110">O `Result` tipo é usado normalmente em monadic tratamento de erros, que é conhecido como [programação orientada a estrada de ferro](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) dentro da comunidade do F #.</span><span class="sxs-lookup"><span data-stu-id="b0be8-110">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="b0be8-111">O exemplo simples a seguir demonstra essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="b0be8-111">The following trivial example demonstrates this approach.</span></span>

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
    | String.Empty -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | String.Empty -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> OK req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (OK req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints " "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (OK req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="b0be8-112">Como você pode ver, é muito fácil unir várias funções de validação se você forçá-los todos para retornar um `Result`.</span><span class="sxs-lookup"><span data-stu-id="b0be8-112">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="b0be8-113">Isso permite que você dividir a funcionalidade desta em pequenas partes que são como Combinável conforme necessário para ser.</span><span class="sxs-lookup"><span data-stu-id="b0be8-113">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="b0be8-114">Isso também tem o valor agregado do *impondo* o uso de [correspondência de padrões](pattern-matching.md) no final de uma sessão de validação, que por sua vez impõe um grau maior de correção do programa.</span><span class="sxs-lookup"><span data-stu-id="b0be8-114">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0be8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0be8-115">See Also</span></span>

[<span data-ttu-id="b0be8-116">Uniões Discriminadas</span><span class="sxs-lookup"><span data-stu-id="b0be8-116">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="b0be8-117">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="b0be8-117">Pattern Matching</span></span>](pattern-matching.md)

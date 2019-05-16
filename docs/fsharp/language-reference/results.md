---
title: Resultados
description: Saiba como usar o F# 'Result' de tipo para ajudá-lo a escrever código tolerante a erros.
ms.date: 04/24/2017
ms.openlocfilehash: 36f60df8a2991c1d318e4921af6c9e89a0156918
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645317"
---
# <a name="results"></a><span data-ttu-id="43a3e-103">Resultados</span><span class="sxs-lookup"><span data-stu-id="43a3e-103">Results</span></span>

<span data-ttu-id="43a3e-104">Começando com F# 4.1, há uma `Result<'T,'TFailure>` tipo de que você pode usar para escrever código tolerante a erros que pode ser composto.</span><span class="sxs-lookup"><span data-stu-id="43a3e-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="43a3e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43a3e-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="43a3e-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="43a3e-106">Remarks</span></span>

<span data-ttu-id="43a3e-107">Observe que o tipo de resultado é um [união discriminada de struct](discriminated-unions.md#struct-discriminated-unions), que é outro recurso introduzido no F# 4.1.</span><span class="sxs-lookup"><span data-stu-id="43a3e-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="43a3e-108">Semântica de igualdade estrutural se aplicam aqui.</span><span class="sxs-lookup"><span data-stu-id="43a3e-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="43a3e-109">O `Result` tipo normalmente é usado em monadic tratamento de erros, que geralmente é conhecido como [programação orientada a ferrovia](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) dentro de F# comunidade.</span><span class="sxs-lookup"><span data-stu-id="43a3e-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="43a3e-110">O exemplo simples a seguir demonstra essa abordagem.</span><span class="sxs-lookup"><span data-stu-id="43a3e-110">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="43a3e-111">Como você pode ver, é muito fácil encadear várias funções de validação se você forçá-los para retornar um `Result`.</span><span class="sxs-lookup"><span data-stu-id="43a3e-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="43a3e-112">Isso permite a você dividir a funcionalidade como este em pequenas partes que são tão Combinável sempre que precisar ser.</span><span class="sxs-lookup"><span data-stu-id="43a3e-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="43a3e-113">Isso também tem o valor agregado do *impondo* o uso de [correspondência de padrões](pattern-matching.md) no final de uma rodada de validação, que impõe um grau maior de correção do programa.</span><span class="sxs-lookup"><span data-stu-id="43a3e-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="43a3e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43a3e-114">See also</span></span>

- [<span data-ttu-id="43a3e-115">Uniões Discriminadas</span><span class="sxs-lookup"><span data-stu-id="43a3e-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="43a3e-116">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="43a3e-116">Pattern Matching</span></span>](pattern-matching.md)

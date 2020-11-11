---
title: 'O que há de novo no guia F # 5,0-F #'
description: 'Obtenha uma visão geral dos novos recursos disponíveis em F # 5,0.'
ms.date: 11/06/2020
ms.openlocfilehash: 0c4c9f42c63a1dc8c90213c43edbadd4061c132d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445825"
---
# <a name="whats-new-in-f-50"></a><span data-ttu-id="d7a71-103">O que há de novo no F # 5,0</span><span class="sxs-lookup"><span data-stu-id="d7a71-103">What's new in F# 5.0</span></span>

<span data-ttu-id="d7a71-104">O f # 5,0 adiciona várias melhorias à linguagem F # e à F# Interativo.</span><span class="sxs-lookup"><span data-stu-id="d7a71-104">F# 5.0 adds several improvements to the F# language and F# Interactive.</span></span> <span data-ttu-id="d7a71-105">Ele é lançado com o **.NET 5**.</span><span class="sxs-lookup"><span data-stu-id="d7a71-105">It is released with **.NET 5**.</span></span>

## <a name="get-started"></a><span data-ttu-id="d7a71-106">Introdução</span><span class="sxs-lookup"><span data-stu-id="d7a71-106">Get started</span></span>

<span data-ttu-id="d7a71-107">O F # 5,0 está disponível em todas as distribuições do .NET Core e ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d7a71-107">F# 5.0 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="d7a71-108">Para obter mais informações, consulte Introdução ao [F #](../get-started/index.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="d7a71-108">For more information, see [Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="package-references-in-f-scripts"></a><span data-ttu-id="d7a71-109">Referências de pacote em scripts F #</span><span class="sxs-lookup"><span data-stu-id="d7a71-109">Package references in F# scripts</span></span>

<span data-ttu-id="d7a71-110">O F # 5 traz suporte para referências de pacote em scripts F # com `#r "nuget:..."` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="d7a71-110">F# 5 brings support for package references in F# scripts with `#r "nuget:..."` syntax.</span></span> <span data-ttu-id="d7a71-111">Por exemplo, considere a seguinte referência de pacote:</span><span class="sxs-lookup"><span data-stu-id="d7a71-111">For example, consider the following package reference:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn "%s" (JsonConvert.SerializeObject o)
```

<span data-ttu-id="d7a71-112">Você também pode fornecer uma versão explícita após o nome do pacote como este:</span><span class="sxs-lookup"><span data-stu-id="d7a71-112">You can also supply an explicit version after the name of the package like this:</span></span>

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

<span data-ttu-id="d7a71-113">As referências de pacote dão suporte a pacotes com dependências nativas, como ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d7a71-113">Package references support packages with native dependencies, such as ML.NET.</span></span>

<span data-ttu-id="d7a71-114">As referências de pacote também dão suporte a pacotes com requisitos especiais sobre como referenciar s dependentes `.dll` .</span><span class="sxs-lookup"><span data-stu-id="d7a71-114">Package references also support packages with special requirements about referencing dependent `.dll`s.</span></span> <span data-ttu-id="d7a71-115">Por exemplo, o pacote [FParsec](https://www.nuget.org/packages/FParsec/) usado para exigir que os usuários verifiquem manualmente se seu dependente foi referenciado `FParsecCS.dll` primeiro antes `FParsec.dll` de foi referenciado no F# interativo.</span><span class="sxs-lookup"><span data-stu-id="d7a71-115">For example, the [FParsec](https://www.nuget.org/packages/FParsec/) package used to require that users manually ensure that its dependent `FParsecCS.dll` was referenced first before `FParsec.dll` was referenced in F# Interactive.</span></span> <span data-ttu-id="d7a71-116">Isso não é mais necessário e você pode fazer referência ao pacote da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d7a71-116">This is no longer needed, and you can reference the package as follows:</span></span>

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn "Success: %A" result
    | Failure(errorMsg, _, _) -> printfn "Failure: %s" errorMsg

test pfloat "1.234"
```

<span data-ttu-id="d7a71-117">Para obter mais informações sobre referências de pacote, consulte o tutorial de [F# interativo](../tutorials/fsharp-interactive/index.md) .</span><span class="sxs-lookup"><span data-stu-id="d7a71-117">For more information on package references, see the [F# Interactive](../tutorials/fsharp-interactive/index.md) tutorial.</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="d7a71-118">Interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d7a71-118">String interpolation</span></span>

<span data-ttu-id="d7a71-119">As cadeias de caracteres interpoladas em F # são bastante semelhantes às cadeias de caracteres interpoladas em C# ou JavaScript, pois permitem escrever código em "buracos" dentro de um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d7a71-119">F# interpolated strings are fairly similar to C# or JavaScript interpolated strings, in that they let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="d7a71-120">Este é um exemplo básico:</span><span class="sxs-lookup"><span data-stu-id="d7a71-120">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="d7a71-121">No entanto, as cadeias de caracteres interpoladas em F # também permitem interpolações com tipo, assim como a `sprintf` função, para impor que uma expressão dentro de um contexto interpolado esteja em conformidade com um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="d7a71-121">However, F# interpolated strings also allow for typed interpolations, just like the `sprintf` function, to enforce that an expression inside of an interpolated context conforms to a particular type.</span></span> <span data-ttu-id="d7a71-122">Ele usa os mesmos especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="d7a71-122">It uses the same format specifiers.</span></span>

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="d7a71-123">No exemplo de interpolação de tipo anterior, o `%s` requer que a interpolação seja do Type `string` , enquanto o `%d` requer que a interpolação seja um `integer` .</span><span class="sxs-lookup"><span data-stu-id="d7a71-123">In the preceding typed interpolation example, the `%s` requires the interpolation to be of type `string`, whereas the `%d` requires the interpolation to be an `integer`.</span></span>

<span data-ttu-id="d7a71-124">Além disso, qualquer expressão F # arbitrária (ou expressões) pode ser colocada no lado de um contexto de interpolação.</span><span class="sxs-lookup"><span data-stu-id="d7a71-124">Additionally, any arbitrary F# expression (or expressions) can be placed in side of an interpolation context.</span></span> <span data-ttu-id="d7a71-125">É possível, até mesmo, escrever uma expressão mais complicada, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d7a71-125">It is even possible to write a more complicated expression, like so:</span></span>

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

<span data-ttu-id="d7a71-126">Embora não seja recomendável fazer isso muito na prática.</span><span class="sxs-lookup"><span data-stu-id="d7a71-126">Although we don't recommend doing this too much in practice.</span></span>

## <a name="support-for-nameof"></a><span data-ttu-id="d7a71-127">Suporte para nameof</span><span class="sxs-lookup"><span data-stu-id="d7a71-127">Support for nameof</span></span>

<span data-ttu-id="d7a71-128">O F # 5 dá suporte ao `nameof` operador, que resolve o símbolo que está sendo usado e produz seu nome na fonte F #.</span><span class="sxs-lookup"><span data-stu-id="d7a71-128">F# 5 supports the `nameof` operator, which resolves the symbol it's being used for and produces its name in F# source.</span></span> <span data-ttu-id="d7a71-129">Isso é útil em vários cenários, como registro em log e protege o registro em log contra alterações no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d7a71-129">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="d7a71-130">A última linha gerará uma exceção e "month" será mostrada na mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="d7a71-130">The last line will throw an exception and "month" will be shown in the error message.</span></span>

<span data-ttu-id="d7a71-131">Você pode usar um nome de quase todas as construções em F #:</span><span class="sxs-lookup"><span data-stu-id="d7a71-131">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn "%s" (M.f 12)
printfn "%s" (nameof M)
printfn "%s" (nameof M.f)
```

<span data-ttu-id="d7a71-132">Três adições finais são alterações na forma como os operadores funcionam: a adição do `nameof<'type-parameter>` formulário para parâmetros de tipo genérico e a capacidade de usar `nameof` como um padrão em uma expressão de correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="d7a71-132">Three final additions are changes to how operators work: the addition of the `nameof<'type-parameter>` form for generic type parameters, and the ability to use `nameof` as a pattern in a pattern match expression.</span></span>

<span data-ttu-id="d7a71-133">Usar um nome de um operador fornece sua cadeia de caracteres de origem.</span><span class="sxs-lookup"><span data-stu-id="d7a71-133">Taking a name of an operator gives its source string.</span></span> <span data-ttu-id="d7a71-134">Se você precisar do formulário compilado, use o nome compilado de um operador:</span><span class="sxs-lookup"><span data-stu-id="d7a71-134">If you need the compiled form, use the compiled name of an operator:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

<span data-ttu-id="d7a71-135">A obtenção do nome de um parâmetro de tipo requer uma sintaxe ligeiramente diferente:</span><span class="sxs-lookup"><span data-stu-id="d7a71-135">Taking the name of a type parameter requires a slightly different syntax:</span></span>

```fsharp

type C<'TType> =
    member _.TypeName = nameof<'TType>
```

<span data-ttu-id="d7a71-136">Isso é semelhante aos `typeof<'T>` operadores e `typedefof<'T>` .</span><span class="sxs-lookup"><span data-stu-id="d7a71-136">This is similar to the `typeof<'T>` and `typedefof<'T>` operators.</span></span>

<span data-ttu-id="d7a71-137">O F # 5 também adiciona suporte a um `nameof` padrão que pode ser usado em `match` expressões:</span><span class="sxs-lookup"><span data-stu-id="d7a71-137">F# 5 also adds support for a `nameof` pattern that can be used in `match` expressions:</span></span>

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

<span data-ttu-id="d7a71-138">O código anterior usa ' nameof ' em vez do literal de cadeia de caracteres na expressão Match.</span><span class="sxs-lookup"><span data-stu-id="d7a71-138">The preceding code uses 'nameof' instead of the string literal in the match expression.</span></span>

## <a name="open-type-declarations"></a><span data-ttu-id="d7a71-139">Abrir declarações de tipo</span><span class="sxs-lookup"><span data-stu-id="d7a71-139">Open type declarations</span></span>

<span data-ttu-id="d7a71-140">O F # 5 também adiciona suporte para declarações de tipo aberto.</span><span class="sxs-lookup"><span data-stu-id="d7a71-140">F# 5 also adds support for open type declarations.</span></span> <span data-ttu-id="d7a71-141">Uma declaração de tipo aberto é como abrir uma classe estática em C#, exceto com alguma sintaxe diferente e um comportamento ligeiramente diferente para se ajustar à semântica de F #.</span><span class="sxs-lookup"><span data-stu-id="d7a71-141">An open type declaration is like opening a static class in C#, except with some different syntax and some slightly different behavior to fit F# semantics.</span></span>

<span data-ttu-id="d7a71-142">Com declarações de tipo aberto, você pode `open` qualquer tipo para expor conteúdo estático dentro dele.</span><span class="sxs-lookup"><span data-stu-id="d7a71-142">With open type declarations, you can `open` any type to expose static contents inside of it.</span></span> <span data-ttu-id="d7a71-143">Além disso, você pode `open` exibir as uniões e registros definidos em F # para expor seu conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d7a71-143">Additionally, you can `open` F#-defined unions and records to expose their contents.</span></span> <span data-ttu-id="d7a71-144">Por exemplo, isso pode ser útil se você tiver uma União definida em um módulo e desejar acessar seus casos, mas não quiser abrir o módulo inteiro.</span><span class="sxs-lookup"><span data-stu-id="d7a71-144">For example, this can be useful if you have a union defined in a module and want to access its cases, but don't want to open the entire module.</span></span>

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn "%A" A
```

<span data-ttu-id="d7a71-145">Diferentemente do C#, quando você `open type` em dois tipos que expõem um membro com o mesmo nome, o membro do último tipo que está sendo `open` Ed sombreia o outro nome.</span><span class="sxs-lookup"><span data-stu-id="d7a71-145">Unlike C#, when you `open type` on two types that expose a member with the same name, the member from the last type being `open`ed shadows the other name.</span></span> <span data-ttu-id="d7a71-146">Isso é consistente com a semântica F # em relação à sombra que já existe.</span><span class="sxs-lookup"><span data-stu-id="d7a71-146">This is consistent with F# semantics around shadowing that exist already.</span></span>

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a><span data-ttu-id="d7a71-147">Comportamento de divisão consistente para tipos de dados internos</span><span class="sxs-lookup"><span data-stu-id="d7a71-147">Consistent slicing behavior for built-in data types</span></span>

<span data-ttu-id="d7a71-148">Comportamento para dividir os tipos de dados internos `FSharp.Core` (matriz, lista, Cadeia de caracteres, matriz 2D, matriz 3D, matriz 4D) usado para não ser consistente antes do F # 5.</span><span class="sxs-lookup"><span data-stu-id="d7a71-148">Behavior for slicing the built-in `FSharp.Core` data types (array, list, string, 2D array, 3D array, 4D array) used to not be consistent prior to F# 5.</span></span> <span data-ttu-id="d7a71-149">Um comportamento de caso de borda lançou uma exceção e algumas delas.</span><span class="sxs-lookup"><span data-stu-id="d7a71-149">Some edge-case behavior threw an exception and some wouldn't.</span></span> <span data-ttu-id="d7a71-150">No F # 5, todos os tipos internos agora retornam fatias vazias para fatias que são impossíveis de gerar:</span><span class="sxs-lookup"><span data-stu-id="d7a71-150">In F# 5, all built-in types now return empty slices for slices that are impossible to generate:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a><span data-ttu-id="d7a71-151">Fatias de índice fixo para matrizes 3D e 4D no FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="d7a71-151">Fixed-index slices for 3D and 4D arrays in FSharp.Core</span></span>

<span data-ttu-id="d7a71-152">O F # 5,0 oferece suporte para fatiar com um índice fixo nos tipos de matriz 3D e 4D internos.</span><span class="sxs-lookup"><span data-stu-id="d7a71-152">F# 5.0 brings support for slicing with a fixed index in the built-in 3D and 4D array types.</span></span>

<span data-ttu-id="d7a71-153">Para ilustrar isso, considere a seguinte matriz 3D:</span><span class="sxs-lookup"><span data-stu-id="d7a71-153">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="d7a71-154">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="d7a71-154">*z = 0*</span></span>
|<span data-ttu-id="d7a71-155">x\y</span><span class="sxs-lookup"><span data-stu-id="d7a71-155">x\y</span></span>|<span data-ttu-id="d7a71-156">0</span><span class="sxs-lookup"><span data-stu-id="d7a71-156">0</span></span>|<span data-ttu-id="d7a71-157">1</span><span class="sxs-lookup"><span data-stu-id="d7a71-157">1</span></span>|
|---|-|-|
|<span data-ttu-id="d7a71-158">**0**</span><span class="sxs-lookup"><span data-stu-id="d7a71-158">**0**</span></span>|<span data-ttu-id="d7a71-159">0</span><span class="sxs-lookup"><span data-stu-id="d7a71-159">0</span></span>|<span data-ttu-id="d7a71-160">1</span><span class="sxs-lookup"><span data-stu-id="d7a71-160">1</span></span>|
|<span data-ttu-id="d7a71-161">**1**</span><span class="sxs-lookup"><span data-stu-id="d7a71-161">**1**</span></span>|<span data-ttu-id="d7a71-162">2</span><span class="sxs-lookup"><span data-stu-id="d7a71-162">2</span></span>|<span data-ttu-id="d7a71-163">3</span><span class="sxs-lookup"><span data-stu-id="d7a71-163">3</span></span>|

<span data-ttu-id="d7a71-164">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="d7a71-164">*z = 1*</span></span>
|<span data-ttu-id="d7a71-165">x\y</span><span class="sxs-lookup"><span data-stu-id="d7a71-165">x\y</span></span>|<span data-ttu-id="d7a71-166">0</span><span class="sxs-lookup"><span data-stu-id="d7a71-166">0</span></span>|<span data-ttu-id="d7a71-167">1</span><span class="sxs-lookup"><span data-stu-id="d7a71-167">1</span></span>|
|---|-|-|
|<span data-ttu-id="d7a71-168">**0**</span><span class="sxs-lookup"><span data-stu-id="d7a71-168">**0**</span></span>|<span data-ttu-id="d7a71-169">4</span><span class="sxs-lookup"><span data-stu-id="d7a71-169">4</span></span>|<span data-ttu-id="d7a71-170">5</span><span class="sxs-lookup"><span data-stu-id="d7a71-170">5</span></span>|
|<span data-ttu-id="d7a71-171">**1**</span><span class="sxs-lookup"><span data-stu-id="d7a71-171">**1**</span></span>|<span data-ttu-id="d7a71-172">6</span><span class="sxs-lookup"><span data-stu-id="d7a71-172">6</span></span>|<span data-ttu-id="d7a71-173">7</span><span class="sxs-lookup"><span data-stu-id="d7a71-173">7</span></span>|

<span data-ttu-id="d7a71-174">E se você quisesse extrair a fatia `[| 4; 5 |]` da matriz?</span><span class="sxs-lookup"><span data-stu-id="d7a71-174">What if you wanted to extract the slice `[| 4; 5 |]` from the array?</span></span> <span data-ttu-id="d7a71-175">Agora isso é muito simples!</span><span class="sxs-lookup"><span data-stu-id="d7a71-175">This is now very simple!</span></span>

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

## <a name="applicative-computation-expressions"></a><span data-ttu-id="d7a71-176">Expressões de computação Applicative</span><span class="sxs-lookup"><span data-stu-id="d7a71-176">Applicative Computation Expressions</span></span>

<span data-ttu-id="d7a71-177">As [expressões de computação (CES)](../language-reference/computation-expressions.md) são usadas hoje para modelar "computações contextuais" ou em uma terminologia amigável de programação mais funcional, computações de monadic.</span><span class="sxs-lookup"><span data-stu-id="d7a71-177">[Computation expressions (CEs)](../language-reference/computation-expressions.md) are used today to model "contextual computations", or in more functional programming friendly terminology, monadic computations.</span></span>

<span data-ttu-id="d7a71-178">O F # 5 apresenta Applicative CEs, que oferece um modelo computacional diferente.</span><span class="sxs-lookup"><span data-stu-id="d7a71-178">F# 5 introduces applicative CEs, which offer a different computational model.</span></span> <span data-ttu-id="d7a71-179">O Applicative CEs permite cálculos mais eficientes, desde que cada computação seja independente e seus resultados sejam acumulados no final.</span><span class="sxs-lookup"><span data-stu-id="d7a71-179">Applicative CEs allow for more efficient computations provided that every computation is independent, and their results are accumulated at the end.</span></span> <span data-ttu-id="d7a71-180">Quando as computações são independentes umas das outras, elas também são trivialmente paralelizáveis, permitindo que os autores de CE escrevam bibliotecas mais eficientes.</span><span class="sxs-lookup"><span data-stu-id="d7a71-180">When computations are independent of one another, they are also trivially parallelizable, allowing CE authors to write more efficient libraries.</span></span> <span data-ttu-id="d7a71-181">No entanto, esse benefício apresenta uma restrição: as computações que dependem de valores calculados anteriormente não são permitidas.</span><span class="sxs-lookup"><span data-stu-id="d7a71-181">This benefit comes at a restriction, though: computations that depend on previously-computed values are not allowed.</span></span>

<span data-ttu-id="d7a71-182">O exemplo a seguir mostra um Applicative CE básico para o `Result` tipo.</span><span class="sxs-lookup"><span data-stu-id="d7a71-182">The follow example shows a basic applicative CE for the `Result` type.</span></span>

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn "%s is: %d" (nameof res1) x
    | Error e -> printfn "%s is: %s" (nameof res1) e

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

<span data-ttu-id="d7a71-183">Se você é um autor de biblioteca que expõe CEs em sua biblioteca hoje, há algumas considerações adicionais que você precisará conhecer.</span><span class="sxs-lookup"><span data-stu-id="d7a71-183">If you're a library author who exposes CEs in their library today, there are some additional considerations you'll need to be aware of.</span></span>

## <a name="interfaces-can-be-implemeneted-at-different-generic-instantiations"></a><span data-ttu-id="d7a71-184">As interfaces podem ser implemeneteddas em instanciações genéricas diferentes</span><span class="sxs-lookup"><span data-stu-id="d7a71-184">Interfaces can be implemeneted at different generic instantiations</span></span>

<span data-ttu-id="d7a71-185">Agora você pode implementar a mesma interface em instanciações genéricas diferentes:</span><span class="sxs-lookup"><span data-stu-id="d7a71-185">You can now implement the same interface at different generic instantiations:</span></span>

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

## <a name="default-interface-member-consumption"></a><span data-ttu-id="d7a71-186">Consumo de membro de interface padrão</span><span class="sxs-lookup"><span data-stu-id="d7a71-186">Default interface member consumption</span></span>

<span data-ttu-id="d7a71-187">O F # 5 permite que você consuma [interfaces com implementações padrão](../../csharp/tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="d7a71-187">F# 5 lets you consume [interfaces with default implementations](../../csharp/tutorials/default-interface-methods-versions.md).</span></span>

<span data-ttu-id="d7a71-188">Considere uma interface definida em C# da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d7a71-188">Consider an interface defined in C# like this:</span></span>

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

<span data-ttu-id="d7a71-189">Você pode consumi-lo em F # por meio de qualquer um dos meios padrão de implementação de uma interface:</span><span class="sxs-lookup"><span data-stu-id="d7a71-189">You can consume it in F# through any of the standard means of implementing an interface:</span></span>

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn "DIM from C#: %d" md.Z

// You can also implement it via an object expression
let md' = { new MyDim }
printfn "DIM from C# but via Object Expression: %d" md'.Z
```

<span data-ttu-id="d7a71-190">Isso permite que você aproveite com segurança os componentes do código C# e do .NET escritos em C# moderno quando eles esperam que os usuários possam consumir uma implementação padrão.</span><span class="sxs-lookup"><span data-stu-id="d7a71-190">This lets you safely take advantage of C# code and .NET components written in modern C# when they expect users to be able to consume a default implementation.</span></span>

## <a name="simplified-interop-with-nullable-value-types"></a><span data-ttu-id="d7a71-191">Interoperabilidade simplificada com tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="d7a71-191">Simplified interop with nullable value types</span></span>

<span data-ttu-id="d7a71-192">Os [tipos anuláveis (de valor)](https://docs.microsoft.com/dotnet/api/system.nullable-1) (chamados de tipos anuláveis historicamente) têm o suporte de F #, mas interagir com eles tem sido tradicionalmente um problema, pois você teria que construir um `Nullable` `Nullable<SomeType>` wrapper ou cada vez que quisesse passar um valor.</span><span class="sxs-lookup"><span data-stu-id="d7a71-192">[Nullable (value) types](https://docs.microsoft.com/dotnet/api/system.nullable-1) (called Nullable Types historically) have long been supported by F#, but interacting with them has traditionally been somewhat of a pain since you'd have to construct a `Nullable` or `Nullable<SomeType>` wrapper every time you wanted to pass a value.</span></span> <span data-ttu-id="d7a71-193">Agora, o compilador converterá implicitamente um tipo de valor em um `Nullable<ThatValueType>` se o tipo de destino corresponder.</span><span class="sxs-lookup"><span data-stu-id="d7a71-193">Now the compiler will implicitly convert a value type into a `Nullable<ThatValueType>` if the target type matches.</span></span> <span data-ttu-id="d7a71-194">O código a seguir agora é possível:</span><span class="sxs-lookup"><span data-stu-id="d7a71-194">The following code is now possible:</span></span>

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

## <a name="preview-reverse-indexes"></a><span data-ttu-id="d7a71-195">Visualização: índices inversos</span><span class="sxs-lookup"><span data-stu-id="d7a71-195">Preview: reverse indexes</span></span>

<span data-ttu-id="d7a71-196">O F # 5 também apresenta uma visualização para permitir índices inversos.</span><span class="sxs-lookup"><span data-stu-id="d7a71-196">F# 5 also introduces a preview for allowing reverse indexes.</span></span> <span data-ttu-id="d7a71-197">A sintaxe é `^idx`.</span><span class="sxs-lookup"><span data-stu-id="d7a71-197">The syntax is `^idx`.</span></span> <span data-ttu-id="d7a71-198">Veja como você pode um valor de elemento 1 do final de uma lista:</span><span class="sxs-lookup"><span data-stu-id="d7a71-198">Here’s how you can an element 1 value from the end of a list:</span></span>

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

<span data-ttu-id="d7a71-199">Você também pode definir índices inversos para seus próprios tipos.</span><span class="sxs-lookup"><span data-stu-id="d7a71-199">You can also define reverse indexes for your own types.</span></span> <span data-ttu-id="d7a71-200">Para fazer isso, você precisará implementar o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="d7a71-200">To do so, you’ll need to implement the following method:</span></span>

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

<span data-ttu-id="d7a71-201">Aqui está um exemplo para o `Span<'T>` tipo:</span><span class="sxs-lookup"><span data-stu-id="d7a71-201">Here’s an example for the `Span<'T>` type:</span></span>

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a><span data-ttu-id="d7a71-202">Visualização: sobrecargas de palavras-chave personalizadas em expressões de computação</span><span class="sxs-lookup"><span data-stu-id="d7a71-202">Preview: overloads of custom keywords in computation expressions</span></span>

<span data-ttu-id="d7a71-203">As expressões de computação são um recurso poderoso para autores de biblioteca e estrutura.</span><span class="sxs-lookup"><span data-stu-id="d7a71-203">Computation expressions are a powerful feature for library and framework authors.</span></span> <span data-ttu-id="d7a71-204">Eles permitem que você aprimore significativamente a expressividade dos componentes, permitindo que você defina membros conhecidos e formate uma DSL para o domínio no qual você está trabalhando.</span><span class="sxs-lookup"><span data-stu-id="d7a71-204">They allow you to greatly improve the expressiveness of your components by letting you define well-known members and form a DSL for the domain you're working in.</span></span>

<span data-ttu-id="d7a71-205">O F # 5 adiciona suporte à visualização para sobrecarregar operações personalizadas em expressões de computação.</span><span class="sxs-lookup"><span data-stu-id="d7a71-205">F# 5 adds preview support for overloading custom operations in Computation Expressions.</span></span> <span data-ttu-id="d7a71-206">Ele permite que o seguinte código seja gravado e consumido:</span><span class="sxs-lookup"><span data-stu-id="d7a71-206">It allows the following code to be writen and consumed:</span></span>

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

<span data-ttu-id="d7a71-207">Antes dessa alteração, você poderia escrever o `InputBuilder` tipo como ele está, mas não poderia usá-lo da maneira como ele é usado no exemplo.</span><span class="sxs-lookup"><span data-stu-id="d7a71-207">Prior to this change, you could write the `InputBuilder` type as it is, but you couldn't use it the way it's used in the example.</span></span> <span data-ttu-id="d7a71-208">Como as sobrecargas, os parâmetros opcionais e os `System.ParamArray` tipos Now são permitidos, tudo funciona exatamente como você esperaria.</span><span class="sxs-lookup"><span data-stu-id="d7a71-208">Since overloads, optional parameters, and now `System.ParamArray` types are allowed, everything just works as you'd expect it to.</span></span>

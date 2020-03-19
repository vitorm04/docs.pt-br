---
title: O que há de novo em F# 4.5 - F# Guide
description: Obtenha uma visão geral dos novos recursos disponíveis em F# 4.5.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186131"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="40ab8-103">O que há de novo em F# 4.5</span><span class="sxs-lookup"><span data-stu-id="40ab8-103">What's new in F# 4.5</span></span>

<span data-ttu-id="40ab8-104">F# 4.5 adiciona várias melhorias ao idioma F#.</span><span class="sxs-lookup"><span data-stu-id="40ab8-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="40ab8-105">Muitos desses recursos foram adicionados para permitir que você escreva código eficiente em F# e, ao mesmo tempo, garanta que esse código seja seguro.</span><span class="sxs-lookup"><span data-stu-id="40ab8-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="40ab8-106">Fazer isso significa adicionar alguns conceitos à linguagem e uma quantidade significativa de análise de compilador ao usar esses construtos.</span><span class="sxs-lookup"><span data-stu-id="40ab8-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="40ab8-107">Introdução</span><span class="sxs-lookup"><span data-stu-id="40ab8-107">Get started</span></span>

<span data-ttu-id="40ab8-108">F# 4.5 está disponível em todas as distribuições .NET Core e ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40ab8-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="40ab8-109">[Comece com F#](../get-started/index.md) para aprender mais.</span><span class="sxs-lookup"><span data-stu-id="40ab8-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="40ab8-110">Span e structs byref-like</span><span class="sxs-lookup"><span data-stu-id="40ab8-110">Span and byref-like structs</span></span>

<span data-ttu-id="40ab8-111">O <xref:System.Span%601> tipo introduzido no .NET Core permite que você represente buffers na memória de uma maneira fortemente digitada, o que agora é permitido em F# começando com F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="40ab8-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="40ab8-112">O exemplo a seguir mostra como você pode <xref:System.Span%601> reutilizar uma função operando em um com diferentes representações de buffer:</span><span class="sxs-lookup"><span data-stu-id="40ab8-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="40ab8-113">Um aspecto importante para isso é que Span e [outras estruturas semelhantes](../language-reference/structures.md#byreflike-structs) a byref têm uma análise estática muito rígida realizada pelo compilador que restringe seu uso de maneiras que você pode achar inesperada.</span><span class="sxs-lookup"><span data-stu-id="40ab8-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="40ab8-114">Esta é a troca fundamental entre desempenho, expressividade e segurança que é introduzida no F# 4.5.</span><span class="sxs-lookup"><span data-stu-id="40ab8-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="40ab8-115">Byrefs renovados</span><span class="sxs-lookup"><span data-stu-id="40ab8-115">Revamped byrefs</span></span>

<span data-ttu-id="40ab8-116">Antes do F# 4.5, [byrefs](../language-reference/byrefs.md) em F# eram inseguros e insalubres para inúmeras aplicações.</span><span class="sxs-lookup"><span data-stu-id="40ab8-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="40ab8-117">Problemas de solidez em torno de byrefs foram abordados em F # 4.5 e a mesma análise estática feita para extensão e estruturas semelhantes a byref também foi aplicada.</span><span class="sxs-lookup"><span data-stu-id="40ab8-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="40ab8-118">inref<'T> e outref<'T></span><span class="sxs-lookup"><span data-stu-id="40ab8-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="40ab8-119">Para representar a noção de ponteiro gerenciado somente leitura, gravação e leitura/gravação, o `inref<'T>` `outref<'T>` F# 4.5 introduz os tipos para representar ponteiros somente leitura e somente gravação, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="40ab8-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="40ab8-120">Cada um tem semântica diferente.</span><span class="sxs-lookup"><span data-stu-id="40ab8-120">Each have different semantics.</span></span> <span data-ttu-id="40ab8-121">Por exemplo, você não `inref<'T>`pode escrever para um:</span><span class="sxs-lookup"><span data-stu-id="40ab8-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="40ab8-122">Por padrão, a inferência de tipo `inref<'T>` inferirá ponteiros gerenciados como estar em consonância com a natureza imutável do código F#, a menos que algo já tenha sido declarado como mutável.</span><span class="sxs-lookup"><span data-stu-id="40ab8-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="40ab8-123">Para fazer algo gravável, você precisará declarar `mutable` um tipo como antes de passar seu endereço para uma função ou membro que o manipule.</span><span class="sxs-lookup"><span data-stu-id="40ab8-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="40ab8-124">Para saber mais, consulte [Byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="40ab8-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="40ab8-125">Structs somente leitura</span><span class="sxs-lookup"><span data-stu-id="40ab8-125">Readonly structs</span></span>

<span data-ttu-id="40ab8-126">Começando com F # 4.5, você pode anotar <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> uma estrutura com como tal:</span><span class="sxs-lookup"><span data-stu-id="40ab8-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="40ab8-127">Isso o impede de declarar um membro mutável na estrutura e emite metadados que permitem que F# e C# o tratem como lido somente quando consumidos de uma montagem.</span><span class="sxs-lookup"><span data-stu-id="40ab8-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="40ab8-128">Para saber mais, consulte [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span><span class="sxs-lookup"><span data-stu-id="40ab8-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="40ab8-129">Ponteiros vazios</span><span class="sxs-lookup"><span data-stu-id="40ab8-129">Void pointers</span></span>

<span data-ttu-id="40ab8-130">O `voidptr` tipo é adicionado ao F# 4.5, assim como as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="40ab8-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="40ab8-131">`NativePtr.ofVoidPtr`para converter um ponteiro vazio em um ponteiro int nativo</span><span class="sxs-lookup"><span data-stu-id="40ab8-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="40ab8-132">`NativePtr.toVoidPtr`para converter um ponteiro int nativo para um ponteiro vazio</span><span class="sxs-lookup"><span data-stu-id="40ab8-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="40ab8-133">Isso é útil ao interagir com um componente nativo que faz uso de ponteiros vazios.</span><span class="sxs-lookup"><span data-stu-id="40ab8-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="40ab8-134">A palavra-chave `match!`</span><span class="sxs-lookup"><span data-stu-id="40ab8-134">The `match!` keyword</span></span>

<span data-ttu-id="40ab8-135">A `match!` palavra-chave aumenta a correspondência de padrões quando dentro de uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="40ab8-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="40ab8-136">Isso permite encurtar o código que muitas vezes envolve misturar opções (ou outros tipos) com expressões de computação, como assincronismo.</span><span class="sxs-lookup"><span data-stu-id="40ab8-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="40ab8-137">Para saber mais, veja [o match!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="40ab8-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="40ab8-138">Requisitos de upcasting relaxados em expressões de matriz, lista e seqüência</span><span class="sxs-lookup"><span data-stu-id="40ab8-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="40ab8-139">A mistura de tipos onde se pode herdar de outro dentro de array, list e sequence expressões `:>` `upcast`tradicionalmente exigiu que você upcast qualquer tipo derivado para o seu tipo pai com ou .</span><span class="sxs-lookup"><span data-stu-id="40ab8-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="40ab8-140">Isso agora é relaxado, demonstrado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="40ab8-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="40ab8-141">Relaxamento de recuo para array e expressões de lista</span><span class="sxs-lookup"><span data-stu-id="40ab8-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="40ab8-142">Antes do F# 4.5, você precisava de matriz de recuo excessiva mente e expressar expressões quando passadocomo argumentos para chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="40ab8-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="40ab8-143">Isso não é mais necessário:</span><span class="sxs-lookup"><span data-stu-id="40ab8-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```

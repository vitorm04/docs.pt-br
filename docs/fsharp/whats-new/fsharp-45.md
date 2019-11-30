---
title: O que há de F# novo no F# guia de 4,5
description: Obtenha uma visão geral dos novos recursos disponíveis em F# 4,5.
ms.date: 11/27/2019
ms.openlocfilehash: 780b33a564432aae5ec99c70ff8620988b553fd1
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644106"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="91b84-103">O que há de F# novo no 4,5</span><span class="sxs-lookup"><span data-stu-id="91b84-103">What's new in F# 4.5</span></span>

<span data-ttu-id="91b84-104">F#4,5 adiciona várias melhorias ao F# idioma.</span><span class="sxs-lookup"><span data-stu-id="91b84-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="91b84-105">Muitos desses recursos foram adicionados juntos para permitir que você escreva um código eficiente no F# enquanto também garante que esse código seja seguro.</span><span class="sxs-lookup"><span data-stu-id="91b84-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="91b84-106">Fazer isso significa adicionar alguns conceitos à linguagem e uma quantidade significativa de análise do compilador ao usar essas construções.</span><span class="sxs-lookup"><span data-stu-id="91b84-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="91b84-107">Introdução</span><span class="sxs-lookup"><span data-stu-id="91b84-107">Get started</span></span>

<span data-ttu-id="91b84-108">F#o 4,5 está disponível em todas as distribuições do .NET Core e ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91b84-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="91b84-109">[Introdução F# ](../get-started/index.md) ao para saber mais.</span><span class="sxs-lookup"><span data-stu-id="91b84-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="91b84-110">Estruturas do tipo "span" e "ByRef"</span><span class="sxs-lookup"><span data-stu-id="91b84-110">Span and byref-like structs</span></span>

<span data-ttu-id="91b84-111">O tipo de <xref:System.Span%601> introduzido no .NET Core permite que você represente buffers na memória de maneira fortemente tipada, que agora é permitido F# a partir F# de 4,5.</span><span class="sxs-lookup"><span data-stu-id="91b84-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly-typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="91b84-112">O exemplo a seguir mostra como você pode usar novamente uma função operando em um <xref:System.Span%601> com diferentes representações de buffer:</span><span class="sxs-lookup"><span data-stu-id="91b84-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

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

<span data-ttu-id="91b84-113">Um aspecto importante disso é que o span e outras [estruturas do tipo ByRef](../language-reference/structures.md#byreflike-structs) têm uma análise estática muito rígida executada pelo compilador que restringe seu uso de maneiras que você talvez ache inesperado.</span><span class="sxs-lookup"><span data-stu-id="91b84-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="91b84-114">Essa é a compensação fundamental entre o desempenho, a expressividade e a segurança que é introduzida em F# 4,5.</span><span class="sxs-lookup"><span data-stu-id="91b84-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="91b84-115">Byrefs remodelados</span><span class="sxs-lookup"><span data-stu-id="91b84-115">Revamped byrefs</span></span>

<span data-ttu-id="91b84-116">Antes de F# 4,5, os [byrefs](../language-reference/byrefs.md) em F# eram inseguros e insons para vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="91b84-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="91b84-117">Os problemas de barulho em relação a byrefs foram F# resolvidos em 4,5 e a mesma análise estática feita para estruturas de span e de ByRef também foi aplicada.</span><span class="sxs-lookup"><span data-stu-id="91b84-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="91b84-118">inref < > e outref < ' t ></span><span class="sxs-lookup"><span data-stu-id="91b84-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="91b84-119">Para representar a noção de um ponteiro gerenciado somente leitura, somente gravação e leitura/gravação, F# 4,5 apresenta a `inref<'T>`, `outref<'T>` tipos para representar ponteiros somente leitura e somente gravação, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="91b84-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="91b84-120">Cada uma tem uma semântica diferente.</span><span class="sxs-lookup"><span data-stu-id="91b84-120">Each have different semantics.</span></span> <span data-ttu-id="91b84-121">Por exemplo, você não pode gravar em um `inref<'T>`:</span><span class="sxs-lookup"><span data-stu-id="91b84-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="91b84-122">Por padrão, a inferência de tipos inferirá ponteiros gerenciados como `inref<'T>` estar em linha com F# a natureza imutável do código, a menos que algo já tenha sido declarado como mutável.</span><span class="sxs-lookup"><span data-stu-id="91b84-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="91b84-123">Para tornar algo gravável, você precisará declarar um tipo como `mutable` antes de passar seu endereço para uma função ou um membro que o manipule.</span><span class="sxs-lookup"><span data-stu-id="91b84-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="91b84-124">Para saber mais, confira [byrefs](../language-reference/byrefs.md).</span><span class="sxs-lookup"><span data-stu-id="91b84-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="91b84-125">Structs ReadOnly</span><span class="sxs-lookup"><span data-stu-id="91b84-125">Readonly structs</span></span>

<span data-ttu-id="91b84-126">A partir F# do 4,5, você pode anotar uma struct com <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> como tal:</span><span class="sxs-lookup"><span data-stu-id="91b84-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="91b84-127">Isso não permite que você declarasse um membro mutável na estrutura e emita metadados que permitam F# e C# tratá-lo como ReadOnly quando consumido de um assembly.</span><span class="sxs-lookup"><span data-stu-id="91b84-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="91b84-128">Para saber mais, veja [structs ReadOnly](../language-reference/structures.md#readonly-structs)</span><span class="sxs-lookup"><span data-stu-id="91b84-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs)</span></span>

## <a name="void-pointers"></a><span data-ttu-id="91b84-129">Ponteiros void</span><span class="sxs-lookup"><span data-stu-id="91b84-129">Void pointers</span></span>

<span data-ttu-id="91b84-130">O tipo de `voidptr` é adicionado F# a 4,5, assim como as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="91b84-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="91b84-131">`NativePtr.ofVoidPtr` converter um ponteiro void em um ponteiro int nativo</span><span class="sxs-lookup"><span data-stu-id="91b84-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="91b84-132">`NativePtr.toVoidPtr` converter um ponteiro int nativo para um ponteiro void</span><span class="sxs-lookup"><span data-stu-id="91b84-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="91b84-133">Isso é útil ao interoperar com um componente nativo que utiliza ponteiros void.</span><span class="sxs-lookup"><span data-stu-id="91b84-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="91b84-134">A palavra-chave `match!`</span><span class="sxs-lookup"><span data-stu-id="91b84-134">The `match!` keyword</span></span>

<span data-ttu-id="91b84-135">A palavra-chave `match!` aprimora a correspondência de padrões quando dentro de uma expressão de computação:</span><span class="sxs-lookup"><span data-stu-id="91b84-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

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

<span data-ttu-id="91b84-136">Isso permite que você encurte o código que geralmente envolve a combinação de opções (ou outros tipos) com expressões de computação, como Async.</span><span class="sxs-lookup"><span data-stu-id="91b84-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="91b84-137">Para saber mais, consulte [correspondência!](../language-reference/computation-expressions.md#match).</span><span class="sxs-lookup"><span data-stu-id="91b84-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="91b84-138">Requisitos de upcast reduzidos em expressões de matriz, lista e sequência</span><span class="sxs-lookup"><span data-stu-id="91b84-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="91b84-139">A combinação de tipos em que um pode herdar de outro dentro de expressões de matriz, lista e sequência exigiu tradicionalmente que você converta qualquer tipo derivado em seu tipo pai com `:>` ou `upcast`.</span><span class="sxs-lookup"><span data-stu-id="91b84-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="91b84-140">Isso agora é relaxado, demonstrado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="91b84-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="91b84-141">Relaxamento de recuo para expressões de matriz e lista</span><span class="sxs-lookup"><span data-stu-id="91b84-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="91b84-142">Antes de F# 4,5, você precisava recuar excessivamente as expressões de matriz e de lista quando passavam como argumentos para chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="91b84-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="91b84-143">Isso não é mais necessário:</span><span class="sxs-lookup"><span data-stu-id="91b84-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```

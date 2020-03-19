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
# <a name="whats-new-in-f-45"></a>O que há de novo em F# 4.5

F# 4.5 adiciona várias melhorias ao idioma F#. Muitos desses recursos foram adicionados para permitir que você escreva código eficiente em F# e, ao mesmo tempo, garanta que esse código seja seguro. Fazer isso significa adicionar alguns conceitos à linguagem e uma quantidade significativa de análise de compilador ao usar esses construtos.

## <a name="get-started"></a>Introdução

F# 4.5 está disponível em todas as distribuições .NET Core e ferramentas do Visual Studio. [Comece com F#](../get-started/index.md) para aprender mais.

## <a name="span-and-byref-like-structs"></a>Span e structs byref-like

O <xref:System.Span%601> tipo introduzido no .NET Core permite que você represente buffers na memória de uma maneira fortemente digitada, o que agora é permitido em F# começando com F# 4.5. O exemplo a seguir mostra como você pode <xref:System.Span%601> reutilizar uma função operando em um com diferentes representações de buffer:

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

Um aspecto importante para isso é que Span e [outras estruturas semelhantes](../language-reference/structures.md#byreflike-structs) a byref têm uma análise estática muito rígida realizada pelo compilador que restringe seu uso de maneiras que você pode achar inesperada. Esta é a troca fundamental entre desempenho, expressividade e segurança que é introduzida no F# 4.5.

## <a name="revamped-byrefs"></a>Byrefs renovados

Antes do F# 4.5, [byrefs](../language-reference/byrefs.md) em F# eram inseguros e insalubres para inúmeras aplicações. Problemas de solidez em torno de byrefs foram abordados em F # 4.5 e a mesma análise estática feita para extensão e estruturas semelhantes a byref também foi aplicada.

### <a name="inreft-and-outreft"></a>inref<'T> e outref<'T>

Para representar a noção de ponteiro gerenciado somente leitura, gravação e leitura/gravação, o `inref<'T>` `outref<'T>` F# 4.5 introduz os tipos para representar ponteiros somente leitura e somente gravação, respectivamente. Cada um tem semântica diferente. Por exemplo, você não `inref<'T>`pode escrever para um:

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Por padrão, a inferência de tipo `inref<'T>` inferirá ponteiros gerenciados como estar em consonância com a natureza imutável do código F#, a menos que algo já tenha sido declarado como mutável. Para fazer algo gravável, você precisará declarar `mutable` um tipo como antes de passar seu endereço para uma função ou membro que o manipule. Para saber mais, consulte [Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Structs somente leitura

Começando com F # 4.5, você pode anotar <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> uma estrutura com como tal:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Isso o impede de declarar um membro mutável na estrutura e emite metadados que permitem que F# e C# o tratem como lido somente quando consumidos de uma montagem. Para saber mais, consulte [ReadOnly structs](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Ponteiros vazios

O `voidptr` tipo é adicionado ao F# 4.5, assim como as seguintes funções:

* `NativePtr.ofVoidPtr`para converter um ponteiro vazio em um ponteiro int nativo
* `NativePtr.toVoidPtr`para converter um ponteiro int nativo para um ponteiro vazio

Isso é útil ao interagir com um componente nativo que faz uso de ponteiros vazios.

## <a name="the-match-keyword"></a>A palavra-chave `match!`

A `match!` palavra-chave aumenta a correspondência de padrões quando dentro de uma expressão de computação:

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

Isso permite encurtar o código que muitas vezes envolve misturar opções (ou outros tipos) com expressões de computação, como assincronismo. Para saber mais, veja [o match!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Requisitos de upcasting relaxados em expressões de matriz, lista e seqüência

A mistura de tipos onde se pode herdar de outro dentro de array, list e sequence expressões `:>` `upcast`tradicionalmente exigiu que você upcast qualquer tipo derivado para o seu tipo pai com ou . Isso agora é relaxado, demonstrado da seguinte forma:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Relaxamento de recuo para array e expressões de lista

Antes do F# 4.5, você precisava de matriz de recuo excessiva mente e expressar expressões quando passadocomo argumentos para chamadas de método. Isso não é mais necessário:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```

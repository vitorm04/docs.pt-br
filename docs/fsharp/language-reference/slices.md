---
title: Fatias (F#)
description: Saiba mais sobre como usar fatias existentes F# tipos de dados e como definir seus próprios fatias para outros tipos de dados.
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675271"
---
# <a name="slices"></a><span data-ttu-id="cc8a0-103">Fatias</span><span class="sxs-lookup"><span data-stu-id="cc8a0-103">Slices</span></span>

<span data-ttu-id="cc8a0-104">No F#, uma fatia é um subconjunto de um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="cc8a0-105">Para poder tirar uma fatia de um tipo de dados, o tipo de dados deve definir um `GetSlice` método ou em um [extensão de tipo](type-extensions.md) que é em escopo.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="cc8a0-106">Este artigo explica como aproveitar as fatias de existente F# tipos e como definir seus próprios.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="cc8a0-107">Fatias são semelhantes às [indexadores](members/indexed-properties.md), mas em vez da estrutura de dados subjacente que rende um valor único, geram várias dessas classes.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-107">Slices are similar to [indexers](members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="cc8a0-108">F#no momento tem suporte intrínseco para matrizes 2D, listas, matrizes e cadeias de caracteres de divisão.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="cc8a0-109">Divisão básica com o F# matrizes e listas</span><span class="sxs-lookup"><span data-stu-id="cc8a0-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="cc8a0-110">Os tipos de dados mais comuns que são subconjuntos são F# matrizes e listas.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="cc8a0-111">O exemplo a seguir demonstra como fazer isso com listas:</span><span class="sxs-lookup"><span data-stu-id="cc8a0-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="cc8a0-112">Matrizes de divisão é exatamente como listas de divisão:</span><span class="sxs-lookup"><span data-stu-id="cc8a0-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="cc8a0-113">Divisão de matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="cc8a0-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="cc8a0-114">F#dá suporte a matrizes multidimensionais no F# biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="cc8a0-115">Assim como ocorre com matrizes unidimensionais, fatias de matrizes multidimensionais também podem ser útil.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="cc8a0-116">No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa tomar as fatias de linhas e colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="cc8a0-117">Os exemplos a seguir demonstram como uma matriz de 2D de fatia:</span><span class="sxs-lookup"><span data-stu-id="cc8a0-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="cc8a0-118">O F# biblioteca principal não define `GetSlice`para matrizes 3D.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="cc8a0-119">Se você quiser dividir aqueles ou outras matrizes ou mais dimensões, você deve definir o `GetSlice` membro por conta própria.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="cc8a0-120">Definir fatias para outras estruturas de dados</span><span class="sxs-lookup"><span data-stu-id="cc8a0-120">Defining slices for other data structures</span></span>

<span data-ttu-id="cc8a0-121">O F# biblioteca principal define fatias para um conjunto limitado de tipos.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="cc8a0-122">Se você quiser definir fatias para mais tipos de dados, você pode fazer isso na definição de tipo em si ou em uma extensão de tipo.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="cc8a0-123">Por exemplo, aqui está como você pode definir fatias para o <xref:System.ArraySegment%601> classe para permitir a manipulação de dados conveniente:</span><span class="sxs-lookup"><span data-stu-id="cc8a0-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="cc8a0-124">Use inlining para evitar a conversão boxing se for necessário</span><span class="sxs-lookup"><span data-stu-id="cc8a0-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="cc8a0-125">Se você estiver definindo fatias para um tipo que é, na verdade, um struct, recomendamos que você `inline` o `GetSlice` membro.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="cc8a0-126">O F# compilador otimizará os argumentos opcionais, evitando as alocações de heap como resultado da divisão.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="cc8a0-127">Isso é extremamente importante para construções de divisão, como <xref:System.Span%601> que não podem ser alocados no heap.</span><span class="sxs-lookup"><span data-stu-id="cc8a0-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a><span data-ttu-id="cc8a0-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc8a0-128">See also</span></span>

- [<span data-ttu-id="cc8a0-129">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="cc8a0-129">Indexed properties</span></span>](members/indexed-properties.md)

---
title: Fatias
description: Saiba como usar fatias para tipos F# de dados existentes e como definir suas próprias fatias para outros tipos de dados.
ms.date: 12/23/2019
ms.openlocfilehash: 3911139c7ce656043817eb23d30f3686555b6efe
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545106"
---
# <a name="slices"></a><span data-ttu-id="100d2-103">Fatias</span><span class="sxs-lookup"><span data-stu-id="100d2-103">Slices</span></span>

<span data-ttu-id="100d2-104">No F#, uma fatia é um subconjunto de qualquer tipo de dados que tem um método `GetSlice` em sua definição ou em uma [extensão de tipo](type-extensions.md)no escopo.</span><span class="sxs-lookup"><span data-stu-id="100d2-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="100d2-105">Ele é mais comumente usado com F# matrizes e listas.</span><span class="sxs-lookup"><span data-stu-id="100d2-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="100d2-106">Este artigo explica como tirar fatias de tipos F# existentes e como definir suas próprias fatias.</span><span class="sxs-lookup"><span data-stu-id="100d2-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="100d2-107">As fatias são semelhantes aos [indexadores](./members/indexed-properties.md), mas em vez de produzir um único valor da estrutura de dados subjacente, elas produzem várias delas.</span><span class="sxs-lookup"><span data-stu-id="100d2-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="100d2-108">F#atualmente tem suporte intrínseco para cadeias de caracteres de divisão, listas, matrizes e matrizes 2D.</span><span class="sxs-lookup"><span data-stu-id="100d2-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="100d2-109">Divisão básica com F# listas e matrizes</span><span class="sxs-lookup"><span data-stu-id="100d2-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="100d2-110">Os tipos de dados mais comuns que são segmentados F# são listas e matrizes.</span><span class="sxs-lookup"><span data-stu-id="100d2-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="100d2-111">O exemplo a seguir demonstra como fazer isso com listas:</span><span class="sxs-lookup"><span data-stu-id="100d2-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="100d2-112">As matrizes de divisão são apenas como listas de fatias:</span><span class="sxs-lookup"><span data-stu-id="100d2-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="100d2-113">Fatiando matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="100d2-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="100d2-114">F#dá suporte a F# matrizes multidimensionais na biblioteca principal.</span><span class="sxs-lookup"><span data-stu-id="100d2-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="100d2-115">Assim como acontece com matrizes unidimensionais, as fatias de matrizes multidimensionais também podem ser úteis.</span><span class="sxs-lookup"><span data-stu-id="100d2-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="100d2-116">No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa colocar fatias de linhas e colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="100d2-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="100d2-117">Os exemplos a seguir demonstram como dividir uma matriz 2D:</span><span class="sxs-lookup"><span data-stu-id="100d2-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="100d2-118">Atualmente F# , a biblioteca principal não define `GetSlice` para matrizes 3D.</span><span class="sxs-lookup"><span data-stu-id="100d2-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="100d2-119">Se você quiser fatiar matrizes 3D ou outras matrizes de mais dimensões, defina o membro `GetSlice` por conta própria.</span><span class="sxs-lookup"><span data-stu-id="100d2-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="100d2-120">Definindo fatias para outras estruturas de dados</span><span class="sxs-lookup"><span data-stu-id="100d2-120">Defining slices for other data structures</span></span>

<span data-ttu-id="100d2-121">A F# biblioteca principal define fatias para um conjunto limitado de tipos.</span><span class="sxs-lookup"><span data-stu-id="100d2-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="100d2-122">Se você quiser definir fatias para mais tipos de dados, poderá fazer isso na própria definição de tipo ou em uma extensão de tipo.</span><span class="sxs-lookup"><span data-stu-id="100d2-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="100d2-123">Por exemplo, veja como você pode definir fatias para a classe <xref:System.ArraySegment%601> para permitir uma manipulação de dados conveniente:</span><span class="sxs-lookup"><span data-stu-id="100d2-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="100d2-124">Use o Outlining para evitar boxing, se necessário</span><span class="sxs-lookup"><span data-stu-id="100d2-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="100d2-125">Se você estiver definindo fatias para um tipo que é realmente uma struct, é recomendável `inline` o membro `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="100d2-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="100d2-126">O F# compilador otimiza os argumentos opcionais, evitando qualquer alocação de heap como resultado de divisão.</span><span class="sxs-lookup"><span data-stu-id="100d2-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="100d2-127">Isso é extremamente importante para as construções de fatias, como <xref:System.Span%601> que não podem ser alocadas no heap.</span><span class="sxs-lookup"><span data-stu-id="100d2-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="100d2-128">As F# fatias internas são inclusivas</span><span class="sxs-lookup"><span data-stu-id="100d2-128">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="100d2-129">Todas as fatias F# intrínsecas no são completas, inclusive ou seja, o limite superior é incluído na fatia.</span><span class="sxs-lookup"><span data-stu-id="100d2-129">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="100d2-130">Para uma determinada fatia com `x` de índice inicial e `y`de índice final, a fatia resultante incluirá o valor *YTH* .</span><span class="sxs-lookup"><span data-stu-id="100d2-130">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="100d2-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="100d2-131">See also</span></span>

- [<span data-ttu-id="100d2-132">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="100d2-132">Indexed properties</span></span>](./members/indexed-properties.md)

---
title: Fatias
description: 'Saiba como usar fatias para tipos de dados F # existentes e como definir suas próprias fatias para outros tipos de dados.'
ms.date: 12/23/2019
ms.openlocfilehash: a3920ad9e1b205b506aaee92c4606bcebf94feba
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557071"
---
# <a name="slices"></a><span data-ttu-id="dd4a0-103">Fatias</span><span class="sxs-lookup"><span data-stu-id="dd4a0-103">Slices</span></span>

<span data-ttu-id="dd4a0-104">Em F #, uma fatia é um subconjunto de qualquer tipo de dados que tem um `GetSlice` método em sua definição ou em uma [extensão de tipo](type-extensions.md)no escopo.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="dd4a0-105">Ele é mais comumente usado com matrizes e listas de F #.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="dd4a0-106">Este artigo explica como tirar fatias de tipos existentes de F # e como definir suas próprias fatias.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="dd4a0-107">As fatias são semelhantes aos [indexadores](./members/indexed-properties.md), mas em vez de produzir um único valor da estrutura de dados subjacente, elas produzem várias delas.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="dd4a0-108">O F # atualmente tem suporte intrínseco para cadeias de caracteres de divisão, listas, matrizes e matrizes 2D.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="dd4a0-109">Divisão básica com listas e matrizes F #</span><span class="sxs-lookup"><span data-stu-id="dd4a0-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="dd4a0-110">Os tipos de dados mais comuns que são segmentados são listas e matrizes de F #.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="dd4a0-111">O exemplo a seguir demonstra como fazer isso com listas:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="dd4a0-112">As matrizes de divisão são apenas como listas de fatias:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="dd4a0-113">Fatiando matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="dd4a0-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="dd4a0-114">O f # dá suporte a matrizes multidimensionais na biblioteca principal do F #.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="dd4a0-115">Assim como acontece com matrizes unidimensionais, as fatias de matrizes multidimensionais também podem ser úteis.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="dd4a0-116">No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa colocar fatias de linhas e colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="dd4a0-117">Os exemplos a seguir demonstram como dividir uma matriz 2D:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="dd4a0-118">A biblioteca de núcleos F # não define atualmente `GetSlice` para matrizes 3D.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="dd4a0-119">Se você quiser fatiar matrizes 3D ou outras matrizes de mais dimensões, defina o `GetSlice` membro por conta própria.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="dd4a0-120">Definindo fatias para outras estruturas de dados</span><span class="sxs-lookup"><span data-stu-id="dd4a0-120">Defining slices for other data structures</span></span>

<span data-ttu-id="dd4a0-121">A biblioteca de núcleos F # define fatias para um conjunto limitado de tipos.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="dd4a0-122">Se você quiser definir fatias para mais tipos de dados, poderá fazer isso na própria definição de tipo ou em uma extensão de tipo.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="dd4a0-123">Por exemplo, veja como você pode definir fatias para a <xref:System.ArraySegment%601> classe para permitir uma manipulação de dados conveniente:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="dd4a0-124">Outro exemplo que usa <xref:System.Span%601> os <xref:System.ReadOnlySpan%601> tipos e:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
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
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="dd4a0-125">As fatias F # internas são inclusivas</span><span class="sxs-lookup"><span data-stu-id="dd4a0-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="dd4a0-126">Todas as fatias intrínsecas em F # são inclusivas; ou seja, o limite superior é incluído na fatia.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="dd4a0-127">Para uma determinada fatia com índice inicial `x` e índice final `y` , a fatia resultante incluirá o valor *YTH* .</span><span class="sxs-lookup"><span data-stu-id="dd4a0-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="dd4a0-128">Fatias internas F # vazias</span><span class="sxs-lookup"><span data-stu-id="dd4a0-128">Built-in F# empty slices</span></span>

<span data-ttu-id="dd4a0-129">Listas F #, matrizes, sequências, cadeias de caracteres, matrizes 2D, matrizes 3D e matrizes 4D produzirão uma fatia vazia se a sintaxe puder produzir uma fatia que não existe.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-129">F# lists, arrays, sequences, strings, 2D arrays, 3D arrays, and 4D arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="dd4a0-130">Considere o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-130">Consider the following:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="dd4a0-131">Os desenvolvedores de C# podem esperar que eles lancem uma exceção em vez de produzir uma fatia vazia.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-131">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="dd4a0-132">Essa é uma decisão de design enraizada no fato de que coleções vazias compõem em F #.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-132">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="dd4a0-133">Uma lista de F # vazia pode ser composta com outra lista de F #, uma cadeia de caracteres vazia pode ser adicionada a uma cadeia de caracteres existente e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-133">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="dd4a0-134">Pode ser comum pegar fatias com base nos valores passados como parâmetros e ser tolerante a fora dos limites, produzindo uma coleção vazia se ajusta à natureza composicional do código F #.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-134">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="dd4a0-135">Fatias de índice fixo para matrizes 3D e 4D</span><span class="sxs-lookup"><span data-stu-id="dd4a0-135">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="dd4a0-136">Para matrizes F # 3D e 4D, você pode "corrigir" um índice específico e fatiar outras dimensões com esse índice fixo.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-136">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="dd4a0-137">Para ilustrar isso, considere a seguinte matriz 3D:</span><span class="sxs-lookup"><span data-stu-id="dd4a0-137">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="dd4a0-138">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="dd4a0-138">*z = 0*</span></span>
| <span data-ttu-id="dd4a0-139">x\y</span><span class="sxs-lookup"><span data-stu-id="dd4a0-139">x\y</span></span>   | <span data-ttu-id="dd4a0-140">0</span><span class="sxs-lookup"><span data-stu-id="dd4a0-140">0</span></span> | <span data-ttu-id="dd4a0-141">1</span><span class="sxs-lookup"><span data-stu-id="dd4a0-141">1</span></span> |
|-------|---|---|
| <span data-ttu-id="dd4a0-142">**0**</span><span class="sxs-lookup"><span data-stu-id="dd4a0-142">**0**</span></span> | <span data-ttu-id="dd4a0-143">0</span><span class="sxs-lookup"><span data-stu-id="dd4a0-143">0</span></span> | <span data-ttu-id="dd4a0-144">1</span><span class="sxs-lookup"><span data-stu-id="dd4a0-144">1</span></span> |
| <span data-ttu-id="dd4a0-145">**1**</span><span class="sxs-lookup"><span data-stu-id="dd4a0-145">**1**</span></span> | <span data-ttu-id="dd4a0-146">2</span><span class="sxs-lookup"><span data-stu-id="dd4a0-146">2</span></span> | <span data-ttu-id="dd4a0-147">3</span><span class="sxs-lookup"><span data-stu-id="dd4a0-147">3</span></span> |

<span data-ttu-id="dd4a0-148">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="dd4a0-148">*z = 1*</span></span>
| <span data-ttu-id="dd4a0-149">x\y</span><span class="sxs-lookup"><span data-stu-id="dd4a0-149">x\y</span></span>   | <span data-ttu-id="dd4a0-150">0</span><span class="sxs-lookup"><span data-stu-id="dd4a0-150">0</span></span> | <span data-ttu-id="dd4a0-151">1</span><span class="sxs-lookup"><span data-stu-id="dd4a0-151">1</span></span> |
|-------|---|---|
| <span data-ttu-id="dd4a0-152">**0**</span><span class="sxs-lookup"><span data-stu-id="dd4a0-152">**0**</span></span> | <span data-ttu-id="dd4a0-153">4</span><span class="sxs-lookup"><span data-stu-id="dd4a0-153">4</span></span> | <span data-ttu-id="dd4a0-154">5</span><span class="sxs-lookup"><span data-stu-id="dd4a0-154">5</span></span> |
| <span data-ttu-id="dd4a0-155">**1**</span><span class="sxs-lookup"><span data-stu-id="dd4a0-155">**1**</span></span> | <span data-ttu-id="dd4a0-156">6</span><span class="sxs-lookup"><span data-stu-id="dd4a0-156">6</span></span> | <span data-ttu-id="dd4a0-157">7</span><span class="sxs-lookup"><span data-stu-id="dd4a0-157">7</span></span> |

<span data-ttu-id="dd4a0-158">Se você quiser extrair a fatia `[| 4; 5 |]` da matriz, use uma fatia de índice fixo.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-158">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

```fsharp
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

<span data-ttu-id="dd4a0-159">A última linha corrige o `y` e as `z` índicos da matriz 3D e leva o restante dos `x` valores que correspondem à matriz.</span><span class="sxs-lookup"><span data-stu-id="dd4a0-159">The last line fixes the `y` and `z` indicies of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd4a0-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd4a0-160">See also</span></span>

- [<span data-ttu-id="dd4a0-161">Propriedades indexadas</span><span class="sxs-lookup"><span data-stu-id="dd4a0-161">Indexed properties</span></span>](./members/indexed-properties.md)

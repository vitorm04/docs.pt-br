---
title: FatiasF#()
description: Saiba mais sobre como usar fatias para F# tipos de dados existentes e como definir suas próprias fatias para outros tipos de dados.
ms.date: 01/22/2019
ms.openlocfilehash: cbff1b055ea99ef708f9db191be49275e630ee90
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798913"
---
# <a name="slices"></a>Fatias

No F#, uma fatia é um subconjunto de um tipo de dados. Para poder tirar uma fatia de um tipo de dados, o tipo de dados deve definir um `GetSlice` método ou em uma [extensão de tipo](type-extensions.md) que esteja no escopo. Este artigo explica como obter fatias de tipos F# existentes e como definir seus próprios.

As fatias são semelhantes aos [indexadores](./members/indexed-properties.md), mas em vez de produzir um único valor da estrutura de dados subjacente, elas produzem várias delas.

F#atualmente tem suporte intrínseco para cadeias de caracteres de divisão, listas, matrizes e matrizes 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Divisão básica com F# listas e matrizes

Os tipos de dados mais comuns que são segmentados F# são listas e matrizes. O exemplo a seguir demonstra como fazer isso com listas:

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

As matrizes de divisão são apenas como listas de fatias:

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

## <a name="slicing-multidimensional-arrays"></a>Fatiando matrizes multidimensionais

F#dá suporte a F# matrizes multidimensionais na biblioteca principal. Assim como acontece com matrizes unidimensionais, as fatias de matrizes multidimensionais também podem ser úteis. No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa colocar fatias de linhas e colunas específicas.

Os exemplos a seguir demonstram como dividir uma matriz 2D:

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

A F# biblioteca principal não define`GetSlice`para matrizes 3D. Se você quiser segmentar essas ou outras matrizes de mais dimensões, você deve definir o membro `GetSlice` por conta própria.

## <a name="defining-slices-for-other-data-structures"></a>Definindo fatias para outras estruturas de dados

A F# biblioteca principal define fatias para um conjunto limitado de tipos. Se você quiser definir fatias para mais tipos de dados, poderá fazer isso na própria definição de tipo ou em uma extensão de tipo.

Por exemplo, veja como você pode definir fatias para a classe <xref:System.ArraySegment%601> para permitir uma manipulação de dados conveniente:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Use o Outlining para evitar boxing, se necessário

Se você estiver definindo fatias para um tipo que é realmente uma struct, é recomendável `inline` o membro `GetSlice`. O F# compilador otimiza os argumentos opcionais, evitando qualquer alocação de heap como resultado de divisão. Isso é extremamente importante para as construções de fatias, como <xref:System.Span%601> que não podem ser alocadas no heap.

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

## <a name="see-also"></a>Consulte também

- [Propriedades indexadas](./members/indexed-properties.md)

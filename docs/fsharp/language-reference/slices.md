---
title: Fatias (F#)
description: Saiba mais sobre como usar fatias existentes F# tipos de dados e como definir seus próprios fatias para outros tipos de dados.
ms.date: 01/22/2019
ms.openlocfilehash: 60b57d4eea40bb26dc43d8255dd933b63ac6303c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970098"
---
# <a name="slices"></a>Fatias

No F#, uma fatia é um subconjunto de um tipo de dados. Para poder tirar uma fatia de um tipo de dados, o tipo de dados deve definir um `GetSlice` método ou em um [extensão de tipo](type-extensions.md) que é em escopo. Este artigo explica como aproveitar as fatias de existente F# tipos e como definir seus próprios.

Fatias são semelhantes às [indexadores](members/indexed-properties.md), mas em vez da estrutura de dados subjacente que rende um valor único, geram várias dessas classes.

F#no momento tem suporte intrínseco para matrizes 2D, listas, matrizes e cadeias de caracteres de divisão.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Divisão básica com o F# matrizes e listas

Os tipos de dados mais comuns que são subconjuntos são F# matrizes e listas. O exemplo a seguir demonstra como fazer isso com listas:

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

Matrizes de divisão é exatamente como listas de divisão:

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

## <a name="slicing-multidimensional-arrays"></a>Divisão de matrizes multidimensionais

F#dá suporte a matrizes multidimensionais no F# biblioteca principal. Assim como ocorre com matrizes unidimensionais, fatias de matrizes multidimensionais também podem ser útil. No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa tomar as fatias de linhas e colunas específicas.

Os exemplos a seguir demonstram como uma matriz de 2D de fatia:

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
printfn "%A" twobyTwo
```

O F# biblioteca principal não define `GetSlice`para matrizes 3D. Se você quiser dividir aqueles ou outras matrizes ou mais dimensões, você deve definir o `GetSlice` membro por conta própria.

## <a name="defining-slices-for-other-data-structures"></a>Definir fatias para outras estruturas de dados

O F# biblioteca principal define fatias para um conjunto limitado de tipos. Se você quiser definir fatias para mais tipos de dados, você pode fazer isso na definição de tipo em si ou em uma extensão de tipo.

Por exemplo, aqui está como você pode definir fatias para o <xref:System.ArraySegment%601> classe para permitir a manipulação de dados conveniente:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Use inlining para evitar a conversão boxing se for necessário

Se você estiver definindo fatias para um tipo que é, na verdade, um struct, recomendamos que você `inline` o `GetSlice` membro. O F# compilador otimizará os argumentos opcionais, evitando as alocações de heap como resultado da divisão. Isso é extremamente importante para construções de divisão, como <xref:System.Span%601> que não podem ser alocados no heap.

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

- [Propriedades indexadas](members/indexed-properties.md)

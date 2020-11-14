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
# <a name="slices"></a>Fatias

Em F #, uma fatia é um subconjunto de qualquer tipo de dados que tem um `GetSlice` método em sua definição ou em uma [extensão de tipo](type-extensions.md)no escopo. Ele é mais comumente usado com matrizes e listas de F #. Este artigo explica como tirar fatias de tipos existentes de F # e como definir suas próprias fatias.

As fatias são semelhantes aos [indexadores](./members/indexed-properties.md), mas em vez de produzir um único valor da estrutura de dados subjacente, elas produzem várias delas.

O F # atualmente tem suporte intrínseco para cadeias de caracteres de divisão, listas, matrizes e matrizes 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Divisão básica com listas e matrizes F #

Os tipos de dados mais comuns que são segmentados são listas e matrizes de F #. O exemplo a seguir demonstra como fazer isso com listas:

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

O f # dá suporte a matrizes multidimensionais na biblioteca principal do F #. Assim como acontece com matrizes unidimensionais, as fatias de matrizes multidimensionais também podem ser úteis. No entanto, a introdução de dimensões adicionais exige uma sintaxe ligeiramente diferente para que você possa colocar fatias de linhas e colunas específicas.

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

A biblioteca de núcleos F # não define atualmente `GetSlice` para matrizes 3D. Se você quiser fatiar matrizes 3D ou outras matrizes de mais dimensões, defina o `GetSlice` membro por conta própria.

## <a name="defining-slices-for-other-data-structures"></a>Definindo fatias para outras estruturas de dados

A biblioteca de núcleos F # define fatias para um conjunto limitado de tipos. Se você quiser definir fatias para mais tipos de dados, poderá fazer isso na própria definição de tipo ou em uma extensão de tipo.

Por exemplo, veja como você pode definir fatias para a <xref:System.ArraySegment%601> classe para permitir uma manipulação de dados conveniente:

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

Outro exemplo que usa <xref:System.Span%601> os <xref:System.ReadOnlySpan%601> tipos e:

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

## <a name="built-in-f-slices-are-end-inclusive"></a>As fatias F # internas são inclusivas

Todas as fatias intrínsecas em F # são inclusivas; ou seja, o limite superior é incluído na fatia. Para uma determinada fatia com índice inicial `x` e índice final `y` , a fatia resultante incluirá o valor *YTH* .

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a>Fatias internas F # vazias

Listas F #, matrizes, sequências, cadeias de caracteres, matrizes 2D, matrizes 3D e matrizes 4D produzirão uma fatia vazia se a sintaxe puder produzir uma fatia que não existe.

Considere o seguinte:

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

Os desenvolvedores de C# podem esperar que eles lancem uma exceção em vez de produzir uma fatia vazia. Essa é uma decisão de design enraizada no fato de que coleções vazias compõem em F #. Uma lista de F # vazia pode ser composta com outra lista de F #, uma cadeia de caracteres vazia pode ser adicionada a uma cadeia de caracteres existente e assim por diante. Pode ser comum pegar fatias com base nos valores passados como parâmetros e ser tolerante a fora dos limites, produzindo uma coleção vazia se ajusta à natureza composicional do código F #.

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a>Fatias de índice fixo para matrizes 3D e 4D

Para matrizes F # 3D e 4D, você pode "corrigir" um índice específico e fatiar outras dimensões com esse índice fixo.

Para ilustrar isso, considere a seguinte matriz 3D:

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Se você quiser extrair a fatia `[| 4; 5 |]` da matriz, use uma fatia de índice fixo.

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

A última linha corrige o `y` e as `z` índicos da matriz 3D e leva o restante dos `x` valores que correspondem à matriz.

## <a name="see-also"></a>Consulte também

- [Propriedades indexadas](./members/indexed-properties.md)

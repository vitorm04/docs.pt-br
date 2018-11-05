---
title: 'A palavra-chave Fixed (F #)'
description: "Saiba como você pode \"pin\" um local para a pilha para evitar a coleta com o F # 'fixed' palavra-chave."
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45624503"
---
# <a name="the-fixed-keyword"></a>A palavra-chave Fixed

F # 4.1 apresenta o `fixed` palavra-chave, que permite que você "fixar" em um local para a pilha para impedir que ele seja coletado ou movido durante a coleta de lixo.  Ele é usado para cenários de programação de nível baixo.

## <a name="syntax"></a>Sintaxe

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Comentários

Isso estende a sintaxe de expressões para permitir a extração de um ponteiro e associá-la a um nome que é impedido de ser coletado ou movido durante a coleta de lixo.  

Um ponteiro de uma expressão é corrigido por meio de `fixed` palavra-chave está associado a um identificador por meio do `use` palavra-chave.  A semântica isso é semelhante ao gerenciamento de recursos por meio de `use` palavra-chave.  O ponteiro é fixa enquanto ele está no escopo e, depois que ele está fora do escopo, não é fixo.  `fixed` não pode ser usado fora do contexto de um `use` associação.  Você deve associar o ponteiro para um nome com `use`.

Uso de `fixed` deve ocorrer dentro de uma expressão em uma função ou um método.  Ele não pode ser usado em um escopo de nível de script ou módulo.

Como todos os códigos de ponteiro, isso é um recurso que não é seguro e emitirá um aviso quando usado.

## <a name="example"></a>Exemplo

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Consulte também

- [Módulo NativePtr](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)

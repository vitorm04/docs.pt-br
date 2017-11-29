---
title: 'A palavra-chave Fixed (F #)'
description: "Saiba como você pode 'Fixar' um local para a pilha para evitar a coleta da a F # 'fixed' palavra-chave."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: ac6be2bb9df8da1b6d0a29c2e27f777eade07cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="the-fixed-keyword"></a>A palavra-chave Fixed

F # 4.1 apresenta o `fixed` palavra-chave, que permite que você "fixar" em um local para a pilha para impedir que ele seja coletado ou movido durante a coleta de lixo.  Ele é usado para cenários de programação de nível inferior.

## <a name="syntax"></a>Sintaxe

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Comentários

Isso estende a sintaxe das expressões para permitir que um ponteiro de extração e vinculá-la a um nome que será impedido de ser coletado ou movido durante a coleta de lixo.  

Um ponteiro de uma expressão é fixa por meio de `fixed` palavra-chave é associada a um identificador por meio de `use` palavra-chave.  A semântica isso é semelhante ao gerenciamento de recursos por meio de `use` palavra-chave.  O ponteiro é fixa enquanto ele está no escopo e, depois que ele está fora do escopo, ela não é fixa.  `fixed`não pode ser usado fora do contexto de um `use` associação.  Você deve associar o ponteiro para um nome com `use`.

O uso de `fixed` deve ocorrer dentro de uma expressão em uma função ou um método.  Ele não pode ser usado em um escopo de nível de script ou módulo.

Como todo o código de ponteiro, isso é um recurso não seguro e emitirá um aviso quando usado.

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

[Módulo NativePtr](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)

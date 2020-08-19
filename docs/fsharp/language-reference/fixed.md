---
title: A palavra-chave Fixed
description: 'Saiba como você pode "fixar" um local na pilha para evitar a coleta com a palavra-chave "fixed" do F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 786ffd706c243fc83f8fb3afc2201d2a34536372
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559174"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="f7168-103">A palavra-chave Fixed</span><span class="sxs-lookup"><span data-stu-id="f7168-103">The fixed keyword</span></span>

<span data-ttu-id="f7168-104">A `fixed` palavra-chave permite que você "fixe" um local na pilha para impedir que ele seja coletado ou movido durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f7168-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="f7168-105">Ele é usado para cenários de programação de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="f7168-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7168-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7168-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="f7168-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7168-107">Remarks</span></span>

<span data-ttu-id="f7168-108">Isso estende a sintaxe de expressões para permitir a extração de um ponteiro e a vinculação a um nome que é impedido de ser coletado ou movido durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="f7168-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="f7168-109">Um ponteiro de uma expressão é corrigido por meio da `fixed` palavra-chave é associado a um identificador por meio da `use` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f7168-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="f7168-110">A semântica disso é semelhante ao gerenciamento de recursos por meio da `use` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f7168-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="f7168-111">O ponteiro é fixo enquanto está no escopo e, quando está fora do escopo, ele não é mais fixo.</span><span class="sxs-lookup"><span data-stu-id="f7168-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="f7168-112">`fixed` Não pode ser usado fora do contexto de uma `use` associação.</span><span class="sxs-lookup"><span data-stu-id="f7168-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="f7168-113">Você deve associar o ponteiro a um nome com `use` .</span><span class="sxs-lookup"><span data-stu-id="f7168-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="f7168-114">O uso de `fixed` deve ocorrer dentro de uma expressão em uma função ou um método.</span><span class="sxs-lookup"><span data-stu-id="f7168-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="f7168-115">Ele não pode ser usado em um escopo de nível de script ou de módulo.</span><span class="sxs-lookup"><span data-stu-id="f7168-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="f7168-116">Como todo o código de ponteiro, esse é um recurso não seguro e emitirá um aviso quando usado.</span><span class="sxs-lookup"><span data-stu-id="f7168-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="f7168-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7168-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f7168-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7168-118">See also</span></span>

- [<span data-ttu-id="f7168-119">Módulo NativePtr</span><span class="sxs-lookup"><span data-stu-id="f7168-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)

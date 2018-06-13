---
title: 'A palavra-chave Fixed (F #)'
description: "Saiba como você pode 'Fixar' um local para a pilha para evitar a coleta da a F # 'fixed' palavra-chave."
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563870"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="9ea91-103">A palavra-chave Fixed</span><span class="sxs-lookup"><span data-stu-id="9ea91-103">The Fixed Keyword</span></span>

<span data-ttu-id="9ea91-104">F # 4.1 apresenta o `fixed` palavra-chave, que permite que você "fixar" em um local para a pilha para impedir que ele seja coletado ou movido durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ea91-104">F# 4.1 introduces the `fixed` keyword, which allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="9ea91-105">Ele é usado para cenários de programação de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="9ea91-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ea91-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ea91-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="9ea91-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ea91-107">Remarks</span></span>

<span data-ttu-id="9ea91-108">Isso estende a sintaxe das expressões para permitir que um ponteiro de extração e vinculá-la a um nome que será impedido de ser coletado ou movido durante a coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9ea91-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="9ea91-109">Um ponteiro de uma expressão é fixa por meio de `fixed` palavra-chave é associada a um identificador por meio de `use` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9ea91-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="9ea91-110">A semântica isso é semelhante ao gerenciamento de recursos por meio de `use` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9ea91-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="9ea91-111">O ponteiro é fixa enquanto ele está no escopo e, depois que ele está fora do escopo, ela não é fixa.</span><span class="sxs-lookup"><span data-stu-id="9ea91-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="9ea91-112">`fixed` não pode ser usado fora do contexto de um `use` associação.</span><span class="sxs-lookup"><span data-stu-id="9ea91-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="9ea91-113">Você deve associar o ponteiro para um nome com `use`.</span><span class="sxs-lookup"><span data-stu-id="9ea91-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="9ea91-114">O uso de `fixed` deve ocorrer dentro de uma expressão em uma função ou um método.</span><span class="sxs-lookup"><span data-stu-id="9ea91-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="9ea91-115">Ele não pode ser usado em um escopo de nível de script ou módulo.</span><span class="sxs-lookup"><span data-stu-id="9ea91-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="9ea91-116">Como todo o código de ponteiro, isso é um recurso não seguro e emitirá um aviso quando usado.</span><span class="sxs-lookup"><span data-stu-id="9ea91-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="9ea91-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ea91-117">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9ea91-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ea91-118">See Also</span></span>

[<span data-ttu-id="9ea91-119">Módulo NativePtr</span><span class="sxs-lookup"><span data-stu-id="9ea91-119">NativePtr Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)

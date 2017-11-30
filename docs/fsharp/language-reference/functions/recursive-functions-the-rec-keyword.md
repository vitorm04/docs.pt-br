---
title: "Funções recursivas: a palavra-chave rec (F#)"
description: "Saiba como a palavra-chave F # 'rec' é usada com a palavra-chave 'let' para definir uma função recursiva."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="5ebfd-104">Funções recursivas: a palavra-chave rec</span><span class="sxs-lookup"><span data-stu-id="5ebfd-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="5ebfd-105">O `rec` palavra-chave é usada junto com o `let` palavra-chave para definir uma função recursiva.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="5ebfd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ebfd-106">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="5ebfd-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ebfd-107">Remarks</span></span>
<span data-ttu-id="5ebfd-108">Funções recursivas, funções que chamam, são identificadas explicitamente na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="5ebfd-109">Isso disponibiliza o identificador que é definido no escopo da função.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="5ebfd-110">O código a seguir ilustra uma função recursiva que calcula o  *n* th Fibonacci número.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="5ebfd-111">Na prática, o código desse acima é desperdício de tempo do processador e memória porque ela envolve o recálculo de valores computados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="5ebfd-112">Métodos são implicitamente recursiva dentro do tipo; não é necessário adicionar o `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="5ebfd-113">Associações Let em classes não são implicitamente recursiva.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="5ebfd-114">Funções mutuamente recursivas</span><span class="sxs-lookup"><span data-stu-id="5ebfd-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="5ebfd-115">Às vezes, são funções *mutuamente recursivas*, que significa que as chamadas formam um círculo, em que uma função chama outro que por sua vez, chama a primeira, com qualquer número de chamadas entre.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="5ebfd-116">Você deve definir essas funções juntas no `let` de associação, usando o `and` palavra-chave para vinculá-los juntos.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="5ebfd-117">O exemplo a seguir mostra duas mutuamente funções recursivas.</span><span class="sxs-lookup"><span data-stu-id="5ebfd-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="5ebfd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ebfd-118">See Also</span></span>
[<span data-ttu-id="5ebfd-119">Funções</span><span class="sxs-lookup"><span data-stu-id="5ebfd-119">Functions</span></span>](index.md)

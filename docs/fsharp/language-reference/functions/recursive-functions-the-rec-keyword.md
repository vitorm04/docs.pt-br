---
title: 'Funções recursivas: a palavra-chave rec (F#)'
description: "Saiba como a palavra-chave F # 'rec' é usada com a palavra-chave 'let' para definir uma função recursiva."
ms.date: 05/16/2016
ms.openlocfilehash: 5aab6ed8ab0fc3c0f0bcfc93c3ce6518ec53254f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710814"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="f989c-103">Funções recursivas: a palavra-chave rec</span><span class="sxs-lookup"><span data-stu-id="f989c-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="f989c-104">O `rec` palavra-chave é usada junto com o `let` palavra-chave para definir uma função recursiva.</span><span class="sxs-lookup"><span data-stu-id="f989c-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="f989c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f989c-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="f989c-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="f989c-106">Remarks</span></span>

<span data-ttu-id="f989c-107">Funções recursivas, funções que chamam seu site, são identificadas explicitamente na linguagem F #.</span><span class="sxs-lookup"><span data-stu-id="f989c-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="f989c-108">Isso disponibiliza o identificador que está sendo definido no escopo da função.</span><span class="sxs-lookup"><span data-stu-id="f989c-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="f989c-109">O código a seguir ilustra uma função recursiva que calcula a *n*<sup>th</sup> número Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="f989c-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="f989c-110">Na prática, o código acima como esse é um desperdício de tempo do processador e memória porque ela envolve o recálculo dos valores computados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f989c-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="f989c-111">Métodos são implicitamente recursivos dentro do tipo; não é necessário adicionar o `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f989c-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="f989c-112">Associações Let em classes não são implicitamente recursivos.</span><span class="sxs-lookup"><span data-stu-id="f989c-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="f989c-113">Funções mutuamente recursivas</span><span class="sxs-lookup"><span data-stu-id="f989c-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="f989c-114">Às vezes, são funções *mutuamente recursivas*, que significa que chamadas formam um círculo, em que uma função chama outra que por sua vez chama o primeiro, com qualquer número de chamadas entre os dois.</span><span class="sxs-lookup"><span data-stu-id="f989c-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="f989c-115">Você deve definir essas funções juntas em um `let` vinculação, usando o `and` palavra-chave para vinculá-los.</span><span class="sxs-lookup"><span data-stu-id="f989c-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="f989c-116">O exemplo a seguir mostra dois mutuamente funções recursivas.</span><span class="sxs-lookup"><span data-stu-id="f989c-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="f989c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f989c-117">See also</span></span>

- [<span data-ttu-id="f989c-118">Funções</span><span class="sxs-lookup"><span data-stu-id="f989c-118">Functions</span></span>](index.md)

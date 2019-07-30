---
title: 'Funções recursivas: A palavra-chave REC'
description: Saiba como a F# palavra-chave ' Rec ' é usada com a palavra-chave ' Let ' para definir uma função recursiva.
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630659"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="f38f2-103">Funções recursivas: A palavra-chave REC</span><span class="sxs-lookup"><span data-stu-id="f38f2-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="f38f2-104">A `rec` palavra-chave é usada junto `let` com a palavra-chave para definir uma função recursiva.</span><span class="sxs-lookup"><span data-stu-id="f38f2-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="f38f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f38f2-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="f38f2-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="f38f2-106">Remarks</span></span>

<span data-ttu-id="f38f2-107">Funções recursivas, funções que chamam a si mesmas, são identificadas explicitamente no F# idioma.</span><span class="sxs-lookup"><span data-stu-id="f38f2-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="f38f2-108">Isso torna o identificador que está sendo definido disponível no escopo da função.</span><span class="sxs-lookup"><span data-stu-id="f38f2-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="f38f2-109">O código a seguir ilustra uma função recursiva que computa o número *n*<sup>ésimo</sup> Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="f38f2-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="f38f2-110">Na prática, um código como esse acima é desperdício de memória e tempo do processador, pois envolve a recomputação de valores calculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f38f2-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="f38f2-111">Os métodos são recursivos implicitamente dentro do tipo; Não é necessário adicionar a `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="f38f2-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="f38f2-112">Permitir que associações dentro de classes não sejam recursivas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="f38f2-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="f38f2-113">Funções recursivas mutuamente</span><span class="sxs-lookup"><span data-stu-id="f38f2-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="f38f2-114">Às vezes, as funções são recursivas *mutuamente*, o que significa que as chamadas formam um círculo, em que uma função chama outra que, por sua vez, chama a primeira, com qualquer número de chamadas entre elas.</span><span class="sxs-lookup"><span data-stu-id="f38f2-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="f38f2-115">Você deve definir essas funções juntas em uma `let` associação, usando a `and` palavra-chave para vinculá-las.</span><span class="sxs-lookup"><span data-stu-id="f38f2-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="f38f2-116">O exemplo a seguir mostra duas funções recursivas mutuamente.</span><span class="sxs-lookup"><span data-stu-id="f38f2-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="f38f2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f38f2-117">See also</span></span>

- [<span data-ttu-id="f38f2-118">Funções</span><span class="sxs-lookup"><span data-stu-id="f38f2-118">Functions</span></span>](index.md)

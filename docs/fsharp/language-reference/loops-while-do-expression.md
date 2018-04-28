---
title: 'Loops: expressão while...do (F#)'
description: Veja como o while... Faça expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true.
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 847f99faab42c8805bd788e42e3f24ad6369ba52
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="9a17b-103">Loops: expressão while...do</span><span class="sxs-lookup"><span data-stu-id="9a17b-103">Loops: while...do Expression</span></span>

<span data-ttu-id="9a17b-104">O `while...do` expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true.</span><span class="sxs-lookup"><span data-stu-id="9a17b-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="9a17b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a17b-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="9a17b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a17b-106">Remarks</span></span>
<span data-ttu-id="9a17b-107">O *expressão de teste* é avaliada; se for `true`, o *corpo da expressão* é executado e a expressão é avaliada novamente.</span><span class="sxs-lookup"><span data-stu-id="9a17b-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="9a17b-108">O *corpo da expressão* deve ser do tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="9a17b-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="9a17b-109">Se a expressão de teste é `false`, as extremidades de iteração.</span><span class="sxs-lookup"><span data-stu-id="9a17b-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="9a17b-110">O exemplo a seguir ilustra o uso do `while...do` expressão.</span><span class="sxs-lookup"><span data-stu-id="9a17b-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="9a17b-111">A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, a última delas é 10.</span><span class="sxs-lookup"><span data-stu-id="9a17b-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="9a17b-112">Você pode usar `while...do` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `while...do` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="9a17b-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="9a17b-113">Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9a17b-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="9a17b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a17b-114">See Also</span></span>
[<span data-ttu-id="9a17b-115">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="9a17b-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="9a17b-116">Loops: `for...in` expressão</span><span class="sxs-lookup"><span data-stu-id="9a17b-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="9a17b-117">Loops: `for...to` expressão</span><span class="sxs-lookup"><span data-stu-id="9a17b-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

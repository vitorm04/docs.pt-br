---
title: "Loops: expressão while...do (F#)"
description: "Veja como o while... Faça expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="26c09-104">Loops: expressão while...do</span><span class="sxs-lookup"><span data-stu-id="26c09-104">Loops: while...do Expression</span></span>

<span data-ttu-id="26c09-105">O `while...do` expressão é usada para realizar execução iterativa (loop) enquanto uma condição de teste especificado é true.</span><span class="sxs-lookup"><span data-stu-id="26c09-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="26c09-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26c09-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="26c09-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="26c09-107">Remarks</span></span>
<span data-ttu-id="26c09-108">O *expressão de teste* é avaliada; se for `true`, o *corpo da expressão* é executado e a expressão é avaliada novamente.</span><span class="sxs-lookup"><span data-stu-id="26c09-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="26c09-109">O *corpo da expressão* deve ser do tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="26c09-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="26c09-110">Se a expressão de teste é `false`, as extremidades de iteração.</span><span class="sxs-lookup"><span data-stu-id="26c09-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="26c09-111">O exemplo a seguir ilustra o uso do `while...do` expressão.</span><span class="sxs-lookup"><span data-stu-id="26c09-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="26c09-112">A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, a última delas é 10.</span><span class="sxs-lookup"><span data-stu-id="26c09-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="26c09-113">Você pode usar `while...do` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `while...do` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="26c09-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="26c09-114">Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="26c09-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="26c09-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26c09-115">See Also</span></span>
[<span data-ttu-id="26c09-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="26c09-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="26c09-117">Loops: `for...in` expressão</span><span class="sxs-lookup"><span data-stu-id="26c09-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="26c09-118">Loops: `for...to` expressão</span><span class="sxs-lookup"><span data-stu-id="26c09-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

---
title: "Computações lentas (F#)"
description: "Saiba como F # computações lentas podem melhorar o desempenho de aplicativos e bibliotecas."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a><span data-ttu-id="242d9-104">Computações lentas</span><span class="sxs-lookup"><span data-stu-id="242d9-104">Lazy Computations</span></span>

<span data-ttu-id="242d9-105">*Computações lentas* são cálculos que não são avaliados imediatamente, mas em vez disso, são avaliados quando o resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="242d9-105">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="242d9-106">Isso pode ajudar a melhorar o desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="242d9-106">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="242d9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="242d9-107">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="242d9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="242d9-108">Remarks</span></span>

<span data-ttu-id="242d9-109">Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado.</span><span class="sxs-lookup"><span data-stu-id="242d9-109">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="242d9-110">O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), onde o tipo que é usado para `'T` é determinado a partir do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="242d9-110">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="242d9-111">Computações lentas permitem melhorar o desempenho, restringindo a execução de um cálculo para somente nas situações em que um resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="242d9-111">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="242d9-112">Para forçar o cálculo a ser executada, você pode chamar o método `Force`.</span><span class="sxs-lookup"><span data-stu-id="242d9-112">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="242d9-113">`Force`faz com que a execução seja executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="242d9-113">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="242d9-114">As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não executa qualquer código.</span><span class="sxs-lookup"><span data-stu-id="242d9-114">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="242d9-115">O código a seguir ilustra o uso de computação lenta e o uso de `Force`.</span><span class="sxs-lookup"><span data-stu-id="242d9-115">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="242d9-116">Nesse código, o tipo de `result` é `Lazy<int>`e o `Force` método retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="242d9-116">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="242d9-117">Avaliação lenta, mas não o `Lazy` digite, também é usado para as sequências.</span><span class="sxs-lookup"><span data-stu-id="242d9-117">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="242d9-118">Para obter mais informações, consulte [sequências](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="242d9-118">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="242d9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="242d9-119">See Also</span></span>

[<span data-ttu-id="242d9-120">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="242d9-120">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="242d9-121">Módulo LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="242d9-121">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)

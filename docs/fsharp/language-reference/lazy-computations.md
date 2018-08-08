---
title: Computações lentas (F#)
description: 'Saiba como F # computações lentas podem melhorar o desempenho de aplicativos e bibliotecas.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563926"
---
# <a name="lazy-computations"></a><span data-ttu-id="684b2-103">Computações lentas</span><span class="sxs-lookup"><span data-stu-id="684b2-103">Lazy Computations</span></span>

<span data-ttu-id="684b2-104">*Computações lentas* são cálculos que não são avaliados imediatamente, mas em vez disso, são avaliados quando o resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="684b2-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="684b2-105">Isso pode ajudar a melhorar o desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="684b2-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="684b2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="684b2-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="684b2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="684b2-107">Remarks</span></span>

<span data-ttu-id="684b2-108">Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado.</span><span class="sxs-lookup"><span data-stu-id="684b2-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="684b2-109">O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), onde o tipo que é usado para `'T` é determinado a partir do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="684b2-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="684b2-110">Computações lentas permitem melhorar o desempenho, restringindo a execução de um cálculo para somente nas situações em que um resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="684b2-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="684b2-111">Para forçar o cálculo a ser executada, você pode chamar o método `Force`.</span><span class="sxs-lookup"><span data-stu-id="684b2-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="684b2-112">`Force` faz com que a execução seja executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="684b2-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="684b2-113">As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não executa qualquer código.</span><span class="sxs-lookup"><span data-stu-id="684b2-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="684b2-114">O código a seguir ilustra o uso de computação lenta e o uso de `Force`.</span><span class="sxs-lookup"><span data-stu-id="684b2-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="684b2-115">Nesse código, o tipo de `result` é `Lazy<int>`e o `Force` método retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="684b2-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="684b2-116">Avaliação lenta, mas não o `Lazy` digite, também é usado para as sequências.</span><span class="sxs-lookup"><span data-stu-id="684b2-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="684b2-117">Para obter mais informações, consulte [sequências](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="684b2-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="684b2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="684b2-118">See Also</span></span>

[<span data-ttu-id="684b2-119">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="684b2-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="684b2-120">Módulo LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="684b2-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)

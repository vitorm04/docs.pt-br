---
title: Computações lentas (F#)
description: 'Saiba como as computações lentas do F # podem melhorar o desempenho de seus aplicativos e bibliotecas.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45698202"
---
# <a name="lazy-computations"></a><span data-ttu-id="f6a65-103">Computações lentas</span><span class="sxs-lookup"><span data-stu-id="f6a65-103">Lazy Computations</span></span>

<span data-ttu-id="f6a65-104">*Computações lentas* são cálculos que não são avaliados imediatamente, mas em vez disso, são avaliados quando o resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="f6a65-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="f6a65-105">Isso pode ajudar a melhorar o desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="f6a65-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="f6a65-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6a65-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="f6a65-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6a65-107">Remarks</span></span>

<span data-ttu-id="f6a65-108">Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado.</span><span class="sxs-lookup"><span data-stu-id="f6a65-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="f6a65-109">O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), em que o valor real de tipo que é usado para `'T` é determinado a partir do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="f6a65-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="f6a65-110">Computações lentas que você possa melhorar o desempenho, restringindo a execução de um cálculo para somente essas situações em que um resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="f6a65-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="f6a65-111">Para forçar o cálculo a ser executada, você chama o método `Force`.</span><span class="sxs-lookup"><span data-stu-id="f6a65-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="f6a65-112">`Force` faz com que a execução a ser executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="f6a65-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="f6a65-113">As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não execute qualquer código.</span><span class="sxs-lookup"><span data-stu-id="f6a65-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="f6a65-114">O código a seguir ilustra o uso de computação lenta e o uso de `Force`.</span><span class="sxs-lookup"><span data-stu-id="f6a65-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="f6a65-115">Nesse código, o tipo de `result` está `Lazy<int>`e o `Force` método retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="f6a65-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="f6a65-116">A avaliação lenta, mas não o `Lazy` de tipo, também é usado para as sequências.</span><span class="sxs-lookup"><span data-stu-id="f6a65-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="f6a65-117">Para obter mais informações, consulte [sequências](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="f6a65-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6a65-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6a65-118">See also</span></span>

- [<span data-ttu-id="f6a65-119">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="f6a65-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f6a65-120">Módulo LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="f6a65-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)

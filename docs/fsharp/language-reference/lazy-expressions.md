---
title: Expressões lentas
description: Saiba como F# expressões lentas podem melhorar o desempenho de seus aplicativos e bibliotecas.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904105"
---
# <a name="lazy-expressions"></a><span data-ttu-id="38be3-103">Expressões lentas</span><span class="sxs-lookup"><span data-stu-id="38be3-103">Lazy Expressions</span></span>

<span data-ttu-id="38be3-104">*Expressões lentas* são expressões que não são avaliadas imediatamente, mas em vez disso, são avaliadas quando o resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="38be3-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="38be3-105">Isso pode ajudar a melhorar o desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="38be3-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="38be3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38be3-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="38be3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="38be3-107">Remarks</span></span>

<span data-ttu-id="38be3-108">Na sintaxe anterior, *expressão* é o código que é avaliado somente quando um resultado é necessário, e *identificador* é um valor que armazena o resultado.</span><span class="sxs-lookup"><span data-stu-id="38be3-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="38be3-109">O valor é do tipo [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), em que o valor real de tipo que é usado para `'T` é determinado a partir do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="38be3-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="38be3-110">Expressões lentas permitem que você melhorar o desempenho, restringindo a execução de uma expressões para somente essas situações em que um resultado é necessária.</span><span class="sxs-lookup"><span data-stu-id="38be3-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="38be3-111">Para forçar as expressões a serem executadas, você chama o método `Force`.</span><span class="sxs-lookup"><span data-stu-id="38be3-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="38be3-112">`Force` faz com que a execução a ser executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="38be3-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="38be3-113">As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não execute qualquer código.</span><span class="sxs-lookup"><span data-stu-id="38be3-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="38be3-114">O código a seguir ilustra o uso de expressões lentas e o uso de `Force`.</span><span class="sxs-lookup"><span data-stu-id="38be3-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="38be3-115">Nesse código, o tipo de `result` está `Lazy<int>`e o `Force` método retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="38be3-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="38be3-116">A avaliação lenta, mas não o `Lazy` de tipo, também é usado para as sequências.</span><span class="sxs-lookup"><span data-stu-id="38be3-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="38be3-117">Para obter mais informações, consulte [sequências](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="38be3-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38be3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38be3-118">See also</span></span>

- [<span data-ttu-id="38be3-119">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="38be3-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="38be3-120">Módulo LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="38be3-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)

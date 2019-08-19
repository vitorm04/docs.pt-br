---
title: Expressões lentas
description: Saiba como F# as expressões lentas podem melhorar o desempenho de seus aplicativos e bibliotecas.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630742"
---
# <a name="lazy-expressions"></a><span data-ttu-id="c4a7d-103">Expressões lentas</span><span class="sxs-lookup"><span data-stu-id="c4a7d-103">Lazy Expressions</span></span>

<span data-ttu-id="c4a7d-104">As *expressões lentas* são expressões que não são avaliadas imediatamente, mas, em vez disso, são avaliadas quando o resultado é necessário.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="c4a7d-105">Isso pode ajudar a melhorar o desempenho do seu código.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4a7d-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4a7d-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="c4a7d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4a7d-107">Remarks</span></span>

<span data-ttu-id="c4a7d-108">Na sintaxe anterior, *expression* é o código que é avaliado somente quando um resultado é necessário e o *identificador* é um valor que armazena o resultado.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="c4a7d-109">O valor é do tipo [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), onde o tipo real usado para `'T` é determinado a partir do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="c4a7d-110">As expressões lentas permitem melhorar o desempenho restringindo a execução de expressões para apenas as situações em que um resultado é necessário.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="c4a7d-111">Para forçar a execução das expressões, você chama o método `Force`.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="c4a7d-112">`Force`faz com que a execução seja executada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="c4a7d-113">As chamadas subsequentes para `Force` retornar o mesmo resultado, mas não executam nenhum código.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="c4a7d-114">O código a seguir ilustra o uso de expressões lentas e o `Force`uso de.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="c4a7d-115">Nesse código, o tipo `result` de é `Lazy<int>`e o `Force` método retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="c4a7d-116">A avaliação lenta, mas não `Lazy` o tipo, também é usada para sequências.</span><span class="sxs-lookup"><span data-stu-id="c4a7d-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="c4a7d-117">Para obter mais informações, consulte [sequences](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="c4a7d-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4a7d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4a7d-118">See also</span></span>

- [<span data-ttu-id="c4a7d-119">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c4a7d-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c4a7d-120">Módulo LazyExtensions</span><span class="sxs-lookup"><span data-stu-id="c4a7d-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)

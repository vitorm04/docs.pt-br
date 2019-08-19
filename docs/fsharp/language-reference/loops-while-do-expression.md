---
title: 'Loops: expressão while...do'
description: Veja como o While... a expressão do é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630757"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="0f35d-103">Loops: expressão while...do</span><span class="sxs-lookup"><span data-stu-id="0f35d-103">Loops: while...do Expression</span></span>

<span data-ttu-id="0f35d-104">A `while...do` expressão é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="0f35d-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f35d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f35d-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="0f35d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f35d-106">Remarks</span></span>

<span data-ttu-id="0f35d-107">A *expressão de teste* é avaliada; Se for `true`, a *expressão Body* será executada e a expressão de teste será avaliada novamente.</span><span class="sxs-lookup"><span data-stu-id="0f35d-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="0f35d-108">A *expressão Body* deve ter o tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="0f35d-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="0f35d-109">Se a expressão de teste `false`for, a iteração terminará.</span><span class="sxs-lookup"><span data-stu-id="0f35d-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="0f35d-110">O exemplo a seguir ilustra o uso da `while...do` expressão.</span><span class="sxs-lookup"><span data-stu-id="0f35d-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="0f35d-111">A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, o último deles é 10.</span><span class="sxs-lookup"><span data-stu-id="0f35d-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="0f35d-112">Você pode usar `while...do` em expressões de sequência e outras expressões de computação, caso em que uma versão personalizada `while...do` da expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="0f35d-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="0f35d-113">Para obter mais informações, consulte [Sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de computação](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0f35d-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f35d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f35d-114">See also</span></span>

- [<span data-ttu-id="0f35d-115">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="0f35d-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0f35d-116">Loops `for...in`Expressão</span><span class="sxs-lookup"><span data-stu-id="0f35d-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="0f35d-117">Loops `for...to`Expressão</span><span class="sxs-lookup"><span data-stu-id="0f35d-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

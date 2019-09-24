---
title: 'Loops: expressão while...do'
description: Veja como o While... a expressão do é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.
ms.date: 05/16/2016
ms.openlocfilehash: 73526279358db101f8d07721a200920f1e87f119
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216629"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="88fc6-103">Loops: expressão while...do</span><span class="sxs-lookup"><span data-stu-id="88fc6-103">Loops: while...do Expression</span></span>

<span data-ttu-id="88fc6-104">A `while...do` expressão é usada para executar a execução iterativa (Looping) enquanto uma condição de teste especificada é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="88fc6-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="88fc6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88fc6-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="88fc6-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="88fc6-106">Remarks</span></span>

<span data-ttu-id="88fc6-107">A *expressão de teste* é avaliada; Se for `true`, a *expressão Body* será executada e a expressão de teste será avaliada novamente.</span><span class="sxs-lookup"><span data-stu-id="88fc6-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="88fc6-108">A *expressão Body* deve ter o tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="88fc6-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="88fc6-109">Se a expressão de teste `false`for, a iteração terminará.</span><span class="sxs-lookup"><span data-stu-id="88fc6-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="88fc6-110">O exemplo a seguir ilustra o uso da `while...do` expressão.</span><span class="sxs-lookup"><span data-stu-id="88fc6-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="88fc6-111">A saída do código anterior é um fluxo de números aleatórios entre 1 e 20, o último deles é 10.</span><span class="sxs-lookup"><span data-stu-id="88fc6-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```console
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="88fc6-112">Você pode usar `while...do` em expressões de sequência e outras expressões de computação, caso em que uma versão personalizada `while...do` da expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="88fc6-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="88fc6-113">Para obter mais informações, consulte [Sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md)e [expressões de computação](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="88fc6-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88fc6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88fc6-114">See also</span></span>

- [<span data-ttu-id="88fc6-115">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="88fc6-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="88fc6-116">Loops `for...in`Expressão</span><span class="sxs-lookup"><span data-stu-id="88fc6-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="88fc6-117">Loops `for...to`Expressão</span><span class="sxs-lookup"><span data-stu-id="88fc6-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

---
title: 'Loops: expressão for...to'
description: Veja como o F# para... a expressão to é usada para iterar em um loop em um intervalo de valores de uma variável de loop.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626617"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="1b582-103">Loops: expressão for...to</span><span class="sxs-lookup"><span data-stu-id="1b582-103">Loops: for...to Expression</span></span>

<span data-ttu-id="1b582-104">A `for...to` expressão é usada para iterar em um loop em um intervalo de valores de uma variável de loop.</span><span class="sxs-lookup"><span data-stu-id="1b582-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b582-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b582-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="1b582-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b582-106">Remarks</span></span>

<span data-ttu-id="1b582-107">O tipo do identificador é inferido do tipo das expressões de *início* e *término* .</span><span class="sxs-lookup"><span data-stu-id="1b582-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="1b582-108">Os tipos para essas expressões devem ser inteiros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="1b582-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="1b582-109">Embora tecnicamente uma expressão `for...to` seja mais como uma instrução tradicional em uma linguagem de programação imperativa.</span><span class="sxs-lookup"><span data-stu-id="1b582-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="1b582-110">O tipo de retorno para a *expressão Body* deve ser `unit`.</span><span class="sxs-lookup"><span data-stu-id="1b582-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="1b582-111">Os exemplos a seguir mostram vários usos da `for...to` expressão.</span><span class="sxs-lookup"><span data-stu-id="1b582-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="1b582-112">A saída do código anterior está a seguir.</span><span class="sxs-lookup"><span data-stu-id="1b582-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="1b582-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b582-113">See also</span></span>

- [<span data-ttu-id="1b582-114">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="1b582-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1b582-115">Loops `for...in`Expressão</span><span class="sxs-lookup"><span data-stu-id="1b582-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="1b582-116">Loops `while...do`Expressão</span><span class="sxs-lookup"><span data-stu-id="1b582-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)

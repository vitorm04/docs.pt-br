---
title: "Loops: expressão for...to (F#)"
description: "Veja como o F # loop for... a expressão é usado para iterar em um loop em um intervalo de valores de uma variável de loop."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="81c4a-104">Loops: expressão for...to</span><span class="sxs-lookup"><span data-stu-id="81c4a-104">Loops: for...to Expression</span></span>

<span data-ttu-id="81c4a-105">O `for...to` expressão é usada para iterar em um loop em um intervalo de valores de uma variável de loop.</span><span class="sxs-lookup"><span data-stu-id="81c4a-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="81c4a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81c4a-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="81c4a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="81c4a-107">Remarks</span></span>
<span data-ttu-id="81c4a-108">O tipo do identificador é inferido do tipo do *iniciar* e *concluir* expressões.</span><span class="sxs-lookup"><span data-stu-id="81c4a-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="81c4a-109">Tipos para essas expressões devem ser inteiros de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="81c4a-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="81c4a-110">Embora tecnicamente uma expressão, `for...to` é mais parecida com uma instrução tradicional em uma linguagem de programação imperativa.</span><span class="sxs-lookup"><span data-stu-id="81c4a-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="81c4a-111">O tipo de retorno para o *corpo da expressão* devem ser `unit`.</span><span class="sxs-lookup"><span data-stu-id="81c4a-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="81c4a-112">Os seguintes exemplos mostram vários usos do `for...to` expressão.</span><span class="sxs-lookup"><span data-stu-id="81c4a-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="81c4a-113">A saída do código anterior está a seguir.</span><span class="sxs-lookup"><span data-stu-id="81c4a-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="81c4a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81c4a-114">See Also</span></span>
[<span data-ttu-id="81c4a-115">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="81c4a-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="81c4a-116">Loops: `for...in` expressão</span><span class="sxs-lookup"><span data-stu-id="81c4a-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="81c4a-117">Loops: `while...do` expressão</span><span class="sxs-lookup"><span data-stu-id="81c4a-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)

---
title: "Expressões condicionais: if...then...else (F#)"
description: "Saiba como escrever expressões condicionais em F # para executar diferentes ramos do código."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 5823e46cd13053fcd31f94f2d79d1f7470ca5118
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="90ed0-104">Expressões condicionais: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="90ed0-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="90ed0-105">O `if...then...else` expressão executa ramificações diferentes do código e também é avaliada como um valor diferente dependendo da expressão booliana fornecido.</span><span class="sxs-lookup"><span data-stu-id="90ed0-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="90ed0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90ed0-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="90ed0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="90ed0-107">Remarks</span></span>
<span data-ttu-id="90ed0-108">Na sintaxe anterior, *expression1* é executado quando a expressão booleana for avaliada como `true`; caso contrário, *expression2* é executado.</span><span class="sxs-lookup"><span data-stu-id="90ed0-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="90ed0-109">Ao contrário em outros idiomas, o `if...then...else` construção é uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="90ed0-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="90ed0-110">Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executado.</span><span class="sxs-lookup"><span data-stu-id="90ed0-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="90ed0-111">Os tipos de valores produzidos em cada ramificação devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="90ed0-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="90ed0-112">Se não houver explícita não `else` ramificação, seu tipo é `unit`.</span><span class="sxs-lookup"><span data-stu-id="90ed0-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="90ed0-113">Portanto, se o tipo do `then` ramificação for qualquer tipo diferente de `unit`, deve haver um `else` branch com o mesmo tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="90ed0-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="90ed0-114">Ao encadear `if...then...else` expressões juntas, você pode usar a palavra-chave `elif` em vez de `else if`; eles são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="90ed0-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="90ed0-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90ed0-115">Example</span></span>
<span data-ttu-id="90ed0-116">O exemplo a seguir ilustra como usar o `if...then...else` expressão.</span><span class="sxs-lookup"><span data-stu-id="90ed0-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="90ed0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90ed0-117">See Also</span></span>
[<span data-ttu-id="90ed0-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="90ed0-118">F# Language Reference</span></span>](index.md)


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
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="af1b3-104">Expressões condicionais:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="af1b3-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="af1b3-105">O `if...then...else` expressão executa ramificações diferentes do código e também é avaliada como um valor diferente dependendo da expressão booliana fornecido.</span><span class="sxs-lookup"><span data-stu-id="af1b3-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="af1b3-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af1b3-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="af1b3-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="af1b3-107">Remarks</span></span>
<span data-ttu-id="af1b3-108">Na sintaxe anterior, *expression1* é executado quando a expressão booleana for avaliada como `true`; caso contrário, *expression2* é executado.</span><span class="sxs-lookup"><span data-stu-id="af1b3-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="af1b3-109">Ao contrário em outros idiomas, o `if...then...else` construção é uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="af1b3-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="af1b3-110">Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executado.</span><span class="sxs-lookup"><span data-stu-id="af1b3-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="af1b3-111">Os tipos de valores produzidos em cada ramificação devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="af1b3-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="af1b3-112">Se não houver explícita não `else` ramificação, seu tipo é `unit`.</span><span class="sxs-lookup"><span data-stu-id="af1b3-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="af1b3-113">Portanto, se o tipo do `then` ramificação for qualquer tipo diferente de `unit`, deve haver um `else` branch com o mesmo tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="af1b3-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="af1b3-114">Ao encadear `if...then...else` expressões juntas, você pode usar a palavra-chave `elif` em vez de `else if`; eles são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="af1b3-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="af1b3-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af1b3-115">Example</span></span>
<span data-ttu-id="af1b3-116">O exemplo a seguir ilustra como usar o `if...then...else` expressão.</span><span class="sxs-lookup"><span data-stu-id="af1b3-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="af1b3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af1b3-117">See Also</span></span>
[<span data-ttu-id="af1b3-118">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="af1b3-118">F# Language Reference</span></span>](index.md)


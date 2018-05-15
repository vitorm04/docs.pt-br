---
title: 'Expressões condicionais: if...then...else (F#)'
description: 'Saiba como escrever expressões condicionais em F # para executar diferentes ramos do código.'
ms.date: 05/16/2016
ms.openlocfilehash: a3ca3c20a659ccf5dc432d0a747ff176ec889e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="36d17-103">Expressões condicionais: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="36d17-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="36d17-104">O `if...then...else` expressão executa ramificações diferentes do código e também é avaliada como um valor diferente dependendo da expressão booliana fornecido.</span><span class="sxs-lookup"><span data-stu-id="36d17-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="36d17-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36d17-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="36d17-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="36d17-106">Remarks</span></span>
<span data-ttu-id="36d17-107">Na sintaxe anterior, *expression1* é executado quando a expressão booleana for avaliada como `true`; caso contrário, *expression2* é executado.</span><span class="sxs-lookup"><span data-stu-id="36d17-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="36d17-108">Ao contrário em outros idiomas, o `if...then...else` construção é uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="36d17-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="36d17-109">Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executado.</span><span class="sxs-lookup"><span data-stu-id="36d17-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="36d17-110">Os tipos de valores produzidos em cada ramificação devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="36d17-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="36d17-111">Se não houver explícita não `else` ramificação, seu tipo é `unit`.</span><span class="sxs-lookup"><span data-stu-id="36d17-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="36d17-112">Portanto, se o tipo do `then` ramificação for qualquer tipo diferente de `unit`, deve haver um `else` branch com o mesmo tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="36d17-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="36d17-113">Ao encadear `if...then...else` expressões juntas, você pode usar a palavra-chave `elif` em vez de `else if`; eles são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="36d17-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="36d17-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36d17-114">Example</span></span>
<span data-ttu-id="36d17-115">O exemplo a seguir ilustra como usar o `if...then...else` expressão.</span><span class="sxs-lookup"><span data-stu-id="36d17-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="36d17-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36d17-116">See Also</span></span>
[<span data-ttu-id="36d17-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="36d17-117">F# Language Reference</span></span>](index.md)


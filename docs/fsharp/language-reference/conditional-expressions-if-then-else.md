---
title: 'Expressões condicionais: If... Então... restante'
description: Saiba como escrever expressões condicionais no F# para executar diferentes ramificações de código.
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630395"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="73bb0-103">Expressões condicionais:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="73bb0-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="73bb0-104">A `if...then...else` expressão executa diferentes ramificações de código e também é avaliada como um valor diferente, dependendo da expressão booliana fornecida.</span><span class="sxs-lookup"><span data-stu-id="73bb0-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="73bb0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73bb0-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="73bb0-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="73bb0-106">Remarks</span></span>

<span data-ttu-id="73bb0-107">Na sintaxe anterior, *expressão1* é executado quando a expressão booliana é avaliada como `true`; caso contrário, a *expression2* é executada.</span><span class="sxs-lookup"><span data-stu-id="73bb0-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="73bb0-108">Ao contrário de outras linguagens `if...then...else` , a construção é uma expressão, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="73bb0-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="73bb0-109">Isso significa que ele produz um valor, que é o valor da última expressão na ramificação que é executada.</span><span class="sxs-lookup"><span data-stu-id="73bb0-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="73bb0-110">Os tipos dos valores produzidos em cada ramificação devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="73bb0-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="73bb0-111">Se não houver nenhuma ramificação explícita `else` , seu tipo será. `unit`</span><span class="sxs-lookup"><span data-stu-id="73bb0-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="73bb0-112">Portanto, se o tipo da `then` ramificação for qualquer tipo diferente de `unit`, deve haver uma `else` ramificação com o mesmo tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="73bb0-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="73bb0-113">Ao encadear `if...then...else` expressões juntas, você pode usar a palavra `elif` -chave `else if`em vez de; elas são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="73bb0-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="73bb0-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73bb0-114">Example</span></span>

<span data-ttu-id="73bb0-115">O exemplo a seguir ilustra como usar a `if...then...else` expressão.</span><span class="sxs-lookup"><span data-stu-id="73bb0-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="73bb0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73bb0-116">See also</span></span>

- [<span data-ttu-id="73bb0-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="73bb0-117">F# Language Reference</span></span>](index.md)

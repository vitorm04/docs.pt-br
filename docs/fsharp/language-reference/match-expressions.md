---
title: "Expressões match (F#)"
description: "Saiba como a expressão de correspondência do F # fornece controle ramificação com base na comparação de uma expressão com um conjunto de padrões."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a><span data-ttu-id="bf333-104">Expressões match</span><span class="sxs-lookup"><span data-stu-id="bf333-104">Match Expressions</span></span>

<span data-ttu-id="bf333-105">O `match` expressão fornece controle ramificação com base na comparação de uma expressão com um conjunto de padrões.</span><span class="sxs-lookup"><span data-stu-id="bf333-105">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf333-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf333-106">Syntax</span></span>

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a><span data-ttu-id="bf333-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf333-107">Remarks</span></span>

<span data-ttu-id="bf333-108">As expressões de correspondência de padrão permitem ramificação complexa com base na comparação de uma expressão de teste com um conjunto de padrões.</span><span class="sxs-lookup"><span data-stu-id="bf333-108">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="bf333-109">No `match` expressão, o *expressão de teste* é comparado com cada padrão, por sua vez, e quando uma correspondência for encontrada, o correspondente *expressão resultante* é avaliada e o valor resultante é retornado como o valor da expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="bf333-109">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="bf333-110">A função mostrada na sintaxe anterior de correspondência de padrão é uma expressão lambda em qual padrão de correspondência é executada imediatamente no argumento.</span><span class="sxs-lookup"><span data-stu-id="bf333-110">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="bf333-111">A função mostrada na sintaxe anterior de correspondência de padrão é equivalente à seguinte.</span><span class="sxs-lookup"><span data-stu-id="bf333-111">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

<span data-ttu-id="bf333-112">Para obter mais informações sobre expressões lambda, consulte [expressões Lambda: A `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="bf333-112">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="bf333-113">Todo o conjunto de padrões deve abranger todas as correspondências possíveis da variável de entrada.</span><span class="sxs-lookup"><span data-stu-id="bf333-113">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="bf333-114">Frequentemente, você pode usar o padrão de curinga (`_`) como o último padrão para corresponder a quaisquer valores de entrada anteriormente não correspondentes.</span><span class="sxs-lookup"><span data-stu-id="bf333-114">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="bf333-115">O código a seguir ilustra algumas das maneiras em que o `match` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="bf333-115">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="bf333-116">Para obter uma referência e exemplos de todos os padrões possíveis que podem ser usados, consulte [correspondência de padrões](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="bf333-116">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="bf333-117">Protege nos padrões</span><span class="sxs-lookup"><span data-stu-id="bf333-117">Guards on Patterns</span></span>

<span data-ttu-id="bf333-118">Você pode usar um `when` cláusula para especificar uma condição adicional que a variável deve atender para corresponder a um padrão.</span><span class="sxs-lookup"><span data-stu-id="bf333-118">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="bf333-119">Essa cláusula é conhecida como um *proteger*.</span><span class="sxs-lookup"><span data-stu-id="bf333-119">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="bf333-120">A seguinte expressão a `when` palavra-chave não é avaliado, a menos que uma correspondência é feita para o padrão associado a essa proteção.</span><span class="sxs-lookup"><span data-stu-id="bf333-120">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="bf333-121">O exemplo a seguir ilustra o uso de uma proteção para especificar um intervalo numérico para um padrão de variável.</span><span class="sxs-lookup"><span data-stu-id="bf333-121">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="bf333-122">Observe que várias condições são combinadas usando operadores boolianos.</span><span class="sxs-lookup"><span data-stu-id="bf333-122">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="bf333-123">Observe que como valores diferentes de literais não podem ser usados no padrão, você deve usar um `when` cláusula se você tiver alguma parte da entrada em relação a um valor de comparar.</span><span class="sxs-lookup"><span data-stu-id="bf333-123">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="bf333-124">Isso será mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="bf333-124">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a><span data-ttu-id="bf333-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf333-125">See Also</span></span>

[<span data-ttu-id="bf333-126">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="bf333-126">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="bf333-127">Padrões Ativos</span><span class="sxs-lookup"><span data-stu-id="bf333-127">Active Patterns</span></span>](active-patterns.md)

[<span data-ttu-id="bf333-128">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="bf333-128">Pattern Matching</span></span>](pattern-matching.md)

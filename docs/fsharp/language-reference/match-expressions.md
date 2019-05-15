---
title: Expressões de correspondência
description: Saiba como o F# expressão de correspondência fornece controle de ramificação com base na comparação de uma expressão com um conjunto de padrões.
ms.date: 04/19/2018
ms.openlocfilehash: 69ff8de1617e6b55d112d310bfcd8b2f967b6e8a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645208"
---
# <a name="match-expressions"></a><span data-ttu-id="3ec8c-103">Expressões de correspondência</span><span class="sxs-lookup"><span data-stu-id="3ec8c-103">Match expressions</span></span>

<span data-ttu-id="3ec8c-104">O `match` expressão fornece controle de ramificação com base na comparação de uma expressão com um conjunto de padrões.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-104">The `match` expression provides branching control that is based on the comparison of an expression with a set of patterns.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ec8c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ec8c-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="3ec8c-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="3ec8c-106">Remarks</span></span>

<span data-ttu-id="3ec8c-107">As expressões de correspondência de padrão permitem a ramificação complexa com base na comparação de uma expressão de teste com um conjunto de padrões.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-107">The pattern matching expressions allow for complex branching based on the comparison of a test expression with a set of patterns.</span></span> <span data-ttu-id="3ec8c-108">No `match` expressão, o *expressão de teste* é comparado com cada padrão, por sua vez, e quando uma correspondência for encontrada, o correspondente *expressão de resultado* é avaliada e o valor resultante é retornado como o valor da expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-108">In the `match` expression, the *test-expression* is compared with each pattern in turn, and when a match is found, the corresponding *result-expression* is evaluated and the resulting value is returned as the value of the match expression.</span></span>

<span data-ttu-id="3ec8c-109">A função mostrada na sintaxe anterior de correspondência de padrão é uma expressão lambda no qual padrão de correspondência é executada imediatamente no argumento.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-109">The pattern matching function shown in the previous syntax is a lambda expression in which pattern matching is performed immediately on the argument.</span></span> <span data-ttu-id="3ec8c-110">A correspondência de função mostrada na sintaxe anterior é equivalente ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-110">The pattern matching function shown in the previous syntax is equivalent to the following.</span></span>

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```

<span data-ttu-id="3ec8c-111">Para obter mais informações sobre expressões lambda, consulte [expressões Lambda: O `fun` palavra-chave](functions/lambda-expressions-the-fun-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="3ec8c-111">For more information about lambda expressions, see [Lambda Expressions: The `fun` Keyword](functions/lambda-expressions-the-fun-keyword.md).</span></span>

<span data-ttu-id="3ec8c-112">O conjunto completo de padrões deve abranger todas as correspondências possíveis a variável de entrada.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-112">The whole set of patterns should cover all the possible matches of the input variable.</span></span> <span data-ttu-id="3ec8c-113">Frequentemente, você pode usar o padrão de curinga (`_`) como o último padrão para coincidir com quaisquer valores de entrada sem correspondência anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-113">Frequently, you use the wildcard pattern (`_`) as the last pattern to match any previously unmatched input values.</span></span>

<span data-ttu-id="3ec8c-114">O código a seguir ilustra algumas das maneiras em que o `match` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-114">The following code illustrates some of the ways in which the `match` expression is used.</span></span> <span data-ttu-id="3ec8c-115">Para obter uma referência e exemplos de todos os padrões possíveis que podem ser usados, consulte [correspondência de padrões](pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="3ec8c-115">For a reference and examples of all the possible patterns that can be used, see [Pattern Matching](pattern-matching.md).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a><span data-ttu-id="3ec8c-116">Proteções de padrões</span><span class="sxs-lookup"><span data-stu-id="3ec8c-116">Guards on patterns</span></span>

<span data-ttu-id="3ec8c-117">Você pode usar um `when` cláusula para especificar uma condição adicional que a variável deve satisfazer para corresponder a um padrão.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-117">You can use a `when` clause to specify an additional condition that the variable must satisfy to match a pattern.</span></span> <span data-ttu-id="3ec8c-118">Essa cláusula é conhecida como um *proteger*.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-118">Such a clause is referred to as a *guard*.</span></span> <span data-ttu-id="3ec8c-119">A expressão após a `when` palavra-chave não é avaliada, a menos que uma correspondência é feita para o padrão associado a essa protetor.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-119">The expression following the `when` keyword is not evaluated unless a match is made to the pattern associated with that guard.</span></span>

<span data-ttu-id="3ec8c-120">O exemplo a seguir ilustra o uso de uma proteção para especificar um intervalo numérico para um padrão de variável.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-120">The following example illustrates the use of a guard to specify a numeric range for a variable pattern.</span></span> <span data-ttu-id="3ec8c-121">Observe que várias condições são combinadas usando operadores boolianos.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-121">Note that multiple conditions are combined by using Boolean operators.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

<span data-ttu-id="3ec8c-122">Observe que como valores diferentes de literais não podem ser usados no padrão, você deve usar um `when` cláusula se você tiver alguma parte da entrada em relação a um valor de comparar.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-122">Note that because values other than literals cannot be used in the pattern, you must use a `when` clause if you have to compare some part of the input against a value.</span></span> <span data-ttu-id="3ec8c-123">Isso é mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3ec8c-123">This is shown in the following code:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

<span data-ttu-id="3ec8c-124">Observe que, quando um padrão de união é coberto por um protetor, a proteção se aplica ao **todos os** de padrões, não apenas o último deles.</span><span class="sxs-lookup"><span data-stu-id="3ec8c-124">Note that when a union pattern is covered by a guard, the guard applies to **all** of the patterns, not just the last one.</span></span> <span data-ttu-id="3ec8c-125">Por exemplo, considerando o código a seguir, o protetor `when a > 12` se aplica a ambos `A a` e `B a`:</span><span class="sxs-lookup"><span data-stu-id="3ec8c-125">For example, given the following code, the guard `when a > 12` applies to both `A a` and `B a`:</span></span>

```fsharp
type Union =
    | A of int
    | B of int

let foo() =
    let test = A 42
    match test with
    | A a
    | B a when a > 41 -> a // the guard applies to both patterns
    | _ -> 1

foo() // returns 42
```

## <a name="see-also"></a><span data-ttu-id="3ec8c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ec8c-126">See also</span></span>

- [<span data-ttu-id="3ec8c-127">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="3ec8c-127">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3ec8c-128">Padrões Ativos</span><span class="sxs-lookup"><span data-stu-id="3ec8c-128">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="3ec8c-129">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="3ec8c-129">Pattern Matching</span></span>](pattern-matching.md)

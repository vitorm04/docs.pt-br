---
title: Operadores lógicos boolianos - referência do C#
description: Saiba mais sobre operadores C# que executam operações de negação lógica, conjunção (AND) e disjunção inclusiva e exclusiva (OR) com operandos booleanos.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: de621b26334bbc9679ba7e48a9d5a0cbaec67eab
ms.sourcegitcommit: d21bee9dbd32b9540ad30f9d0e2e874227040be3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59427312"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="1bfc3-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="1bfc3-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="1bfc3-104">Os operadores a seguir executam operações lógicas com os operandos [bool](../keywords/bool.md):</span><span class="sxs-lookup"><span data-stu-id="1bfc3-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="1bfc3-105">Operador unário [`!` (negação lógica)](#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="1bfc3-106">Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="1bfc3-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="1bfc3-108">Operadores binários [`&&` (AND lógico condicional)](#conditional-logical-and-operator-) e [`||` (OR lógico condicional)](#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="1bfc3-109">Esses operadores avaliam o segundo operando apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="1bfc3-110">Para os operandos de tipos [integrais](../keywords/integral-types-table.md), os operadores `&`, `|` e `^` executam operações lógicas bit a bit.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-110">For the operands of [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="1bfc3-111">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="1bfc3-111">Logical negation operator !</span></span>

<span data-ttu-id="1bfc3-112">O operador `!` calcula a negação lógica de seu operando.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-112">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="1bfc3-113">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-113">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="1bfc3-114">Operador AND lógico &amp;</span><span class="sxs-lookup"><span data-stu-id="1bfc3-114">Logical AND operator &amp;</span></span>

<span data-ttu-id="1bfc3-115">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-115">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="1bfc3-116">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-116">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="1bfc3-117">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-117">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="1bfc3-118">O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-118">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="1bfc3-119">No exemplo a seguir, o segundo operando do operador `&` é uma chamada de método, que é executada independentemente do valor do primeiro operando:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-119">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="1bfc3-120">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-120">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="1bfc3-121">Para os operandos de tipos integrais, o operador `&` computa o [AND lógico bit a bit](and-operator.md#integer-logical-bitwise-and-operator) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-121">For the operands of integral types, the `&` operator computes [bitwise logical AND](and-operator.md#integer-logical-bitwise-and-operator) of its operands.</span></span> <span data-ttu-id="1bfc3-122">O operador `&` unário é o [operador address-of](and-operator.md#unary-address-of-operator).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-122">The unary `&` operator is the [address-of operator](and-operator.md#unary-address-of-operator).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="1bfc3-123">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="1bfc3-123">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="1bfc3-124">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-124">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="1bfc3-125">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-125">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="1bfc3-126">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-126">Otherwise, the result is `false`.</span></span> <span data-ttu-id="1bfc3-127">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-127">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="1bfc3-128">Para os operandos de tipos integrais, o operador `^` computa o [OR exclusivo lógico bit a bit](xor-operator.md) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-128">For the operands of integral types, the `^` operator computes [bitwise logical exclusive OR](xor-operator.md) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="1bfc3-129">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="1bfc3-129">Logical OR operator |</span></span>

<span data-ttu-id="1bfc3-130">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-130">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="1bfc3-131">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-131">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="1bfc3-132">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-132">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="1bfc3-133">O operador `|` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `true`, de modo que o resultado deve ser `true`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-133">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="1bfc3-134">No exemplo a seguir, o segundo operando do operador `|` é uma chamada de método, que é executada independentemente do valor do primeiro operando:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-134">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="1bfc3-135">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-135">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="1bfc3-136">Para os operandos de tipos integrais, o operador `|` computa o [OR lógico bit a bit](or-operator.md) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-136">For the operands of integral types, the `|` operator computes [bitwise logical OR](or-operator.md) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="1bfc3-137">Operador AND lógico condicional &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="1bfc3-137">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="1bfc3-138">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-138">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="1bfc3-139">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-139">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="1bfc3-140">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-140">Otherwise, the result is `false`.</span></span> <span data-ttu-id="1bfc3-141">Se o primeiro operando for avaliado como `false`, o segundo operando não é avaliado.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-141">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="1bfc3-142">No exemplo a seguir, o segundo operando do operador `&&` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-142">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="1bfc3-143">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-143">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="1bfc3-144">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="1bfc3-144">Conditional logical OR operator ||</span></span>

<span data-ttu-id="1bfc3-145">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-145">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="1bfc3-146">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-146">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="1bfc3-147">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-147">Otherwise, the result is `false`.</span></span> <span data-ttu-id="1bfc3-148">Se o primeiro operando for avaliado como `true`, o segundo operando não é avaliado.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-148">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="1bfc3-149">No exemplo a seguir, o segundo operando do operador `||` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-149">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="1bfc3-150">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-150">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="1bfc3-151">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="1bfc3-151">Nullable Boolean logical operators</span></span>

<span data-ttu-id="1bfc3-152">Para os operandos `bool?`, os operadores `&` e `|` oferecem suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-152">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="1bfc3-153">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-153">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="1bfc3-154">x</span><span class="sxs-lookup"><span data-stu-id="1bfc3-154">x</span></span>|<span data-ttu-id="1bfc3-155">y</span><span class="sxs-lookup"><span data-stu-id="1bfc3-155">y</span></span>|<span data-ttu-id="1bfc3-156">x&y</span><span class="sxs-lookup"><span data-stu-id="1bfc3-156">x&y</span></span>|<span data-ttu-id="1bfc3-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="1bfc3-157">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="1bfc3-158">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-158">true</span></span>|<span data-ttu-id="1bfc3-159">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-159">true</span></span>|<span data-ttu-id="1bfc3-160">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-160">true</span></span>|<span data-ttu-id="1bfc3-161">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-161">true</span></span>|  
|<span data-ttu-id="1bfc3-162">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-162">true</span></span>|<span data-ttu-id="1bfc3-163">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-163">false</span></span>|<span data-ttu-id="1bfc3-164">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-164">false</span></span>|<span data-ttu-id="1bfc3-165">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-165">true</span></span>|  
|<span data-ttu-id="1bfc3-166">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-166">true</span></span>|<span data-ttu-id="1bfc3-167">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-167">null</span></span>|<span data-ttu-id="1bfc3-168">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-168">null</span></span>|<span data-ttu-id="1bfc3-169">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-169">true</span></span>|  
|<span data-ttu-id="1bfc3-170">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-170">false</span></span>|<span data-ttu-id="1bfc3-171">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-171">true</span></span>|<span data-ttu-id="1bfc3-172">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-172">false</span></span>|<span data-ttu-id="1bfc3-173">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-173">true</span></span>|  
|<span data-ttu-id="1bfc3-174">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-174">false</span></span>|<span data-ttu-id="1bfc3-175">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-175">false</span></span>|<span data-ttu-id="1bfc3-176">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-176">false</span></span>|<span data-ttu-id="1bfc3-177">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-177">false</span></span>|  
|<span data-ttu-id="1bfc3-178">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-178">false</span></span>|<span data-ttu-id="1bfc3-179">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-179">null</span></span>|<span data-ttu-id="1bfc3-180">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-180">false</span></span>|<span data-ttu-id="1bfc3-181">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-181">null</span></span>|  
|<span data-ttu-id="1bfc3-182">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-182">null</span></span>|<span data-ttu-id="1bfc3-183">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-183">true</span></span>|<span data-ttu-id="1bfc3-184">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-184">null</span></span>|<span data-ttu-id="1bfc3-185">true</span><span class="sxs-lookup"><span data-stu-id="1bfc3-185">true</span></span>|  
|<span data-ttu-id="1bfc3-186">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-186">null</span></span>|<span data-ttu-id="1bfc3-187">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-187">false</span></span>|<span data-ttu-id="1bfc3-188">false</span><span class="sxs-lookup"><span data-stu-id="1bfc3-188">false</span></span>|<span data-ttu-id="1bfc3-189">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-189">null</span></span>|  
|<span data-ttu-id="1bfc3-190">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-190">null</span></span>|<span data-ttu-id="1bfc3-191">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-191">null</span></span>|<span data-ttu-id="1bfc3-192">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-192">null</span></span>|<span data-ttu-id="1bfc3-193">nulo</span><span class="sxs-lookup"><span data-stu-id="1bfc3-193">null</span></span>|  

<span data-ttu-id="1bfc3-194">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-194">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="1bfc3-195">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-195">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="1bfc3-196">Esse operador produz `null` se algum de seus operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-196">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="1bfc3-197">No entanto, os operadores `&` e `|` podem produzir não nulos, mesmo se um dos operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-197">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="1bfc3-198">Para obter mais informações sobre o comportamento do operador com tipos de valor nulos, confira a seção [Operadores](../../programming-guide/nullable-types/using-nullable-types.md#operators) no artigo [Usando tipos nulos](../../programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-198">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="1bfc3-199">Você também pode usar os operadores `!` e `^`com os operandos`bool?`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-199">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="1bfc3-200">Os operadores lógicos condicionais `&&` e `||` não oferecem suporte aos operandos `bool?`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-200">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="1bfc3-201">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="1bfc3-201">Compound assignment</span></span>

<span data-ttu-id="1bfc3-202">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="1bfc3-202">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="1bfc3-203">equivale a</span><span class="sxs-lookup"><span data-stu-id="1bfc3-203">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="1bfc3-204">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-204">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1bfc3-205">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-205">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="1bfc3-206">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-206">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="1bfc3-207">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="1bfc3-207">Operator precedence</span></span>

<span data-ttu-id="1bfc3-208">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-208">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="1bfc3-209">Operador de negação lógico</span><span class="sxs-lookup"><span data-stu-id="1bfc3-209">Logical negation operator</span></span> `!`
- <span data-ttu-id="1bfc3-210">Operador AND lógico</span><span class="sxs-lookup"><span data-stu-id="1bfc3-210">Logical AND operator</span></span> `&`
- <span data-ttu-id="1bfc3-211">Operador OR exclusivo lógico</span><span class="sxs-lookup"><span data-stu-id="1bfc3-211">Logical exclusive OR operator</span></span> `^`
- <span data-ttu-id="1bfc3-212">Operador lógico OU</span><span class="sxs-lookup"><span data-stu-id="1bfc3-212">Logical OR operator</span></span> `|`
- <span data-ttu-id="1bfc3-213">Operador AND lógico condicional</span><span class="sxs-lookup"><span data-stu-id="1bfc3-213">Conditional logical AND operator</span></span> `&&`
- <span data-ttu-id="1bfc3-214">Operador OR lógico condicional</span><span class="sxs-lookup"><span data-stu-id="1bfc3-214">Conditional logical OR operator</span></span> `||`

<span data-ttu-id="1bfc3-215">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="1bfc3-215">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="1bfc3-216">Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-216">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1bfc3-217">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="1bfc3-217">Operator overloadability</span></span>

<span data-ttu-id="1bfc3-218">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `!`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-218">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="1bfc3-219">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-219">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="1bfc3-220">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-220">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="1bfc3-221">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-221">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="1bfc3-222">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](../keywords/true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="1bfc3-222">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="1bfc3-223">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1bfc3-223">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1bfc3-224">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1bfc3-224">C# language specification</span></span>

<span data-ttu-id="1bfc3-225">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="1bfc3-225">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1bfc3-226">Operador de negação lógico</span><span class="sxs-lookup"><span data-stu-id="1bfc3-226">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="1bfc3-227">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="1bfc3-227">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="1bfc3-228">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="1bfc3-228">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)

## <a name="see-also"></a><span data-ttu-id="1bfc3-229">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bfc3-229">See also</span></span>

- [<span data-ttu-id="1bfc3-230">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1bfc3-230">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1bfc3-231">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1bfc3-231">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1bfc3-232">Operadores em C#</span><span class="sxs-lookup"><span data-stu-id="1bfc3-232">C# Operators</span></span>](index.md)

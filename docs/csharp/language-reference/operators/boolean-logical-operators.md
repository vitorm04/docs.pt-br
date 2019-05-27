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
ms.openlocfilehash: b666c915506872930b16c1c5890de24e9cbe4f7a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880575"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="fa563-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="fa563-103">Boolean logical operators (C# Reference)</span></span>

<span data-ttu-id="fa563-104">Os operadores a seguir executam operações lógicas com os operandos [bool](../keywords/bool.md):</span><span class="sxs-lookup"><span data-stu-id="fa563-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="fa563-105">Operador unário [`!` (negação lógica)](#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="fa563-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="fa563-106">Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="fa563-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="fa563-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="fa563-108">Operadores binários [`&&` (AND lógico condicional)](#conditional-logical-and-operator-) e [`||` (OR lógico condicional)](#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="fa563-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="fa563-109">Esses operadores avaliam o segundo operando apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="fa563-109">Those operators evaluate the second operand only if it's necessary.</span></span>

<span data-ttu-id="fa563-110">Para os operandos de tipos [integrais](../keywords/integral-types-table.md), os operadores `&`, `|` e `^` executam operações lógicas bit a bit.</span><span class="sxs-lookup"><span data-stu-id="fa563-110">For the operands of the [integral](../keywords/integral-types-table.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="fa563-111">Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="fa563-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="fa563-112">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="fa563-112">Logical negation operator !</span></span>

<span data-ttu-id="fa563-113">O operador `!` calcula a negação lógica de seu operando.</span><span class="sxs-lookup"><span data-stu-id="fa563-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="fa563-114">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="fa563-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a><span data-ttu-id="fa563-115">Operador AND lógico &amp;</span><span class="sxs-lookup"><span data-stu-id="fa563-115">Logical AND operator &amp;</span></span>

<span data-ttu-id="fa563-116">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-116">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="fa563-117">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-117">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="fa563-118">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-118">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="fa563-119">O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="fa563-119">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span>

<span data-ttu-id="fa563-120">No exemplo a seguir, o segundo operando do operador `&` é uma chamada de método, que é executada independentemente do valor do primeiro operando:</span><span class="sxs-lookup"><span data-stu-id="fa563-120">In the following example, the second operand of the `&` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

<span data-ttu-id="fa563-121">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-121">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="fa563-122">Para os operandos de tipos integrais, o operador `&` computa o [AND lógico bit a bit](bitwise-and-shift-operators.md#logical-and-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-122">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="fa563-123">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="fa563-123">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="fa563-124">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="fa563-124">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="fa563-125">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-125">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="fa563-126">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-126">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="fa563-127">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-127">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fa563-128">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="fa563-128">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

<span data-ttu-id="fa563-129">Para os operandos de tipos integrais, o operador `^` computa o [OR exclusivo bit a bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-129">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="fa563-130">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="fa563-130">Logical OR operator |</span></span>

<span data-ttu-id="fa563-131">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-131">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="fa563-132">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-132">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="fa563-133">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-133">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="fa563-134">O operador `|` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `true`, de modo que o resultado deve ser `true`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="fa563-134">The `|` operator evaluates both operands even if the first operand evaluates to `true`, so that the result must be `true` regardless of the value of the second operand.</span></span>

<span data-ttu-id="fa563-135">No exemplo a seguir, o segundo operando do operador `|` é uma chamada de método, que é executada independentemente do valor do primeiro operando:</span><span class="sxs-lookup"><span data-stu-id="fa563-135">In the following example, the second operand of the `|` operator is a method call, which is performed regardless of the value of the first operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

<span data-ttu-id="fa563-136">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-136">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the second operand if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="fa563-137">Para os operandos de tipos integrais, o operador `|` computa o [OR lógico bit a bit](bitwise-and-shift-operators.md#logical-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-137">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><span data-ttu-id="fa563-138">Operador AND lógico condicional &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="fa563-138">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="fa563-139">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-139">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="fa563-140">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-140">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="fa563-141">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-141">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fa563-142">Se o primeiro operando for avaliado como `false`, o segundo operando não é avaliado.</span><span class="sxs-lookup"><span data-stu-id="fa563-142">If the first operand evaluates to `false`, the second operand is not evaluated.</span></span>

<span data-ttu-id="fa563-143">No exemplo a seguir, o segundo operando do operador `&&` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="fa563-143">In the following example, the second operand of the `&&` operator is a method call, which isn't performed if the first operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="fa563-144">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-144">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="fa563-145">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="fa563-145">Conditional logical OR operator ||</span></span>

<span data-ttu-id="fa563-146">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-146">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="fa563-147">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="fa563-147">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="fa563-148">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="fa563-148">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fa563-149">Se o primeiro operando for avaliado como `true`, o segundo operando não é avaliado.</span><span class="sxs-lookup"><span data-stu-id="fa563-149">If the first operand evaluates to `true`, the second operand is not evaluated.</span></span>

<span data-ttu-id="fa563-150">No exemplo a seguir, o segundo operando do operador `||` é uma chamada de método, que não é executada se o primeiro operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="fa563-150">In the following example, the second operand of the `||` operator is a method call, which isn't performed if the first operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="fa563-151">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="fa563-151">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="fa563-152">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="fa563-152">Nullable Boolean logical operators</span></span>

<span data-ttu-id="fa563-153">Para os operandos `bool?`, os operadores `&` e `|` oferecem suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="fa563-153">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="fa563-154">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa563-154">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="fa563-155">x</span><span class="sxs-lookup"><span data-stu-id="fa563-155">x</span></span>|<span data-ttu-id="fa563-156">y</span><span class="sxs-lookup"><span data-stu-id="fa563-156">y</span></span>|<span data-ttu-id="fa563-157">x&y</span><span class="sxs-lookup"><span data-stu-id="fa563-157">x&y</span></span>|<span data-ttu-id="fa563-158">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="fa563-158">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="fa563-159">true</span><span class="sxs-lookup"><span data-stu-id="fa563-159">true</span></span>|<span data-ttu-id="fa563-160">true</span><span class="sxs-lookup"><span data-stu-id="fa563-160">true</span></span>|<span data-ttu-id="fa563-161">true</span><span class="sxs-lookup"><span data-stu-id="fa563-161">true</span></span>|<span data-ttu-id="fa563-162">true</span><span class="sxs-lookup"><span data-stu-id="fa563-162">true</span></span>|  
|<span data-ttu-id="fa563-163">true</span><span class="sxs-lookup"><span data-stu-id="fa563-163">true</span></span>|<span data-ttu-id="fa563-164">false</span><span class="sxs-lookup"><span data-stu-id="fa563-164">false</span></span>|<span data-ttu-id="fa563-165">false</span><span class="sxs-lookup"><span data-stu-id="fa563-165">false</span></span>|<span data-ttu-id="fa563-166">true</span><span class="sxs-lookup"><span data-stu-id="fa563-166">true</span></span>|  
|<span data-ttu-id="fa563-167">true</span><span class="sxs-lookup"><span data-stu-id="fa563-167">true</span></span>|<span data-ttu-id="fa563-168">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-168">null</span></span>|<span data-ttu-id="fa563-169">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-169">null</span></span>|<span data-ttu-id="fa563-170">true</span><span class="sxs-lookup"><span data-stu-id="fa563-170">true</span></span>|  
|<span data-ttu-id="fa563-171">false</span><span class="sxs-lookup"><span data-stu-id="fa563-171">false</span></span>|<span data-ttu-id="fa563-172">true</span><span class="sxs-lookup"><span data-stu-id="fa563-172">true</span></span>|<span data-ttu-id="fa563-173">false</span><span class="sxs-lookup"><span data-stu-id="fa563-173">false</span></span>|<span data-ttu-id="fa563-174">true</span><span class="sxs-lookup"><span data-stu-id="fa563-174">true</span></span>|  
|<span data-ttu-id="fa563-175">false</span><span class="sxs-lookup"><span data-stu-id="fa563-175">false</span></span>|<span data-ttu-id="fa563-176">false</span><span class="sxs-lookup"><span data-stu-id="fa563-176">false</span></span>|<span data-ttu-id="fa563-177">false</span><span class="sxs-lookup"><span data-stu-id="fa563-177">false</span></span>|<span data-ttu-id="fa563-178">false</span><span class="sxs-lookup"><span data-stu-id="fa563-178">false</span></span>|  
|<span data-ttu-id="fa563-179">false</span><span class="sxs-lookup"><span data-stu-id="fa563-179">false</span></span>|<span data-ttu-id="fa563-180">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-180">null</span></span>|<span data-ttu-id="fa563-181">false</span><span class="sxs-lookup"><span data-stu-id="fa563-181">false</span></span>|<span data-ttu-id="fa563-182">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-182">null</span></span>|  
|<span data-ttu-id="fa563-183">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-183">null</span></span>|<span data-ttu-id="fa563-184">true</span><span class="sxs-lookup"><span data-stu-id="fa563-184">true</span></span>|<span data-ttu-id="fa563-185">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-185">null</span></span>|<span data-ttu-id="fa563-186">true</span><span class="sxs-lookup"><span data-stu-id="fa563-186">true</span></span>|  
|<span data-ttu-id="fa563-187">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-187">null</span></span>|<span data-ttu-id="fa563-188">false</span><span class="sxs-lookup"><span data-stu-id="fa563-188">false</span></span>|<span data-ttu-id="fa563-189">false</span><span class="sxs-lookup"><span data-stu-id="fa563-189">false</span></span>|<span data-ttu-id="fa563-190">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-190">null</span></span>|  
|<span data-ttu-id="fa563-191">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-191">null</span></span>|<span data-ttu-id="fa563-192">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-192">null</span></span>|<span data-ttu-id="fa563-193">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-193">null</span></span>|<span data-ttu-id="fa563-194">nulo</span><span class="sxs-lookup"><span data-stu-id="fa563-194">null</span></span>|  

<span data-ttu-id="fa563-195">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="fa563-195">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="fa563-196">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="fa563-196">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="fa563-197">Esse operador produz `null` se algum de seus operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="fa563-197">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="fa563-198">No entanto, os operadores `&` e `|` podem produzir não nulos, mesmo se um dos operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="fa563-198">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="fa563-199">Para obter mais informações sobre o comportamento do operador com tipos de valor nulos, confira a seção [Operadores](../../programming-guide/nullable-types/using-nullable-types.md#operators) no artigo [Usando tipos nulos](../../programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="fa563-199">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="fa563-200">Você também pode usar os operadores `!` e `^`com os operandos`bool?`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa563-200">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="fa563-201">Os operadores lógicos condicionais `&&` e `||` não oferecem suporte aos operandos `bool?`.</span><span class="sxs-lookup"><span data-stu-id="fa563-201">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="fa563-202">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="fa563-202">Compound assignment</span></span>

<span data-ttu-id="fa563-203">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="fa563-203">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="fa563-204">equivale a</span><span class="sxs-lookup"><span data-stu-id="fa563-204">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="fa563-205">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="fa563-205">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="fa563-206">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fa563-206">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="fa563-207">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="fa563-207">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="fa563-208">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="fa563-208">Operator precedence</span></span>

<span data-ttu-id="fa563-209">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="fa563-209">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="fa563-210">Operador de negação lógico `!`</span><span class="sxs-lookup"><span data-stu-id="fa563-210">Logical negation operator `!`</span></span>
- <span data-ttu-id="fa563-211">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="fa563-211">Logical AND operator `&`</span></span>
- <span data-ttu-id="fa563-212">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="fa563-212">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="fa563-213">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="fa563-213">Logical OR operator `|`</span></span>
- <span data-ttu-id="fa563-214">Operador AND lógico condicional `&&`</span><span class="sxs-lookup"><span data-stu-id="fa563-214">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="fa563-215">Operador OR lógico condicional `||`</span><span class="sxs-lookup"><span data-stu-id="fa563-215">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="fa563-216">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="fa563-216">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

<span data-ttu-id="fa563-217">Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="fa563-217">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="fa563-218">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="fa563-218">Operator overloadability</span></span>

<span data-ttu-id="fa563-219">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `!`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="fa563-219">A user-defined type can [overload](../keywords/operator.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="fa563-220">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="fa563-220">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="fa563-221">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="fa563-221">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="fa563-222">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="fa563-222">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="fa563-223">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](../keywords/true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="fa563-223">However, if a user-defined type overloads the [true and false operators](../keywords/true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="fa563-224">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="fa563-224">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fa563-225">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="fa563-225">C# language specification</span></span>

<span data-ttu-id="fa563-226">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="fa563-226">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="fa563-227">Operador de negação lógico</span><span class="sxs-lookup"><span data-stu-id="fa563-227">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="fa563-228">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="fa563-228">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="fa563-229">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="fa563-229">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="fa563-230">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="fa563-230">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="fa563-231">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa563-231">See also</span></span>

- [<span data-ttu-id="fa563-232">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fa563-232">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fa563-233">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fa563-233">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fa563-234">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="fa563-234">C# Operators</span></span>](index.md)
- [<span data-ttu-id="fa563-235">Operadores shift e bit a bit</span><span class="sxs-lookup"><span data-stu-id="fa563-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)

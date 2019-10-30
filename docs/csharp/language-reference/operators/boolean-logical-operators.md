---
title: Operadores lógicos boolianos – referência do C#
description: Saiba mais sobre operadores C# que executam operações de negação lógica, conjunção (AND) e disjunção inclusiva e exclusiva (OR) com operandos booleanos.
ms.date: 09/27/2019
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
ms.openlocfilehash: 4a3e6986060b8e22d49110b8b9f275f41b743af2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036399"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="5fc41-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="5fc41-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="5fc41-104">Os operadores a seguir executam operações lógicas com operandos [bool](../keywords/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="5fc41-104">The following operators perform logical operations with [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="5fc41-105">Operador unário [`!` (negação lógica)](#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="5fc41-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="5fc41-106">Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="5fc41-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="5fc41-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="5fc41-108">Operadores binários [`&&` (AND lógico condicional)](#conditional-logical-and-operator-) e [`||` (OR lógico condicional)](#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="5fc41-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="5fc41-109">Esses operadores avaliam o operando à direita apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="5fc41-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="5fc41-110">Para os operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), os operadores `&`, `|`e `^` executam operações lógicas bit-a-bit.</span><span class="sxs-lookup"><span data-stu-id="5fc41-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="5fc41-111">Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5fc41-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="5fc41-112">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="5fc41-112">Logical negation operator !</span></span>

<span data-ttu-id="5fc41-113">O operador `!` de prefixo unário computa a negação lógica de seu operando.</span><span class="sxs-lookup"><span data-stu-id="5fc41-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="5fc41-114">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="5fc41-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="5fc41-115">Começando com C# o 8,0, o sufixo unário`!`Operator é o [operador NULL-tolerante](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="5fc41-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="5fc41-116">Operador AND lógico &amp;</span><span class="sxs-lookup"><span data-stu-id="5fc41-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="5fc41-117">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="5fc41-118">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="5fc41-119">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="5fc41-120">O operador `&` avalia os dois operandos mesmo que o operando esquerdo seja avaliado como `false`, de modo que o resultado da operação seja `false`, independentemente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="5fc41-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="5fc41-121">No exemplo a seguir, o operando à direita do operador `&` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="5fc41-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="5fc41-122">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="5fc41-123">Para os operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o operador de `&` computa a [lógica de bit e](bitwise-and-shift-operators.md#logical-and-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="5fc41-124">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="5fc41-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="5fc41-125">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="5fc41-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="5fc41-126">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="5fc41-127">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="5fc41-128">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5fc41-129">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="5fc41-130">Para os operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o operador de `^` computa o [bit lógico Exclusive ou](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="5fc41-131">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="5fc41-131">Logical OR operator |</span></span>

<span data-ttu-id="5fc41-132">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="5fc41-133">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="5fc41-134">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="5fc41-135">O operador `|` avalia os dois operandos mesmo que o operando esquerdo seja avaliado como `true`, de modo que o resultado da operação seja `true`, independentemente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="5fc41-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="5fc41-136">No exemplo a seguir, o operando à direita do operador `|` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="5fc41-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="5fc41-137">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="5fc41-138">Para os operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o operador de `|` computa o bit-a [lógico ou](bitwise-and-shift-operators.md#logical-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="5fc41-139">Operador AND lógico condicional &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="5fc41-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="5fc41-140">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="5fc41-141">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="5fc41-142">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5fc41-143">Se `x` for avaliado como `false`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="5fc41-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="5fc41-144">No exemplo a seguir, o operando à direita do operador `&&` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="5fc41-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="5fc41-145">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="5fc41-146">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="5fc41-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="5fc41-147">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="5fc41-148">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="5fc41-149">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="5fc41-150">Se `x` for avaliado como `true`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="5fc41-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="5fc41-151">No exemplo a seguir, o operando à direita do operador `||` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="5fc41-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="5fc41-152">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="5fc41-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="5fc41-153">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="5fc41-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="5fc41-154">Para operandos `bool?`, os operadores de `&` e `|` dão suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="5fc41-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="5fc41-155">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fc41-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="5fc41-156">x</span><span class="sxs-lookup"><span data-stu-id="5fc41-156">x</span></span>|<span data-ttu-id="5fc41-157">s</span><span class="sxs-lookup"><span data-stu-id="5fc41-157">y</span></span>|<span data-ttu-id="5fc41-158">x&y</span><span class="sxs-lookup"><span data-stu-id="5fc41-158">x&y</span></span>|<span data-ttu-id="5fc41-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="5fc41-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="5fc41-160">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-160">true</span></span>|<span data-ttu-id="5fc41-161">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-161">true</span></span>|<span data-ttu-id="5fc41-162">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-162">true</span></span>|<span data-ttu-id="5fc41-163">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-163">true</span></span>|  
|<span data-ttu-id="5fc41-164">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-164">true</span></span>|<span data-ttu-id="5fc41-165">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-165">false</span></span>|<span data-ttu-id="5fc41-166">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-166">false</span></span>|<span data-ttu-id="5fc41-167">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-167">true</span></span>|  
|<span data-ttu-id="5fc41-168">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-168">true</span></span>|<span data-ttu-id="5fc41-169">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-169">null</span></span>|<span data-ttu-id="5fc41-170">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-170">null</span></span>|<span data-ttu-id="5fc41-171">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-171">true</span></span>|  
|<span data-ttu-id="5fc41-172">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-172">false</span></span>|<span data-ttu-id="5fc41-173">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-173">true</span></span>|<span data-ttu-id="5fc41-174">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-174">false</span></span>|<span data-ttu-id="5fc41-175">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-175">true</span></span>|  
|<span data-ttu-id="5fc41-176">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-176">false</span></span>|<span data-ttu-id="5fc41-177">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-177">false</span></span>|<span data-ttu-id="5fc41-178">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-178">false</span></span>|<span data-ttu-id="5fc41-179">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-179">false</span></span>|  
|<span data-ttu-id="5fc41-180">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-180">false</span></span>|<span data-ttu-id="5fc41-181">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-181">null</span></span>|<span data-ttu-id="5fc41-182">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-182">false</span></span>|<span data-ttu-id="5fc41-183">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-183">null</span></span>|  
|<span data-ttu-id="5fc41-184">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-184">null</span></span>|<span data-ttu-id="5fc41-185">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-185">true</span></span>|<span data-ttu-id="5fc41-186">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-186">null</span></span>|<span data-ttu-id="5fc41-187">true</span><span class="sxs-lookup"><span data-stu-id="5fc41-187">true</span></span>|  
|<span data-ttu-id="5fc41-188">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-188">null</span></span>|<span data-ttu-id="5fc41-189">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-189">false</span></span>|<span data-ttu-id="5fc41-190">false</span><span class="sxs-lookup"><span data-stu-id="5fc41-190">false</span></span>|<span data-ttu-id="5fc41-191">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-191">null</span></span>|  
|<span data-ttu-id="5fc41-192">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-192">null</span></span>|<span data-ttu-id="5fc41-193">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-193">null</span></span>|<span data-ttu-id="5fc41-194">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-194">null</span></span>|<span data-ttu-id="5fc41-195">nulo</span><span class="sxs-lookup"><span data-stu-id="5fc41-195">null</span></span>|  

<span data-ttu-id="5fc41-196">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="5fc41-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="5fc41-197">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="5fc41-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="5fc41-198">Esse operador produz `null` se qualquer um de seus operandos for avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="5fc41-199">No entanto, os operadores `&` e `|` podem produzir não nulo mesmo que um dos operandos seja avaliado como `null`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="5fc41-200">Para obter mais informações sobre o comportamento do operador com tipos de valores anuláveis, consulte a seção [operadores](../../programming-guide/nullable-types/using-nullable-types.md#operators) do artigo [usando tipos de valores anuláveis](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="5fc41-200">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="5fc41-201">Você também pode usar os operadores `!` e `^` com operandos `bool?`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fc41-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="5fc41-202">Os operadores lógicos condicionais `&&` e `||` não dão suporte a operandos `bool?`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="5fc41-203">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="5fc41-203">Compound assignment</span></span>

<span data-ttu-id="5fc41-204">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="5fc41-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="5fc41-205">equivale a</span><span class="sxs-lookup"><span data-stu-id="5fc41-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="5fc41-206">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="5fc41-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="5fc41-207">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fc41-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="5fc41-208">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="5fc41-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="5fc41-209">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="5fc41-209">Operator precedence</span></span>

<span data-ttu-id="5fc41-210">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="5fc41-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="5fc41-211">Operador de negação lógico `!`</span><span class="sxs-lookup"><span data-stu-id="5fc41-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="5fc41-212">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="5fc41-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="5fc41-213">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="5fc41-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="5fc41-214">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="5fc41-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="5fc41-215">Operador AND lógico condicional `&&`</span><span class="sxs-lookup"><span data-stu-id="5fc41-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="5fc41-216">Operador OR lógico condicional `||`</span><span class="sxs-lookup"><span data-stu-id="5fc41-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="5fc41-217">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="5fc41-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="5fc41-218">Para obter a lista completa C# de operadores ordenados por nível de precedência, consulte a seção [precedência de operador](index.md#operator-precedence) do artigo [ C# operadores](index.md) .</span><span class="sxs-lookup"><span data-stu-id="5fc41-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="5fc41-219">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="5fc41-219">Operator overloadability</span></span>

<span data-ttu-id="5fc41-220">Os tipos definidos pelo usuário podem [sobrecarregar](operator-overloading.md) os operadores `!`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="5fc41-221">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="5fc41-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="5fc41-222">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="5fc41-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="5fc41-223">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="5fc41-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="5fc41-224">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="5fc41-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="5fc41-225">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5fc41-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5fc41-226">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="5fc41-226">C# language specification</span></span>

<span data-ttu-id="5fc41-227">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5fc41-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5fc41-228">Operador de negação lógico</span><span class="sxs-lookup"><span data-stu-id="5fc41-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="5fc41-229">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="5fc41-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="5fc41-230">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="5fc41-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="5fc41-231">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="5fc41-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="5fc41-232">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fc41-232">See also</span></span>

- [<span data-ttu-id="5fc41-233">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="5fc41-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5fc41-234">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="5fc41-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="5fc41-235">Operadores shift e bit a bit</span><span class="sxs-lookup"><span data-stu-id="5fc41-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)

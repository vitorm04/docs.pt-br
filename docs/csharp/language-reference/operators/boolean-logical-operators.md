---
title: Operadores lógicos boolianos – referência do C#
description: Saiba mais sobre operadores C# que executam operações de negação lógica, conjunção (AND) e disjunção inclusiva e exclusiva (OR) com operandos booleanos.
ms.date: 06/29/2020
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
ms.openlocfilehash: cdabae0a4dbdcc3b1289bca7f1c42cb0a26b440f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555403"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="23c46-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="23c46-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="23c46-104">Os operadores a seguir executam operações lógicas com operandos [bool](../builtin-types/bool.md) :</span><span class="sxs-lookup"><span data-stu-id="23c46-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="23c46-105">Operador unário [ `!` (negação lógica)](#logical-negation-operator-) .</span><span class="sxs-lookup"><span data-stu-id="23c46-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="23c46-106">Operadores Binary [ `&` (and lógico)](#logical-and-operator-), [ `|` (OR lógico)](#logical-or-operator-)e [ `^` (exclusivo lógico)](#logical-exclusive-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="23c46-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="23c46-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="23c46-108">Operadores Binary [ `&&` (and lógico condicional and)](#conditional-logical-and-operator-) e [ `||` (OR lógico condicional)](#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="23c46-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="23c46-109">Esses operadores avaliam o operando à direita apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="23c46-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="23c46-110">Para operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), os `&` `|` operadores, e `^` executam operações lógicas de bit-nte.</span><span class="sxs-lookup"><span data-stu-id="23c46-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="23c46-111">Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="23c46-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="23c46-112">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="23c46-112">Logical negation operator !</span></span>

<span data-ttu-id="23c46-113">O operador de prefixo unário `!` computa a negação lógica de seu operando.</span><span class="sxs-lookup"><span data-stu-id="23c46-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="23c46-114">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="23c46-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="23c46-115">A partir do C# 8,0, o operador de sufixo unário `!` é o [operador NULL-tolerante](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="23c46-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a><span data-ttu-id="23c46-116">Operador AND lógico&amp;</span><span class="sxs-lookup"><span data-stu-id="23c46-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="23c46-117">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="23c46-118">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="23c46-119">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="23c46-120">O `&` operador avalia os dois operandos mesmo se o operando esquerdo for avaliado `false` , de modo que o resultado da operação seja `false` independente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="23c46-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="23c46-121">No exemplo a seguir, o operando à direita do operador `&` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="23c46-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="23c46-122">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="23c46-123">Para operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o `&` operador computa a [lógica e os opera bits de bit e](bitwise-and-shift-operators.md#logical-and-operator-) de seus operando.</span><span class="sxs-lookup"><span data-stu-id="23c46-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="23c46-124">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="23c46-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="23c46-125">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="23c46-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="23c46-126">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="23c46-127">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="23c46-128">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="23c46-129">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="23c46-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="23c46-130">Para operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o `^` operador computa o [bit lógico Exclusive ou](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="23c46-131">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="23c46-131">Logical OR operator |</span></span>

<span data-ttu-id="23c46-132">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="23c46-133">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="23c46-134">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="23c46-135">O `|` operador avalia os dois operandos mesmo se o operando esquerdo for avaliado `true` , de modo que o resultado da operação seja `true` independente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="23c46-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="23c46-136">No exemplo a seguir, o operando à direita do operador `|` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="23c46-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="23c46-137">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="23c46-138">Para os operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md), o `|` operador computa o [bit lógico ou](bitwise-and-shift-operators.md#logical-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a><span data-ttu-id="23c46-139">Operador AND lógico condicional&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="23c46-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="23c46-140">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="23c46-141">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="23c46-142">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="23c46-143">Se `x` for avaliado como `false`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="23c46-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="23c46-144">No exemplo a seguir, o operando à direita do operador `&&` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="23c46-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="23c46-145">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="23c46-146">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="23c46-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="23c46-147">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="23c46-148">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="23c46-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="23c46-149">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="23c46-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="23c46-150">Se `x` for avaliado como `true`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="23c46-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="23c46-151">No exemplo a seguir, o operando à direita do operador `||` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="23c46-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="23c46-152">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="23c46-153">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="23c46-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="23c46-154">Para `bool?` operandos, os operadores [ `&` (and lógico)](#logical-and-operator-) e [ `|` (lógico](#logical-or-operator-) ) oferecem suporte à lógica de três valores, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="23c46-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="23c46-155">O `&` operador só produzirá `true` se ambos os operandos forem avaliados como `true` .</span><span class="sxs-lookup"><span data-stu-id="23c46-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="23c46-156">Se `x` ou `y` for avaliada como `false` , `x & y` produz `false` (mesmo que outro operando seja avaliado como `null` ).</span><span class="sxs-lookup"><span data-stu-id="23c46-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="23c46-157">Caso contrário, o resultado de `x & y` é `null` .</span><span class="sxs-lookup"><span data-stu-id="23c46-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="23c46-158">O `|` operador só produzirá `false` se ambos os operandos forem avaliados como `false` .</span><span class="sxs-lookup"><span data-stu-id="23c46-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="23c46-159">Se `x` ou `y` for avaliada como `true` , `x | y` produz `true` (mesmo que outro operando seja avaliado como `null` ).</span><span class="sxs-lookup"><span data-stu-id="23c46-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="23c46-160">Caso contrário, o resultado de `x | y` é `null` .</span><span class="sxs-lookup"><span data-stu-id="23c46-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="23c46-161">A tabela a seguir apresenta essa semântica:</span><span class="sxs-lookup"><span data-stu-id="23c46-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="23c46-162">x</span><span class="sxs-lookup"><span data-stu-id="23c46-162">x</span></span>|<span data-ttu-id="23c46-163">a</span><span class="sxs-lookup"><span data-stu-id="23c46-163">y</span></span>|<span data-ttu-id="23c46-164">x&y</span><span class="sxs-lookup"><span data-stu-id="23c46-164">x&y</span></span>|<span data-ttu-id="23c46-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="23c46-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="23c46-166">true</span><span class="sxs-lookup"><span data-stu-id="23c46-166">true</span></span>|<span data-ttu-id="23c46-167">true</span><span class="sxs-lookup"><span data-stu-id="23c46-167">true</span></span>|<span data-ttu-id="23c46-168">true</span><span class="sxs-lookup"><span data-stu-id="23c46-168">true</span></span>|<span data-ttu-id="23c46-169">true</span><span class="sxs-lookup"><span data-stu-id="23c46-169">true</span></span>|  
|<span data-ttu-id="23c46-170">true</span><span class="sxs-lookup"><span data-stu-id="23c46-170">true</span></span>|<span data-ttu-id="23c46-171">false</span><span class="sxs-lookup"><span data-stu-id="23c46-171">false</span></span>|<span data-ttu-id="23c46-172">false</span><span class="sxs-lookup"><span data-stu-id="23c46-172">false</span></span>|<span data-ttu-id="23c46-173">true</span><span class="sxs-lookup"><span data-stu-id="23c46-173">true</span></span>|  
|<span data-ttu-id="23c46-174">true</span><span class="sxs-lookup"><span data-stu-id="23c46-174">true</span></span>|<span data-ttu-id="23c46-175">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-175">null</span></span>|<span data-ttu-id="23c46-176">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-176">null</span></span>|<span data-ttu-id="23c46-177">true</span><span class="sxs-lookup"><span data-stu-id="23c46-177">true</span></span>|  
|<span data-ttu-id="23c46-178">false</span><span class="sxs-lookup"><span data-stu-id="23c46-178">false</span></span>|<span data-ttu-id="23c46-179">true</span><span class="sxs-lookup"><span data-stu-id="23c46-179">true</span></span>|<span data-ttu-id="23c46-180">false</span><span class="sxs-lookup"><span data-stu-id="23c46-180">false</span></span>|<span data-ttu-id="23c46-181">true</span><span class="sxs-lookup"><span data-stu-id="23c46-181">true</span></span>|  
|<span data-ttu-id="23c46-182">false</span><span class="sxs-lookup"><span data-stu-id="23c46-182">false</span></span>|<span data-ttu-id="23c46-183">false</span><span class="sxs-lookup"><span data-stu-id="23c46-183">false</span></span>|<span data-ttu-id="23c46-184">false</span><span class="sxs-lookup"><span data-stu-id="23c46-184">false</span></span>|<span data-ttu-id="23c46-185">false</span><span class="sxs-lookup"><span data-stu-id="23c46-185">false</span></span>|  
|<span data-ttu-id="23c46-186">false</span><span class="sxs-lookup"><span data-stu-id="23c46-186">false</span></span>|<span data-ttu-id="23c46-187">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-187">null</span></span>|<span data-ttu-id="23c46-188">false</span><span class="sxs-lookup"><span data-stu-id="23c46-188">false</span></span>|<span data-ttu-id="23c46-189">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-189">null</span></span>|  
|<span data-ttu-id="23c46-190">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-190">null</span></span>|<span data-ttu-id="23c46-191">true</span><span class="sxs-lookup"><span data-stu-id="23c46-191">true</span></span>|<span data-ttu-id="23c46-192">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-192">null</span></span>|<span data-ttu-id="23c46-193">true</span><span class="sxs-lookup"><span data-stu-id="23c46-193">true</span></span>|  
|<span data-ttu-id="23c46-194">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-194">null</span></span>|<span data-ttu-id="23c46-195">false</span><span class="sxs-lookup"><span data-stu-id="23c46-195">false</span></span>|<span data-ttu-id="23c46-196">false</span><span class="sxs-lookup"><span data-stu-id="23c46-196">false</span></span>|<span data-ttu-id="23c46-197">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-197">null</span></span>|  
|<span data-ttu-id="23c46-198">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-198">null</span></span>|<span data-ttu-id="23c46-199">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-199">null</span></span>|<span data-ttu-id="23c46-200">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-200">null</span></span>|<span data-ttu-id="23c46-201">nulo</span><span class="sxs-lookup"><span data-stu-id="23c46-201">null</span></span>|  

<span data-ttu-id="23c46-202">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="23c46-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="23c46-203">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="23c46-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="23c46-204">Tal operador produz `null` se qualquer um de seus operandos é avaliado como `null` .</span><span class="sxs-lookup"><span data-stu-id="23c46-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="23c46-205">No entanto, os `&` `|` operadores e podem produzir não nulo mesmo se um dos operandos for avaliado como `null` .</span><span class="sxs-lookup"><span data-stu-id="23c46-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="23c46-206">Para obter mais informações sobre o comportamento do operador com tipos de valores anuláveis, consulte a seção [operadores levantados](../builtin-types/nullable-value-types.md#lifted-operators) do artigo [tipos de valores anuláveis](../builtin-types/nullable-value-types.md) .</span><span class="sxs-lookup"><span data-stu-id="23c46-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="23c46-207">Você também pode usar os `!` `^` operadores e com `bool?` operandos, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="23c46-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="23c46-208">Os operadores lógicos condicionais `&&` e `||` não dão suporte a `bool?` operandos.</span><span class="sxs-lookup"><span data-stu-id="23c46-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="23c46-209">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="23c46-209">Compound assignment</span></span>

<span data-ttu-id="23c46-210">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="23c46-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="23c46-211">é equivalente a</span><span class="sxs-lookup"><span data-stu-id="23c46-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="23c46-212">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="23c46-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="23c46-213">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="23c46-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="23c46-214">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="23c46-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="23c46-215">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="23c46-215">Operator precedence</span></span>

<span data-ttu-id="23c46-216">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="23c46-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="23c46-217">Operador de negação lógica `!`</span><span class="sxs-lookup"><span data-stu-id="23c46-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="23c46-218">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="23c46-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="23c46-219">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="23c46-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="23c46-220">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="23c46-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="23c46-221">Operador AND lógico condicional `&&`</span><span class="sxs-lookup"><span data-stu-id="23c46-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="23c46-222">Operador OR lógico condicional `||`</span><span class="sxs-lookup"><span data-stu-id="23c46-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="23c46-223">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="23c46-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="23c46-224">Para obter a lista completa de operadores C# ordenados por nível de precedência, consulte a seção [precedência de operador](index.md#operator-precedence) do artigo sobre [operadores do c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="23c46-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="23c46-225">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="23c46-225">Operator overloadability</span></span>

<span data-ttu-id="23c46-226">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) os `!` operadores,, `&` `|` e `^` .</span><span class="sxs-lookup"><span data-stu-id="23c46-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="23c46-227">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="23c46-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="23c46-228">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="23c46-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="23c46-229">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="23c46-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="23c46-230">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="23c46-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="23c46-231">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="23c46-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="23c46-232">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="23c46-232">C# language specification</span></span>

<span data-ttu-id="23c46-233">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="23c46-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="23c46-234">Operador de negação lógica</span><span class="sxs-lookup"><span data-stu-id="23c46-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="23c46-235">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="23c46-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="23c46-236">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="23c46-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="23c46-237">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="23c46-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="23c46-238">Confira também</span><span class="sxs-lookup"><span data-stu-id="23c46-238">See also</span></span>

- [<span data-ttu-id="23c46-239">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="23c46-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="23c46-240">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="23c46-240">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="23c46-241">Operadores shift e bit a bit</span><span class="sxs-lookup"><span data-stu-id="23c46-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)

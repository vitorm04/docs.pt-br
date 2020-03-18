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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399493"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="dcf49-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="dcf49-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="dcf49-104">Os seguintes operadores realizam operações lógicas com [bool](../builtin-types/bool.md) operands:</span><span class="sxs-lookup"><span data-stu-id="dcf49-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="dcf49-105">Operador unary [ `!` (negação lógica).](#logical-negation-operator-)</span><span class="sxs-lookup"><span data-stu-id="dcf49-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="dcf49-106">Operadores binários [ `&` (lógicos e)](#logical-and-operator-) [ `|` (lógicos)](#logical-or-operator-)e [ `^` (lógico exclusivos) operadores.](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="dcf49-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="dcf49-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="dcf49-108">Operadores binários [ `&&` (lógicos condicionais E)](#conditional-logical-and-operator-) e [ `||` (condicionais lógicos)](#conditional-logical-or-operator-) operadores.</span><span class="sxs-lookup"><span data-stu-id="dcf49-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="dcf49-109">Esses operadores avaliam o operando à direita apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="dcf49-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="dcf49-110">Para os operadores dos [tipos numéricos integrais,](../builtin-types/integral-numeric-types.md)os `&` `|`operadores e `^` os operadores realizam operações lógicas bitwise.</span><span class="sxs-lookup"><span data-stu-id="dcf49-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="dcf49-111">Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dcf49-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="dcf49-112">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="dcf49-112">Logical negation operator !</span></span>

<span data-ttu-id="dcf49-113">O operador `!` de prefixo unary calcula a negação lógica de seu operato.</span><span class="sxs-lookup"><span data-stu-id="dcf49-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="dcf49-114">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="dcf49-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="dcf49-115">Começando com C# 8.0, o `!` operador postfix unary é o [operador de perdão nulo](null-forgiving.md).</span><span class="sxs-lookup"><span data-stu-id="dcf49-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-"></a><span data-ttu-id="dcf49-116">Lógico E operador&amp;</span><span class="sxs-lookup"><span data-stu-id="dcf49-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="dcf49-117">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="dcf49-118">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="dcf49-119">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="dcf49-120">O `&` operador avalia ambos os operands mesmo que o `false`oper e o oper esquerdo avalie para , de modo que o resultado da operação é `false` independentemente do valor do operand direito.</span><span class="sxs-lookup"><span data-stu-id="dcf49-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="dcf49-121">No exemplo a seguir, o operando à direita do operador `&` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="dcf49-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="dcf49-122">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="dcf49-123">Para operands dos [tipos numéricos integrais,](../builtin-types/integral-numeric-types.md)o `&` operador calcula o [bitwise lógico e](bitwise-and-shift-operators.md#logical-and-operator-) de seus operands.</span><span class="sxs-lookup"><span data-stu-id="dcf49-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="dcf49-124">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="dcf49-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="dcf49-125">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="dcf49-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="dcf49-126">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="dcf49-127">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="dcf49-128">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dcf49-129">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="dcf49-130">Para operands dos [tipos numéricos integrais,](../builtin-types/integral-numeric-types.md)o `^` operador calcula o [bitwise lógico exclusivo OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operands.</span><span class="sxs-lookup"><span data-stu-id="dcf49-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="dcf49-131">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="dcf49-131">Logical OR operator |</span></span>

<span data-ttu-id="dcf49-132">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="dcf49-133">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="dcf49-134">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="dcf49-135">O `|` operador avalia ambos os operands mesmo que o `true`oper e o oper esquerdo avalie para , de modo que o resultado da operação é `true` independentemente do valor do operand direito.</span><span class="sxs-lookup"><span data-stu-id="dcf49-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="dcf49-136">No exemplo a seguir, o operando à direita do operador `|` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="dcf49-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="dcf49-137">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="dcf49-138">Para operands dos [tipos numéricos integrais,](../builtin-types/integral-numeric-types.md)o `|` operador calcula o [or bitwise lógico](bitwise-and-shift-operators.md#logical-or-operator-) de seus operands.</span><span class="sxs-lookup"><span data-stu-id="dcf49-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a><span data-ttu-id="dcf49-139">Lógico condicional e operador&amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="dcf49-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="dcf49-140">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="dcf49-141">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="dcf49-142">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dcf49-143">Se `x` for avaliado como `false`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="dcf49-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="dcf49-144">No exemplo a seguir, o operando à direita do operador `&&` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="dcf49-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="dcf49-145">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="dcf49-146">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="dcf49-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="dcf49-147">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="dcf49-148">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="dcf49-149">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="dcf49-150">Se `x` for avaliado como `true`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="dcf49-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="dcf49-151">No exemplo a seguir, o operando à direita do operador `||` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="dcf49-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="dcf49-152">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="dcf49-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="dcf49-153">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="dcf49-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="dcf49-154">Para `bool?` os operadores, `&` `|` os operadores e os operadores suportam a lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="dcf49-154">For `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="dcf49-155">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="dcf49-155">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="dcf49-156">x</span><span class="sxs-lookup"><span data-stu-id="dcf49-156">x</span></span>|<span data-ttu-id="dcf49-157">y</span><span class="sxs-lookup"><span data-stu-id="dcf49-157">y</span></span>|<span data-ttu-id="dcf49-158">x&y</span><span class="sxs-lookup"><span data-stu-id="dcf49-158">x&y</span></span>|<span data-ttu-id="dcf49-159">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="dcf49-159">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="dcf49-160">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-160">true</span></span>|<span data-ttu-id="dcf49-161">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-161">true</span></span>|<span data-ttu-id="dcf49-162">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-162">true</span></span>|<span data-ttu-id="dcf49-163">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-163">true</span></span>|  
|<span data-ttu-id="dcf49-164">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-164">true</span></span>|<span data-ttu-id="dcf49-165">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-165">false</span></span>|<span data-ttu-id="dcf49-166">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-166">false</span></span>|<span data-ttu-id="dcf49-167">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-167">true</span></span>|  
|<span data-ttu-id="dcf49-168">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-168">true</span></span>|<span data-ttu-id="dcf49-169">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-169">null</span></span>|<span data-ttu-id="dcf49-170">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-170">null</span></span>|<span data-ttu-id="dcf49-171">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-171">true</span></span>|  
|<span data-ttu-id="dcf49-172">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-172">false</span></span>|<span data-ttu-id="dcf49-173">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-173">true</span></span>|<span data-ttu-id="dcf49-174">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-174">false</span></span>|<span data-ttu-id="dcf49-175">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-175">true</span></span>|  
|<span data-ttu-id="dcf49-176">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-176">false</span></span>|<span data-ttu-id="dcf49-177">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-177">false</span></span>|<span data-ttu-id="dcf49-178">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-178">false</span></span>|<span data-ttu-id="dcf49-179">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-179">false</span></span>|  
|<span data-ttu-id="dcf49-180">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-180">false</span></span>|<span data-ttu-id="dcf49-181">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-181">null</span></span>|<span data-ttu-id="dcf49-182">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-182">false</span></span>|<span data-ttu-id="dcf49-183">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-183">null</span></span>|  
|<span data-ttu-id="dcf49-184">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-184">null</span></span>|<span data-ttu-id="dcf49-185">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-185">true</span></span>|<span data-ttu-id="dcf49-186">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-186">null</span></span>|<span data-ttu-id="dcf49-187">true</span><span class="sxs-lookup"><span data-stu-id="dcf49-187">true</span></span>|  
|<span data-ttu-id="dcf49-188">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-188">null</span></span>|<span data-ttu-id="dcf49-189">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-189">false</span></span>|<span data-ttu-id="dcf49-190">false</span><span class="sxs-lookup"><span data-stu-id="dcf49-190">false</span></span>|<span data-ttu-id="dcf49-191">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-191">null</span></span>|  
|<span data-ttu-id="dcf49-192">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-192">null</span></span>|<span data-ttu-id="dcf49-193">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-193">null</span></span>|<span data-ttu-id="dcf49-194">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-194">null</span></span>|<span data-ttu-id="dcf49-195">nulo</span><span class="sxs-lookup"><span data-stu-id="dcf49-195">null</span></span>|  

<span data-ttu-id="dcf49-196">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="dcf49-196">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="dcf49-197">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="dcf49-197">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="dcf49-198">Tal operador produz `null` se algum de seus operands avaliar . `null`</span><span class="sxs-lookup"><span data-stu-id="dcf49-198">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="dcf49-199">No entanto, os `&` operadores e `|` operadores podem produzir não nulos mesmo se um dos operands avaliar . `null`</span><span class="sxs-lookup"><span data-stu-id="dcf49-199">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="dcf49-200">Para obter mais informações sobre o comportamento do operador com tipos de valor anulados, consulte a seção [Operadores Suspensos](../builtin-types/nullable-value-types.md#lifted-operators) do artigo [Tipos de valor Anulado.](../builtin-types/nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="dcf49-200">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="dcf49-201">Você também pode `!` `^` usar os `bool?` operadores e operadores com operands, como o exemplo a seguir mostra:</span><span class="sxs-lookup"><span data-stu-id="dcf49-201">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="dcf49-202">Os operadores lógicos condicionais `&&` e `||` não suportam `bool?` operadores.</span><span class="sxs-lookup"><span data-stu-id="dcf49-202">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="dcf49-203">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="dcf49-203">Compound assignment</span></span>

<span data-ttu-id="dcf49-204">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="dcf49-204">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="dcf49-205">é equivalente a</span><span class="sxs-lookup"><span data-stu-id="dcf49-205">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="dcf49-206">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="dcf49-206">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="dcf49-207">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="dcf49-207">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="dcf49-208">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="dcf49-208">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="dcf49-209">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="dcf49-209">Operator precedence</span></span>

<span data-ttu-id="dcf49-210">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="dcf49-210">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="dcf49-211">Operador de negação lógico `!`</span><span class="sxs-lookup"><span data-stu-id="dcf49-211">Logical negation operator `!`</span></span>
- <span data-ttu-id="dcf49-212">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="dcf49-212">Logical AND operator `&`</span></span>
- <span data-ttu-id="dcf49-213">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="dcf49-213">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="dcf49-214">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="dcf49-214">Logical OR operator `|`</span></span>
- <span data-ttu-id="dcf49-215">Operador AND lógico condicional `&&`</span><span class="sxs-lookup"><span data-stu-id="dcf49-215">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="dcf49-216">Operador OR lógico condicional `||`</span><span class="sxs-lookup"><span data-stu-id="dcf49-216">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="dcf49-217">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="dcf49-217">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="dcf49-218">Para obter a lista completa de operadores C# ordenados por nível de precedência, consulte a seção de [precedência](index.md#operator-precedence) do operador [C#.](index.md)</span><span class="sxs-lookup"><span data-stu-id="dcf49-218">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dcf49-219">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="dcf49-219">Operator overloadability</span></span>

<span data-ttu-id="dcf49-220">Um tipo definido pelo usuário `&` `|`pode `^` [sobrecarregar](operator-overloading.md) os `!`operadores e operadores.</span><span class="sxs-lookup"><span data-stu-id="dcf49-220">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="dcf49-221">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="dcf49-221">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="dcf49-222">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="dcf49-222">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="dcf49-223">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="dcf49-223">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="dcf49-224">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="dcf49-224">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="dcf49-225">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="dcf49-225">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dcf49-226">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dcf49-226">C# language specification</span></span>

<span data-ttu-id="dcf49-227">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="dcf49-227">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="dcf49-228">Operador de negação lógica</span><span class="sxs-lookup"><span data-stu-id="dcf49-228">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="dcf49-229">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="dcf49-229">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="dcf49-230">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="dcf49-230">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="dcf49-231">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="dcf49-231">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="dcf49-232">Confira também</span><span class="sxs-lookup"><span data-stu-id="dcf49-232">See also</span></span>

- [<span data-ttu-id="dcf49-233">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="dcf49-233">C# reference</span></span>](../index.md)
- [<span data-ttu-id="dcf49-234">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="dcf49-234">C# operators</span></span>](index.md)
- [<span data-ttu-id="dcf49-235">Operadores shift e bit a bit</span><span class="sxs-lookup"><span data-stu-id="dcf49-235">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)

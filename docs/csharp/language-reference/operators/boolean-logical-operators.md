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
ms.openlocfilehash: cc25d4bfd444dc0acb30fc1c6e6c3c9918af537c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698676"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="378c1-103">Operadores lógicos boolianos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="378c1-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="378c1-104">Os operadores a seguir executam operações lógicas com os operandos [bool](../keywords/bool.md):</span><span class="sxs-lookup"><span data-stu-id="378c1-104">The following operators perform logical operations with the [bool](../keywords/bool.md) operands:</span></span>

- <span data-ttu-id="378c1-105">Operador unário [`!` (negação lógica)](#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="378c1-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="378c1-106">Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="378c1-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="378c1-107">Esses operadores sempre avaliam os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="378c1-108">Operadores binários [`&&` (AND lógico condicional)](#conditional-logical-and-operator-) e [`||` (OR lógico condicional)](#conditional-logical-or-operator-).</span><span class="sxs-lookup"><span data-stu-id="378c1-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="378c1-109">Esses operadores avaliam o operando à direita apenas se for necessário.</span><span class="sxs-lookup"><span data-stu-id="378c1-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="378c1-110">Para os operandos de tipos [integrais](../builtin-types/integral-numeric-types.md), os operadores `&`, `|` e `^` executam operações lógicas bit a bit.</span><span class="sxs-lookup"><span data-stu-id="378c1-110">For the operands of the [integral](../builtin-types/integral-numeric-types.md) types, the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="378c1-111">Para obter mais informações, veja [Operadores bit a bit e shift](bitwise-and-shift-operators.md).</span><span class="sxs-lookup"><span data-stu-id="378c1-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="378c1-112">Operador de negação lógica !</span><span class="sxs-lookup"><span data-stu-id="378c1-112">Logical negation operator !</span></span>

<span data-ttu-id="378c1-113">O operador `!` calcula a negação lógica de seu operando.</span><span class="sxs-lookup"><span data-stu-id="378c1-113">The `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="378c1-114">Ou seja, ele produz `true`, se o operando for avaliado como `false`, e `false`, se o operando for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="378c1-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="378c1-115">A partir C# do 8,0, o operador `!` de sufixo unário é um operador NULL-tolerante.</span><span class="sxs-lookup"><span data-stu-id="378c1-115">Starting with C# 8.0, the unary postfix `!` operator is a null-forgiving operator.</span></span> <span data-ttu-id="378c1-116">Em um contexto de anotação anulável habilitado, você o usa para declarar que a expressão `x` de um tipo de referência anulável não é nula: `x!`.</span><span class="sxs-lookup"><span data-stu-id="378c1-116">In an enabled nullable annotation context, you use it to declare that expression `x` of a nullable reference type isn't null: `x!`.</span></span> <span data-ttu-id="378c1-117">Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="378c1-117">For more information, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="378c1-118">Operador AND lógico &amp;</span><span class="sxs-lookup"><span data-stu-id="378c1-118">Logical AND operator &amp;</span></span>

<span data-ttu-id="378c1-119">O operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-119">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="378c1-120">O resultado de `x & y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-120">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="378c1-121">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-121">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="378c1-122">O operador `&` avalia os dois operandos, mesmo se o operando à esquerda for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="378c1-122">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the result must be `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="378c1-123">No exemplo a seguir, o operando à direita do operador `&` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="378c1-123">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="378c1-124">O [operador AND lógico condicional](#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-124">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="378c1-125">Para os operandos de tipos integrais, o operador `&` computa o [AND lógico bit a bit](bitwise-and-shift-operators.md#logical-and-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-125">For the operands of the integral types, the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="378c1-126">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="378c1-126">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="378c1-127">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="378c1-127">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="378c1-128">O operador `^` computa o OR exclusivo lógico, também conhecido como o XOR lógico, de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-128">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="378c1-129">O resultado de `x ^ y` é `true` se `x` é avaliado como `true` e `y` avaliado como `false`, ou `x` avaliado como `false` e `y` avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-129">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="378c1-130">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-130">Otherwise, the result is `false`.</span></span> <span data-ttu-id="378c1-131">Ou seja, para os operandos `bool`, o operador `^` computa o mesmo resultado que o [operador de desigualdade](equality-operators.md#inequality-operator-) `!=`.</span><span class="sxs-lookup"><span data-stu-id="378c1-131">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="378c1-132">Para os operandos de tipos integrais, o operador `^` computa o [OR exclusivo bit a bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-132">For the operands of the integral types, the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="378c1-133">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="378c1-133">Logical OR operator |</span></span>

<span data-ttu-id="378c1-134">O operador `|` computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-134">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="378c1-135">O resultado de `x | y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-135">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="378c1-136">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-136">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="378c1-137">O operador `|` avalia os dois operandos, mesmo se o operando à esquerda for avaliado como `true`, de modo que o resultado deve ser `true`, independentemente do valor do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="378c1-137">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the result must be `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="378c1-138">No exemplo a seguir, o operando à direita do operador `|` é uma chamada de método, que é executada independentemente do valor do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="378c1-138">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="378c1-139">O [operador OR lógico condicional](#conditional-logical-or-operator-) `||` também computa o OR lógico e seus operandos, mas não avalia o operando à direita se o operando à esquerda for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-139">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="378c1-140">Para os operandos de tipos integrais, o operador `|` computa o [OR lógico bit a bit](bitwise-and-shift-operators.md#logical-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-140">For the operands of the integral types, the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-"></a> <span data-ttu-id="378c1-141">Operador AND lógico condicional &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="378c1-141">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="378c1-142">O operador AND lógico condicional `&&`, também conhecido como operador AND lógico de "curto-circuito", computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-142">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="378c1-143">O resultado de `x && y` será `true` se ambos `x` e `y` forem avaliados como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-143">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="378c1-144">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-144">Otherwise, the result is `false`.</span></span> <span data-ttu-id="378c1-145">Se `x` for avaliado como `false`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="378c1-145">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="378c1-146">No exemplo a seguir, o operando à direita do operador `&&` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `false`:</span><span class="sxs-lookup"><span data-stu-id="378c1-146">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="378c1-147">O [operador AND lógico](#logical-and-operator-) `&` também computa o AND lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-147">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="378c1-148">Operador OR lógico condicional ||</span><span class="sxs-lookup"><span data-stu-id="378c1-148">Conditional logical OR operator ||</span></span>

<span data-ttu-id="378c1-149">O operador OR lógico condicional `||`, também conhecido como operador OR lógico de "curto-circuito", computa o OR lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-149">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="378c1-150">O resultado de `x || y` será `true` se `x` ou `y` for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="378c1-150">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="378c1-151">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="378c1-151">Otherwise, the result is `false`.</span></span> <span data-ttu-id="378c1-152">Se `x` for avaliado como `true`, `y` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="378c1-152">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="378c1-153">No exemplo a seguir, o operando à direita do operador `||` é uma chamada de método, que não é executada se o operando à esquerda for avaliado como `true`:</span><span class="sxs-lookup"><span data-stu-id="378c1-153">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="378c1-154">O [operador OR lógico](#logical-or-operator-) `|` também computa o OR lógico de seus operandos, mas sempre avalia os dois operandos.</span><span class="sxs-lookup"><span data-stu-id="378c1-154">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="378c1-155">Operadores lógicos booleanos anuláveis</span><span class="sxs-lookup"><span data-stu-id="378c1-155">Nullable Boolean logical operators</span></span>

<span data-ttu-id="378c1-156">Para os operandos `bool?`, os operadores `&` e `|` oferecem suporte à lógica de três valores.</span><span class="sxs-lookup"><span data-stu-id="378c1-156">For the `bool?` operands, the `&` and `|` operators support the three-valued logic.</span></span> <span data-ttu-id="378c1-157">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="378c1-157">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="378c1-158">x</span><span class="sxs-lookup"><span data-stu-id="378c1-158">x</span></span>|<span data-ttu-id="378c1-159">y</span><span class="sxs-lookup"><span data-stu-id="378c1-159">y</span></span>|<span data-ttu-id="378c1-160">x&y</span><span class="sxs-lookup"><span data-stu-id="378c1-160">x&y</span></span>|<span data-ttu-id="378c1-161">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="378c1-161">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="378c1-162">true</span><span class="sxs-lookup"><span data-stu-id="378c1-162">true</span></span>|<span data-ttu-id="378c1-163">true</span><span class="sxs-lookup"><span data-stu-id="378c1-163">true</span></span>|<span data-ttu-id="378c1-164">true</span><span class="sxs-lookup"><span data-stu-id="378c1-164">true</span></span>|<span data-ttu-id="378c1-165">true</span><span class="sxs-lookup"><span data-stu-id="378c1-165">true</span></span>|  
|<span data-ttu-id="378c1-166">true</span><span class="sxs-lookup"><span data-stu-id="378c1-166">true</span></span>|<span data-ttu-id="378c1-167">false</span><span class="sxs-lookup"><span data-stu-id="378c1-167">false</span></span>|<span data-ttu-id="378c1-168">false</span><span class="sxs-lookup"><span data-stu-id="378c1-168">false</span></span>|<span data-ttu-id="378c1-169">true</span><span class="sxs-lookup"><span data-stu-id="378c1-169">true</span></span>|  
|<span data-ttu-id="378c1-170">true</span><span class="sxs-lookup"><span data-stu-id="378c1-170">true</span></span>|<span data-ttu-id="378c1-171">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-171">null</span></span>|<span data-ttu-id="378c1-172">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-172">null</span></span>|<span data-ttu-id="378c1-173">true</span><span class="sxs-lookup"><span data-stu-id="378c1-173">true</span></span>|  
|<span data-ttu-id="378c1-174">false</span><span class="sxs-lookup"><span data-stu-id="378c1-174">false</span></span>|<span data-ttu-id="378c1-175">true</span><span class="sxs-lookup"><span data-stu-id="378c1-175">true</span></span>|<span data-ttu-id="378c1-176">false</span><span class="sxs-lookup"><span data-stu-id="378c1-176">false</span></span>|<span data-ttu-id="378c1-177">true</span><span class="sxs-lookup"><span data-stu-id="378c1-177">true</span></span>|  
|<span data-ttu-id="378c1-178">false</span><span class="sxs-lookup"><span data-stu-id="378c1-178">false</span></span>|<span data-ttu-id="378c1-179">false</span><span class="sxs-lookup"><span data-stu-id="378c1-179">false</span></span>|<span data-ttu-id="378c1-180">false</span><span class="sxs-lookup"><span data-stu-id="378c1-180">false</span></span>|<span data-ttu-id="378c1-181">false</span><span class="sxs-lookup"><span data-stu-id="378c1-181">false</span></span>|  
|<span data-ttu-id="378c1-182">false</span><span class="sxs-lookup"><span data-stu-id="378c1-182">false</span></span>|<span data-ttu-id="378c1-183">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-183">null</span></span>|<span data-ttu-id="378c1-184">false</span><span class="sxs-lookup"><span data-stu-id="378c1-184">false</span></span>|<span data-ttu-id="378c1-185">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-185">null</span></span>|  
|<span data-ttu-id="378c1-186">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-186">null</span></span>|<span data-ttu-id="378c1-187">true</span><span class="sxs-lookup"><span data-stu-id="378c1-187">true</span></span>|<span data-ttu-id="378c1-188">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-188">null</span></span>|<span data-ttu-id="378c1-189">true</span><span class="sxs-lookup"><span data-stu-id="378c1-189">true</span></span>|  
|<span data-ttu-id="378c1-190">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-190">null</span></span>|<span data-ttu-id="378c1-191">false</span><span class="sxs-lookup"><span data-stu-id="378c1-191">false</span></span>|<span data-ttu-id="378c1-192">false</span><span class="sxs-lookup"><span data-stu-id="378c1-192">false</span></span>|<span data-ttu-id="378c1-193">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-193">null</span></span>|  
|<span data-ttu-id="378c1-194">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-194">null</span></span>|<span data-ttu-id="378c1-195">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-195">null</span></span>|<span data-ttu-id="378c1-196">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-196">null</span></span>|<span data-ttu-id="378c1-197">nulo</span><span class="sxs-lookup"><span data-stu-id="378c1-197">null</span></span>|  

<span data-ttu-id="378c1-198">O comportamento desses operadores difere do comportamento típico do operador com tipos de valores anuláveis.</span><span class="sxs-lookup"><span data-stu-id="378c1-198">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="378c1-199">Normalmente, um operador que é definido para operandos de um tipo de valor também pode ser usado com operandos do tipo de valor anulável correspondente.</span><span class="sxs-lookup"><span data-stu-id="378c1-199">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="378c1-200">Esse operador produz `null` se algum de seus operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="378c1-200">Such an operator produces `null` if any of its operands is `null`.</span></span> <span data-ttu-id="378c1-201">No entanto, os operadores `&` e `|` podem produzir não nulos, mesmo se um dos operandos for `null`.</span><span class="sxs-lookup"><span data-stu-id="378c1-201">However, the `&` and `|` operators can produce non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="378c1-202">Para obter mais informações sobre o comportamento do operador com tipos de valores anuláveis, consulte a seção [operadores](../../programming-guide/nullable-types/using-nullable-types.md#operators) do artigo [usando tipos de valores anuláveis](../../programming-guide/nullable-types/using-nullable-types.md) .</span><span class="sxs-lookup"><span data-stu-id="378c1-202">For more information about the operator behavior with nullable value types, see the [Operators](../../programming-guide/nullable-types/using-nullable-types.md#operators) section of the [Using nullable value types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

<span data-ttu-id="378c1-203">Você também pode usar os operadores `!` e `^`com os operandos`bool?`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="378c1-203">You can also use the `!` and `^` operators with the `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="378c1-204">Os operadores lógicos condicionais `&&` e `||` não oferecem suporte aos operandos `bool?`.</span><span class="sxs-lookup"><span data-stu-id="378c1-204">The conditional logical operators `&&` and `||` don't support the `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="378c1-205">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="378c1-205">Compound assignment</span></span>

<span data-ttu-id="378c1-206">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="378c1-206">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="378c1-207">equivale a</span><span class="sxs-lookup"><span data-stu-id="378c1-207">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="378c1-208">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="378c1-208">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="378c1-209">Os operadores `&`, `|` e `^` suportam a atribuição de compostos, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="378c1-209">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

<span data-ttu-id="378c1-210">Os operadores lógicos condicionais `&&` e `||` não suportam a atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="378c1-210">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="378c1-211">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="378c1-211">Operator precedence</span></span>

<span data-ttu-id="378c1-212">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="378c1-212">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="378c1-213">Operador de negação lógico `!`</span><span class="sxs-lookup"><span data-stu-id="378c1-213">Logical negation operator `!`</span></span>
- <span data-ttu-id="378c1-214">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="378c1-214">Logical AND operator `&`</span></span>
- <span data-ttu-id="378c1-215">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="378c1-215">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="378c1-216">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="378c1-216">Logical OR operator `|`</span></span>
- <span data-ttu-id="378c1-217">Operador AND lógico condicional `&&`</span><span class="sxs-lookup"><span data-stu-id="378c1-217">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="378c1-218">Operador OR lógico condicional `||`</span><span class="sxs-lookup"><span data-stu-id="378c1-218">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="378c1-219">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="378c1-219">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="378c1-220">Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="378c1-220">For the complete list of C# operators ordered by precedence level, see [C# operators](index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="378c1-221">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="378c1-221">Operator overloadability</span></span>

<span data-ttu-id="378c1-222">Os tipos definidos pelo usuário podem [sobrecarregar](operator-overloading.md) os operadores `!`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="378c1-222">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="378c1-223">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="378c1-223">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="378c1-224">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="378c1-224">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="378c1-225">Um tipo definido pelo usuário não pode sobrecarregar os operadores lógicos condicionais `&&` e `||`.</span><span class="sxs-lookup"><span data-stu-id="378c1-225">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="378c1-226">No entanto, se um tipo definido pelo usuário sobrecarregar os operadores [true e false](true-false-operators.md) e o operador `&` ou `|` de uma determinada maneira, a operação `&&` ou `||`, respectivamente, pode ser avaliada para os operandos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="378c1-226">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="378c1-227">Para obter mais informações, veja a seção [Operadores lógicos condicionais definidos pelo usuário](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) na [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="378c1-227">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="378c1-228">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="378c1-228">C# language specification</span></span>

<span data-ttu-id="378c1-229">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="378c1-229">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="378c1-230">Operador de negação lógico</span><span class="sxs-lookup"><span data-stu-id="378c1-230">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="378c1-231">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="378c1-231">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="378c1-232">Operadores lógicos condicionais</span><span class="sxs-lookup"><span data-stu-id="378c1-232">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="378c1-233">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="378c1-233">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="378c1-234">Consulte também</span><span class="sxs-lookup"><span data-stu-id="378c1-234">See also</span></span>

- [<span data-ttu-id="378c1-235">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="378c1-235">C# reference</span></span>](../index.md)
- [<span data-ttu-id="378c1-236">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="378c1-236">C# operators</span></span>](index.md)
- [<span data-ttu-id="378c1-237">Operadores shift e bit a bit</span><span class="sxs-lookup"><span data-stu-id="378c1-237">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)

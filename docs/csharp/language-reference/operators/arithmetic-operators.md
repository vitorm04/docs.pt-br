---
title: Operadores aritméticos – referência do C#
description: Saiba mais sobre os operadores do C# que executam operações de multiplicação, divisão, resto, adição e subtração com tipos numéricos.
ms.date: 05/11/2020
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
- '%=_CSharpKeyword'
- '*=_CSharpKeyword'
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: f5da9c4433ffcf3e6a110bbb1543343289240778
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916944"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="1fad6-103">Operadores aritméticos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="1fad6-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="1fad6-104">Os operadores a seguir executam operações aritméticas com operandos de tipos numéricos:</span><span class="sxs-lookup"><span data-stu-id="1fad6-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="1fad6-105">Operadores unários [ `++` (incremento](#increment-operator-)), [ `--` (decrementar)](#decrement-operator---), [ `+` (além)](#unary-plus-and-minus-operators)e [ `-` (menos)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="1fad6-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="1fad6-106">Operadores binário [ `*` (multiplicação)](#multiplication-operator-), [ `/` (divisão)](#division-operator-), [ `%` (restante)](#remainder-operator-), [ `+` (adição)](#addition-operator-)e [ `-` (subtração)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="1fad6-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="1fad6-107">Esses operadores têm suporte de todos os tipos numéricos [integral](../builtin-types/integral-numeric-types.md) e [de ponto flutuante](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

<span data-ttu-id="1fad6-108">No caso de tipos integrais, esses operadores (exceto os `++` `--` operadores e) são definidos para os `int` `uint` tipos,, `long` e `ulong` .</span><span class="sxs-lookup"><span data-stu-id="1fad6-108">In the case of integral types, those operators (except the `++` and `--` operators) are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="1fad6-109">Quando operandos são de outros tipos integrais (,,, `sbyte` `byte` `short` `ushort` ou `char` ), seus valores são convertidos para o `int` tipo, que também é o tipo de resultado de uma operação.</span><span class="sxs-lookup"><span data-stu-id="1fad6-109">When operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="1fad6-110">Quando operandos são de diferentes tipos de ponto flutuante ou integral, seus valores são convertidos para o tipo recipiente mais próximo, se esse tipo existir.</span><span class="sxs-lookup"><span data-stu-id="1fad6-110">When operands are of different integral or floating-point types, their values are converted to the closest containing type, if such a type exists.</span></span> <span data-ttu-id="1fad6-111">Para saber mais, confira a seção [Promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="1fad6-112">Os `++` `--` operadores e são definidos para todos os tipos de inteiro e numérico de ponto flutuante e o tipo [Char](../builtin-types/char.md) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-112">The `++` and `--` operators are defined for all integral and floating-point numeric types and the [char](../builtin-types/char.md) type.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="1fad6-113">Operador de incremento ++</span><span class="sxs-lookup"><span data-stu-id="1fad6-113">Increment operator ++</span></span>

<span data-ttu-id="1fad6-114">O operador de incremento unário `++` incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="1fad6-114">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="1fad6-115">O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-115">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="1fad6-116">Há duas formas de suporte para o operador de incremento: o operador de incremento pós-fixado, `x++`, e o operador de incremento pré-fixado, `++x`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-116">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="1fad6-117">Operador de incremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="1fad6-117">Postfix increment operator</span></span>

<span data-ttu-id="1fad6-118">O resultado de `x++` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fad6-118">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](snippets/shared/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="1fad6-119">Operador de incremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="1fad6-119">Prefix increment operator</span></span>

<span data-ttu-id="1fad6-120">O resultado de `++x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fad6-120">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](snippets/shared/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="1fad6-121">Operador de decremento --</span><span class="sxs-lookup"><span data-stu-id="1fad6-121">Decrement operator --</span></span>

<span data-ttu-id="1fad6-122">O operador de decremento unário `--` decrementa o operando em 1.</span><span class="sxs-lookup"><span data-stu-id="1fad6-122">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="1fad6-123">O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-123">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="1fad6-124">Há duas formas de suporte para o operador de decremento: o operador de decremento pós-fixado, `x--`, e o operador de decremento pré-fixado, `--x`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-124">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="1fad6-125">Operador de decremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="1fad6-125">Postfix decrement operator</span></span>

<span data-ttu-id="1fad6-126">O resultado de `x--` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fad6-126">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](snippets/shared/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="1fad6-127">Operador de decremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="1fad6-127">Prefix decrement operator</span></span>

<span data-ttu-id="1fad6-128">O resultado de `--x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1fad6-128">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](snippets/shared/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="1fad6-129">Operadores unários de adição e subtração</span><span class="sxs-lookup"><span data-stu-id="1fad6-129">Unary plus and minus operators</span></span>

<span data-ttu-id="1fad6-130">O operador unário `+` retorna o valor do operando.</span><span class="sxs-lookup"><span data-stu-id="1fad6-130">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="1fad6-131">O operador unário `-` calcula a negação numérica do operando.</span><span class="sxs-lookup"><span data-stu-id="1fad6-131">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](snippets/shared/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="1fad6-132">O tipo [ULONG](../builtin-types/integral-numeric-types.md) não dá suporte ao `-` operador unário.</span><span class="sxs-lookup"><span data-stu-id="1fad6-132">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="1fad6-133">Operador de multiplicação \*</span><span class="sxs-lookup"><span data-stu-id="1fad6-133">Multiplication operator \*</span></span>

<span data-ttu-id="1fad6-134">O operador de multiplicação `*` calcula o produto dos operandos:</span><span class="sxs-lookup"><span data-stu-id="1fad6-134">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](snippets/shared/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="1fad6-135">O operador unário `*` é o [operador de indireção de ponteiro](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="1fad6-135">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="1fad6-136">Operador de divisão /</span><span class="sxs-lookup"><span data-stu-id="1fad6-136">Division operator /</span></span>

<span data-ttu-id="1fad6-137">O operador de divisão `/` divide o operando à esquerda pelo operando à direita.</span><span class="sxs-lookup"><span data-stu-id="1fad6-137">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="1fad6-138">Divisão de inteiros</span><span class="sxs-lookup"><span data-stu-id="1fad6-138">Integer division</span></span>

<span data-ttu-id="1fad6-139">Para os operandos de tipos inteiros, o resultado do operador `/` é de um tipo inteiro e igual ao quociente dos dois operandos arredondados para zero:</span><span class="sxs-lookup"><span data-stu-id="1fad6-139">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](snippets/shared/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="1fad6-140">Para obter o quociente dos dois operandos como um número de ponto flutuante, use o tipo `float`, `double` ou `decimal`:</span><span class="sxs-lookup"><span data-stu-id="1fad6-140">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](snippets/shared/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="1fad6-141">Divisão de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="1fad6-141">Floating-point division</span></span>

<span data-ttu-id="1fad6-142">Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:</span><span class="sxs-lookup"><span data-stu-id="1fad6-142">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](snippets/shared/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="1fad6-143">Se um dos operandos é `decimal`, outro operando não pode ser `float` nem `double`, porque nem `float` ou `double` é implicitamente conversível para `decimal`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-143">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="1fad6-144">Você deve converter explicitamente o operando `float` ou `double` para o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-144">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="1fad6-145">Para obter mais informações sobre conversões entre tipos numéricos, consulte [conversões numéricas internas](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-145">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="1fad6-146">Operador de resto %</span><span class="sxs-lookup"><span data-stu-id="1fad6-146">Remainder operator %</span></span>

<span data-ttu-id="1fad6-147">O operador de resto `%` calcula o resto após dividir o operando à esquerda pelo à direita.</span><span class="sxs-lookup"><span data-stu-id="1fad6-147">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="1fad6-148">Resto inteiro</span><span class="sxs-lookup"><span data-stu-id="1fad6-148">Integer remainder</span></span>

<span data-ttu-id="1fad6-149">Para os operandos de tipos inteiros, o resultado de `a % b` é o valor produzido por `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-149">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="1fad6-150">O sinal do resto diferente de zero é o mesmo que o do operando à esquerda, conforme mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="1fad6-150">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](snippets/shared/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="1fad6-151">Use o método <xref:System.Math.DivRem%2A?displayProperty=nameWithType> para calcular a divisão de inteiros e os resultados do resto.</span><span class="sxs-lookup"><span data-stu-id="1fad6-151">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="1fad6-152">Resto de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="1fad6-152">Floating-point remainder</span></span>

<span data-ttu-id="1fad6-153">Para os operandos `float` e `double`, o resultado de `x % y` para o `x` e o `y` finitos é o valor `z` tal que</span><span class="sxs-lookup"><span data-stu-id="1fad6-153">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="1fad6-154">O sinal de `z`, se diferente de zero, é o mesmo que o sinal de `x`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-154">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="1fad6-155">O valor absoluto de `z` é o valor produzido por `|x| - n * |y|`, em que `n` é o maior inteiro possível que é inferior ou igual a `|x| / |y|`, e `|x|` e `|y|` são os valores absolutos de `x` e `y`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1fad6-155">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="1fad6-156">Esse método de computação do resto é análogo ao usado para operandos inteiros, mas diferente da especificação IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="1fad6-156">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="1fad6-157">Se você precisar da operação restante que está em conformidade com a especificação IEEE 754, use o <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="1fad6-157">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1fad6-158">Para saber mais sobre o comportamento do operador `%` com operandos não finitos, confira a seção [Operador de restante](~/_csharplang/spec/expressions.md#remainder-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-158">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="1fad6-159">Para os operandos `decimal`, o operador de resto `%` é equivalente ao [operador de resto](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) do tipo <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1fad6-159">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="1fad6-160">O seguinte exemplo demonstra o comportamento do operador de resto com os operandos de ponto flutuante:</span><span class="sxs-lookup"><span data-stu-id="1fad6-160">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](snippets/shared/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="1fad6-161">Operador de adição +</span><span class="sxs-lookup"><span data-stu-id="1fad6-161">Addition operator +</span></span>

<span data-ttu-id="1fad6-162">O operador de adição `+` calcula a soma dos operandos:</span><span class="sxs-lookup"><span data-stu-id="1fad6-162">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](snippets/shared/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="1fad6-163">Você também pode usar o `+` operador para concatenação de cadeia de caracteres e combinação de delegado.</span><span class="sxs-lookup"><span data-stu-id="1fad6-163">You can also use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="1fad6-164">Para obter mais informações, consulte o artigo [ `+` `+=` operadores e](addition-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-164">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="1fad6-165">Operador de subtração -</span><span class="sxs-lookup"><span data-stu-id="1fad6-165">Subtraction operator -</span></span>

<span data-ttu-id="1fad6-166">O operador de subtração `-` subtrai o operando à direita do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="1fad6-166">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](snippets/shared/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="1fad6-167">Você também pode usar o `-` operador para remoção de delegado.</span><span class="sxs-lookup"><span data-stu-id="1fad6-167">You can also use the `-` operator for delegate removal.</span></span> <span data-ttu-id="1fad6-168">Para obter mais informações, consulte o artigo [ `-` `-=` operadores e](subtraction-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-168">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="1fad6-169">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="1fad6-169">Compound assignment</span></span>

<span data-ttu-id="1fad6-170">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="1fad6-170">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="1fad6-171">é equivalente a</span><span class="sxs-lookup"><span data-stu-id="1fad6-171">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="1fad6-172">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1fad6-172">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="1fad6-173">O seguinte exemplo demonstra o uso da atribuição composta com operadores aritméticos:</span><span class="sxs-lookup"><span data-stu-id="1fad6-173">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](snippets/shared/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="1fad6-174">Devido a [promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions), o resultado da operação `op` pode não ser implicitamente conversível no tipo `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="1fad6-174">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="1fad6-175">Nesse caso, se `op` for um operador predefinido e o resultado da operação for explicitamente convertido no tipo `T` de `x`, uma expressão de atribuição composta da forma `x op= y` será equivalente a `x = (T)(x op y)`, exceto que `x` será avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="1fad6-175">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="1fad6-176">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="1fad6-176">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](snippets/shared/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="1fad6-177">Você também usa os `+=` `-=` operadores e para assinar e cancelar a assinatura de um [evento](../keywords/event.md), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1fad6-177">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="1fad6-178">Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="1fad6-178">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="1fad6-179">Precedência e associatividade do operador</span><span class="sxs-lookup"><span data-stu-id="1fad6-179">Operator precedence and associativity</span></span>

<span data-ttu-id="1fad6-180">A seguinte lista ordena os operadores aritméticos da precedência mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="1fad6-180">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="1fad6-181">Incluir um pós-fixo a operadores de incremento `x++` e decremento `x--`</span><span class="sxs-lookup"><span data-stu-id="1fad6-181">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="1fad6-182">Incluir um prefixo a operadores de incremento `++x` e de decremento `--x` e operadores unários `+` e `-`</span><span class="sxs-lookup"><span data-stu-id="1fad6-182">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="1fad6-183">Operadores de multiplicação `*`, `/` e `%`</span><span class="sxs-lookup"><span data-stu-id="1fad6-183">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="1fad6-184">Operadores de adição `+` e `-`</span><span class="sxs-lookup"><span data-stu-id="1fad6-184">Additive `+` and `-` operators</span></span>

<span data-ttu-id="1fad6-185">Operadores aritméticos binários são associativos à esquerda.</span><span class="sxs-lookup"><span data-stu-id="1fad6-185">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="1fad6-186">Ou seja, os operadores com o mesmo nível de precedência são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="1fad6-186">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="1fad6-187">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência e pela capacidade de associação do operador.</span><span class="sxs-lookup"><span data-stu-id="1fad6-187">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](snippets/shared/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="1fad6-188">Para obter a lista completa de operadores C# ordenados por nível de precedência, consulte a seção [precedência de operador](index.md#operator-precedence) do artigo sobre [operadores do c#](index.md) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-188">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="1fad6-189">Estouro aritmético e divisão por zero</span><span class="sxs-lookup"><span data-stu-id="1fad6-189">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="1fad6-190">Quando o resultado de uma operação aritmética está fora do intervalo de valores finitos possíveis do tipo numérico envolvido, o comportamento de um operador aritmético depende do tipo dos operandos.</span><span class="sxs-lookup"><span data-stu-id="1fad6-190">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="1fad6-191">Estouro aritmético de inteiros</span><span class="sxs-lookup"><span data-stu-id="1fad6-191">Integer arithmetic overflow</span></span>

<span data-ttu-id="1fad6-192">A divisão de inteiro por zero sempre lança um <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="1fad6-192">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="1fad6-193">No caso de um estouro aritmético de inteiros, um contexto de verificação de estouro, que pode ser [verificado ou não verificado](../keywords/checked-and-unchecked.md), controla o comportamento resultante:</span><span class="sxs-lookup"><span data-stu-id="1fad6-193">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="1fad6-194">Em um contexto verificado, se o estouro acontece em uma expressão de constante, ocorre um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="1fad6-194">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="1fad6-195">Caso contrário, quando a operação é executada em tempo de execução, uma <xref:System.OverflowException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="1fad6-195">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="1fad6-196">Em um contexto não verificado, o resultado é truncado pelo descarte dos bits de ordem superior que não se ajustam ao tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="1fad6-196">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="1fad6-197">Juntamente com as instruções [verificadas e não verificadas](../keywords/checked-and-unchecked.md), você pode usar os operadores `checked` e `unchecked` para controlar o contexto de verificação de estouro, no qual uma expressão é avaliada:</span><span class="sxs-lookup"><span data-stu-id="1fad6-197">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](snippets/shared/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="1fad6-198">Por padrão, as operações aritméticas ocorrem em um contexto *não verificado*.</span><span class="sxs-lookup"><span data-stu-id="1fad6-198">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="1fad6-199">Estouro aritmético de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="1fad6-199">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="1fad6-200">As operações aritméticas com os tipos `float` e `double` nunca geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1fad6-200">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="1fad6-201">O resultado de operações aritméticas com esses tipos pode ser um dos valores especiais que representam o infinito e um valor não é um número:</span><span class="sxs-lookup"><span data-stu-id="1fad6-201">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](snippets/shared/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="1fad6-202">Para os operandos do tipo `decimal`, o estouro aritmético sempre gera uma <xref:System.OverflowException> e a divisão por zero sempre gera uma <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="1fad6-202">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="1fad6-203">Erros de arredondamento</span><span class="sxs-lookup"><span data-stu-id="1fad6-203">Round-off errors</span></span>

<span data-ttu-id="1fad6-204">Devido a limitações gerais da representação de ponto flutuante de números reais e aritméticas de ponto flutuante, erros de arredondamento podem ocorrer em cálculos com tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="1fad6-204">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="1fad6-205">Ou seja, o resultado produzido de uma expressão pode diferir do resultado matemático esperado.</span><span class="sxs-lookup"><span data-stu-id="1fad6-205">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="1fad6-206">O seguinte exemplo demonstra vários casos desse tipo:</span><span class="sxs-lookup"><span data-stu-id="1fad6-206">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](snippets/shared/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="1fad6-207">Para obter mais informações, consulte comentários nas páginas de referência [System. Double](/dotnet/api/system.double#remarks), [System. single](/dotnet/api/system.single#remarks)ou [System. decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="1fad6-207">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="1fad6-208">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="1fad6-208">Operator overloadability</span></span>

<span data-ttu-id="1fad6-209">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) os operadores aritméticos unários ( `++` , `--` , `+` , e `-` ) e binary ( `*` , `/` ,, `%` `+` e `-` ).</span><span class="sxs-lookup"><span data-stu-id="1fad6-209">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="1fad6-210">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="1fad6-210">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="1fad6-211">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="1fad6-211">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1fad6-212">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1fad6-212">C# language specification</span></span>

<span data-ttu-id="1fad6-213">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="1fad6-213">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="1fad6-214">Operadores de incremento e decremento pós-fixados</span><span class="sxs-lookup"><span data-stu-id="1fad6-214">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="1fad6-215">Operadores de incremento e decremento pré-fixados</span><span class="sxs-lookup"><span data-stu-id="1fad6-215">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="1fad6-216">Operador de adição de unário</span><span class="sxs-lookup"><span data-stu-id="1fad6-216">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="1fad6-217">Operador de subtração de unário</span><span class="sxs-lookup"><span data-stu-id="1fad6-217">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="1fad6-218">Operador de multiplicação</span><span class="sxs-lookup"><span data-stu-id="1fad6-218">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="1fad6-219">Operador de divisão</span><span class="sxs-lookup"><span data-stu-id="1fad6-219">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="1fad6-220">Operador de resto</span><span class="sxs-lookup"><span data-stu-id="1fad6-220">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="1fad6-221">Operador de adição</span><span class="sxs-lookup"><span data-stu-id="1fad6-221">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="1fad6-222">Operador de subtração</span><span class="sxs-lookup"><span data-stu-id="1fad6-222">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="1fad6-223">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="1fad6-223">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="1fad6-224">Os operadores verificados e não verificados</span><span class="sxs-lookup"><span data-stu-id="1fad6-224">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="1fad6-225">Promoções numéricas</span><span class="sxs-lookup"><span data-stu-id="1fad6-225">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="1fad6-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fad6-226">See also</span></span>

- [<span data-ttu-id="1fad6-227">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1fad6-227">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1fad6-228">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="1fad6-228">C# operators and expressions</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="1fad6-229">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="1fad6-229">Numerics in .NET</span></span>](../../../standard/numerics.md)

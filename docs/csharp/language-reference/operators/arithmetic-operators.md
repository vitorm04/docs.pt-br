---
title: Operadores aritméticos – referência do C#
description: Saiba mais sobre os operadores do C# que executam operações de multiplicação, divisão, resto, adição e subtração com tipos numéricos.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
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
ms.openlocfilehash: 8701991542f1e950914d5b4275ae8dcd68ad83a1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345360"
---
# <a name="arithmetic-operators-c-reference"></a><span data-ttu-id="4e185-103">Operadores aritméticos (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="4e185-103">Arithmetic operators (C# reference)</span></span>

<span data-ttu-id="4e185-104">Os operadores a seguir executam operações aritméticas com operandos de tipos numéricos:</span><span class="sxs-lookup"><span data-stu-id="4e185-104">The following operators perform arithmetic operations with operands of numeric types:</span></span>

- <span data-ttu-id="4e185-105">Operadores unários [`++` (incremento)](#increment-operator-), [`--` (decremento)](#decrement-operator---), [`+` (adição)](#unary-plus-and-minus-operators) e [`-` (subtração)](#unary-plus-and-minus-operators)</span><span class="sxs-lookup"><span data-stu-id="4e185-105">Unary [`++` (increment)](#increment-operator-), [`--` (decrement)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators), and [`-` (minus)](#unary-plus-and-minus-operators) operators</span></span>
- <span data-ttu-id="4e185-106">Operadores binários [`*` (multiplicação)](#multiplication-operator-), [`/` (divisão)](#division-operator-), [`%` (resto)](#remainder-operator-), [`+` (adição)](#addition-operator-) e [`-` (subtração)](#subtraction-operator--)</span><span class="sxs-lookup"><span data-stu-id="4e185-106">Binary [`*` (multiplication)](#multiplication-operator-), [`/` (division)](#division-operator-), [`%` (remainder)](#remainder-operator-), [`+` (addition)](#addition-operator-), and [`-` (subtraction)](#subtraction-operator--) operators</span></span>

<span data-ttu-id="4e185-107">Esses operadores têm suporte de todos os tipos numéricos [integral](../builtin-types/integral-numeric-types.md) e [de ponto flutuante](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="4e185-107">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

## <a name="increment-operator-"></a><span data-ttu-id="4e185-108">Operador de incremento ++</span><span class="sxs-lookup"><span data-stu-id="4e185-108">Increment operator ++</span></span>

<span data-ttu-id="4e185-109">O operador de incremento unário `++` incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="4e185-109">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="4e185-110">O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-110">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4e185-111">Há duas formas de suporte para o operador de incremento: o operador de incremento pós-fixado, `x++`, e o operador de incremento pré-fixado, `++x`.</span><span class="sxs-lookup"><span data-stu-id="4e185-111">The increment operator is supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

### <a name="postfix-increment-operator"></a><span data-ttu-id="4e185-112">Operador de incremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="4e185-112">Postfix increment operator</span></span>

<span data-ttu-id="4e185-113">O resultado de `x++` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e185-113">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a><span data-ttu-id="4e185-114">Operador de incremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="4e185-114">Prefix increment operator</span></span>

<span data-ttu-id="4e185-115">O resultado de `++x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e185-115">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a><span data-ttu-id="4e185-116">Operador de decremento --</span><span class="sxs-lookup"><span data-stu-id="4e185-116">Decrement operator --</span></span>

<span data-ttu-id="4e185-117">O operador de decremento unário `--` decrementa o operando em 1.</span><span class="sxs-lookup"><span data-stu-id="4e185-117">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="4e185-118">O operando precisa ser uma variável, um acesso de [propriedade](../../programming-guide/classes-and-structs/properties.md) ou um acesso de [indexador](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-118">The operand must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../programming-guide/indexers/index.md) access.</span></span>

<span data-ttu-id="4e185-119">Há duas formas de suporte para o operador de decremento: o operador de decremento pós-fixado, `x--`, e o operador de decremento pré-fixado, `--x`.</span><span class="sxs-lookup"><span data-stu-id="4e185-119">The decrement operator is supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

### <a name="postfix-decrement-operator"></a><span data-ttu-id="4e185-120">Operador de decremento pós-fixado</span><span class="sxs-lookup"><span data-stu-id="4e185-120">Postfix decrement operator</span></span>

<span data-ttu-id="4e185-121">O resultado de `x--` é o valor de `x` *antes* da operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e185-121">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a><span data-ttu-id="4e185-122">Operador de decremento de prefixo</span><span class="sxs-lookup"><span data-stu-id="4e185-122">Prefix decrement operator</span></span>

<span data-ttu-id="4e185-123">O resultado de `--x` é o valor de `x` *após* a operação, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4e185-123">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a><span data-ttu-id="4e185-124">Operadores unários de adição e subtração</span><span class="sxs-lookup"><span data-stu-id="4e185-124">Unary plus and minus operators</span></span>

<span data-ttu-id="4e185-125">O operador unário `+` retorna o valor do operando.</span><span class="sxs-lookup"><span data-stu-id="4e185-125">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="4e185-126">O operador unário `-` calcula a negação numérica do operando.</span><span class="sxs-lookup"><span data-stu-id="4e185-126">The unary `-` operator computes the numeric negation of its operand.</span></span>

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

<span data-ttu-id="4e185-127">O tipo [ULONG](../builtin-types/integral-numeric-types.md) não dá suporte ao operador de `-` unário.</span><span class="sxs-lookup"><span data-stu-id="4e185-127">The [ulong](../builtin-types/integral-numeric-types.md) type doesn't support the unary `-` operator.</span></span>

## <a name="multiplication-operator-"></a><span data-ttu-id="4e185-128">Operador de multiplicação \*</span><span class="sxs-lookup"><span data-stu-id="4e185-128">Multiplication operator \*</span></span>

<span data-ttu-id="4e185-129">O operador de multiplicação `*` calcula o produto dos operandos:</span><span class="sxs-lookup"><span data-stu-id="4e185-129">The multiplication operator `*` computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

<span data-ttu-id="4e185-130">O operador unário `*` é o [operador de indireção de ponteiro](pointer-related-operators.md#pointer-indirection-operator-).</span><span class="sxs-lookup"><span data-stu-id="4e185-130">The unary `*` operator is the [pointer indirection operator](pointer-related-operators.md#pointer-indirection-operator-).</span></span>

## <a name="division-operator-"></a><span data-ttu-id="4e185-131">Operador de divisão /</span><span class="sxs-lookup"><span data-stu-id="4e185-131">Division operator /</span></span>

<span data-ttu-id="4e185-132">O operador de divisão `/` divide o operando à esquerda pelo operando à direita.</span><span class="sxs-lookup"><span data-stu-id="4e185-132">The division operator `/` divides its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-division"></a><span data-ttu-id="4e185-133">Divisão de inteiros</span><span class="sxs-lookup"><span data-stu-id="4e185-133">Integer division</span></span>

<span data-ttu-id="4e185-134">Para os operandos de tipos inteiros, o resultado do operador `/` é de um tipo inteiro e igual ao quociente dos dois operandos arredondados para zero:</span><span class="sxs-lookup"><span data-stu-id="4e185-134">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

<span data-ttu-id="4e185-135">Para obter o quociente dos dois operandos como um número de ponto flutuante, use o tipo `float`, `double` ou `decimal`:</span><span class="sxs-lookup"><span data-stu-id="4e185-135">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a><span data-ttu-id="4e185-136">Divisão de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="4e185-136">Floating-point division</span></span>

<span data-ttu-id="4e185-137">Para os tipos `float`, `double` e `decimal`, o resultado do operador `/` é o quociente dos dois operandos:</span><span class="sxs-lookup"><span data-stu-id="4e185-137">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

<span data-ttu-id="4e185-138">Se um dos operandos é `decimal`, outro operando não pode ser `float` nem `double`, porque nem `float` ou `double` é implicitamente conversível para `decimal`.</span><span class="sxs-lookup"><span data-stu-id="4e185-138">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="4e185-139">Você deve converter explicitamente o operando `float` ou `double` para o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="4e185-139">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="4e185-140">Para obter mais informações sobre conversões entre tipos numéricos, consulte [conversões numéricas internas](../builtin-types/numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-140">For more information about conversions between numeric types, see [Built-in numeric conversions](../builtin-types/numeric-conversions.md).</span></span>

## <a name="remainder-operator-"></a><span data-ttu-id="4e185-141">Operador de resto %</span><span class="sxs-lookup"><span data-stu-id="4e185-141">Remainder operator %</span></span>

<span data-ttu-id="4e185-142">O operador de resto `%` calcula o resto após dividir o operando à esquerda pelo à direita.</span><span class="sxs-lookup"><span data-stu-id="4e185-142">The remainder operator `%` computes the remainder after dividing its left-hand operand by its right-hand operand.</span></span>

### <a name="integer-remainder"></a><span data-ttu-id="4e185-143">Resto inteiro</span><span class="sxs-lookup"><span data-stu-id="4e185-143">Integer remainder</span></span>

<span data-ttu-id="4e185-144">Para os operandos de tipos inteiros, o resultado de `a % b` é o valor produzido por `a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="4e185-144">For the operands of integer types, the result of `a % b` is the value produced by `a - (a / b) * b`.</span></span> <span data-ttu-id="4e185-145">O sinal do resto diferente de zero é o mesmo que o do operando à esquerda, conforme mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="4e185-145">The sign of the non-zero remainder is the same as that of the left-hand operand, as the following example shows:</span></span>

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<span data-ttu-id="4e185-146">Use o método <xref:System.Math.DivRem%2A?displayProperty=nameWithType> para calcular a divisão de inteiros e os resultados do resto.</span><span class="sxs-lookup"><span data-stu-id="4e185-146">Use the <xref:System.Math.DivRem%2A?displayProperty=nameWithType> method to compute both integer division and remainder results.</span></span>

### <a name="floating-point-remainder"></a><span data-ttu-id="4e185-147">Resto de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="4e185-147">Floating-point remainder</span></span>

<span data-ttu-id="4e185-148">Para os operandos `float` e `double`, o resultado de `x % y` para o `x` e o `y` finitos é o valor `z` tal que</span><span class="sxs-lookup"><span data-stu-id="4e185-148">For the `float` and `double` operands, the result of `x % y` for the finite `x` and `y` is the value `z` such that</span></span>

- <span data-ttu-id="4e185-149">O sinal de `z`, se diferente de zero, é o mesmo que o sinal de `x`.</span><span class="sxs-lookup"><span data-stu-id="4e185-149">The sign of `z`, if non-zero, is the same as the sign of `x`.</span></span>
- <span data-ttu-id="4e185-150">O valor absoluto de `z` é o valor produzido por `|x| - n * |y|`, em que `n` é o maior inteiro possível que é inferior ou igual a `|x| / |y|`, e `|x|` e `|y|` são os valores absolutos de `x` e `y`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4e185-150">The absolute value of `z` is the value produced by `|x| - n * |y|` where `n` is the largest possible integer that is less than or equal to `|x| / |y|` and `|x|` and `|y|` are the absolute values of `x` and `y`, respectively.</span></span>

> [!NOTE]
> <span data-ttu-id="4e185-151">Esse método de computação do resto é análogo ao usado para operandos inteiros, mas diferente da especificação IEEE 754.</span><span class="sxs-lookup"><span data-stu-id="4e185-151">This method of computing the remainder is analogous to that used for integer operands, but different from the IEEE 754 specification.</span></span> <span data-ttu-id="4e185-152">Se você precisar da operação restante que está em conformidade com a especificação IEEE 754, use o método <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e185-152">If you need the remainder operation that complies with the IEEE 754 specification, use the <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4e185-153">Para saber mais sobre o comportamento do operador `%` com operandos não finitos, confira a seção [Operador de restante](~/_csharplang/spec/expressions.md#remainder-operator) da [especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-153">For information about the behavior of the `%` operator with non-finite operands, see the [Remainder operator](~/_csharplang/spec/expressions.md#remainder-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="4e185-154">Para os operandos `decimal`, o operador de resto `%` é equivalente ao [operador de resto](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) do tipo <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e185-154">For the `decimal` operands, the remainder operator `%` is equivalent to the [remainder operator](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) of the <xref:System.Decimal?displayProperty=nameWithType> type.</span></span>

<span data-ttu-id="4e185-155">O seguinte exemplo demonstra o comportamento do operador de resto com os operandos de ponto flutuante:</span><span class="sxs-lookup"><span data-stu-id="4e185-155">The following example demonstrates the behavior of the remainder operator with floating-point operands:</span></span>

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a><span data-ttu-id="4e185-156">Operador de adição +</span><span class="sxs-lookup"><span data-stu-id="4e185-156">Addition operator +</span></span>

<span data-ttu-id="4e185-157">O operador de adição `+` calcula a soma dos operandos:</span><span class="sxs-lookup"><span data-stu-id="4e185-157">The addition operator `+` computes the sum of its operands:</span></span>

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

<span data-ttu-id="4e185-158">Você também pode usar o operador `+` para a combinação de delegado e concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4e185-158">You also can use the `+` operator for string concatenation and delegate combination.</span></span> <span data-ttu-id="4e185-159">Para obter mais informações, confira o artigo [Operadores `+` e `+=`](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-159">For more information, see the [`+` and `+=` operators](addition-operator.md) article.</span></span>

## <a name="subtraction-operator--"></a><span data-ttu-id="4e185-160">Operador de subtração -</span><span class="sxs-lookup"><span data-stu-id="4e185-160">Subtraction operator -</span></span>

<span data-ttu-id="4e185-161">O operador de subtração `-` subtrai o operando à direita do operando à esquerda:</span><span class="sxs-lookup"><span data-stu-id="4e185-161">The subtraction operator `-` subtracts its right-hand operand from its left-hand operand:</span></span>

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

<span data-ttu-id="4e185-162">Você também pode usar o operador `-` para a remoção de delegado.</span><span class="sxs-lookup"><span data-stu-id="4e185-162">You also can use the `-` operator for delegate removal.</span></span> <span data-ttu-id="4e185-163">Para obter mais informações, confira o artigo [Operadores `-` e `-=`](subtraction-operator.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-163">For more information, see the [`-` and `-=` operators](subtraction-operator.md) article.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="4e185-164">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="4e185-164">Compound assignment</span></span>

<span data-ttu-id="4e185-165">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="4e185-165">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="4e185-166">equivale a</span><span class="sxs-lookup"><span data-stu-id="4e185-166">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="4e185-167">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="4e185-167">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="4e185-168">O seguinte exemplo demonstra o uso da atribuição composta com operadores aritméticos:</span><span class="sxs-lookup"><span data-stu-id="4e185-168">The following example demonstrates the usage of compound assignment with arithmetic operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

<span data-ttu-id="4e185-169">Devido a [promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions), o resultado da operação `op` pode não ser implicitamente conversível no tipo `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="4e185-169">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="4e185-170">Nesse caso, se `op` for um operador predefinido e o resultado da operação for explicitamente convertido no tipo `T` de `x`, uma expressão de atribuição composta da forma `x op= y` será equivalente a `x = (T)(x op y)`, exceto que `x` será avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="4e185-170">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="4e185-171">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="4e185-171">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

<span data-ttu-id="4e185-172">Você também usa os operadores `+=` e `-=` para assinar e cancelar a assinatura de um [evento](../keywords/event.md), respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4e185-172">You also use the `+=` and `-=` operators to subscribe to and unsubscribe from an [event](../keywords/event.md), respectively.</span></span> <span data-ttu-id="4e185-173">Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="4e185-173">For more information, see [How to subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="4e185-174">Precedência e associatividade do operador</span><span class="sxs-lookup"><span data-stu-id="4e185-174">Operator precedence and associativity</span></span>

<span data-ttu-id="4e185-175">A seguinte lista ordena os operadores aritméticos da precedência mais alta para a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="4e185-175">The following list orders arithmetic operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="4e185-176">Incluir um pós-fixo a operadores de incremento `x++` e decremento `x--`</span><span class="sxs-lookup"><span data-stu-id="4e185-176">Postfix increment `x++` and decrement `x--` operators</span></span>
- <span data-ttu-id="4e185-177">Incluir um prefixo a operadores de incremento `++x` e de decremento `--x` e operadores unários `+` e `-`</span><span class="sxs-lookup"><span data-stu-id="4e185-177">Prefix increment `++x` and decrement `--x` and unary `+` and `-` operators</span></span>
- <span data-ttu-id="4e185-178">Operadores de multiplicação `*`, `/` e `%`</span><span class="sxs-lookup"><span data-stu-id="4e185-178">Multiplicative `*`, `/`, and `%` operators</span></span>
- <span data-ttu-id="4e185-179">Operadores de adição `+` e `-`</span><span class="sxs-lookup"><span data-stu-id="4e185-179">Additive `+` and `-` operators</span></span>

<span data-ttu-id="4e185-180">Operadores aritméticos binários são associativos à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4e185-180">Binary arithmetic operators are left-associative.</span></span> <span data-ttu-id="4e185-181">Ou seja, os operadores com o mesmo nível de precedência são avaliados da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="4e185-181">That is, operators with the same precedence level are evaluated from left to right.</span></span>

<span data-ttu-id="4e185-182">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência e pela capacidade de associação do operador.</span><span class="sxs-lookup"><span data-stu-id="4e185-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence and associativity.</span></span>

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

<span data-ttu-id="4e185-183">Para obter a lista completa C# de operadores ordenados por nível de precedência, consulte a seção [precedência de operador](index.md#operator-precedence) do artigo [ C# operadores](index.md) .</span><span class="sxs-lookup"><span data-stu-id="4e185-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="arithmetic-overflow-and-division-by-zero"></a><span data-ttu-id="4e185-184">Estouro aritmético e divisão por zero</span><span class="sxs-lookup"><span data-stu-id="4e185-184">Arithmetic overflow and division by zero</span></span>

<span data-ttu-id="4e185-185">Quando o resultado de uma operação aritmética está fora do intervalo de valores finitos possíveis do tipo numérico envolvido, o comportamento de um operador aritmético depende do tipo dos operandos.</span><span class="sxs-lookup"><span data-stu-id="4e185-185">When the result of an arithmetic operation is outside the range of possible finite values of the involved numeric type, the behavior of an arithmetic operator depends on the type of its operands.</span></span>

### <a name="integer-arithmetic-overflow"></a><span data-ttu-id="4e185-186">Estouro aritmético de inteiros</span><span class="sxs-lookup"><span data-stu-id="4e185-186">Integer arithmetic overflow</span></span>

<span data-ttu-id="4e185-187">A divisão de inteiro por zero sempre lança um <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="4e185-187">Integer division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

<span data-ttu-id="4e185-188">No caso de um estouro aritmético de inteiros, um contexto de verificação de estouro, que pode ser [verificado ou não verificado](../keywords/checked-and-unchecked.md), controla o comportamento resultante:</span><span class="sxs-lookup"><span data-stu-id="4e185-188">In case of integer arithmetic overflow, an overflow checking context, which can be [checked or unchecked](../keywords/checked-and-unchecked.md), controls the resulting behavior:</span></span>

- <span data-ttu-id="4e185-189">Em um contexto verificado, se o estouro acontece em uma expressão de constante, ocorre um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="4e185-189">In a checked context, if overflow happens in a constant expression, a compile-time error occurs.</span></span> <span data-ttu-id="4e185-190">Caso contrário, quando a operação é executada em tempo de execução, uma <xref:System.OverflowException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="4e185-190">Otherwise, when the operation is performed at run time, an <xref:System.OverflowException> is thrown.</span></span>
- <span data-ttu-id="4e185-191">Em um contexto não verificado, o resultado é truncado pelo descarte dos bits de ordem superior que não se ajustam ao tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="4e185-191">In an unchecked context, the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>

<span data-ttu-id="4e185-192">Juntamente com as instruções [verificadas e não verificadas](../keywords/checked-and-unchecked.md), você pode usar os operadores `checked` e `unchecked` para controlar o contexto de verificação de estouro, no qual uma expressão é avaliada:</span><span class="sxs-lookup"><span data-stu-id="4e185-192">Along with the [checked and unchecked](../keywords/checked-and-unchecked.md) statements, you can use the `checked` and `unchecked` operators to control the overflow checking context, in which an expression is evaluated:</span></span>

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

<span data-ttu-id="4e185-193">Por padrão, as operações aritméticas ocorrem em um contexto *não verificado*.</span><span class="sxs-lookup"><span data-stu-id="4e185-193">By default, arithmetic operations occur in an *unchecked* context.</span></span>

### <a name="floating-point-arithmetic-overflow"></a><span data-ttu-id="4e185-194">Estouro aritmético de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="4e185-194">Floating-point arithmetic overflow</span></span>

<span data-ttu-id="4e185-195">As operações aritméticas com os tipos `float` e `double` nunca geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4e185-195">Arithmetic operations with the `float` and `double` types never throw an exception.</span></span> <span data-ttu-id="4e185-196">O resultado de operações aritméticas com esses tipos pode ser um dos valores especiais que representam o infinito e um valor não é um número:</span><span class="sxs-lookup"><span data-stu-id="4e185-196">The result of arithmetic operations with those types can be one of special values that represent infinity and not-a-number:</span></span>

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

<span data-ttu-id="4e185-197">Para os operandos do tipo `decimal`, o estouro aritmético sempre gera uma <xref:System.OverflowException> e a divisão por zero sempre gera uma <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="4e185-197">For the operands of the `decimal` type, arithmetic overflow always throws an <xref:System.OverflowException> and division by zero always throws a <xref:System.DivideByZeroException>.</span></span>

## <a name="round-off-errors"></a><span data-ttu-id="4e185-198">Erros de arredondamento</span><span class="sxs-lookup"><span data-stu-id="4e185-198">Round-off errors</span></span>

<span data-ttu-id="4e185-199">Devido a limitações gerais da representação de ponto flutuante de números reais e aritméticas de ponto flutuante, erros de arredondamento podem ocorrer em cálculos com tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="4e185-199">Because of general limitations of the floating-point representation of real numbers and floating-point arithmetic, round-off errors might occur in calculations with floating-point types.</span></span> <span data-ttu-id="4e185-200">Ou seja, o resultado produzido de uma expressão pode diferir do resultado matemático esperado.</span><span class="sxs-lookup"><span data-stu-id="4e185-200">That is, the produced result of an expression might differ from the expected mathematical result.</span></span> <span data-ttu-id="4e185-201">O seguinte exemplo demonstra vários casos desse tipo:</span><span class="sxs-lookup"><span data-stu-id="4e185-201">The following example demonstrates several such cases:</span></span>

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

<span data-ttu-id="4e185-202">Para obter mais informações, consulte comentários nas páginas de referência [System. Double](/dotnet/api/system.double#remarks), [System. single](/dotnet/api/system.single#remarks)ou [System. decimal](/dotnet/api/system.decimal#remarks) .</span><span class="sxs-lookup"><span data-stu-id="4e185-202">For more information, see remarks at the [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), or [System.Decimal](/dotnet/api/system.decimal#remarks) reference pages.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4e185-203">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="4e185-203">Operator overloadability</span></span>

<span data-ttu-id="4e185-204">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) os operadores aritméticos unários (`++`, `--`, `+` e `-`) e binários (`*`, `/`, `%`, `+` e `-`).</span><span class="sxs-lookup"><span data-stu-id="4e185-204">A user-defined type can [overload](operator-overloading.md) the unary (`++`, `--`, `+`, and `-`) and binary (`*`, `/`, `%`, `+`, and `-`) arithmetic operators.</span></span> <span data-ttu-id="4e185-205">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="4e185-205">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="4e185-206">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="4e185-206">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4e185-207">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="4e185-207">C# language specification</span></span>

<span data-ttu-id="4e185-208">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="4e185-208">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="4e185-209">Operadores de incremento e decremento pós-fixados</span><span class="sxs-lookup"><span data-stu-id="4e185-209">Postfix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [<span data-ttu-id="4e185-210">Operadores de incremento e decremento pré-fixados</span><span class="sxs-lookup"><span data-stu-id="4e185-210">Prefix increment and decrement operators</span></span>](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [<span data-ttu-id="4e185-211">Operador unário de adição</span><span class="sxs-lookup"><span data-stu-id="4e185-211">Unary plus operator</span></span>](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [<span data-ttu-id="4e185-212">Operador unário de subtração</span><span class="sxs-lookup"><span data-stu-id="4e185-212">Unary minus operator</span></span>](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [<span data-ttu-id="4e185-213">Operador de multiplicação</span><span class="sxs-lookup"><span data-stu-id="4e185-213">Multiplication operator</span></span>](~/_csharplang/spec/expressions.md#multiplication-operator)
- [<span data-ttu-id="4e185-214">Operador de divisão</span><span class="sxs-lookup"><span data-stu-id="4e185-214">Division operator</span></span>](~/_csharplang/spec/expressions.md#division-operator)
- [<span data-ttu-id="4e185-215">Operador de resto</span><span class="sxs-lookup"><span data-stu-id="4e185-215">Remainder operator</span></span>](~/_csharplang/spec/expressions.md#remainder-operator)
- [<span data-ttu-id="4e185-216">Operador de adição</span><span class="sxs-lookup"><span data-stu-id="4e185-216">Addition operator</span></span>](~/_csharplang/spec/expressions.md#addition-operator)
- [<span data-ttu-id="4e185-217">Operador de subtração</span><span class="sxs-lookup"><span data-stu-id="4e185-217">Subtraction operator</span></span>](~/_csharplang/spec/expressions.md#subtraction-operator)
- [<span data-ttu-id="4e185-218">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="4e185-218">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="4e185-219">Os operadores verificados e não verificados</span><span class="sxs-lookup"><span data-stu-id="4e185-219">The checked and unchecked operators</span></span>](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [<span data-ttu-id="4e185-220">Promoções numéricas</span><span class="sxs-lookup"><span data-stu-id="4e185-220">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="4e185-221">Veja também</span><span class="sxs-lookup"><span data-stu-id="4e185-221">See also</span></span>

- [<span data-ttu-id="4e185-222">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4e185-222">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4e185-223">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4e185-223">C# operators</span></span>](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [<span data-ttu-id="4e185-224">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="4e185-224">Numerics in .NET</span></span>](../../../standard/numerics.md)

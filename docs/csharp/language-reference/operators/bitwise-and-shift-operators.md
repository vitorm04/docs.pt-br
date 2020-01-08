---
title: Operadores bit a bit e de deslocamento – referência do C#
description: Saiba mais sobre operadores C# que executam operações de deslocamento ou lógicas bit a bit com operandos de tipos integrais.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: f14b92aba270eab845ca50e5407da3502b5c4087
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345335"
---
# <a name="bitwise-and-shift-operators-c-reference"></a><span data-ttu-id="536ea-103">Operadores bit a bit e de deslocamento (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="536ea-103">Bitwise and shift operators (C# reference)</span></span>

<span data-ttu-id="536ea-104">Os operadores a seguir executam operações de Shift ou or de bit com operandos dos [tipos numéricos inteiros](../builtin-types/integral-numeric-types.md) ou do tipo [Char](../builtin-types/char.md) :</span><span class="sxs-lookup"><span data-stu-id="536ea-104">The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:</span></span>

- <span data-ttu-id="536ea-105">Operador unário [`~` (complemento bit a bit)](#bitwise-complement-operator-)</span><span class="sxs-lookup"><span data-stu-id="536ea-105">Unary [`~` (bitwise complement)](#bitwise-complement-operator-) operator</span></span>
- <span data-ttu-id="536ea-106">Operadores binários [`<<` (deslocamento à esquerda)](#left-shift-operator-) e [`>>` (deslocamento à direita)](#right-shift-operator-)</span><span class="sxs-lookup"><span data-stu-id="536ea-106">Binary [`<<` (left shift)](#left-shift-operator-) and [`>>` (right shift)](#right-shift-operator-) shift operators</span></span>
- <span data-ttu-id="536ea-107">Operadores binários [`&` (AND lógico)](#logical-and-operator-), [`|` (OR lógico)](#logical-or-operator-) e [`^` (OR exclusivo lógico)](#logical-exclusive-or-operator-)</span><span class="sxs-lookup"><span data-stu-id="536ea-107">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators</span></span>

<span data-ttu-id="536ea-108">Esses operadores são definidos para os tipos `int`, `uint`, `long` e `ulong`.</span><span class="sxs-lookup"><span data-stu-id="536ea-108">Those operators are defined for the `int`, `uint`, `long`, and `ulong` types.</span></span> <span data-ttu-id="536ea-109">Quando ambos os operandos são de outros tipos integrais (`sbyte`, `byte`, `short`, `ushort` ou `char`), seus valores são convertidos no tipo `int`, que também é o tipo de resultado de uma operação.</span><span class="sxs-lookup"><span data-stu-id="536ea-109">When both operands are of other integral types (`sbyte`, `byte`, `short`, `ushort`, or `char`), their values are converted to the `int` type, which is also the result type of an operation.</span></span> <span data-ttu-id="536ea-110">Quando os operandos são de tipos integrais diferentes, seus valores são convertidos no tipo integral mais próximo que o contém.</span><span class="sxs-lookup"><span data-stu-id="536ea-110">When operands are of different integral types, their values are converted to the closest containing integral type.</span></span> <span data-ttu-id="536ea-111">Para saber mais, confira a seção [Promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="536ea-111">For more information, see the [Numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="536ea-112">Os operadores `&`, `|`e `^` também são definidos para operandos do tipo `bool`.</span><span class="sxs-lookup"><span data-stu-id="536ea-112">The `&`, `|`, and `^` operators are also defined for operands of the `bool` type.</span></span> <span data-ttu-id="536ea-113">Para obter mais informações, veja [Operadores lógicos boolianos](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="536ea-113">For more information, see [Boolean logical operators](boolean-logical-operators.md).</span></span>

<span data-ttu-id="536ea-114">As operações de deslocamento e bit a bit nunca causam estouro e produzem os mesmos resultados nos contextos [marcados e desmarcados](../keywords/checked-and-unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="536ea-114">Bitwise and shift operations never cause overflow and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="bitwise-complement-operator-"></a><span data-ttu-id="536ea-115">Operador de complemento bit a bit ~</span><span class="sxs-lookup"><span data-stu-id="536ea-115">Bitwise complement operator ~</span></span>

<span data-ttu-id="536ea-116">O operador `~` produz um complemento bit a bit de seu operando invertendo cada bit:</span><span class="sxs-lookup"><span data-stu-id="536ea-116">The `~` operator produces a bitwise complement of its operand by reversing each bit:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

<span data-ttu-id="536ea-117">Você também pode usar o símbolo `~` para declarar finalizadores.</span><span class="sxs-lookup"><span data-stu-id="536ea-117">You can also use the `~` symbol to declare finalizers.</span></span> <span data-ttu-id="536ea-118">Para mais informações, consulte [Finalizadores](../../programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="536ea-118">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

## <a name="left-shift-operator-"></a><span data-ttu-id="536ea-119">Operador de deslocamento à esquerda \<\<</span><span class="sxs-lookup"><span data-stu-id="536ea-119">Left-shift operator \<\<</span></span>

<span data-ttu-id="536ea-120">O operador `<<` desloca para esquerda o operando à esquerda pelo número de bits definido pelo seu operando à direita.</span><span class="sxs-lookup"><span data-stu-id="536ea-120">The `<<` operator shifts its left-hand operand left by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="536ea-121">A operação de deslocamento à esquerda descarta os bits de ordem superior que estão fora do intervalo do tipo de resultado e define as posições de bits vazios de ordem inferior como zero, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="536ea-121">The left-shift operation discards the high-order bits that are outside the range of the result type and sets the low-order empty bit positions to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

<span data-ttu-id="536ea-122">Como os operadores de deslocamento são definidos apenas para os tipos `int`, `uint`, `long` e `ulong`, o resultado de uma operação sempre contém pelo menos 32 bits.</span><span class="sxs-lookup"><span data-stu-id="536ea-122">Because the shift operators are defined only for the `int`, `uint`, `long`, and `ulong` types, the result of an operation always contains at least 32 bits.</span></span> <span data-ttu-id="536ea-123">Se o operando à esquerda for de outro tipo integral (`sbyte`, `byte`, `short`, `ushort` ou `char`), seu valor será convertido no tipo `int`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="536ea-123">If the left-hand operand is of another integral type (`sbyte`, `byte`, `short`, `ushort`, or `char`), its value is converted to the `int` type, as the following example shows:</span></span>

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

<span data-ttu-id="536ea-124">Para saber mais sobre como o operando à direita do operador `<<` define a contagem de deslocamento, veja a seção [Contagem de deslocamento dos operadores de deslocamento](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="536ea-124">For information about how the right-hand operand of the `<<` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="right-shift-operator-"></a><span data-ttu-id="536ea-125">Operador de deslocamento à direita >></span><span class="sxs-lookup"><span data-stu-id="536ea-125">Right-shift operator >></span></span>

<span data-ttu-id="536ea-126">O operador `>>` desloca para direita o operando à esquerda pelo número de bits definido pelo seu operando à direita.</span><span class="sxs-lookup"><span data-stu-id="536ea-126">The `>>` operator shifts its left-hand operand right by the number of bits defined by its right-hand operand.</span></span>

<span data-ttu-id="536ea-127">A operação de deslocamento à direita descarta os bits de ordem inferior, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="536ea-127">The right-shift operation discards the low-order bits, as the following example shows:</span></span>

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

<span data-ttu-id="536ea-128">As posições vazias de bit de ordem superior são definidas com base no tipo do operando à esquerda da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="536ea-128">The high-order empty bit positions are set based on the type of the left-hand operand as follows:</span></span>

- <span data-ttu-id="536ea-129">Se o operando esquerdo for do tipo `int` ou `long`, o operador right-shift executará um deslocamento *aritmético* : o valor do bit mais significativo (o bit de sinal) do operando esquerdo será propagado para as posições de bits vazias de ordem superior.</span><span class="sxs-lookup"><span data-stu-id="536ea-129">If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="536ea-130">Ou seja, as posições vazias de bit de ordem superior são definidas como zero se o operando à esquerda for positivo e definidas como um se ele for negativo.</span><span class="sxs-lookup"><span data-stu-id="536ea-130">That is, the high-order empty bit positions are set to zero if the left-hand operand is non-negative and set to one if it's negative.</span></span>

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- <span data-ttu-id="536ea-131">Se o operando esquerdo for do tipo `uint` ou `ulong`, o operador right-shift executará um deslocamento *lógico* : as posições de bit vazio de ordem superior são sempre definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="536ea-131">If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.</span></span>

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

<span data-ttu-id="536ea-132">Para saber mais sobre como o operando à direita do operador `>>` define a contagem de deslocamento, veja a seção [Contagem de deslocamento dos operadores de deslocamento](#shift-count-of-the-shift-operators).</span><span class="sxs-lookup"><span data-stu-id="536ea-132">For information about how the right-hand operand of the `>>` operator defines the shift count, see the [Shift count of the shift operators](#shift-count-of-the-shift-operators) section.</span></span>

## <a name="logical-and-operator-"></a> <span data-ttu-id="536ea-133">Operador AND lógico &amp;</span><span class="sxs-lookup"><span data-stu-id="536ea-133">Logical AND operator &amp;</span></span>

<span data-ttu-id="536ea-134">O operador `&` computa o AND lógico bit a bit de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="536ea-134">The `&` operator computes the bitwise logical AND of its operands:</span></span>

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

<span data-ttu-id="536ea-135">Para os operandos de `bool`, o operador `&` computa a [lógica e](boolean-logical-operators.md#logical-and-operator-) seus operandos.</span><span class="sxs-lookup"><span data-stu-id="536ea-135">For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="536ea-136">O operador `&` unário é o [operador address-of](pointer-related-operators.md#address-of-operator-).</span><span class="sxs-lookup"><span data-stu-id="536ea-136">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="536ea-137">Operador OR exclusivo lógico ^</span><span class="sxs-lookup"><span data-stu-id="536ea-137">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="536ea-138">O operador `^` computa o OR exclusivo lógico bit a bit, também conhecido como o XOR lógico bit a bit, de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="536ea-138">The `^` operator computes the bitwise logical exclusive OR, also known as the bitwise logical XOR, of its operands:</span></span>

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

<span data-ttu-id="536ea-139">Para operandos `bool`, o operador `^` computa o [exclusivo lógico ou](boolean-logical-operators.md#logical-exclusive-or-operator-) de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="536ea-139">For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="536ea-140">Operador OR lógico |</span><span class="sxs-lookup"><span data-stu-id="536ea-140">Logical OR operator |</span></span>

<span data-ttu-id="536ea-141">O operador `|` computa o OR lógico bit a bit de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="536ea-141">The `|` operator computes the bitwise logical OR of its operands:</span></span>

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

<span data-ttu-id="536ea-142">Para operandos `bool`, o operador `|` computa a [lógica ou](boolean-logical-operators.md#logical-or-operator-) seus operandos.</span><span class="sxs-lookup"><span data-stu-id="536ea-142">For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="536ea-143">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="536ea-143">Compound assignment</span></span>

<span data-ttu-id="536ea-144">Para um operador binário `op`, uma expressão de atribuição composta do formato</span><span class="sxs-lookup"><span data-stu-id="536ea-144">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="536ea-145">equivale a</span><span class="sxs-lookup"><span data-stu-id="536ea-145">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="536ea-146">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="536ea-146">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="536ea-147">O seguinte exemplo demonstra o uso da atribuição composta com operadores bit a bit e de deslocamento:</span><span class="sxs-lookup"><span data-stu-id="536ea-147">The following example demonstrates the usage of compound assignment with bitwise and shift operators:</span></span>

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

<span data-ttu-id="536ea-148">Devido a [promoções numéricas](~/_csharplang/spec/expressions.md#numeric-promotions), o resultado da operação `op` pode não ser implicitamente conversível no tipo `T` de `x`.</span><span class="sxs-lookup"><span data-stu-id="536ea-148">Because of [numeric promotions](~/_csharplang/spec/expressions.md#numeric-promotions), the result of the `op` operation might be not implicitly convertible to the type `T` of `x`.</span></span> <span data-ttu-id="536ea-149">Nesse caso, se `op` for um operador predefinido e o resultado da operação for explicitamente convertido no tipo `T` de `x`, uma expressão de atribuição composta da forma `x op= y` será equivalente a `x = (T)(x op y)`, exceto que `x` será avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="536ea-149">In such a case, if `op` is a predefined operator and the result of the operation is explicitly convertible to the type `T` of `x`, a compound assignment expression of the form `x op= y` is equivalent to `x = (T)(x op y)`, except that `x` is only evaluated once.</span></span> <span data-ttu-id="536ea-150">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="536ea-150">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a><span data-ttu-id="536ea-151">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="536ea-151">Operator precedence</span></span>

<span data-ttu-id="536ea-152">A lista a seguir ordena os operadores lógicos, começando da mais alta precedência até a mais baixa:</span><span class="sxs-lookup"><span data-stu-id="536ea-152">The following list orders bitwise and shift operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="536ea-153">Operador de complemento bit a bit `~`</span><span class="sxs-lookup"><span data-stu-id="536ea-153">Bitwise complement operator `~`</span></span>
- <span data-ttu-id="536ea-154">Operadores de deslocamento `<<` e `>>`</span><span class="sxs-lookup"><span data-stu-id="536ea-154">Shift operators `<<` and `>>`</span></span>
- <span data-ttu-id="536ea-155">Operador AND lógico `&`</span><span class="sxs-lookup"><span data-stu-id="536ea-155">Logical AND operator `&`</span></span>
- <span data-ttu-id="536ea-156">Operador OR exclusivo lógico `^`</span><span class="sxs-lookup"><span data-stu-id="536ea-156">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="536ea-157">Operador OR lógico `|`</span><span class="sxs-lookup"><span data-stu-id="536ea-157">Logical OR operator `|`</span></span>

<span data-ttu-id="536ea-158">Use parênteses, `()`, para alterar a ordem de avaliação imposta pela precedência do operador:</span><span class="sxs-lookup"><span data-stu-id="536ea-158">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

<span data-ttu-id="536ea-159">Para obter a lista completa C# de operadores ordenados por nível de precedência, consulte a seção [precedência de operador](index.md#operator-precedence) do artigo [ C# operadores](index.md) .</span><span class="sxs-lookup"><span data-stu-id="536ea-159">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="shift-count-of-the-shift-operators"></a><span data-ttu-id="536ea-160">Contagem de deslocamento dos operadores de deslocamento</span><span class="sxs-lookup"><span data-stu-id="536ea-160">Shift count of the shift operators</span></span>

<span data-ttu-id="536ea-161">Para os operadores de deslocamento `<<` e `>>`, o tipo do operando à direita deve ser `int` ou um tipo que tenha uma [conversão de numérico implícita predefinida](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) para `int`.</span><span class="sxs-lookup"><span data-stu-id="536ea-161">For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.</span></span>

<span data-ttu-id="536ea-162">Para as expressões `x << count` e `x >> count`, a contagem real de deslocamento depende do tipo de `x` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="536ea-162">For the `x << count` and `x >> count` expressions, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="536ea-163">Se o tipo de `x` for `int` ou `uint`, a contagem de deslocamento será definida pelos *cinco* bits de ordem inferior do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="536ea-163">If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand.</span></span> <span data-ttu-id="536ea-164">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x1F` (ou `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="536ea-164">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="536ea-165">Se o tipo de `x` for `long` ou `ulong`, a contagem de deslocamento será definida pelos *seis* bits de ordem inferior do operando à direita.</span><span class="sxs-lookup"><span data-stu-id="536ea-165">If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand.</span></span> <span data-ttu-id="536ea-166">Ou seja, a contagem de deslocamentos é calculada a partir de `count & 0x3F` (ou `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="536ea-166">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="536ea-167">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="536ea-167">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a><span data-ttu-id="536ea-168">Operadores lógicos de enumeração</span><span class="sxs-lookup"><span data-stu-id="536ea-168">Enumeration logical operators</span></span>

<span data-ttu-id="536ea-169">Os operadores `~`, `&`, `|`e `^` também têm suporte de qualquer tipo de [Enumeração](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="536ea-169">The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../builtin-types/enum.md) type.</span></span> <span data-ttu-id="536ea-170">Para operandos do mesmo tipo de enumeração, uma operação lógica é executada nos valores correspondentes do tipo integral subjacente.</span><span class="sxs-lookup"><span data-stu-id="536ea-170">For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type.</span></span> <span data-ttu-id="536ea-171">Por exemplo, para qualquer `x` e `y` de um tipo de enumeração `T` com um tipo subjacente `U`, a expressão `x & y` produz o mesmo resultado que a expressão `(T)((U)x & (U)y)`.</span><span class="sxs-lookup"><span data-stu-id="536ea-171">For example, for any `x` and `y` of an enumeration type `T` with an underlying type `U`, the `x & y` expression produces the same result as the `(T)((U)x & (U)y)` expression.</span></span>

<span data-ttu-id="536ea-172">Geralmente, você usa os operadores lógicos bit a bit com um tipo de enumeração definido com o atributo [sinalizadores](xref:System.FlagsAttribute).</span><span class="sxs-lookup"><span data-stu-id="536ea-172">You typically use bitwise logical operators with an enumeration type which is defined with the [Flags](xref:System.FlagsAttribute) attribute.</span></span> <span data-ttu-id="536ea-173">Para obter mais informações, veja a seção [Tipos de enumeração como sinalizadores de bit](../builtin-types/enum.md#enumeration-types-as-bit-flags) do artigo [Tipos de enumeração](../builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="536ea-173">For more information, see the [Enumeration types as bit flags](../builtin-types/enum.md#enumeration-types-as-bit-flags) section of the [Enumeration types](../builtin-types/enum.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="536ea-174">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="536ea-174">Operator overloadability</span></span>

<span data-ttu-id="536ea-175">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) os operadores `~`, `<<`, `>>`, `&`, `|` e `^`.</span><span class="sxs-lookup"><span data-stu-id="536ea-175">A user-defined type can [overload](operator-overloading.md) the `~`, `<<`, `>>`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="536ea-176">Quando um operador binário está sobrecarregado, o operador de atribuição composta correspondente também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="536ea-176">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="536ea-177">Um tipo definido pelo usuário não pode sobrecarregar explicitamente um operador de atribuição composta.</span><span class="sxs-lookup"><span data-stu-id="536ea-177">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="536ea-178">Se um tipo definido pelo usuário `T` sobrecarregar o operador `<<` ou `>>`, o tipo do operando à esquerda deverá ser `T` e o tipo do operando à direita deverá ser `int`.</span><span class="sxs-lookup"><span data-stu-id="536ea-178">If a user-defined type `T` overloads the `<<` or `>>` operator, the type of the left-hand operand must be `T` and the type of the right-hand operand must be `int`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="536ea-179">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="536ea-179">C# language specification</span></span>

<span data-ttu-id="536ea-180">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="536ea-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="536ea-181">Operador de complemento bit a bit</span><span class="sxs-lookup"><span data-stu-id="536ea-181">Bitwise complement operator</span></span>](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [<span data-ttu-id="536ea-182">Operadores shift</span><span class="sxs-lookup"><span data-stu-id="536ea-182">Shift operators</span></span>](~/_csharplang/spec/expressions.md#shift-operators)
- [<span data-ttu-id="536ea-183">Operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="536ea-183">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="536ea-184">Atribuição composta</span><span class="sxs-lookup"><span data-stu-id="536ea-184">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)
- [<span data-ttu-id="536ea-185">Promoções numéricas</span><span class="sxs-lookup"><span data-stu-id="536ea-185">Numeric promotions</span></span>](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a><span data-ttu-id="536ea-186">Veja também</span><span class="sxs-lookup"><span data-stu-id="536ea-186">See also</span></span>

- [<span data-ttu-id="536ea-187">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="536ea-187">C# reference</span></span>](../index.md)
- [<span data-ttu-id="536ea-188">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="536ea-188">C# operators</span></span>](index.md)
- [<span data-ttu-id="536ea-189">Operadores lógicos boolianos</span><span class="sxs-lookup"><span data-stu-id="536ea-189">Boolean logical operators</span></span>](boolean-logical-operators.md)

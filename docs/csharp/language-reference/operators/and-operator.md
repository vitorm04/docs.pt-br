---
title: Operador &amp; – Referência de C#
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 67d60709e1c6c76071ecfb7aac74c83dec6f372a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310038"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="dfbf8-102">Operador &amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dfbf8-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="dfbf8-103">Há suporte para o operador `&` de duas formas: um operador address-of unário ou um operador lógico binário.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="dfbf8-104">Operador address-of unário</span><span class="sxs-lookup"><span data-stu-id="dfbf8-104">Unary address-of operator</span></span>

<span data-ttu-id="dfbf8-105">O operador `&` unário retorna o endereço de seu operando.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="dfbf8-106">Para obter mais informações, veja [Como obter o endereço de uma variável](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="dfbf8-107">O operador address-of `&` requer contexto [não seguro](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="dfbf8-108">Operador AND lógico bit a bit do inteiro</span><span class="sxs-lookup"><span data-stu-id="dfbf8-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="dfbf8-109">Para os tipos de inteiro, o operador `&` computa o AND lógico bit a bit de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="dfbf8-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="dfbf8-110">O exemplo anterior usa os literais binários [introduzidos no C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) e [aprimorados no C#7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="dfbf8-111">Como as operações em tipos de inteiro geralmente são permitidas em tipos de enumeração, o operador `&` também oferece suporte a operandos [enum](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="dfbf8-112">Operador AND lógico booliano</span><span class="sxs-lookup"><span data-stu-id="dfbf8-112">Boolean logical AND operator</span></span>

<span data-ttu-id="dfbf8-113">Para operandos [bool](../keywords/bool.md), o operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="dfbf8-114">O resultado de `x & y` será `true` se ambos `x` e `y` forem `true`.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="dfbf8-115">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="dfbf8-116">O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="dfbf8-117">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="dfbf8-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="dfbf8-118">O [operador AND condicional](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` também computa o AND lógico e seus operandos, mas não avalia o segundo operando se o primeiro for avaliado como `false`.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-118">The [conditional AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the second operand if the first operand evaluates to `false`.</span></span>

<span data-ttu-id="dfbf8-119">Para operandos bool que permitem valor nulo, o comportamento do operador `&` é consistente com a lógica de três valores do SQL.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="dfbf8-120">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-120">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dfbf8-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="dfbf8-121">Operator overloadability</span></span>

<span data-ttu-id="dfbf8-122">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `&` binário.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="dfbf8-123">Quando um operador `&` binário é sobrecarregado, o [operador de atribuição AND](and-assignment-operator.md) `&=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="dfbf8-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dfbf8-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="dfbf8-124">C# language specification</span></span>

<span data-ttu-id="dfbf8-125">Para obter mais informações, veja as seções [O operador address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) e [Operadores lógicos](~/_csharplang/spec/expressions.md#logical-operators) da [Especificação de linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfbf8-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfbf8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfbf8-126">See also</span></span>

- [<span data-ttu-id="dfbf8-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dfbf8-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfbf8-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dfbf8-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfbf8-129">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="dfbf8-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="dfbf8-130">Operadores lógicos boolianos</span><span class="sxs-lookup"><span data-stu-id="dfbf8-130">Boolean logical operators</span></span>](boolean-logical-operators.md)
- [<span data-ttu-id="dfbf8-131">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="dfbf8-131">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="dfbf8-132">Operador |</span><span class="sxs-lookup"><span data-stu-id="dfbf8-132">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="dfbf8-133">Operador ^</span><span class="sxs-lookup"><span data-stu-id="dfbf8-133">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="dfbf8-134">Operador ~</span><span class="sxs-lookup"><span data-stu-id="dfbf8-134">~ operator</span></span>](bitwise-complement-operator.md)

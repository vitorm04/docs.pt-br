---
title: Operador &amp; (Referência de C#)
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510972"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="f25ee-102">Operador &amp; (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f25ee-102">&amp; Operator (C# Reference)</span></span>

<span data-ttu-id="f25ee-103">Há suporte para o operador `&` de duas formas: um operador address-of unário ou um operador lógico binário.</span><span class="sxs-lookup"><span data-stu-id="f25ee-103">The `&` operator is supported in two forms: a unary address-of operator or a binary logical operator.</span></span>

## <a name="unary-address-of-operator"></a><span data-ttu-id="f25ee-104">Operador address-of unário</span><span class="sxs-lookup"><span data-stu-id="f25ee-104">Unary address-of operator</span></span>

<span data-ttu-id="f25ee-105">O operador `&` unário retorna o endereço de seu operando.</span><span class="sxs-lookup"><span data-stu-id="f25ee-105">The unary `&` operator returns the address of its operand.</span></span> <span data-ttu-id="f25ee-106">Para obter mais informações, veja [Como obter o endereço de uma variável](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="f25ee-106">For more information, see [How to: obtain the address of a variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).</span></span>

<span data-ttu-id="f25ee-107">O operador address-of `&` requer contexto [não seguro](../keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="f25ee-107">The address-of operator `&` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="integer-logical-bitwise-and-operator"></a><span data-ttu-id="f25ee-108">Operador AND lógico bit a bit do inteiro</span><span class="sxs-lookup"><span data-stu-id="f25ee-108">Integer logical bitwise AND operator</span></span>

<span data-ttu-id="f25ee-109">Para os tipos de inteiro, o operador `&` computa o AND lógico bit a bit de seus operandos:</span><span class="sxs-lookup"><span data-stu-id="f25ee-109">For integer types, the `&` operator computes the logical bitwise AND of its operands:</span></span>

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> <span data-ttu-id="f25ee-110">O exemplo anterior usa os literais binários [introduzidos no C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) e [aprimorados no C#7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span><span class="sxs-lookup"><span data-stu-id="f25ee-110">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

<span data-ttu-id="f25ee-111">Como as operações em tipos de inteiro geralmente são permitidas em tipos de enumeração, o operador `&` também oferece suporte a operandos [enum](../keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="f25ee-111">Because operations on integer types are generally allowed on enumeration types, the `&` operator also supports [enum](../keywords/enum.md) operands.</span></span>

## <a name="boolean-logical-and-operator"></a><span data-ttu-id="f25ee-112">Operador AND lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f25ee-112">Boolean logical AND operator</span></span>

<span data-ttu-id="f25ee-113">Para operandos [bool](../keywords/bool.md), o operador `&` computa o AND lógico de seus operandos.</span><span class="sxs-lookup"><span data-stu-id="f25ee-113">For [bool](../keywords/bool.md) operands, the `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="f25ee-114">O resultado de `x & y` será `true` se ambos `x` e `y` forem `true`.</span><span class="sxs-lookup"><span data-stu-id="f25ee-114">The result of `x & y` is `true` if both `x` and `y` are `true`.</span></span> <span data-ttu-id="f25ee-115">Caso contrário, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="f25ee-115">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="f25ee-116">O operador `&` avalia os dois operandos, mesmo se o primeiro operando for avaliado como `false`, de modo que o resultado deve ser `false`, independentemente do valor do segundo operando.</span><span class="sxs-lookup"><span data-stu-id="f25ee-116">The `&` operator evaluates both operands even if the first operand evaluates to `false`, so that the result must be `false` regardless of the value of the second operand.</span></span> <span data-ttu-id="f25ee-117">O exemplo a seguir demonstra esse comportamento:</span><span class="sxs-lookup"><span data-stu-id="f25ee-117">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

<span data-ttu-id="f25ee-118">O [operador AND condicional](conditional-and-operator.md) `&&` também computa o AND lógico e seus operandos, mas avaliará o segundo operando somente se o primeiro for avaliado como `true`.</span><span class="sxs-lookup"><span data-stu-id="f25ee-118">The [conditional AND operator](conditional-and-operator.md) `&&` also computes the logical AND of its operands, but evaluates the second operand only if the first operand evaluates to `true`.</span></span>

<span data-ttu-id="f25ee-119">Para operandos bool que permitem valor nulo, o comportamento do operador `&` é consistente com a lógica de três valores do SQL.</span><span class="sxs-lookup"><span data-stu-id="f25ee-119">For nullable bool operands, the behavior of the `&` operator is consistent with SQL's three-valued logic.</span></span> <span data-ttu-id="f25ee-120">Para obter mais informações, veja a seção [O tipo bool?](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) do artigo [Usando tipos que permitem valor nulo](../../programming-guide/nullable-types/using-nullable-types.md).</span><span class="sxs-lookup"><span data-stu-id="f25ee-120">For more information, see the [The bool? type](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) section of the [Using nullable types](../../programming-guide/nullable-types/using-nullable-types.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="f25ee-121">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f25ee-121">Operator overloadability</span></span>

<span data-ttu-id="f25ee-122">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `&` binário.</span><span class="sxs-lookup"><span data-stu-id="f25ee-122">User-defined types can [overload](../keywords/operator.md) the binary `&` operator.</span></span> <span data-ttu-id="f25ee-123">Quando um operador `&` binário é sobrecarregado, o [operador de atribuição AND](and-assignment-operator.md) `&=` também é implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="f25ee-123">When a binary `&` operator is overloaded, the [AND assignment operator](and-assignment-operator.md) `&=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f25ee-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f25ee-124">C# language specification</span></span>

<span data-ttu-id="f25ee-125">Para obter mais informações, veja as seções [O operador address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) e [Operadores lógicos](~/_csharplang/spec/expressions.md#logical-operators) da [Especificação de linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f25ee-125">For more information, see [The address-of operator](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) and [Logical operators](~/_csharplang/spec/expressions.md#logical-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f25ee-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f25ee-126">See also</span></span>

- [<span data-ttu-id="f25ee-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f25ee-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f25ee-128">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f25ee-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f25ee-129">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="f25ee-129">C# Operators</span></span>](index.md)
- [<span data-ttu-id="f25ee-130">Tipos de ponteiro</span><span class="sxs-lookup"><span data-stu-id="f25ee-130">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f25ee-131">Operador |</span><span class="sxs-lookup"><span data-stu-id="f25ee-131">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="f25ee-132">Operador ^</span><span class="sxs-lookup"><span data-stu-id="f25ee-132">^ operator</span></span>](xor-operator.md)
- [<span data-ttu-id="f25ee-133">Operador ~</span><span class="sxs-lookup"><span data-stu-id="f25ee-133">~ operator</span></span>](bitwise-complement-operator.md)
- [<span data-ttu-id="f25ee-134">Operador &&</span><span class="sxs-lookup"><span data-stu-id="f25ee-134">&& operator</span></span>](conditional-and-operator.md)

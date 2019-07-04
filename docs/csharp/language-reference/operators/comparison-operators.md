---
title: Operadores de comparação – referência do C#
description: Saiba mais sobre operadores de comparação em C# que você pode usar para verificar a ordem dos valores numéricos.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 7d8a6b7f5bf83719f96009c301867056da755822
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025214"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="b0816-103">Operadores de comparação (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="b0816-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="b0816-104">Os operadores de comparação [`<` (menor que)](#less-than-operator-), [`>` (maior que)](#greater-than-operator-), [`<=` (menor ou igual)](#less-than-or-equal-operator-) e [`>=` ( maior que ou igual)](#greater-than-or-equal-operator-), também conhecida como relacionais, comparam seus operandos.</span><span class="sxs-lookup"><span data-stu-id="b0816-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="b0816-105">Esses operadores dão suporte a todos os tipos numéricos [integrais](../keywords/integral-types-table.md) e de [ponto flutuante](../keywords/floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="b0816-105">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="b0816-106">Para os operadores `==`, `<`, `>`, `<=` e `>=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="b0816-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="b0816-107">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="b0816-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="b0816-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b0816-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="b0816-109">Tipos de enumeração também dão suporte a operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="b0816-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="b0816-110">No caso dos operandos do mesmo tipo de [enum](../keywords/enum.md), os valores correspondentes do tipo integral subjacente são comparados.</span><span class="sxs-lookup"><span data-stu-id="b0816-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="b0816-111">Os operadores [`==` e `!=`](equality-operators.md) verificam se seus operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="b0816-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="b0816-112">Operador menor que \<</span><span class="sxs-lookup"><span data-stu-id="b0816-112">Less than operator \<</span></span>

<span data-ttu-id="b0816-113">O operador `<` retornará `true` se o primeiro operando for menor do que o segundo; caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="b0816-113">The `<` operator returns `true` if its first operand is less than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="b0816-114">Operador maior que ></span><span class="sxs-lookup"><span data-stu-id="b0816-114">Greater than operator ></span></span>

<span data-ttu-id="b0816-115">O operador `>` retornará `true` se o primeiro operando for maior do que o segundo; caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="b0816-115">The `>` operator returns `true` if its first operand is greater than its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="b0816-116">Operador menor ou igual \<=</span><span class="sxs-lookup"><span data-stu-id="b0816-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="b0816-117">O operador `<=` retornará `true` se o primeiro operando for menor ou igual ao segundo; caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="b0816-117">The `<=` operator returns `true` if its first operand is less than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="b0816-118">Operador maior ou igual >=</span><span class="sxs-lookup"><span data-stu-id="b0816-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="b0816-119">O operador `>=` retornará `true` se o primeiro operando for maior ou igual ao segundo; caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="b0816-119">The `>=` operator returns `true` if its first operand is greater than or equal to its second operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="b0816-120">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="b0816-120">Operator overloadability</span></span>

<span data-ttu-id="b0816-121">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `<`, `>`, `<=` e `>=`.</span><span class="sxs-lookup"><span data-stu-id="b0816-121">A user-defined type can [overload](../keywords/operator.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="b0816-122">Se um tipo sobrecarregar um dos operadores `<` ou `>`, ele deverá sobrecarregar tanto `<` quanto `>`.</span><span class="sxs-lookup"><span data-stu-id="b0816-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="b0816-123">Se um tipo sobrecarregar um dos operadores `<=` ou `>=`, ele deverá sobrecarregar tanto `<=` quanto `>=`.</span><span class="sxs-lookup"><span data-stu-id="b0816-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0816-124">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b0816-124">C# language specification</span></span>

<span data-ttu-id="b0816-125">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b0816-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0816-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0816-126">See also</span></span>

- [<span data-ttu-id="b0816-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b0816-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b0816-128">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="b0816-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="b0816-129">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="b0816-129">Equality operators</span></span>](equality-operators.md)

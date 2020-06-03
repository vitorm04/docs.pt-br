---
title: Operadores de comparação – referência do C#
description: Saiba mais sobre operadores de comparação em C# que você pode usar para verificar a ordem dos valores numéricos.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207222"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="eb03a-103">Operadores de comparação (referência do C#)</span><span class="sxs-lookup"><span data-stu-id="eb03a-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="eb03a-104">A comparação [ `<` (menor que)](#less-than-operator-), [ `>` (maior que)](#greater-than-operator-), [ `<=` (menor que ou igual)](#less-than-or-equal-operator-)e [ `>=` (maior que ou igual)](#greater-than-or-equal-operator-) , também conhecida como operadores relacionais, comparam seus operandos.</span><span class="sxs-lookup"><span data-stu-id="eb03a-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="eb03a-105">Esses operadores têm suporte de todos os tipos numéricos [integral](../builtin-types/integral-numeric-types.md) e [de ponto flutuante](../builtin-types/floating-point-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="eb03a-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="eb03a-106">Para os operadores `==`, `<`, `>`, `<=` e `>=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="eb03a-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="eb03a-107">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="eb03a-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="eb03a-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb03a-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="eb03a-109">O tipo [Char](../builtin-types/char.md) também dá suporte a operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="eb03a-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="eb03a-110">No caso dos `char` operandos, os códigos de caractere correspondentes são comparados.</span><span class="sxs-lookup"><span data-stu-id="eb03a-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="eb03a-111">Tipos de enumeração também dão suporte a operadores de comparação.</span><span class="sxs-lookup"><span data-stu-id="eb03a-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="eb03a-112">No caso dos operandos do mesmo tipo de [enum](../builtin-types/enum.md), os valores correspondentes do tipo integral subjacente são comparados.</span><span class="sxs-lookup"><span data-stu-id="eb03a-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="eb03a-113">Os [ `==` `!=` operadores e](equality-operators.md) verificam se seus operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="eb03a-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="eb03a-114">Operador menor que \<</span><span class="sxs-lookup"><span data-stu-id="eb03a-114">Less than operator \<</span></span>

<span data-ttu-id="eb03a-115">O operador `<` retornará `true` se o operando à esquerda for menor do que o operando à direita, caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="eb03a-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="eb03a-116">Operador maior que ></span><span class="sxs-lookup"><span data-stu-id="eb03a-116">Greater than operator ></span></span>

<span data-ttu-id="eb03a-117">O operador `>` retornará `true` se o operando à esquerda for maior do que o operando à direita, caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="eb03a-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="eb03a-118">Operador menor ou igual \<=</span><span class="sxs-lookup"><span data-stu-id="eb03a-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="eb03a-119">O operador `<=` retornará `true` se o operando à esquerda for menor ou igual ao operando à direita, caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="eb03a-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="eb03a-120">Operador maior ou igual >=</span><span class="sxs-lookup"><span data-stu-id="eb03a-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="eb03a-121">O operador `>=` retornará `true` se o operando à esquerda for maior ou igual ao operando à direita, caso contrário, `false`:</span><span class="sxs-lookup"><span data-stu-id="eb03a-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="eb03a-122">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="eb03a-122">Operator overloadability</span></span>

<span data-ttu-id="eb03a-123">Um tipo definido pelo usuário pode [sobrecarregar](operator-overloading.md) os `<` operadores,, `>` `<=` e `>=` .</span><span class="sxs-lookup"><span data-stu-id="eb03a-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="eb03a-124">Se um tipo sobrecarregar um dos operadores `<` ou `>`, ele deverá sobrecarregar tanto `<` quanto `>`.</span><span class="sxs-lookup"><span data-stu-id="eb03a-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="eb03a-125">Se um tipo sobrecarregar um dos operadores `<=` ou `>=`, ele deverá sobrecarregar tanto `<=` quanto `>=`.</span><span class="sxs-lookup"><span data-stu-id="eb03a-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb03a-126">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="eb03a-126">C# language specification</span></span>

<span data-ttu-id="eb03a-127">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="eb03a-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb03a-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="eb03a-128">See also</span></span>

- [<span data-ttu-id="eb03a-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="eb03a-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="eb03a-130">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="eb03a-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="eb03a-131">Operadores de igualdade</span><span class="sxs-lookup"><span data-stu-id="eb03a-131">Equality operators</span></span>](equality-operators.md)

---
title: Operadores de igualdade - Referência de C#
description: Saiba mais sobre operadores de comparação de igualdade em C#.
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: f60d62d1823a8bd06b0417638719a81e95d7438b
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267692"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="304c8-103">Operadores de igualdade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="304c8-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="304c8-104">Os operadores [`==` (igualdade)](#equality-operator-) e [`!=` (desigualdade)](#inequality-operator-) verificam se os operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="304c8-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="304c8-105">Operador de igualdade ==</span><span class="sxs-lookup"><span data-stu-id="304c8-105">Equality operator ==</span></span>

<span data-ttu-id="304c8-106">O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="304c8-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="304c8-107">Igualdade de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="304c8-107">Value types equality</span></span>

<span data-ttu-id="304c8-108">Os operandos dos [tipos de valor internos](../keywords/value-types-table.md) serão iguais se seus valores forem iguais:</span><span class="sxs-lookup"><span data-stu-id="304c8-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="304c8-109">Para os operadores `==`, [`<`, `>`, `<=` e `>=`](comparison-operators.md), se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="304c8-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="304c8-110">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="304c8-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="304c8-111">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="304c8-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="304c8-112">Dois operandos do mesmo tipo de [enum](../keywords/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.</span><span class="sxs-lookup"><span data-stu-id="304c8-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="304c8-113">Os tipos [struct](../keywords/struct.md) definidos pelo usuário não dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="304c8-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="304c8-114">Para dar suporte ao operador `==`, um struct definido pelo usuário precisa [sobrecarregá-lo](#operator-overloadability).</span><span class="sxs-lookup"><span data-stu-id="304c8-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="304c8-115">A partir do C# 7.3, os operadores `==` e `!=` são compatíveis com as [tuplas](../../tuples.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="304c8-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="304c8-116">Para obter mais informações, consulte a seção [Igualdade e tuplas](../../tuples.md#equality-and-tuples) do artigo [Tipos de tupla do C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="304c8-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="304c8-117">Igualdade da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="304c8-117">String equality</span></span>

<span data-ttu-id="304c8-118">Dois operandos da [cadeia de caracteres](../keywords/string.md) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:</span><span class="sxs-lookup"><span data-stu-id="304c8-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="304c8-119">Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="304c8-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="304c8-120">Para obter mais informações sobre a comparação de cadeias de caracteres, confira [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="304c8-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="304c8-121">Igualdade de tipos de referência</span><span class="sxs-lookup"><span data-stu-id="304c8-121">Reference types equality</span></span>

<span data-ttu-id="304c8-122">Dois operandos de um tipo de referência diferente de `string` serão iguais quando eles se referirem ao mesmo objeto:</span><span class="sxs-lookup"><span data-stu-id="304c8-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="304c8-123">Como mostra o exemplo, os tipos de referência definidos pelo usuário dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="304c8-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="304c8-124">No entanto, um tipo de referência definido pelo usuário pode sobrecarregar o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="304c8-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="304c8-125">Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="304c8-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="304c8-126">Operador de desigualdade !=</span><span class="sxs-lookup"><span data-stu-id="304c8-126">Inequality operator !=</span></span>

<span data-ttu-id="304c8-127">O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="304c8-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="304c8-128">No caso dos operandos de [tipos internos](../keywords/built-in-types-table.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="304c8-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="304c8-129">Para obter mais informações sobre a igualdade de tipos, confira a seção [Operador de igualdade](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="304c8-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="304c8-130">O exemplo a seguir demonstra o uso do operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="304c8-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="304c8-131">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="304c8-131">Operator overloadability</span></span>

<span data-ttu-id="304c8-132">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="304c8-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="304c8-133">Se um tipo sobrecarregar um dos dois operadores, ele também precisará sobrecarregar o outro.</span><span class="sxs-lookup"><span data-stu-id="304c8-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="304c8-134">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="304c8-134">C# language specification</span></span>

<span data-ttu-id="304c8-135">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="304c8-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="304c8-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="304c8-136">See also</span></span>

- [<span data-ttu-id="304c8-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="304c8-137">C# reference</span></span>](../index.md)
- [<span data-ttu-id="304c8-138">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="304c8-138">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="304c8-139">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="304c8-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="304c8-140">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="304c8-140">Comparison operators</span></span>](comparison-operators.md)

---
title: Operadores de igualdade – Referência de C#
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545884"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="6f0fe-102">Operadores de igualdade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6f0fe-102">Equality operators (C# Reference)</span></span>

<span data-ttu-id="6f0fe-103">Os operadores [`==` (igualdade)](#equality-operator-) e [`!=` (desigualdade)](#inequality-operator-) verificam se os operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-103">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="6f0fe-104">Operador de igualdade ==</span><span class="sxs-lookup"><span data-stu-id="6f0fe-104">Equality operator ==</span></span>

<span data-ttu-id="6f0fe-105">O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-105">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="6f0fe-106">Igualdade de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="6f0fe-106">Value types equality</span></span>

<span data-ttu-id="6f0fe-107">Os operandos dos [tipos de valor internos](../keywords/value-types-table.md) serão iguais se seus valores forem iguais:</span><span class="sxs-lookup"><span data-stu-id="6f0fe-107">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="6f0fe-108">No caso dos operadores de igualdade e relacionais `==`, `>`, `<`, `>=` e `<=`, se um dos operandos não for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-108">For equality and relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="6f0fe-109">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-109">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="6f0fe-110">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-110">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="6f0fe-111">Dois operandos do mesmo tipo de [enum](../keywords/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-111">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="6f0fe-112">Os tipos [struct](../keywords/struct.md) definidos pelo usuário não dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-112">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="6f0fe-113">Para dar suporte ao operador `==`, um struct definido pelo usuário precisa [sobrecarregá-lo](#operator-overloadability).</span><span class="sxs-lookup"><span data-stu-id="6f0fe-113">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="6f0fe-114">A partir do C# 7.3, os operadores `==` e `!=` são compatíveis com as [tuplas](../../tuples.md) do C#.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-114">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="6f0fe-115">Para obter mais informações, consulte a seção [Igualdade e tuplas](../../tuples.md#equality-and-tuples) do artigo [Tipos de tupla do C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="6f0fe-115">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="6f0fe-116">Igualdade da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f0fe-116">String equality</span></span>

<span data-ttu-id="6f0fe-117">Dois operandos da [cadeia de caracteres](../keywords/string.md) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:</span><span class="sxs-lookup"><span data-stu-id="6f0fe-117">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="6f0fe-118">Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-118">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="6f0fe-119">Para obter mais informações sobre a comparação de cadeias de caracteres, confira [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="6f0fe-119">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="6f0fe-120">Igualdade de tipos de referência</span><span class="sxs-lookup"><span data-stu-id="6f0fe-120">Reference types equality</span></span>

<span data-ttu-id="6f0fe-121">Dois operandos de um tipo de referência diferente de `string` serão iguais quando eles se referirem ao mesmo objeto:</span><span class="sxs-lookup"><span data-stu-id="6f0fe-121">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="6f0fe-122">Como mostra o exemplo, os tipos de referência definidos pelo usuário dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-122">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="6f0fe-123">No entanto, um tipo de referência definido pelo usuário pode sobrecarregar o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-123">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="6f0fe-124">Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-124">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="6f0fe-125">Operador de desigualdade !=</span><span class="sxs-lookup"><span data-stu-id="6f0fe-125">Inequality operator !=</span></span>

<span data-ttu-id="6f0fe-126">O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-126">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="6f0fe-127">No caso dos operandos de [tipos internos](../keywords/built-in-types-table.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-127">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="6f0fe-128">Para obter mais informações sobre a igualdade de tipos, confira a seção [Operador de igualdade](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="6f0fe-128">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="6f0fe-129">O exemplo a seguir demonstra o uso do operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="6f0fe-129">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="6f0fe-130">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="6f0fe-130">Operator overloadability</span></span>

<span data-ttu-id="6f0fe-131">Os tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) os operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-131">User-defined types can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="6f0fe-132">Se um tipo sobrecarregar um dos dois operadores, ele também precisará sobrecarregar o outro.</span><span class="sxs-lookup"><span data-stu-id="6f0fe-132">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6f0fe-133">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6f0fe-133">C# language specification</span></span>

<span data-ttu-id="6f0fe-134">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6f0fe-134">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f0fe-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f0fe-135">See also</span></span>

- [<span data-ttu-id="6f0fe-136">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6f0fe-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6f0fe-137">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6f0fe-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6f0fe-138">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6f0fe-138">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6f0fe-139">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="6f0fe-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)

---
title: Operador == – Referência de C#
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655953"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="db4a1-102">Operador == (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="db4a1-102">== Operator (C# Reference)</span></span>

<span data-ttu-id="db4a1-103">O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-103">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

## <a name="value-types-equality"></a><span data-ttu-id="db4a1-104">Igualdade de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="db4a1-104">Value types equality</span></span>

<span data-ttu-id="db4a1-105">Os operandos dos [tipos de valor internos](../keywords/value-types-table.md) serão iguais se seus valores forem iguais:</span><span class="sxs-lookup"><span data-stu-id="db4a1-105">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="db4a1-106">No caso dos operadores relacionais `==`, `>`, `<`, `>=` e `<=`, se nenhum dos operandos for um número (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), o resultado da operação será `false`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="db4a1-107">Isso significa que o valor `NaN` não é maior, menor, nem igual a nenhum outro valor `double` (ou `float`).</span><span class="sxs-lookup"><span data-stu-id="db4a1-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="db4a1-108">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db4a1-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="db4a1-109">Dois operandos do mesmo tipo de [enum](../keywords/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.</span><span class="sxs-lookup"><span data-stu-id="db4a1-109">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="db4a1-110">Por padrão, o operador `==` não está definido para um tipo de [struct](../keywords/struct.md) definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="db4a1-110">By default, the `==` operator is not defined for a user-defined [struct](../keywords/struct.md) type.</span></span> <span data-ttu-id="db4a1-111">Um tipo definido pelo usuário pode [sobrecarregar](#operator-overloadability) o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-111">A user-defined type can [overload](#operator-overloadability) the `==` operator.</span></span>

<span data-ttu-id="db4a1-112">Começando com C# 7.3, os operadores `==`, [, `!=` e ](not-equal-operator.md) são compatíveis com as [tuplas](../../tuples.md) de C#.</span><span class="sxs-lookup"><span data-stu-id="db4a1-112">Beginning with C# 7.3, the `==` and [`!=`](not-equal-operator.md) operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="db4a1-113">Para obter mais informações, consulte a seção [Igualdade e tuplas](../../tuples.md#equality-and-tuples) do artigo [Tipos de tupla do C#](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="db4a1-113">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

## <a name="string-equality"></a><span data-ttu-id="db4a1-114">Igualdade da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="db4a1-114">String equality</span></span>

<span data-ttu-id="db4a1-115">Dois operandos da [cadeia de caracteres](../keywords/string.md) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:</span><span class="sxs-lookup"><span data-stu-id="db4a1-115">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="db4a1-116">Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="db4a1-116">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="db4a1-117">Para obter mais informações sobre como comparar cadeias de caracteres, consulte [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="db4a1-117">For more information about how to compare strings, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

## <a name="reference-types-equality"></a><span data-ttu-id="db4a1-118">Igualdade de tipos de referência</span><span class="sxs-lookup"><span data-stu-id="db4a1-118">Reference types equality</span></span>

<span data-ttu-id="db4a1-119">Dois operandos de um tipo de referência diferente de `string` serão iguais quando eles se referirem ao mesmo objeto:</span><span class="sxs-lookup"><span data-stu-id="db4a1-119">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="db4a1-120">O exemplo mostra que o operador `==` é compatível com os tipos de referência definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="db4a1-120">The example shows that the `==` operator is supported by user-defined reference types.</span></span> <span data-ttu-id="db4a1-121">No entanto, um tipo de referência definido pelo usuário pode sobrecarregar o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-121">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="db4a1-122">Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="db4a1-122">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="db4a1-123">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="db4a1-123">Operator overloadability</span></span>

<span data-ttu-id="db4a1-124">Tipos definidos pelo usuário podem [sobrecarregar](../keywords/operator.md) o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-124">User-defined types can [overload](../keywords/operator.md) the `==` operator.</span></span> <span data-ttu-id="db4a1-125">Se um tipo sobrecarregar o operador de igualdade `==`, ele também sobrecarregará o [operador de desigualdade](not-equal-operator.md) `!=`.</span><span class="sxs-lookup"><span data-stu-id="db4a1-125">If a type overloads the equality operator `==`, it must also overload the [inequality operator](not-equal-operator.md) `!=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="db4a1-126">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="db4a1-126">C# language specification</span></span>

<span data-ttu-id="db4a1-127">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="db4a1-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db4a1-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db4a1-128">See also</span></span>

- [<span data-ttu-id="db4a1-129">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="db4a1-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="db4a1-130">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="db4a1-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="db4a1-131">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="db4a1-131">C# Operators</span></span>](index.md)
- [<span data-ttu-id="db4a1-132">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="db4a1-132">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)

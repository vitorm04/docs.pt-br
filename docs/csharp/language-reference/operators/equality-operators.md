---
title: Operadores de igualdade - Referência de C#
description: Saiba mais sobre os operadores de comparação de igualdade C# e a igualdade do tipo C#.
ms.date: 06/26/2019
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
ms.openlocfilehash: 47e550226cdef31c82b30348d779207200f32b90
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916831"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="84d96-103">Operadores de igualdade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="84d96-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="84d96-104">Os operadores [ `==` (igualdade)](#equality-operator-) e [ `!=` (desigualdade)](#inequality-operator-) verificam se os operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="84d96-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="84d96-105">Operador de igualdade ==</span><span class="sxs-lookup"><span data-stu-id="84d96-105">Equality operator ==</span></span>

<span data-ttu-id="84d96-106">O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="84d96-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="84d96-107">Igualdade de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="84d96-107">Value types equality</span></span>

<span data-ttu-id="84d96-108">Os operandos dos [tipos de valor internos](../builtin-types/value-types.md#built-in-value-types) serão iguais se seus valores forem iguais:</span><span class="sxs-lookup"><span data-stu-id="84d96-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="84d96-109">Para os `==` operadores,, [ `<` `>` , `<=` e `>=` ](comparison-operators.md) , se qualquer um dos operandos não for um número ( <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType> ), o resultado da operação será `false` .</span><span class="sxs-lookup"><span data-stu-id="84d96-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="84d96-110">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="84d96-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="84d96-111">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84d96-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="84d96-112">Dois operandos do mesmo tipo de [enum](../builtin-types/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.</span><span class="sxs-lookup"><span data-stu-id="84d96-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="84d96-113">Os tipos [struct](../builtin-types/struct.md) definidos pelo usuário não dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="84d96-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="84d96-114">Para dar suporte ao operador `==`, um struct definido pelo usuário precisa [sobrecarregá-lo](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="84d96-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="84d96-115">Começando com C# 7.3, os operadores `==`, `!=`,  e  são compatíveis com as [tuplas](../builtin-types/value-tuples.md) de C#.</span><span class="sxs-lookup"><span data-stu-id="84d96-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="84d96-116">Para obter mais informações, consulte a seção de [igualdade de tupla](../builtin-types/value-tuples.md#tuple-equality) do artigo [tipos de tupla](../builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="84d96-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="84d96-117">Igualdade de tipos de referência</span><span class="sxs-lookup"><span data-stu-id="84d96-117">Reference types equality</span></span>

<span data-ttu-id="84d96-118">Por padrão, dois operandos do tipo de referência são iguais quando se referem ao mesmo objeto:</span><span class="sxs-lookup"><span data-stu-id="84d96-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="84d96-119">Como mostra o exemplo, os tipos de referência definidos pelo usuário dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="84d96-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="84d96-120">No entanto, um tipo de referência pode sobrecarregar o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="84d96-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="84d96-121">Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="84d96-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="84d96-122">Igualdade da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="84d96-122">String equality</span></span>

<span data-ttu-id="84d96-123">Dois operandos da [cadeia de caracteres](../builtin-types/reference-types.md#the-string-type) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:</span><span class="sxs-lookup"><span data-stu-id="84d96-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="84d96-124">Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="84d96-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="84d96-125">Para obter mais informações sobre a comparação de cadeias de caracteres, confira [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="84d96-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="84d96-126">Igualdade de delegado</span><span class="sxs-lookup"><span data-stu-id="84d96-126">Delegate equality</span></span>

<span data-ttu-id="84d96-127">Os dois operandos [delegar](../../programming-guide/delegates/index.md) do mesmo tipo de runtime são iguais quando ambos são `null` ou suas listas de invocação são do mesmo comprimento e tem entradas iguais em cada posição:</span><span class="sxs-lookup"><span data-stu-id="84d96-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="84d96-128">Saiba mais na seção [Operadores de igualdade de delegados](~/_csharplang/spec/expressions.md#delegate-equality-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="84d96-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="84d96-129">Os delegados produzidos pela avaliação de [expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) semanticamente idênticas não são iguais, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="84d96-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="84d96-130">Operador de desigualdade !=</span><span class="sxs-lookup"><span data-stu-id="84d96-130">Inequality operator !=</span></span>

<span data-ttu-id="84d96-131">O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="84d96-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="84d96-132">No caso dos operandos de [tipos internos](../builtin-types/built-in-types.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="84d96-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="84d96-133">Para obter mais informações sobre a igualdade de tipos, confira a seção [Operador de igualdade](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="84d96-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="84d96-134">O exemplo a seguir demonstra o uso do operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="84d96-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="84d96-135">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="84d96-135">Operator overloadability</span></span>

<span data-ttu-id="84d96-136">Os tipos definidos pelo usuário podem [sobrecarregar](operator-overloading.md) os operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="84d96-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="84d96-137">Se um tipo sobrecarrega um dos dois operadores, ele também deve sobrecarregar o outro.</span><span class="sxs-lookup"><span data-stu-id="84d96-137">If a type overloads one of the two operators, it must also overload the other one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="84d96-138">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="84d96-138">C# language specification</span></span>

<span data-ttu-id="84d96-139">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="84d96-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="84d96-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84d96-140">See also</span></span>

- [<span data-ttu-id="84d96-141">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="84d96-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="84d96-142">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="84d96-142">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="84d96-143">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="84d96-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="84d96-144">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="84d96-144">Comparison operators</span></span>](comparison-operators.md)

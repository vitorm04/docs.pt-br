---
title: Operadores de igualdade - Referência de C#
description: Saiba mais sobre os operadores de comparação de igualdade C# e a igualdade do tipo C#.
ms.date: 10/30/2020
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
ms.openlocfilehash: 39461157c33fea0effb5c8808ded1c9981900e17
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063209"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="f59af-103">Operadores de igualdade (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f59af-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="f59af-104">Os operadores [ `==` (igualdade)](#equality-operator-) e [ `!=` (desigualdade)](#inequality-operator-) verificam se os operandos são iguais ou não.</span><span class="sxs-lookup"><span data-stu-id="f59af-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="f59af-105">Operador de igualdade ==</span><span class="sxs-lookup"><span data-stu-id="f59af-105">Equality operator ==</span></span>

<span data-ttu-id="f59af-106">O operador de igualdade `==` retornará `true` se seus operandos forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f59af-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="f59af-107">Igualdade de tipos de valor</span><span class="sxs-lookup"><span data-stu-id="f59af-107">Value types equality</span></span>

<span data-ttu-id="f59af-108">Os operandos dos [tipos de valor internos](../builtin-types/value-types.md#built-in-value-types) serão iguais se seus valores forem iguais:</span><span class="sxs-lookup"><span data-stu-id="f59af-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="f59af-109">Para os `==` operadores,, [ `<` `>` , `<=` e `>=` ](comparison-operators.md) , se qualquer um dos operandos não for um número ( <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType> ), o resultado da operação será `false` .</span><span class="sxs-lookup"><span data-stu-id="f59af-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="f59af-110">Isso significa que o valor `NaN` não é superior, inferior nem igual a nenhum outro valor `double` (ou `float`), incluindo `NaN`.</span><span class="sxs-lookup"><span data-stu-id="f59af-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="f59af-111">Para obter mais informações e exemplos, consulte o artigo de referência <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f59af-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="f59af-112">Dois operandos do mesmo tipo de [enum](../builtin-types/enum.md) serão iguais se os valores correspondentes do tipo integral subjacente forem iguais.</span><span class="sxs-lookup"><span data-stu-id="f59af-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="f59af-113">Os tipos [struct](../builtin-types/struct.md) definidos pelo usuário não dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="f59af-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="f59af-114">Para dar suporte ao operador `==`, um struct definido pelo usuário precisa [sobrecarregá-lo](operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="f59af-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="f59af-115">Começando com C# 7.3, os operadores `==`, `!=`,  e  são compatíveis com as [tuplas](../builtin-types/value-tuples.md) de C#.</span><span class="sxs-lookup"><span data-stu-id="f59af-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="f59af-116">Para obter mais informações, consulte a seção de [igualdade de tupla](../builtin-types/value-tuples.md#tuple-equality) do artigo [tipos de tupla](../builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="f59af-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="f59af-117">Igualdade de tipos de referência</span><span class="sxs-lookup"><span data-stu-id="f59af-117">Reference types equality</span></span>

<span data-ttu-id="f59af-118">Por padrão, dois operandos de tipo de referência sem registro são iguais se se referirem ao mesmo objeto:</span><span class="sxs-lookup"><span data-stu-id="f59af-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="f59af-119">Como mostra o exemplo, os tipos de referência definidos pelo usuário dão suporte ao operador `==`, por padrão.</span><span class="sxs-lookup"><span data-stu-id="f59af-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="f59af-120">No entanto, um tipo de referência pode sobrecarregar o operador `==`.</span><span class="sxs-lookup"><span data-stu-id="f59af-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="f59af-121">Se um tipo de referência sobrecarregar o operador `==`, use o método <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> para verificar se as duas referências desse tipo dizem respeito ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="f59af-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="f59af-122">Igualdade de tipos de registro</span><span class="sxs-lookup"><span data-stu-id="f59af-122">Record types equality</span></span>

<span data-ttu-id="f59af-123">Disponível em C# 9,0 e posterior, os [tipos de registro](../../whats-new/csharp-9.md#record-types) dão suporte aos `==` operadores e `!=` que, por padrão, fornecem semântica de igualdade de valor.</span><span class="sxs-lookup"><span data-stu-id="f59af-123">Available in C# 9.0 and later, [record types](../../whats-new/csharp-9.md#record-types) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="f59af-124">Ou seja, dois operandos de registro são iguais quando ambos são `null` ou valores correspondentes de todos os campos e propriedades auto implementadas são iguais.</span><span class="sxs-lookup"><span data-stu-id="f59af-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="f59af-125">Como mostra o exemplo anterior, no caso de membros de tipo de referência que não são de registro, seus valores de referência são comparados, não as instâncias referenciadas.</span><span class="sxs-lookup"><span data-stu-id="f59af-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="f59af-126">Igualdade da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f59af-126">String equality</span></span>

<span data-ttu-id="f59af-127">Dois operandos da [cadeia de caracteres](../builtin-types/reference-types.md#the-string-type) serão iguais quando ambos forem `null` ou ambas as instâncias da cadeia de caracteres tiverem o mesmo comprimento e caracteres idênticos em cada posição de caractere:</span><span class="sxs-lookup"><span data-stu-id="f59af-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="f59af-128">Essa é uma comparação ordinal que diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f59af-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="f59af-129">Para obter mais informações sobre a comparação de cadeias de caracteres, confira [Como comparar cadeias de caracteres no C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="f59af-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="f59af-130">Igualdade de delegado</span><span class="sxs-lookup"><span data-stu-id="f59af-130">Delegate equality</span></span>

<span data-ttu-id="f59af-131">Os dois operandos [delegar](../../programming-guide/delegates/index.md) do mesmo tipo de runtime são iguais quando ambos são `null` ou suas listas de invocação são do mesmo comprimento e tem entradas iguais em cada posição:</span><span class="sxs-lookup"><span data-stu-id="f59af-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="f59af-132">Saiba mais na seção [Operadores de igualdade de delegados](~/_csharplang/spec/expressions.md#delegate-equality-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f59af-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f59af-133">Os delegados produzidos pela avaliação de [expressões lambda](lambda-expressions.md) semanticamente idênticas não são iguais, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="f59af-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="f59af-134">Operador de desigualdade !=</span><span class="sxs-lookup"><span data-stu-id="f59af-134">Inequality operator !=</span></span>

<span data-ttu-id="f59af-135">O operador de desigualdade `!=` retornará `true` se seus operandos não forem iguais; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="f59af-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="f59af-136">No caso dos operandos de [tipos internos](../builtin-types/built-in-types.md), a expressão `x != y` gera o mesmo resultado que a expressão `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="f59af-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="f59af-137">Para obter mais informações sobre a igualdade de tipos, confira a seção [Operador de igualdade](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="f59af-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="f59af-138">O exemplo a seguir demonstra o uso do operador `!=`:</span><span class="sxs-lookup"><span data-stu-id="f59af-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="f59af-139">Capacidade de sobrecarga do operador</span><span class="sxs-lookup"><span data-stu-id="f59af-139">Operator overloadability</span></span>

<span data-ttu-id="f59af-140">Os tipos definidos pelo usuário podem [sobrecarregar](operator-overloading.md) os operadores `==` e `!=`.</span><span class="sxs-lookup"><span data-stu-id="f59af-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="f59af-141">Se um tipo sobrecarrega um dos dois operadores, ele também deve sobrecarregar o outro.</span><span class="sxs-lookup"><span data-stu-id="f59af-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="f59af-142">Um tipo de registro não pode sobrecarregar explicitamente os `==` `!=` operadores e.</span><span class="sxs-lookup"><span data-stu-id="f59af-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="f59af-143">Se você precisar alterar o comportamento dos `==` `!=` operadores e para o tipo de registro `T` , implemente o <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> método com a assinatura a seguir:</span><span class="sxs-lookup"><span data-stu-id="f59af-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="f59af-144">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f59af-144">C# language specification</span></span>

<span data-ttu-id="f59af-145">Para obter mais informações, consulte a seção [Operadores de teste de tipo e relacional](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f59af-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="f59af-146">Para obter mais informações sobre a igualdade de tipos de registro, consulte a seção [membros de igualdade](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) da nota de proposta de [recurso de registros](~/_csharplang/proposals/csharp-9.0/records.md).</span><span class="sxs-lookup"><span data-stu-id="f59af-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f59af-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f59af-147">See also</span></span>

- [<span data-ttu-id="f59af-148">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f59af-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f59af-149">Operadores e expressões C#</span><span class="sxs-lookup"><span data-stu-id="f59af-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f59af-150">Comparações de igualdade</span><span class="sxs-lookup"><span data-stu-id="f59af-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="f59af-151">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="f59af-151">Comparison operators</span></span>](comparison-operators.md)

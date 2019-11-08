---
title: Tipos de valor Anulável C# -referência
description: Saiba mais C# sobre os tipos de valor anulável e como usá-los
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: b9400cd76eb0430dbe9c278e835a3cec7f9f131e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741161"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="9be15-103">Tipos de valores anuláveis (C# referência)</span><span class="sxs-lookup"><span data-stu-id="9be15-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="9be15-104">Um tipo de valor anulável `T?` representa todos os valores de seu [tipo de valor](../keywords/value-types.md) subjacente `T` e um valor [nulo](../keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="9be15-104">A nullable value type `T?` represents all values of its underlying [value type](../keywords/value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="9be15-105">Por exemplo, você pode atribuir qualquer um dos três valores a seguir a uma `bool?` variável: `true`, `false`ou `null`.</span><span class="sxs-lookup"><span data-stu-id="9be15-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="9be15-106">Um tipo de valor subjacente `T` não pode ser um tipo de valor anulável em si.</span><span class="sxs-lookup"><span data-stu-id="9be15-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="9be15-107">C#8,0 apresenta o recurso de tipos de referência anulável.</span><span class="sxs-lookup"><span data-stu-id="9be15-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="9be15-108">Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="9be15-108">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="9be15-109">Os tipos de valor anulável estão disponíveis a C# partir de 2.</span><span class="sxs-lookup"><span data-stu-id="9be15-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="9be15-110">Qualquer tipo de valor anulável é uma instância da estrutura de <xref:System.Nullable%601?displayProperty=nameWithType> genérica.</span><span class="sxs-lookup"><span data-stu-id="9be15-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="9be15-111">Você pode se referir a um tipo de valor anulável com um tipo subjacente `T` em qualquer um dos seguintes formulários intercambiáveis: `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="9be15-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="9be15-112">Normalmente, você usa um tipo de valor anulável quando precisa representar o valor indefinido de um tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="9be15-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="9be15-113">Por exemplo, um booliano ou `bool`variável só pode ser `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="9be15-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="9be15-114">No entanto, em alguns aplicativos, um valor de variável pode ser indefinido ou estar ausente.</span><span class="sxs-lookup"><span data-stu-id="9be15-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="9be15-115">Por exemplo, um campo de banco de dados pode conter `true` ou `false`ou não pode conter nenhum valor, ou seja, `NULL`.</span><span class="sxs-lookup"><span data-stu-id="9be15-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="9be15-116">Você pode usar o tipo de `bool?` nesse cenário.</span><span class="sxs-lookup"><span data-stu-id="9be15-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="9be15-117">Declaração e atribuição</span><span class="sxs-lookup"><span data-stu-id="9be15-117">Declaration and assignment</span></span>

<span data-ttu-id="9be15-118">Como um tipo de valor é implicitamente conversível para o tipo de valor anulável correspondente, você pode atribuir um valor a uma variável de um tipo de valor anulável, como faria com o tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="9be15-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="9be15-119">Você também pode atribuir o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="9be15-119">You also can assign the `null` value.</span></span> <span data-ttu-id="9be15-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9be15-120">For example:</span></span>

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="9be15-121">O valor padrão de um tipo de valor anulável representa `null`, ou seja, é uma instância cuja propriedade <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="9be15-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="9be15-122">Exame de uma instância de um tipo de valor anulável</span><span class="sxs-lookup"><span data-stu-id="9be15-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="9be15-123">A partir C# do 7,0, você pode usar o [operador de`is` com um padrão de tipo](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) para examinar uma instância de um tipo de valor anulável para `null` e recuperar um valor de um tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="9be15-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="9be15-124">Você sempre pode usar as seguintes propriedades somente leitura para examinar e obter um valor de uma variável de tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="9be15-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="9be15-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indica se uma instância de um tipo de valor anulável tem um valor de seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="9be15-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="9be15-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="9be15-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="9be15-127">Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="9be15-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="9be15-128">O exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-la:</span><span class="sxs-lookup"><span data-stu-id="9be15-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="9be15-129">Você também pode comparar uma variável de um tipo de valor anulável com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9be15-129">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="9be15-130">Conversão de um tipo de valor anulável para um tipo subjacente</span><span class="sxs-lookup"><span data-stu-id="9be15-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="9be15-131">Se você quiser atribuir um valor de tipo de valor anulável a uma variável de tipo de valor não anulável, talvez seja necessário especificar o valor a ser atribuído no lugar de `null`.</span><span class="sxs-lookup"><span data-stu-id="9be15-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="9be15-132">Use o [operador de União nulo `??`](../operators/null-coalescing-operator.md) para fazer isso (você também pode usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para a mesma finalidade):</span><span class="sxs-lookup"><span data-stu-id="9be15-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="9be15-133">Se você quiser usar o valor [padrão](../keywords/default-values-table.md) do tipo de valor subjacente no lugar de `null`, use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9be15-133">If you want to use the [default](../keywords/default-values-table.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9be15-134">Você também pode converter explicitamente um tipo de valor anulável para um tipo não anulável, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9be15-134">You also can explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

<span data-ttu-id="9be15-135">Em tempo de execução, se o valor de um tipo de valor anulável for `null`, a conversão explícita lançará um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="9be15-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="9be15-136">Um tipo de valor não anulável `T` é implicitamente conversível para o tipo de valor anulável correspondente `T?`.</span><span class="sxs-lookup"><span data-stu-id="9be15-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="9be15-137">Operadores levantados</span><span class="sxs-lookup"><span data-stu-id="9be15-137">Lifted operators</span></span>

<span data-ttu-id="9be15-138">Os operadores unários e binários predefinidos ou quaisquer operadores sobrecarregados com suporte de um tipo de valor `T` também são suportados pelo tipo de valor anulável correspondente `T?`.</span><span class="sxs-lookup"><span data-stu-id="9be15-138">The predefined unary and binary operators or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="9be15-139">Esses operadores, também conhecidos como *operadores levantados*, produzem `null` se um ou ambos os operandos forem `null`; caso contrário, o operador usa os valores contidos de seus operandos para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="9be15-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="9be15-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9be15-140">For example:</span></span>

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="9be15-141">Para o tipo de `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nesta seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo que um dos operandos seja `null`.</span><span class="sxs-lookup"><span data-stu-id="9be15-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="9be15-142">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9be15-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="9be15-143">Para os [operadores de comparação](../operators/comparison-operators.md) `<`, `>`, `<=`e `>=`, se um ou ambos os operandos forem `null`, o resultado será `false`; caso contrário, os valores contidos dos operandos serão comparados.</span><span class="sxs-lookup"><span data-stu-id="9be15-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise the contained values of operands are compared.</span></span> <span data-ttu-id="9be15-144">Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="9be15-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="9be15-145">O exemplo a seguir mostra que 10</span><span class="sxs-lookup"><span data-stu-id="9be15-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="9be15-146">Nem maior ou igual a `null`</span><span class="sxs-lookup"><span data-stu-id="9be15-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="9be15-147">Nem menor que `null`</span><span class="sxs-lookup"><span data-stu-id="9be15-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="9be15-148">O exemplo anterior também mostra que uma comparação de igualdade de duas instâncias de tipo de valor anulável que são `null` são avaliadas como `true`.</span><span class="sxs-lookup"><span data-stu-id="9be15-148">The preceding example also shows that an equality comparison of two nullable value type instances that are both `null` evaluates to `true`.</span></span>

<span data-ttu-id="9be15-149">Se existir uma [conversão definida pelo usuário](../operators/user-defined-conversion-operators.md) entre dois tipos de valor, a mesma conversão também poderá ser usada entre os tipos de valores anuláveis correspondentes.</span><span class="sxs-lookup"><span data-stu-id="9be15-149">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="9be15-150">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="9be15-150">Boxing and unboxing</span></span>

<span data-ttu-id="9be15-151">Uma instância de um tipo de valor anulável `T?` é [a](../../programming-guide/types/boxing-and-unboxing.md) seguinte:</span><span class="sxs-lookup"><span data-stu-id="9be15-151">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="9be15-152">Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.</span><span class="sxs-lookup"><span data-stu-id="9be15-152">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="9be15-153">Se <xref:System.Nullable%601.HasValue%2A> retornar `true`, o valor correspondente do tipo de valor subjacente `T` será in a box, não a instância de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="9be15-153">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="9be15-154">Você pode unbox um valor em caixa de um tipo de valor `T` para o tipo de valor anulável correspondente `T?`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9be15-154">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="9be15-155">Como identificar um tipo de valor anulável</span><span class="sxs-lookup"><span data-stu-id="9be15-155">How to identify a nullable value type</span></span>

<span data-ttu-id="9be15-156">O exemplo a seguir mostra como determinar se uma instância de <xref:System.Type?displayProperty=nameWithType> representa um tipo de valor anulável construído, ou seja, o tipo de <xref:System.Nullable%601?displayProperty=nameWithType> com um parâmetro de tipo especificado `T`:</span><span class="sxs-lookup"><span data-stu-id="9be15-156">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="9be15-157">Como mostra o exemplo, você usa o operador [typeof](../operators/type-testing-and-cast.md#typeof-operator) para criar uma instância de <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9be15-157">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="9be15-158">Se você quiser determinar se uma instância é de um tipo de valor anulável, não use o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> para obter uma instância de <xref:System.Type> a ser testada com o código anterior.</span><span class="sxs-lookup"><span data-stu-id="9be15-158">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="9be15-159">Quando você chama o método <xref:System.Object.GetType%2A?displayProperty=nameWithType> em uma instância de um tipo de valor anulável, a instância é [encaixada](#boxing-and-unboxing) para <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9be15-159">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="9be15-160">Como Boxing de uma instância não nula de um tipo de valor anulável é equivalente à Boxing de um valor do tipo subjacente, <xref:System.Object.GetType%2A> retorna uma instância de <xref:System.Type> que representa o tipo subjacente de um tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="9be15-160">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

<span data-ttu-id="9be15-161">Além disso, não use o operador [is](../operators/type-testing-and-cast.md#is-operator) para determinar se uma instância é de um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="9be15-161">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="9be15-162">Como mostra o exemplo a seguir, você não pode distinguir tipos de uma instância de tipo de valor anulável e sua instância de tipo subjacente com o operador de `is`:</span><span class="sxs-lookup"><span data-stu-id="9be15-162">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="9be15-163">Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="9be15-163">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="9be15-164">Os métodos descritos nesta seção não são aplicáveis no caso de tipos de [referência anuláveis](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="9be15-164">The methods described in this section are not applicable in the case of [nullable reference types](../../nullable-references.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9be15-165">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9be15-165">C# language specification</span></span>

<span data-ttu-id="9be15-166">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="9be15-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="9be15-167">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="9be15-167">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="9be15-168">Operadores levantados</span><span class="sxs-lookup"><span data-stu-id="9be15-168">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="9be15-169">Conversões anuláveis implícitas</span><span class="sxs-lookup"><span data-stu-id="9be15-169">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="9be15-170">Conversões anuláveis explícitas</span><span class="sxs-lookup"><span data-stu-id="9be15-170">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="9be15-171">Operadores de conversão levantados</span><span class="sxs-lookup"><span data-stu-id="9be15-171">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="9be15-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9be15-172">See also</span></span>

- [<span data-ttu-id="9be15-173">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9be15-173">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9be15-174">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="9be15-174">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9be15-175">Tipos de referência nula</span><span class="sxs-lookup"><span data-stu-id="9be15-175">Nullable reference types</span></span>](../../nullable-references.md)

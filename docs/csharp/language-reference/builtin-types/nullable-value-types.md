---
title: Tipos de valor anulados - referência C#
description: Saiba mais sobre os tipos de valor nulo C# e como usá-los
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: fcd49d7d25b0ad23363db8cb61596004b2e87a8d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738992"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="b8527-103">Tipos de valor anulados (referência C#)</span><span class="sxs-lookup"><span data-stu-id="b8527-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="b8527-104">Um *tipo* `T?` de valor anulado representa todos os valores do seu [tipo](value-types.md) `T` de valor subjacente e um valor [nulo](../keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="b8527-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="b8527-105">Por exemplo, você pode atribuir qualquer um `bool?` dos `true`três `false`valores a uma variável: , ou `null`.</span><span class="sxs-lookup"><span data-stu-id="b8527-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="b8527-106">Um tipo `T` de valor subjacente não pode ser um tipo de valor anulado em si.</span><span class="sxs-lookup"><span data-stu-id="b8527-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="b8527-107">C# 8.0 introduz o recurso de tipos de referência anulados.</span><span class="sxs-lookup"><span data-stu-id="b8527-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="b8527-108">Para obter mais informações, consulte [tipos de referência nulamente](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b8527-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="b8527-109">Os tipos de valor anulados estão disponíveis a partir de C# 2.</span><span class="sxs-lookup"><span data-stu-id="b8527-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="b8527-110">Qualquer tipo de valor anulado é <xref:System.Nullable%601?displayProperty=nameWithType> uma instância da estrutura genérica.</span><span class="sxs-lookup"><span data-stu-id="b8527-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="b8527-111">Você pode consultar um tipo de valor `T` anulado com um tipo subjacente `Nullable<T>` `T?`em qualquer uma das seguintes formas intercambiáveis: ou .</span><span class="sxs-lookup"><span data-stu-id="b8527-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="b8527-112">Você normalmente usa um tipo de valor anulado quando precisa representar o valor indefinido de um tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="b8527-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="b8527-113">Por exemplo, uma variável `bool`booleana, `true` ou `false`, só pode ser ou .</span><span class="sxs-lookup"><span data-stu-id="b8527-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="b8527-114">No entanto, em alguns aplicativos um valor variável pode ser indefinido ou ausente.</span><span class="sxs-lookup"><span data-stu-id="b8527-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="b8527-115">Por exemplo, um campo `true` `false`de banco de dados pode conter ou `NULL`, ou pode conter nenhum valor, ou seja, .</span><span class="sxs-lookup"><span data-stu-id="b8527-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="b8527-116">Você pode `bool?` usar o tipo nesse cenário.</span><span class="sxs-lookup"><span data-stu-id="b8527-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="b8527-117">Declaração e atribuição</span><span class="sxs-lookup"><span data-stu-id="b8527-117">Declaration and assignment</span></span>

<span data-ttu-id="b8527-118">Como um tipo de valor é implicitamente conversível para o tipo de valor nulo correspondente, você pode atribuir um valor a uma variável de um tipo de valor anulado como você faria para o seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="b8527-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="b8527-119">Você também pode `null` atribuir o valor.</span><span class="sxs-lookup"><span data-stu-id="b8527-119">You can also assign the `null` value.</span></span> <span data-ttu-id="b8527-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b8527-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="b8527-121">O valor padrão de um tipo `null`de valor anulado representa, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> ou `false`seja, é uma instância cuja propriedade retorna.</span><span class="sxs-lookup"><span data-stu-id="b8527-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="b8527-122">Exame de uma instância de um tipo de valor anulado</span><span class="sxs-lookup"><span data-stu-id="b8527-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="b8527-123">Começando com C# 7.0, você pode usar o `null` [ `is` operador com um padrão de tipo](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) para examinar uma instância de um tipo de valor anulado e recuperar um valor de um tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="b8527-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="b8527-124">Você sempre pode usar as seguintes propriedades somente leitura para examinar e obter um valor de uma variável de tipo de valor anulado:</span><span class="sxs-lookup"><span data-stu-id="b8527-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="b8527-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>indica se uma instância de um tipo de valor anulado tem um valor de seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="b8527-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="b8527-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="b8527-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="b8527-127">Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="b8527-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="b8527-128">O exemplo a `HasValue` seguir usa a propriedade para testar se a variável contém um valor antes de exibi-la:</span><span class="sxs-lookup"><span data-stu-id="b8527-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="b8527-129">Você também pode comparar uma variável de `null` um tipo `HasValue` de valor anulado com em vez de usar a propriedade, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8527-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="b8527-130">Conversão de um tipo de valor anulado para um tipo subjacente</span><span class="sxs-lookup"><span data-stu-id="b8527-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="b8527-131">Se você quiser atribuir um valor de um tipo de valor anulado a uma variável de tipo de valor `null`não anulado, talvez seja necessário especificar o valor a ser atribuído no lugar de .</span><span class="sxs-lookup"><span data-stu-id="b8527-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="b8527-132">Use o [operador `??` de coalizão nula](../operators/null-coalescing-operator.md) para fazer isso <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (você também pode usar o método para o mesmo propósito):</span><span class="sxs-lookup"><span data-stu-id="b8527-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="b8527-133">Se você quiser usar o valor [padrão](default-values.md) do tipo `null`de <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> valor subjacente no lugar de , use o método.</span><span class="sxs-lookup"><span data-stu-id="b8527-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b8527-134">Você também pode lançar explicitamente um tipo de valor anulado a um tipo não anulado, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8527-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

<span data-ttu-id="b8527-135">No tempo de execução, se o `null`valor de um <xref:System.InvalidOperationException>tipo de valor anulado for, o elenco explícito lança um .</span><span class="sxs-lookup"><span data-stu-id="b8527-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="b8527-136">Um tipo `T` de valor não anulado é implicitamente `T?`conversível para o tipo de valor nulo correspondente .</span><span class="sxs-lookup"><span data-stu-id="b8527-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="b8527-137">Operadores suspensos</span><span class="sxs-lookup"><span data-stu-id="b8527-137">Lifted operators</span></span>

<span data-ttu-id="b8527-138">Os [operadores indefinidos](../operators/index.md) e binários predefinidos ou quaisquer operadores sobrecarregados que são suportados por um tipo de `T` valor também são suportados pelo tipo `T?`de valor nulo correspondente .</span><span class="sxs-lookup"><span data-stu-id="b8527-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="b8527-139">Esses operadores, também conhecidos como `null` *operadores suspensos,* produzem `null`se um ou ambos os orperands são; caso contrário, o operador utiliza os valores contidos de seus operands para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="b8527-139">These operators, also known as *lifted operators*, produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="b8527-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b8527-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="b8527-141">Para `bool?` o tipo, `&` os `|` operadores pré-definidos e os operadores não seguem as regras descritas nesta seção: o `null`resultado de uma avaliação do operador pode ser não nulo mesmo se um dos operands for .</span><span class="sxs-lookup"><span data-stu-id="b8527-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="b8527-142">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="b8527-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="b8527-143">Para os [operadores](../operators/comparison-operators.md) `<` `<=`de `>=`comparação, `>`e, se um `null`ou ambos `false`os operands forem, o resultado é; caso contrário, os valores contidos de operands são comparados.</span><span class="sxs-lookup"><span data-stu-id="b8527-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="b8527-144">Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="b8527-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="b8527-145">O exemplo a seguir mostra que 10</span><span class="sxs-lookup"><span data-stu-id="b8527-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="b8527-146">nem maior do que ou igual a`null`</span><span class="sxs-lookup"><span data-stu-id="b8527-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="b8527-147">nem menos do que`null`</span><span class="sxs-lookup"><span data-stu-id="b8527-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="b8527-148">Para o [operador](../operators/equality-operators.md#equality-operator-) `==`da igualdade , se `null`ambos os `true`operands são , o `null`resultado é `false`, se apenas um dos operands é , o resultado é ; caso contrário, os valores contidos de operands são comparados.</span><span class="sxs-lookup"><span data-stu-id="b8527-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="b8527-149">Para o [operador](../operators/equality-operators.md#inequality-operator-) `!=`da desigualdade , se `null`ambos os `false`operands são , o `null`resultado é `true`, se apenas um dos operands é , o resultado é ; caso contrário, os valores contidos de operands são comparados.</span><span class="sxs-lookup"><span data-stu-id="b8527-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="b8527-150">Se existir uma [conversão definida pelo usuário](../operators/user-defined-conversion-operators.md) entre dois tipos de valor, a mesma conversão também pode ser usada entre os tipos de valor anulados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b8527-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="b8527-151">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="b8527-151">Boxing and unboxing</span></span>

<span data-ttu-id="b8527-152">Uma instância de um `T?` tipo de valor anulado é [encaixotada](../../programming-guide/types/boxing-and-unboxing.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b8527-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="b8527-153">Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.</span><span class="sxs-lookup"><span data-stu-id="b8527-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="b8527-154">Se <xref:System.Nullable%601.HasValue%2A> `true`as devoluções, o valor `T` correspondente do tipo de <xref:System.Nullable%601>valor subjacente é encaixotado, não a instância de .</span><span class="sxs-lookup"><span data-stu-id="b8527-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="b8527-155">Você pode desembaficar um `T` valor em caixa de `T?`um tipo de valor para o tipo de valor anulado correspondente, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8527-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="b8527-156">Como identificar um tipo de valor anulado</span><span class="sxs-lookup"><span data-stu-id="b8527-156">How to identify a nullable value type</span></span>

<span data-ttu-id="b8527-157">O exemplo a seguir mostra <xref:System.Type?displayProperty=nameWithType> como determinar se uma instância representa um <xref:System.Nullable%601?displayProperty=nameWithType> tipo de valor anulado `T`construído, ou seja, o tipo com um parâmetro de tipo especificado:</span><span class="sxs-lookup"><span data-stu-id="b8527-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="b8527-158">Como o exemplo mostra, você usa o <xref:System.Type?displayProperty=nameWithType> [tipode](../operators/type-testing-and-cast.md#typeof-operator) operador para criar uma instância.</span><span class="sxs-lookup"><span data-stu-id="b8527-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="b8527-159">Se você quiser determinar se uma instância é de um tipo <xref:System.Object.GetType%2A?displayProperty=nameWithType> de valor <xref:System.Type> anulado, não use o método para obter uma instância a ser testada com o código anterior.</span><span class="sxs-lookup"><span data-stu-id="b8527-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="b8527-160">Quando você <xref:System.Object.GetType%2A?displayProperty=nameWithType> chama o método em uma instância de um tipo <xref:System.Object>de valor anulado, a instância é [encaixotada](#boxing-and-unboxing) em .</span><span class="sxs-lookup"><span data-stu-id="b8527-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="b8527-161">Como o boxe de uma instância não nula de um tipo de valor <xref:System.Object.GetType%2A> nulo <xref:System.Type> é equivalente ao boxe de um valor do tipo subjacente, retorna uma instância que representa o tipo subjacente de um tipo de valor nulo:</span><span class="sxs-lookup"><span data-stu-id="b8527-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

<span data-ttu-id="b8527-162">Além disso, não use o [operador do is](../operators/type-testing-and-cast.md#is-operator) para determinar se uma instância é de um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="b8527-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="b8527-163">Como o exemplo a seguir mostra, você não pode distinguir tipos de `is` uma instância de tipo de valor anulada e sua instância de tipo subjacente com o operador:</span><span class="sxs-lookup"><span data-stu-id="b8527-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="b8527-164">Você pode usar o código apresentado no exemplo a seguir para determinar se uma instância é de um tipo de valor anulado:</span><span class="sxs-lookup"><span data-stu-id="b8527-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="b8527-165">Os métodos descritos nesta seção não são aplicáveis no caso de tipos de [referência anulados](nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b8527-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b8527-166">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b8527-166">C# language specification</span></span>

<span data-ttu-id="b8527-167">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b8527-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b8527-168">Tipos anulados</span><span class="sxs-lookup"><span data-stu-id="b8527-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="b8527-169">Operadores suspensos</span><span class="sxs-lookup"><span data-stu-id="b8527-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="b8527-170">Conversões anuladas implícitas</span><span class="sxs-lookup"><span data-stu-id="b8527-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="b8527-171">Conversões anuladas explícitas</span><span class="sxs-lookup"><span data-stu-id="b8527-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="b8527-172">Operadores de conversão levantados</span><span class="sxs-lookup"><span data-stu-id="b8527-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="b8527-173">Confira também</span><span class="sxs-lookup"><span data-stu-id="b8527-173">See also</span></span>

- [<span data-ttu-id="b8527-174">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="b8527-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b8527-175">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="b8527-175">What exactly does 'lifted' mean?</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b8527-176">Tipos de referência anuláveis</span><span class="sxs-lookup"><span data-stu-id="b8527-176">Nullable reference types</span></span>](nullable-reference-types.md)

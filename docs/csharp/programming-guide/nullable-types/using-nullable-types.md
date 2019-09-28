---
title: Usando tipos de valor Anulável C# -guia de programação
ms.custom: seodec18
description: Saiba como trabalhar com tipos C# de valor anulável
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396169"
---
# <a name="using-nullable-value-types-c-programming-guide"></a><span data-ttu-id="727dc-103">Usando tipos de valor AnulávelC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="727dc-103">Using nullable value types (C# Programming Guide)</span></span>

<span data-ttu-id="727dc-104">Tipos de valor anulável são tipos que representam todos os valores de um tipo de valor subjacente `T` e um valor [nulo](../../language-reference/keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="727dc-104">Nullable value types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="727dc-105">Para obter mais informações, consulte o tópico [tipos de valor anulável](index.md) .</span><span class="sxs-lookup"><span data-stu-id="727dc-105">For more information, see the [Nullable value types](index.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="727dc-106">C#8,0 apresenta o recurso de tipos de referência anulável.</span><span class="sxs-lookup"><span data-stu-id="727dc-106">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="727dc-107">Para obter mais informações, consulte [tipos de referência anuláveis](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="727dc-107">For more information, see [Nullable reference types](../../nullable-references.md).</span></span> <span data-ttu-id="727dc-108">Os tipos de valor anulável estão disponíveis a C# partir de 2.</span><span class="sxs-lookup"><span data-stu-id="727dc-108">The nullable value types are available starting with C# 2.</span></span>

<span data-ttu-id="727dc-109">Você pode se referir a um tipo de valor anulável em qualquer um dos seguintes formulários intercambiáveis: `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="727dc-109">You can refer to a nullable value type in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="727dc-110">`T` deve ser um tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="727dc-110">`T` must be a value type.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="727dc-111">Declaração e atribuição</span><span class="sxs-lookup"><span data-stu-id="727dc-111">Declaration and assignment</span></span>

<span data-ttu-id="727dc-112">Como um tipo de valor pode ser convertido implicitamente no tipo de valor anulável correspondente, você atribui um valor a um tipo anulável como você faria para o tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="727dc-112">As a value type can be implicitly converted to the corresponding nullable value type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="727dc-113">Você também pode atribuir o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="727dc-113">You also can assign the `null` value.</span></span> <span data-ttu-id="727dc-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="727dc-114">For example:</span></span>

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="727dc-115">Exame de um valor de tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="727dc-115">Examination of a nullable type value</span></span>

<span data-ttu-id="727dc-116">Use as seguintes propriedades ReadOnly para examinar uma instância de um tipo de valor anulável para NULL e recuperar um valor de um tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="727dc-116">Use the following readonly properties to examine an instance of a nullable value type for null and retrieve a value of an underlying type:</span></span>

- <span data-ttu-id="727dc-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Indica se uma instância de um tipo que permite valor nulo tem um valor de seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="727dc-117"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>

- <span data-ttu-id="727dc-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="727dc-118"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="727dc-119">Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="727dc-119">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="727dc-120">O código no exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:</span><span class="sxs-lookup"><span data-stu-id="727dc-120">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

<span data-ttu-id="727dc-121">Você também pode comparar uma variável de um tipo de valor anulável com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="727dc-121">You also can compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="727dc-122">A partir C# do 7,0, você pode usar a [correspondência de padrões](../../pattern-matching.md) para examinar e obter um valor de um tipo de valor anulável:</span><span class="sxs-lookup"><span data-stu-id="727dc-122">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable value type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="727dc-123">Conversão de um tipo de valor anulável para um tipo subjacente</span><span class="sxs-lookup"><span data-stu-id="727dc-123">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="727dc-124">Se você precisar atribuir um valor de um tipo de valor anulável a um tipo não anulável, use o [operador de União nula `??`](../../language-reference/operators/null-coalescing-operator.md) para especificar o valor a ser atribuído se um valor de um tipo de valor anulável for nulo (você também poderá usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para fazer isso) :</span><span class="sxs-lookup"><span data-stu-id="727dc-124">If you need to assign a value of a nullable value type to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a value of a nullable value type is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="727dc-125">Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de um tipo de valor anulável for `null` deve ser o valor padrão do tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="727dc-125">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a value of a nullable value type is `null` should be the default value of the underlying value type.</span></span>

<span data-ttu-id="727dc-126">Você pode converter explicitamente um tipo de valor anulável em um tipo não anulável.</span><span class="sxs-lookup"><span data-stu-id="727dc-126">You can explicitly cast a nullable value type to a non-nullable type.</span></span> <span data-ttu-id="727dc-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="727dc-127">For example:</span></span>

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="727dc-128">Em tempo de execução, se o valor de um tipo de valor anulável for `null`, a conversão explícita lançará um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="727dc-128">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="727dc-129">Um tipo de valor que não permite valor nulo é convertido implicitamente no tipo que permite valor nulo correspondente.</span><span class="sxs-lookup"><span data-stu-id="727dc-129">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>

## <a name="operators"></a><span data-ttu-id="727dc-130">Operadores</span><span class="sxs-lookup"><span data-stu-id="727dc-130">Operators</span></span>

<span data-ttu-id="727dc-131">Os operadores unários e binários predefinidos e quaisquer operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos anuláveis correspondentes.</span><span class="sxs-lookup"><span data-stu-id="727dc-131">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by corresponding nullable types.</span></span> <span data-ttu-id="727dc-132">Esses operadores produzem `null` se um ou ambos os operandos forem `null`; caso contrário, o operador usará os valores contidos para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="727dc-132">These operators produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="727dc-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="727dc-133">For example:</span></span>

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="727dc-134">Para o tipo `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nesta seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo que um dos operandos seja `null`.</span><span class="sxs-lookup"><span data-stu-id="727dc-134">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="727dc-135">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../../language-reference/operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="727dc-135">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="727dc-136">Para os operadores relacionais (`<`, `>`, `<=`, `>=`), se um ou ambos os operandos forem `null`, o resultado será `false`.</span><span class="sxs-lookup"><span data-stu-id="727dc-136">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are `null`, the result is `false`.</span></span> <span data-ttu-id="727dc-137">Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="727dc-137">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="727dc-138">O exemplo a seguir mostra que 10</span><span class="sxs-lookup"><span data-stu-id="727dc-138">The following example shows that 10 is</span></span>

- <span data-ttu-id="727dc-139">Nem maior ou igual a `null`,</span><span class="sxs-lookup"><span data-stu-id="727dc-139">neither greater than or equal to `null`,</span></span>
- <span data-ttu-id="727dc-140">Nem menor que `null`.</span><span class="sxs-lookup"><span data-stu-id="727dc-140">nor less than `null`.</span></span>

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

<span data-ttu-id="727dc-141">O exemplo acima também mostra que uma comparação de igualdade de dois tipos de valores anuláveis nulos é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="727dc-141">The above example also shows that an equality comparison of two nullable value types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="727dc-142">Para obter mais informações, confira a seção [Operadores suspensos](~/_csharplang/spec/expressions.md#lifted-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="727dc-142">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="727dc-143">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="727dc-143">Boxing and unboxing</span></span>

<span data-ttu-id="727dc-144">Um tipo de valor que permite valor nulo passa pela [conversão boxing](../types/boxing-and-unboxing.md) por meio das seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="727dc-144">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="727dc-145">Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.</span><span class="sxs-lookup"><span data-stu-id="727dc-145">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="727dc-146">Se <xref:System.Nullable%601.HasValue%2A> retorna `true`, um valor do tipo de valor subjacente `T` passa pela conversão boxing, não a instância de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="727dc-146">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="727dc-147">Você pode aplicar a conversão unboxing no tipo de valor que passou pela conversão boxing convertendo-a no tipo que permite valor nulo correspondente, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="727dc-147">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="727dc-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="727dc-148">See also</span></span>

- [<span data-ttu-id="727dc-149">Tipos de valor anuláveis</span><span class="sxs-lookup"><span data-stu-id="727dc-149">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="727dc-150">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="727dc-150">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)

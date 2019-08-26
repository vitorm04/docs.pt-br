---
title: Uso de tipos que permitem valor nulo – Guia de programação em C#
ms.custom: seodec18
description: Saiba como trabalhar com tipos que permitem valor nulo do C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588825"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="7c2e7-103">Usando tipos que permitem valor nulo (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="7c2e7-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="7c2e7-104">Os tipos que permitem valor nulo representam todos os valores de um tipo de valor subjacente `T` e um valor [null](../../language-reference/keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="7c2e7-105">Para obter mais informações, confira o tópico [Tipos que permitem valor nulo](index.md).</span><span class="sxs-lookup"><span data-stu-id="7c2e7-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="7c2e7-106">Você pode se referir a um tipo que permite valor nulo de uma destas formas: `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="7c2e7-107">Essas duas formas são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="7c2e7-108">Declaração e atribuição</span><span class="sxs-lookup"><span data-stu-id="7c2e7-108">Declaration and assignment</span></span>

<span data-ttu-id="7c2e7-109">Como um tipo de valor pode ser convertido implicitamente no tipo que permite valor nulo correspondente, você pode atribuir um valor a um tipo que permite valor nulo como faria para seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="7c2e7-110">Você também pode atribuir o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="7c2e7-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="7c2e7-112">Exame de um valor de tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="7c2e7-112">Examination of a nullable type value</span></span>

<span data-ttu-id="7c2e7-113">Use as seguintes propriedades readonly para examinar se uma instância de um tipo que permite valor nulo é nula e recuperar um valor de um tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="7c2e7-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Indica se uma instância de um tipo que permite valor nulo tem um valor de seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="7c2e7-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="7c2e7-116">Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="7c2e7-117">O código no exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="7c2e7-118">Você também pode comparar uma variável de tipo que permite valor nulo com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="7c2e7-119">Começando no C# 7.0, você pode usar [correspondência de padrões](../../pattern-matching.md) tanto examinar e obter um valor de um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="7c2e7-120">Conversão de um tipo que permite valor nulo em um tipo subjacente</span><span class="sxs-lookup"><span data-stu-id="7c2e7-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="7c2e7-121">Se você precisar atribuir um valor de tipo que permite valor nulo a um tipo que não permite valor nulo, use o [operador de união nula `??`](../../language-reference/operators/null-coalescing-operator.md) para especificar o valor a ser atribuído quando um valor de tipo que permite valor nulo for nulo (você também poderá usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para fazer isso):</span><span class="sxs-lookup"><span data-stu-id="7c2e7-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="7c2e7-122">Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo é nulo deve ser o valor padrão do tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="7c2e7-123">Você pode converter explicitamente um tipo que permite valor nulo em um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="7c2e7-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="7c2e7-125">No tempo de execução, quando o valor de um tipo que permite valor nulo é nulo, a conversão explícita gera um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="7c2e7-126">Um tipo de valor que não permite valor nulo é convertido implicitamente no tipo que permite valor nulo correspondente.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="7c2e7-127">Operadores</span><span class="sxs-lookup"><span data-stu-id="7c2e7-127">Operators</span></span>

<span data-ttu-id="7c2e7-128">Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="7c2e7-129">Esses operadores produzem um valor nulo quando um ou ambos os operandos são nulos. Caso contrário, o operador usa os valores contidos para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="7c2e7-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> <span data-ttu-id="7c2e7-131">Para o tipo `bool?`, os operadores predefinidos `&` e `|` não seguem as regras descritas nessa seção: o resultado de uma avaliação de operador pode ser não nulo, mesmo quando um dos operandos é nulo.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-131">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span> <span data-ttu-id="7c2e7-132">Para obter mais informações, confira a seção [Operadores lógicos booleanos anuláveis](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) do artigo [Operadores lógicos boolianos](../../language-reference/operators/boolean-logical-operators.md).</span><span class="sxs-lookup"><span data-stu-id="7c2e7-132">For more information, see the [Nullable Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../../language-reference/operators/boolean-logical-operators.md) article.</span></span>
  
<span data-ttu-id="7c2e7-133">Para os operadores relacionais (`<`, `>`, `<=` e `>=`), quando um ou ambos os operandos são nulos, o resultado é `false`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-133">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="7c2e7-134">Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-134">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="7c2e7-135">O exemplo a seguir mostra que 10</span><span class="sxs-lookup"><span data-stu-id="7c2e7-135">The following example shows that 10 is</span></span>

- <span data-ttu-id="7c2e7-136">não é maior nem igual a nulo,</span><span class="sxs-lookup"><span data-stu-id="7c2e7-136">neither greater than or equal to null,</span></span>
- <span data-ttu-id="7c2e7-137">nem menor que nulo.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-137">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="7c2e7-138">O exemplo acima também mostra que uma comparação de igualdade de dois tipos que permitem valor nulo e são nulos é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-138">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

<span data-ttu-id="7c2e7-139">Para obter mais informações, confira a seção [Operadores suspensos](~/_csharplang/spec/expressions.md#lifted-operators) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7c2e7-139">For more information, see the [Lifted operators](~/_csharplang/spec/expressions.md#lifted-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="7c2e7-140">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="7c2e7-140">Boxing and unboxing</span></span>

<span data-ttu-id="7c2e7-141">Um tipo de valor que permite valor nulo passa pela [conversão boxing](../types/boxing-and-unboxing.md) por meio das seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-141">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="7c2e7-142">Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-142">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="7c2e7-143">Se <xref:System.Nullable%601.HasValue%2A> retorna `true`, um valor do tipo de valor subjacente `T` passa pela conversão boxing, não a instância de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="7c2e7-143">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="7c2e7-144">Você pode aplicar a conversão unboxing no tipo de valor que passou pela conversão boxing convertendo-a no tipo que permite valor nulo correspondente, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c2e7-144">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a><span data-ttu-id="7c2e7-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c2e7-145">See also</span></span>

- [<span data-ttu-id="7c2e7-146">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="7c2e7-146">Nullable types</span></span>](index.md)
- [<span data-ttu-id="7c2e7-147">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7c2e7-147">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c2e7-148">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="7c2e7-148">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)

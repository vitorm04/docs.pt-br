---
title: Uso de tipos que permitem valor nulo – Guia de programação em C#
ms.custom: seodec18
description: Saiba como trabalhar com tipos que permitem valor nulo do C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2c6f2f78ed71558b71adcc1d4d8cc9a6f459d75
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235209"
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="4bafb-103">Usando tipos que permitem valor nulo (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4bafb-103">Using nullable types (C# Programming Guide)</span></span>

<span data-ttu-id="4bafb-104">Os tipos que permitem valor nulo representam todos os valores de um tipo de valor subjacente `T` e um valor [null](../../language-reference/keywords/null.md) adicional.</span><span class="sxs-lookup"><span data-stu-id="4bafb-104">Nullable types are types that represent all the values of an underlying value type `T`, and an additional [null](../../language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="4bafb-105">Para obter mais informações, confira o tópico [Tipos que permitem valor nulo](index.md).</span><span class="sxs-lookup"><span data-stu-id="4bafb-105">For more information, see the [Nullable types](index.md) topic.</span></span>

<span data-ttu-id="4bafb-106">Você pode se referir a um tipo que permite valor nulo de uma destas formas: `Nullable<T>` ou `T?`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-106">You can refer to a nullable type in any of the following forms: `Nullable<T>` or `T?`.</span></span> <span data-ttu-id="4bafb-107">Essas duas formas são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="4bafb-107">These two forms are interchangeable.</span></span>  
  
## <a name="declaration-and-assignment"></a><span data-ttu-id="4bafb-108">Declaração e atribuição</span><span class="sxs-lookup"><span data-stu-id="4bafb-108">Declaration and assignment</span></span>

<span data-ttu-id="4bafb-109">Como um tipo de valor pode ser convertido implicitamente no tipo que permite valor nulo correspondente, você pode atribuir um valor a um tipo que permite valor nulo como faria para seu tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="4bafb-109">As a value type can be implicitly converted to the corresponding nullable type, you assign a value to a nullable type as you would for its underlying value type.</span></span> <span data-ttu-id="4bafb-110">Você também pode atribuir o valor `null`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-110">You also can assign the `null` value.</span></span>  <span data-ttu-id="4bafb-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4bafb-111">For example:</span></span>
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a><span data-ttu-id="4bafb-112">Exame de um valor de tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-112">Examination of a nullable type value</span></span>

<span data-ttu-id="4bafb-113">Use as seguintes propriedades readonly para examinar se uma instância de um tipo que permite valor nulo é nula e recuperar um valor de um tipo subjacente:</span><span class="sxs-lookup"><span data-stu-id="4bafb-113">Use the following readonly properties to examine an instance of a nullable type for null and retrieve a value of an underlying type:</span></span>  
  
- <span data-ttu-id="4bafb-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Indica se uma instância de um tipo que permite valor nulo tem um valor de seu tipo subjacente.</span><span class="sxs-lookup"><span data-stu-id="4bafb-114"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable type has a value of its underlying type.</span></span>
  
- <span data-ttu-id="4bafb-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtém o valor de um tipo subjacente quando <xref:System.Nullable%601.HasValue%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-115"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="4bafb-116">Quando <xref:System.Nullable%601.HasValue%2A> é `false`, a propriedade <xref:System.Nullable%601.Value%2A> gera uma <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-116">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>
  
<span data-ttu-id="4bafb-117">O código no exemplo a seguir usa a propriedade `HasValue` para testar se a variável contém um valor antes de exibi-lo:</span><span class="sxs-lookup"><span data-stu-id="4bafb-117">The code in the following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
<span data-ttu-id="4bafb-118">Você também pode comparar uma variável de tipo que permite valor nulo com `null` em vez de usar a propriedade `HasValue`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4bafb-118">You also can compare a nullable type variable with `null` instead of using the `HasValue` property, as the following example shows:</span></span>  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

<span data-ttu-id="4bafb-119">Começando no C# 7.0, você pode usar [correspondência de padrões](../../pattern-matching.md) tanto examinar e obter um valor de um tipo que permite valor nulo:</span><span class="sxs-lookup"><span data-stu-id="4bafb-119">Beginning with C# 7.0, you can use [pattern matching](../../pattern-matching.md) to both examine and get a value of a nullable type:</span></span>

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a><span data-ttu-id="4bafb-120">Conversão de um tipo que permite valor nulo em um tipo subjacente</span><span class="sxs-lookup"><span data-stu-id="4bafb-120">Conversion from a nullable type to an underlying type</span></span>

<span data-ttu-id="4bafb-121">Se você precisar atribuir um valor de tipo que permite valor nulo a um tipo que não permite valor nulo, use o [operador de união nula `??`](../../language-reference/operators/null-coalescing-operator.md) para especificar o valor a ser atribuído quando um valor de tipo que permite valor nulo for nulo (você também poderá usar o método <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> para fazer isso):</span><span class="sxs-lookup"><span data-stu-id="4bafb-121">If you need to assign a nullable type value to a non-nullable type, use the [null-coalescing operator `??`](../../language-reference/operators/null-coalescing-operator.md) to specify the value to be assigned if a nullable type value is null (you also can use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method to do that):</span></span>
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

<span data-ttu-id="4bafb-122">Use o método <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> se o valor a ser usado quando um valor de tipo que permite valor nulo é nulo deve ser o valor padrão do tipo de valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="4bafb-122">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is null should be the default value of the underlying value type.</span></span>
  
<span data-ttu-id="4bafb-123">Você pode converter explicitamente um tipo que permite valor nulo em um tipo que não permite valor nulo.</span><span class="sxs-lookup"><span data-stu-id="4bafb-123">You can explicitly cast a nullable type to a non-nullable type.</span></span> <span data-ttu-id="4bafb-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4bafb-124">For example:</span></span>  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

<span data-ttu-id="4bafb-125">No tempo de execução, quando o valor de um tipo que permite valor nulo é nulo, a conversão explícita gera um <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-125">At run time, if the value of a nullable type is null, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="4bafb-126">Um tipo de valor que não permite valor nulo é convertido implicitamente no tipo que permite valor nulo correspondente.</span><span class="sxs-lookup"><span data-stu-id="4bafb-126">A non-nullable value type is implicitly converted to the corresponding nullable type.</span></span>
  
## <a name="operators"></a><span data-ttu-id="4bafb-127">Operadores</span><span class="sxs-lookup"><span data-stu-id="4bafb-127">Operators</span></span>

<span data-ttu-id="4bafb-128">Os operadores unários e binários predefinidos e os operadores definidos pelo usuário que existem para tipos de valor também podem ser usados por tipos que permitem valor nulo.</span><span class="sxs-lookup"><span data-stu-id="4bafb-128">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="4bafb-129">Esses operadores produzem um valor nulo quando um ou ambos os operandos são nulos. Caso contrário, o operador usa os valores contidos para calcular o resultado.</span><span class="sxs-lookup"><span data-stu-id="4bafb-129">These operators produce a null value if one or both operands are null; otherwise, the operator uses the contained values to calculate the result.</span></span> <span data-ttu-id="4bafb-130">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4bafb-130">For example:</span></span>  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
<span data-ttu-id="4bafb-131">Para os operadores relacionais (`<`, `>`, `<=` e `>=`), quando um ou ambos os operandos são nulos, o resultado é `false`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-131">For the relational operators (`<`, `>`, `<=`, `>=`), if one or both operands are null, the result is `false`.</span></span> <span data-ttu-id="4bafb-132">Não presuma que como uma comparação (por exemplo, `<=`) retorna `false`, a comparação oposta (`>`) retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-132">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="4bafb-133">O exemplo a seguir mostra que 10</span><span class="sxs-lookup"><span data-stu-id="4bafb-133">The following example shows that 10 is</span></span>

- <span data-ttu-id="4bafb-134">não é maior nem igual a nulo,</span><span class="sxs-lookup"><span data-stu-id="4bafb-134">neither greater than or equal to null,</span></span>
- <span data-ttu-id="4bafb-135">nem menor que nulo.</span><span class="sxs-lookup"><span data-stu-id="4bafb-135">nor less than null.</span></span>
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
<span data-ttu-id="4bafb-136">O exemplo acima também mostra que uma comparação de igualdade de dois tipos que permitem valor nulo e são nulos é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-136">The above example also shows that an equality comparison of two nullable types that are both null evaluates to `true`.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="4bafb-137">Conversões boxing e unboxing</span><span class="sxs-lookup"><span data-stu-id="4bafb-137">Boxing and unboxing</span></span>

<span data-ttu-id="4bafb-138">Um tipo de valor que permite valor nulo passa pela [conversão boxing](../types/boxing-and-unboxing.md) por meio das seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="4bafb-138">A nullable value type is [boxed](../types/boxing-and-unboxing.md) by the following rules:</span></span>

- <span data-ttu-id="4bafb-139">Se <xref:System.Nullable%601.HasValue%2A> retorna `false`, a referência nula é produzida.</span><span class="sxs-lookup"><span data-stu-id="4bafb-139">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>  
- <span data-ttu-id="4bafb-140">Se <xref:System.Nullable%601.HasValue%2A> retorna `true`, um valor do tipo de valor subjacente `T` passa pela conversão boxing, não a instância de <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-140">If <xref:System.Nullable%601.HasValue%2A> returns `true`, a value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="4bafb-141">Você pode aplicar a conversão unboxing no tipo de valor que passou pela conversão boxing convertendo-a no tipo que permite valor nulo correspondente, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4bafb-141">You can unbox the boxed value type to the corresponding nullable type, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a><span data-ttu-id="4bafb-142">O tipo bool?</span><span class="sxs-lookup"><span data-stu-id="4bafb-142">The bool? type</span></span>

<span data-ttu-id="4bafb-143">O tipo que permite valor nulo `bool?` pode conter três valores diferentes: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) e [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="4bafb-143">The `bool?` nullable type can contain three different values: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), and [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="4bafb-144">O tipo `bool?` é como o tipo de variável booliano que é usado em SQL.</span><span class="sxs-lookup"><span data-stu-id="4bafb-144">The `bool?` type is like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="4bafb-145">Para garantir que os resultados produzidos pelos operadores `&` e `|` são consistentes com o tipo booliano de três valores no SQL, os seguintes operadores predefinidos são fornecidos:</span><span class="sxs-lookup"><span data-stu-id="4bafb-145">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
<span data-ttu-id="4bafb-146">A semântica desses operadores é definida pela tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="4bafb-146">The semantics of these operators is defined by the following table:</span></span>  
  
|<span data-ttu-id="4bafb-147">x</span><span class="sxs-lookup"><span data-stu-id="4bafb-147">x</span></span>|<span data-ttu-id="4bafb-148">y</span><span class="sxs-lookup"><span data-stu-id="4bafb-148">y</span></span>|<span data-ttu-id="4bafb-149">x&y</span><span class="sxs-lookup"><span data-stu-id="4bafb-149">x&y</span></span>|<span data-ttu-id="4bafb-150">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="4bafb-150">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="4bafb-151">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-151">true</span></span>|<span data-ttu-id="4bafb-152">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-152">true</span></span>|<span data-ttu-id="4bafb-153">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-153">true</span></span>|<span data-ttu-id="4bafb-154">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-154">true</span></span>|  
|<span data-ttu-id="4bafb-155">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-155">true</span></span>|<span data-ttu-id="4bafb-156">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-156">false</span></span>|<span data-ttu-id="4bafb-157">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-157">false</span></span>|<span data-ttu-id="4bafb-158">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-158">true</span></span>|  
|<span data-ttu-id="4bafb-159">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-159">true</span></span>|<span data-ttu-id="4bafb-160">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-160">null</span></span>|<span data-ttu-id="4bafb-161">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-161">null</span></span>|<span data-ttu-id="4bafb-162">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-162">true</span></span>|  
|<span data-ttu-id="4bafb-163">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-163">false</span></span>|<span data-ttu-id="4bafb-164">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-164">true</span></span>|<span data-ttu-id="4bafb-165">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-165">false</span></span>|<span data-ttu-id="4bafb-166">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-166">true</span></span>|  
|<span data-ttu-id="4bafb-167">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-167">false</span></span>|<span data-ttu-id="4bafb-168">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-168">false</span></span>|<span data-ttu-id="4bafb-169">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-169">false</span></span>|<span data-ttu-id="4bafb-170">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-170">false</span></span>|  
|<span data-ttu-id="4bafb-171">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-171">false</span></span>|<span data-ttu-id="4bafb-172">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-172">null</span></span>|<span data-ttu-id="4bafb-173">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-173">false</span></span>|<span data-ttu-id="4bafb-174">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-174">null</span></span>|  
|<span data-ttu-id="4bafb-175">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-175">null</span></span>|<span data-ttu-id="4bafb-176">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-176">true</span></span>|<span data-ttu-id="4bafb-177">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-177">null</span></span>|<span data-ttu-id="4bafb-178">true</span><span class="sxs-lookup"><span data-stu-id="4bafb-178">true</span></span>|  
|<span data-ttu-id="4bafb-179">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-179">null</span></span>|<span data-ttu-id="4bafb-180">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-180">false</span></span>|<span data-ttu-id="4bafb-181">false</span><span class="sxs-lookup"><span data-stu-id="4bafb-181">false</span></span>|<span data-ttu-id="4bafb-182">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-182">null</span></span>|  
|<span data-ttu-id="4bafb-183">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-183">null</span></span>|<span data-ttu-id="4bafb-184">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-184">null</span></span>|<span data-ttu-id="4bafb-185">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-185">null</span></span>|<span data-ttu-id="4bafb-186">nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-186">null</span></span>|  

<span data-ttu-id="4bafb-187">Observe que esses dois operadores não seguem as regras descritas na seção [Operadores](#operators): o resultado de uma avaliação de operador pode ser não nulo, mesmo quando um dos operandos é nulo.</span><span class="sxs-lookup"><span data-stu-id="4bafb-187">Note that these two operators don't follow the rules described in the [Operators](#operators) section: the result of an operator evaluation can be non-null even if one of the operands is null.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4bafb-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bafb-188">See Also</span></span>

- [<span data-ttu-id="4bafb-189">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="4bafb-189">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="4bafb-190">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4bafb-190">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="4bafb-191">O que exatamente "levantado" significa?</span><span class="sxs-lookup"><span data-stu-id="4bafb-191">What exactly does 'lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  

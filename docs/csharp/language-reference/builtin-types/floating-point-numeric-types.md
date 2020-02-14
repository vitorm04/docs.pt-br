---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: 'Saiba mais sobre os tipos de C# ponto flutuante internos: float, Double e decimal'
ms.date: 02/10/2020
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 95b7f266654bbbcdcd0f81e3aa11cfc94af9f0e5
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215248"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="8b1f5-103">Tipos numéricos de ponto flutuante (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8b1f5-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="8b1f5-104">Os *tipos numéricos de ponto flutuante* representam números reais.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="8b1f5-105">Todos os tipos numéricos de ponto flutuante são [tipos de valor](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b1f5-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="8b1f5-106">Eles também são [tipos simples](value-types.md#built-in-value-types) e podem ser inicializados com [literais](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="8b1f5-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="8b1f5-107">Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="8b1f5-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="8b1f5-108">Características dos tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="8b1f5-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="8b1f5-109">O C# é compatível com os seguintes tipos de pontos flutuantes predefinidos:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="8b1f5-110">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="8b1f5-110">C# type/keyword</span></span>|<span data-ttu-id="8b1f5-111">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="8b1f5-111">Approximate range</span></span>|<span data-ttu-id="8b1f5-112">Precisão</span><span class="sxs-lookup"><span data-stu-id="8b1f5-112">Precision</span></span>|<span data-ttu-id="8b1f5-113">Tamanho</span><span class="sxs-lookup"><span data-stu-id="8b1f5-113">Size</span></span>|<span data-ttu-id="8b1f5-114">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8b1f5-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="8b1f5-115">±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="8b1f5-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="8b1f5-116">Aproximadamente de 6 a 9 dígitos</span><span class="sxs-lookup"><span data-stu-id="8b1f5-116">~6-9 digits</span></span>|<span data-ttu-id="8b1f5-117">4 bytes</span><span class="sxs-lookup"><span data-stu-id="8b1f5-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="8b1f5-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="8b1f5-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="8b1f5-119">~15 a 17 dígitos</span><span class="sxs-lookup"><span data-stu-id="8b1f5-119">~15-17 digits</span></span>|<span data-ttu-id="8b1f5-120">8 bytes</span><span class="sxs-lookup"><span data-stu-id="8b1f5-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="8b1f5-121">±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="8b1f5-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="8b1f5-122">28 a 29 dígitos</span><span class="sxs-lookup"><span data-stu-id="8b1f5-122">28-29 digits</span></span>|<span data-ttu-id="8b1f5-123">16 bytes</span><span class="sxs-lookup"><span data-stu-id="8b1f5-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="8b1f5-124">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="8b1f5-125">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-125">They are interchangeable.</span></span> <span data-ttu-id="8b1f5-126">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="8b1f5-127">O valor padrão de cada tipo de ponto flutuante é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="8b1f5-128">Cada um dos tipos de ponto flutuante possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="8b1f5-129">Os tipos `float` e `double` também fornecem constantes que representam valores não numéricos e infinitos.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="8b1f5-130">Por exemplo, o tipo `double` fornece as seguintes constantes: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> e <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8b1f5-131">Como o tipo `decimal` tem mais precisão e um intervalo menor que `float` e `double`, ele é apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-131">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="8b1f5-132">Você pode misturar tipos [integrais](integral-numeric-types.md) e os tipos `float` e `double` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-132">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="8b1f5-133">Nesse caso, os tipos integrais são convertidos implicitamente em um dos tipos de ponto flutuante e, se necessário, o tipo de `float` é implicitamente convertido em `double`.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-133">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="8b1f5-134">A expressão é avaliada como segue:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-134">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="8b1f5-135">Se houver `double` tipo na expressão, a expressão será avaliada como `double`ou para [`bool`](bool.md) em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-135">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="8b1f5-136">Se não houver nenhum tipo de `double` na expressão, a expressão será avaliada como `float`ou para `bool` em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-136">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="8b1f5-137">Você também pode misturar tipos integrais e o tipo de `decimal` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-137">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="8b1f5-138">Nesse caso, os tipos integrais são convertidos implicitamente no tipo de `decimal` e a expressão é avaliada como `decimal`ou para `bool` em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-138">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="8b1f5-139">Não é possível misturar o tipo de `decimal` com os tipos `float` e `double` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-139">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="8b1f5-140">Nesse caso, se você quiser executar operações aritméticas, de comparação ou de igualdade, deverá converter explicitamente os operandos de ou para o tipo de `decimal`, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-140">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="8b1f5-141">É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-141">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="8b1f5-142">Literais reais</span><span class="sxs-lookup"><span data-stu-id="8b1f5-142">Real literals</span></span>

<span data-ttu-id="8b1f5-143">O tipo de um literal real é determinado pelo seu sufixo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-143">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="8b1f5-144">O literal sem sufixo ou com o sufixo `d` ou `D` é do tipo `double`</span><span class="sxs-lookup"><span data-stu-id="8b1f5-144">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="8b1f5-145">O literal com o sufixo `f` ou `F` é do tipo `float`</span><span class="sxs-lookup"><span data-stu-id="8b1f5-145">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="8b1f5-146">O literal com o sufixo `m` ou `M` é do tipo `decimal`</span><span class="sxs-lookup"><span data-stu-id="8b1f5-146">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="8b1f5-147">O código a seguir demonstra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-147">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="8b1f5-148">O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-148">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="8b1f5-149">Você pode usar o separador de dígitos com todos os tipos de literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-149">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="8b1f5-150">Você também pode usar a notação científica, ou seja, especificar uma parte exponencial de um literal real, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="8b1f5-150">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="8b1f5-151">Conversões</span><span class="sxs-lookup"><span data-stu-id="8b1f5-151">Conversions</span></span>

<span data-ttu-id="8b1f5-152">Há apenas uma conversão implícita entre tipos numéricos de ponto flutuante: de `float` para `double`.</span><span class="sxs-lookup"><span data-stu-id="8b1f5-152">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="8b1f5-153">No entanto, você pode converter qualquer tipo de ponto flutuante para qualquer outro tipo de ponto flutuante com a [conversão explícita](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="8b1f5-153">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="8b1f5-154">Para obter mais informações, consulte [conversões numéricas internas](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8b1f5-154">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8b1f5-155">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8b1f5-155">C# language specification</span></span>

<span data-ttu-id="8b1f5-156">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="8b1f5-156">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="8b1f5-157">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="8b1f5-157">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="8b1f5-158">O tipo decimal</span><span class="sxs-lookup"><span data-stu-id="8b1f5-158">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="8b1f5-159">Literais reais</span><span class="sxs-lookup"><span data-stu-id="8b1f5-159">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="8b1f5-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b1f5-160">See also</span></span>

- [<span data-ttu-id="8b1f5-161">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8b1f5-161">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8b1f5-162">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="8b1f5-162">Value types</span></span>](value-types.md)
- [<span data-ttu-id="8b1f5-163">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="8b1f5-163">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="8b1f5-164">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="8b1f5-164">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="8b1f5-165">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="8b1f5-165">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>

---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: Visão geral sobre os tipos de ponto flutuante internos do C#
ms.date: 10/22/2019
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
ms.openlocfilehash: 4d71f7eea3f574e483dc4250f5c87e1ffd551f2f
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771900"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="83ea6-103">Tipos numéricos de ponto flutuante (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="83ea6-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="83ea6-104">Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="83ea6-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="83ea6-105">Todos os tipos de ponto flutuante também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="83ea6-105">All floating-point types are also value types.</span></span> <span data-ttu-id="83ea6-106">Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="83ea6-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="83ea6-107">Características dos tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="83ea6-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="83ea6-108">O C# é compatível com os seguintes tipos de pontos flutuantes predefinidos:</span><span class="sxs-lookup"><span data-stu-id="83ea6-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="83ea6-109">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="83ea6-109">C# type/keyword</span></span>|<span data-ttu-id="83ea6-110">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="83ea6-110">Approximate range</span></span>|<span data-ttu-id="83ea6-111">Precisão</span><span class="sxs-lookup"><span data-stu-id="83ea6-111">Precision</span></span>|<span data-ttu-id="83ea6-112">Tamanho</span><span class="sxs-lookup"><span data-stu-id="83ea6-112">Size</span></span>|<span data-ttu-id="83ea6-113">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="83ea6-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="83ea6-114">±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="83ea6-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="83ea6-115">~6 a 9 dígitos</span><span class="sxs-lookup"><span data-stu-id="83ea6-115">~6-9 digits</span></span>|<span data-ttu-id="83ea6-116">4 bytes</span><span class="sxs-lookup"><span data-stu-id="83ea6-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="83ea6-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="83ea6-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="83ea6-118">~15 a 17 dígitos</span><span class="sxs-lookup"><span data-stu-id="83ea6-118">~15-17 digits</span></span>|<span data-ttu-id="83ea6-119">8 bytes</span><span class="sxs-lookup"><span data-stu-id="83ea6-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="83ea6-120">±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="83ea6-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="83ea6-121">28 a 29 dígitos</span><span class="sxs-lookup"><span data-stu-id="83ea6-121">28-29 digits</span></span>|<span data-ttu-id="83ea6-122">16 bytes</span><span class="sxs-lookup"><span data-stu-id="83ea6-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="83ea6-123">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="83ea6-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="83ea6-124">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="83ea6-124">They are interchangeable.</span></span> <span data-ttu-id="83ea6-125">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="83ea6-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="83ea6-126">O valor padrão de cada tipo de ponto flutuante é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="83ea6-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="83ea6-127">Cada um dos tipos de ponto flutuante possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="83ea6-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="83ea6-128">Os tipos `float` e `double` também fornecem constantes que representam valores não numéricos e infinitos.</span><span class="sxs-lookup"><span data-stu-id="83ea6-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="83ea6-129">Por exemplo, o tipo `double` fornece as seguintes constantes: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> e <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83ea6-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="83ea6-130">Como o tipo `decimal` tem mais precisão e um intervalo menor que `float` e `double`, ele é apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="83ea6-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="83ea6-131">É possível misturar tipos [integrais](integral-numeric-types.md) e de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="83ea6-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="83ea6-132">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83ea6-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="83ea6-133">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="83ea6-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="83ea6-134">Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="83ea6-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="83ea6-135">Se não houver nenhum tipo de `double` na expressão, a expressão será avaliada como `float` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="83ea6-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="83ea6-136">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="83ea6-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="83ea6-137">Zero positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="83ea6-137">Positive and negative zero</span></span>
- <span data-ttu-id="83ea6-138">Infinito positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="83ea6-138">Positive and negative infinity</span></span>
- <span data-ttu-id="83ea6-139">Valor NaN (não é um número)</span><span class="sxs-lookup"><span data-stu-id="83ea6-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="83ea6-140">O conjunto finito de valores diferentes de zero</span><span class="sxs-lookup"><span data-stu-id="83ea6-140">The finite set of nonzero values</span></span>

<span data-ttu-id="83ea6-141">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="83ea6-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="83ea6-142">É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="83ea6-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="83ea6-143">Literais reais</span><span class="sxs-lookup"><span data-stu-id="83ea6-143">Real literals</span></span>

<span data-ttu-id="83ea6-144">O tipo de um literal real é determinado pelo seu sufixo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="83ea6-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="83ea6-145">O literal sem sufixo ou com o sufixo `d` ou `D` é do tipo `double`</span><span class="sxs-lookup"><span data-stu-id="83ea6-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="83ea6-146">O literal com o sufixo `f` ou `F` é do tipo `float`</span><span class="sxs-lookup"><span data-stu-id="83ea6-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="83ea6-147">O literal com o sufixo `m` ou `M` é do tipo `decimal`</span><span class="sxs-lookup"><span data-stu-id="83ea6-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="83ea6-148">O código a seguir demonstra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="83ea6-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="83ea6-149">O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="83ea6-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="83ea6-150">Você pode usar o separador de dígitos com todos os tipos de literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="83ea6-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="83ea6-151">Você também pode usar a notação científica, ou seja, especificar uma parte exponencial de um literal real, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="83ea6-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="83ea6-152">Conversões</span><span class="sxs-lookup"><span data-stu-id="83ea6-152">Conversions</span></span>

<span data-ttu-id="83ea6-153">Há apenas uma conversão implícita entre tipos numéricos de ponto flutuante: de `float` para `double`.</span><span class="sxs-lookup"><span data-stu-id="83ea6-153">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="83ea6-154">No entanto, você pode converter qualquer tipo de ponto flutuante para qualquer outro tipo de ponto flutuante com a [conversão explícita](../operators/type-testing-and-cast.md#cast-operator-).</span><span class="sxs-lookup"><span data-stu-id="83ea6-154">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-operator-).</span></span> <span data-ttu-id="83ea6-155">Para obter mais informações, consulte [conversões numéricas internas](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="83ea6-155">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83ea6-156">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="83ea6-156">C# language specification</span></span>

<span data-ttu-id="83ea6-157">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="83ea6-157">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="83ea6-158">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="83ea6-158">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="83ea6-159">O tipo decimal</span><span class="sxs-lookup"><span data-stu-id="83ea6-159">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="83ea6-160">Literais reais</span><span class="sxs-lookup"><span data-stu-id="83ea6-160">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="83ea6-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83ea6-161">See also</span></span>

- [<span data-ttu-id="83ea6-162">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="83ea6-162">C# reference</span></span>](../index.md)
- [<span data-ttu-id="83ea6-163">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="83ea6-163">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="83ea6-164">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="83ea6-164">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="83ea6-165">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="83ea6-165">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="83ea6-166">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="83ea6-166">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="83ea6-167">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="83ea6-167">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>

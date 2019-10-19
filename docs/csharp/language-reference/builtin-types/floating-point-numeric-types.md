---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: Visão geral sobre os tipos de ponto flutuante internos do C#
ms.date: 10/18/2019
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
ms.openlocfilehash: fa6cbb869d90113414cc6f8ffe231386c3596b1d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579379"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="b53a7-103">Tipos numéricos de ponto flutuante (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b53a7-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="b53a7-104">Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#real-literals).</span><span class="sxs-lookup"><span data-stu-id="b53a7-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#real-literals).</span></span> <span data-ttu-id="b53a7-105">Todos os tipos de ponto flutuante também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="b53a7-105">All floating-point types are also value types.</span></span> <span data-ttu-id="b53a7-106">Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="b53a7-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="b53a7-107">Características dos tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="b53a7-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="b53a7-108">O C# é compatível com os seguintes tipos de pontos flutuantes predefinidos:</span><span class="sxs-lookup"><span data-stu-id="b53a7-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="b53a7-109">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="b53a7-109">C# type/keyword</span></span>|<span data-ttu-id="b53a7-110">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="b53a7-110">Approximate range</span></span>|<span data-ttu-id="b53a7-111">Precisão</span><span class="sxs-lookup"><span data-stu-id="b53a7-111">Precision</span></span>|<span data-ttu-id="b53a7-112">Tamanho</span><span class="sxs-lookup"><span data-stu-id="b53a7-112">Size</span></span>|<span data-ttu-id="b53a7-113">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="b53a7-113">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="b53a7-114">±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="b53a7-114">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="b53a7-115">~6 a 9 dígitos</span><span class="sxs-lookup"><span data-stu-id="b53a7-115">~6-9 digits</span></span>|<span data-ttu-id="b53a7-116">4 bytes</span><span class="sxs-lookup"><span data-stu-id="b53a7-116">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="b53a7-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="b53a7-117">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="b53a7-118">~15 a 17 dígitos</span><span class="sxs-lookup"><span data-stu-id="b53a7-118">~15-17 digits</span></span>|<span data-ttu-id="b53a7-119">8 bytes</span><span class="sxs-lookup"><span data-stu-id="b53a7-119">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="b53a7-120">±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="b53a7-120">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="b53a7-121">28 a 29 dígitos</span><span class="sxs-lookup"><span data-stu-id="b53a7-121">28-29 digits</span></span>|<span data-ttu-id="b53a7-122">16 bytes</span><span class="sxs-lookup"><span data-stu-id="b53a7-122">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="b53a7-123">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="b53a7-123">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="b53a7-124">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="b53a7-124">They are interchangeable.</span></span> <span data-ttu-id="b53a7-125">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="b53a7-125">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="b53a7-126">O valor padrão de cada tipo de ponto flutuante é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="b53a7-126">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="b53a7-127">Cada um dos tipos de ponto flutuante possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="b53a7-127">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="b53a7-128">Os tipos `float` e `double` também fornecem constantes que representam valores não numéricos e infinitos.</span><span class="sxs-lookup"><span data-stu-id="b53a7-128">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="b53a7-129">Por exemplo, o tipo `double` fornece as seguintes constantes: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> e <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b53a7-129">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b53a7-130">Como o tipo `decimal` tem mais precisão e um intervalo menor que `float` e `double`, ele é apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="b53a7-130">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="b53a7-131">É possível misturar tipos [integrais](integral-numeric-types.md) e de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="b53a7-131">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="b53a7-132">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="b53a7-132">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="b53a7-133">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="b53a7-133">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="b53a7-134">Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="b53a7-134">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="b53a7-135">Se não houver nenhum tipo de `double` na expressão, a expressão será avaliada como `float` ou [bool](../keywords/bool.md) em comparações relacionais e de igualdade.</span><span class="sxs-lookup"><span data-stu-id="b53a7-135">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational and equality comparisons.</span></span>

<span data-ttu-id="b53a7-136">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="b53a7-136">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="b53a7-137">Zero positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="b53a7-137">Positive and negative zero</span></span>
- <span data-ttu-id="b53a7-138">Infinito positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="b53a7-138">Positive and negative infinity</span></span>
- <span data-ttu-id="b53a7-139">Valor NaN (não é um número)</span><span class="sxs-lookup"><span data-stu-id="b53a7-139">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="b53a7-140">O conjunto finito de valores diferentes de zero</span><span class="sxs-lookup"><span data-stu-id="b53a7-140">The finite set of nonzero values</span></span>

<span data-ttu-id="b53a7-141">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="b53a7-141">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="b53a7-142">É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="b53a7-142">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="b53a7-143">Literais reais</span><span class="sxs-lookup"><span data-stu-id="b53a7-143">Real literals</span></span>

<span data-ttu-id="b53a7-144">O tipo de um literal real é determinado pelo seu sufixo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b53a7-144">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="b53a7-145">O literal sem sufixo ou com o sufixo `d` ou `D` é do tipo `double`</span><span class="sxs-lookup"><span data-stu-id="b53a7-145">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="b53a7-146">O literal com o sufixo `f` ou `F` é do tipo `float`</span><span class="sxs-lookup"><span data-stu-id="b53a7-146">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="b53a7-147">O literal com o sufixo `m` ou `M` é do tipo `decimal`</span><span class="sxs-lookup"><span data-stu-id="b53a7-147">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="b53a7-148">O código a seguir demonstra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="b53a7-148">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="b53a7-149">O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="b53a7-149">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="b53a7-150">Você pode usar o separador de dígitos com todos os tipos de literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="b53a7-150">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="b53a7-151">Você também pode usar a notação científica, ou seja, especificar uma parte exponencial de um literal real, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b53a7-151">You also can use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42;

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="b53a7-152">Conversões</span><span class="sxs-lookup"><span data-stu-id="b53a7-152">Conversions</span></span>

<span data-ttu-id="b53a7-153">Há uma conversão implícita (chamada de *conversão de expansão*) de `float` em `double` porque o intervalo dos valores `float` é um subconjunto adequado de `double` e não há perda de precisão de `float` para `double`.</span><span class="sxs-lookup"><span data-stu-id="b53a7-153">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="b53a7-154">É necessário usar uma conversão explícita para converter um tipo de ponto flutuante em outro quando uma conversão implícita não está definida do tipo de origem para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="b53a7-154">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="b53a7-155">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="b53a7-155">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="b53a7-156">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="b53a7-156">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="b53a7-157">Não há conversão implícita entre outros tipos de ponto flutuante e o tipo `decimal` porque o tipo `decimal` tem maior precisão do que `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="b53a7-157">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="b53a7-158">Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b53a7-158">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="b53a7-159">Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="b53a7-159">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b53a7-160">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b53a7-160">C# language specification</span></span>

<span data-ttu-id="b53a7-161">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="b53a7-161">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="b53a7-162">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="b53a7-162">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="b53a7-163">O tipo decimal</span><span class="sxs-lookup"><span data-stu-id="b53a7-163">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="b53a7-164">Literais reais</span><span class="sxs-lookup"><span data-stu-id="b53a7-164">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="b53a7-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b53a7-165">See also</span></span>

- [<span data-ttu-id="b53a7-166">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b53a7-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b53a7-167">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="b53a7-167">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="b53a7-168">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="b53a7-168">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="b53a7-169">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="b53a7-169">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="b53a7-170">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="b53a7-170">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="b53a7-171">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="b53a7-171">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="b53a7-172">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="b53a7-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)

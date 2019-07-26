---
title: Tipos numéricos de ponto flutuante – Referência de C#
description: Visão geral sobre os tipos de ponto flutuante internos do C#
ms.date: 06/30/2019
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
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: 0d97b3ffd587e8398e5572706a47937716a6e709
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236054"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="40d37-103">Tipos numéricos de ponto flutuante (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="40d37-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="40d37-104">Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="40d37-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="40d37-105">Todos os tipos de ponto flutuante também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="40d37-105">All floating-point types are also value types.</span></span> <span data-ttu-id="40d37-106">Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md) [de comparação e de igualdade](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="40d37-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="40d37-107">Características dos tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="40d37-107">Characteristics of the floating-point types</span></span>

<span data-ttu-id="40d37-108">O C# é compatível com os seguintes tipos de pontos flutuantes predefinidos:</span><span class="sxs-lookup"><span data-stu-id="40d37-108">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="40d37-109">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="40d37-109">C# type/keyword</span></span>|<span data-ttu-id="40d37-110">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="40d37-110">Approximate range</span></span>|<span data-ttu-id="40d37-111">Precisão</span><span class="sxs-lookup"><span data-stu-id="40d37-111">Precision</span></span>|<span data-ttu-id="40d37-112">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="40d37-112">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|
|`float`|<span data-ttu-id="40d37-113">±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="40d37-113">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="40d37-114">Aproximadamente de 6 a 9 dígitos</span><span class="sxs-lookup"><span data-stu-id="40d37-114">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="40d37-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="40d37-115">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="40d37-116">Aproximadamente de 15 a 17 dígitos</span><span class="sxs-lookup"><span data-stu-id="40d37-116">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="40d37-117">±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="40d37-117">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="40d37-118">28 a 29 dígitos</span><span class="sxs-lookup"><span data-stu-id="40d37-118">28-29 digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="40d37-119">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="40d37-119">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="40d37-120">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="40d37-120">They are interchangeable.</span></span> <span data-ttu-id="40d37-121">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="40d37-121">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="40d37-122">O valor padrão de cada tipo de ponto flutuante é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="40d37-122">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="40d37-123">Cada um dos tipos de ponto flutuante possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="40d37-123">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="40d37-124">Os tipos `float` e `double` também fornecem constantes que representam valores não numéricos e infinitos.</span><span class="sxs-lookup"><span data-stu-id="40d37-124">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="40d37-125">Por exemplo, o tipo `double` fornece as seguintes constantes: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> e <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="40d37-125">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="40d37-126">Como o tipo `decimal` tem mais precisão e um intervalo menor que `float` e `double`, ele é apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="40d37-126">Because the `decimal` type has more precision and a smaller range than both `float` and `double`, it's appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="40d37-127">É possível misturar tipos [integrais](integral-numeric-types.md) e de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="40d37-127">You can mix [integral](integral-numeric-types.md) types and floating-point types in an expression.</span></span> <span data-ttu-id="40d37-128">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="40d37-128">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="40d37-129">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="40d37-129">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="40d37-130">Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.</span><span class="sxs-lookup"><span data-stu-id="40d37-130">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="40d37-131">Se não houver nenhum tipo `double` na expressão, ela será avaliada como `float` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.</span><span class="sxs-lookup"><span data-stu-id="40d37-131">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="40d37-132">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="40d37-132">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="40d37-133">Zero positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="40d37-133">Positive and negative zero</span></span>
- <span data-ttu-id="40d37-134">Infinito positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="40d37-134">Positive and negative infinity</span></span>
- <span data-ttu-id="40d37-135">Valor NaN (não é um número)</span><span class="sxs-lookup"><span data-stu-id="40d37-135">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="40d37-136">O conjunto finito de valores diferentes de zero</span><span class="sxs-lookup"><span data-stu-id="40d37-136">The finite set of nonzero values</span></span>

<span data-ttu-id="40d37-137">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="40d37-137">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="40d37-138">É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="40d37-138">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="40d37-139">Literais de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="40d37-139">Floating-point literals</span></span>

<span data-ttu-id="40d37-140">Por padrão, um literal numérico de ponto flutuante no lado direito do operador de atribuição é tratado como `double`.</span><span class="sxs-lookup"><span data-stu-id="40d37-140">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="40d37-141">É possível usar sufixos para converter um literal integral ou de ponto flutuante em um tipo específico:</span><span class="sxs-lookup"><span data-stu-id="40d37-141">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="40d37-142">O sufixo `d` ou `D` converte um literal em um `double`.</span><span class="sxs-lookup"><span data-stu-id="40d37-142">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="40d37-143">O sufixo `f` ou `F` converte um literal em um `float`.</span><span class="sxs-lookup"><span data-stu-id="40d37-143">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="40d37-144">O sufixo `m` ou `M` converte um literal em um `decimal`.</span><span class="sxs-lookup"><span data-stu-id="40d37-144">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="40d37-145">Os exemplos a seguir mostram cada sufixo:</span><span class="sxs-lookup"><span data-stu-id="40d37-145">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="40d37-146">Conversões</span><span class="sxs-lookup"><span data-stu-id="40d37-146">Conversions</span></span>

<span data-ttu-id="40d37-147">Há uma conversão implícita (chamada de *conversão de expansão*) de `float` em `double` porque o intervalo dos valores `float` é um subconjunto adequado de `double` e não há perda de precisão de `float` para `double`.</span><span class="sxs-lookup"><span data-stu-id="40d37-147">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span>

<span data-ttu-id="40d37-148">É necessário usar uma conversão explícita para converter um tipo de ponto flutuante em outro quando uma conversão implícita não está definida do tipo de origem para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="40d37-148">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="40d37-149">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="40d37-149">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="40d37-150">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="40d37-150">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="40d37-151">Não há conversão implícita entre outros tipos de ponto flutuante e o tipo `decimal` porque o tipo `decimal` tem maior precisão do que `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="40d37-151">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="40d37-152">Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="40d37-152">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="40d37-153">Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="40d37-153">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40d37-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40d37-154">See also</span></span>

- [<span data-ttu-id="40d37-155">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="40d37-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40d37-156">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="40d37-156">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="40d37-157">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="40d37-157">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="40d37-158">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="40d37-158">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="40d37-159">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="40d37-159">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="40d37-160">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="40d37-160">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="40d37-161">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="40d37-161">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="40d37-162">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="40d37-162">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="40d37-163">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="40d37-163">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)

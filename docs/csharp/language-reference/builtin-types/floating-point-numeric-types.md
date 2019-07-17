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
ms.openlocfilehash: 738368abd9db75fbd97d1913324cab3b6e869c56
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664186"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="47e92-103">Tipos numéricos de ponto flutuante (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="47e92-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="47e92-104">Os **tipos de ponto flutuante** são um subconjunto dos **tipos simples** e podem ser inicializados com [*literais*](#floating-point-literals).</span><span class="sxs-lookup"><span data-stu-id="47e92-104">The **floating-point types** are a subset of the **simple types** and can be initialized with [*literals*](#floating-point-literals).</span></span> <span data-ttu-id="47e92-105">Todos os tipos de ponto flutuante também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="47e92-105">All floating-point types are also value types.</span></span> <span data-ttu-id="47e92-106">Todos os tipos numéricos de ponto flutuante dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md) [de comparação e de igualdade](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="47e92-106">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md) [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

<span data-ttu-id="47e92-107">A tabela a seguir mostra os intervalos de precisão e aproximados para os tipos de ponto flutuante:</span><span class="sxs-lookup"><span data-stu-id="47e92-107">The following table shows the precision and approximate ranges for the floating-point types:</span></span>
  
|<span data-ttu-id="47e92-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="47e92-108">Type</span></span>|<span data-ttu-id="47e92-109">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="47e92-109">Approximate range</span></span>|<span data-ttu-id="47e92-110">Precisão</span><span class="sxs-lookup"><span data-stu-id="47e92-110">Precision</span></span>|  
|----------|-----------------------|---------------|  
|`float`|<span data-ttu-id="47e92-111">±1,5 x 10<sup>−45</sup> para ±3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="47e92-111">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="47e92-112">Aproximadamente de 6 a 9 dígitos</span><span class="sxs-lookup"><span data-stu-id="47e92-112">~6-9 digits</span></span>|  
|`double`|<span data-ttu-id="47e92-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="47e92-113">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="47e92-114">Aproximadamente de 15 a 17 dígitos</span><span class="sxs-lookup"><span data-stu-id="47e92-114">~15-17 digits</span></span>|  
|`decimal`|<span data-ttu-id="47e92-115">±1,0 x 10<sup>-28</sup> para ±7,9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="47e92-115">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="47e92-116">28 a 29 dígitos</span><span class="sxs-lookup"><span data-stu-id="47e92-116">28-29 digits</span></span>|  

<span data-ttu-id="47e92-117">O valor padrão para todos os tipos de ponto flutuante é `0`.</span><span class="sxs-lookup"><span data-stu-id="47e92-117">The default value for all floating-point types is `0`.</span></span> <span data-ttu-id="47e92-118">Cada um dos tipos de ponto flutuante tem constantes denominadas `MinValue` e `MaxValue` para o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="47e92-118">Each of the floating-point types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span> <span data-ttu-id="47e92-119">Os tipos `float` e `double` têm outras constantes para `PositiveInfinity`, `NegativeInfinity`e `NaN` (para "Não é um número").</span><span class="sxs-lookup"><span data-stu-id="47e92-119">The `float` and `double` types have additional constants for `PositiveInfinity`, `NegativeInfinity`, and `NaN` (for "Not a Number").</span></span> <span data-ttu-id="47e92-120">O tipo `decimal` inclui constantes para `Zero`, `One` e `MinusOne`.</span><span class="sxs-lookup"><span data-stu-id="47e92-120">The `decimal` type includes constants for `Zero`, `One`, and `MinusOne`.</span></span>

<span data-ttu-id="47e92-121">O tipo `decimal` tem mais precisão e um intervalo menor do que `float` e `double`, o que o torna apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="47e92-121">The `decimal` type has more precision and a smaller range than both `float` and `double`, which makes it appropriate for financial and monetary calculations.</span></span>

<span data-ttu-id="47e92-122">É possível misturar tipos integrais e de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="47e92-122">You can mix integral types and floating-point types in an expression.</span></span> <span data-ttu-id="47e92-123">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="47e92-123">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="47e92-124">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="47e92-124">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="47e92-125">Se um dos tipos de ponto flutuante for `double`, a expressão será avaliada como `double` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.</span><span class="sxs-lookup"><span data-stu-id="47e92-125">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>
- <span data-ttu-id="47e92-126">Se não houver nenhum tipo `double` na expressão, ela será avaliada como `float` ou como [bool](../keywords/bool.md) em comparações relacionais ou de igualdade.</span><span class="sxs-lookup"><span data-stu-id="47e92-126">If there is no `double` type in the expression, the expression evaluates to `float`, or to [bool](../keywords/bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="47e92-127">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="47e92-127">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="47e92-128">Zero positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="47e92-128">Positive and negative zero</span></span>
- <span data-ttu-id="47e92-129">Infinito positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="47e92-129">Positive and negative infinity</span></span>
- <span data-ttu-id="47e92-130">Valor NaN (não é um número)</span><span class="sxs-lookup"><span data-stu-id="47e92-130">Not-a-Number value (NaN)</span></span>
- <span data-ttu-id="47e92-131">O conjunto finito de valores diferentes de zero</span><span class="sxs-lookup"><span data-stu-id="47e92-131">The finite set of nonzero values</span></span>

<span data-ttu-id="47e92-132">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](https://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="47e92-132">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

<span data-ttu-id="47e92-133">É possível usar [cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md) ou [cadeias de caracteres de formato numérico personalizado](../../../standard/base-types/custom-numeric-format-strings.md) para formatar um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="47e92-133">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="floating-point-literals"></a><span data-ttu-id="47e92-134">Literais de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="47e92-134">Floating-point literals</span></span>

<span data-ttu-id="47e92-135">Por padrão, um literal numérico de ponto flutuante no lado direito do operador de atribuição é tratado como `double`.</span><span class="sxs-lookup"><span data-stu-id="47e92-135">By default, a floating-point numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="47e92-136">É possível usar sufixos para converter um literal integral ou de ponto flutuante em um tipo específico:</span><span class="sxs-lookup"><span data-stu-id="47e92-136">You can use suffixes to convert a floating-point or integral literal to a specific type:</span></span>

- <span data-ttu-id="47e92-137">O sufixo `d` ou `D` converte um literal em um `double`.</span><span class="sxs-lookup"><span data-stu-id="47e92-137">The `d` or `D` suffix converts a literal to a `double`.</span></span>
- <span data-ttu-id="47e92-138">O sufixo `f` ou `F` converte um literal em um `float`.</span><span class="sxs-lookup"><span data-stu-id="47e92-138">The `f` or `F` suffix converts a literal to a `float`.</span></span>
- <span data-ttu-id="47e92-139">O sufixo `m` ou `M` converte um literal em um `decimal`.</span><span class="sxs-lookup"><span data-stu-id="47e92-139">The `m` or `M` suffix converts a literal to a `decimal`.</span></span>

<span data-ttu-id="47e92-140">Os exemplos a seguir mostram cada sufixo:</span><span class="sxs-lookup"><span data-stu-id="47e92-140">The following examples show each suffix:</span></span>

```csharp
double d = 3D;
d = 4d;
float f = 3.5F;
f = 5.4f;
decimal myMoney = 300.5m;
myMoney = 400.75M;
```

## <a name="conversions"></a><span data-ttu-id="47e92-141">Conversões</span><span class="sxs-lookup"><span data-stu-id="47e92-141">Conversions</span></span>

<span data-ttu-id="47e92-142">Há uma conversão implícita (chamada de *conversão de expansão*) de `float` em `double` porque o intervalo dos valores `float` é um subconjunto adequado de `double` e não há perda de precisão de `float` para `double`.</span><span class="sxs-lookup"><span data-stu-id="47e92-142">There's an implicit conversion (called a *widening conversion*) from `float` to `double` because the range of `float` values is a proper subset of `double` and there is no loss of precision from `float` to `double`.</span></span> 

<span data-ttu-id="47e92-143">É necessário usar uma conversão explícita para converter um tipo de ponto flutuante em outro quando uma conversão implícita não está definida do tipo de origem para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="47e92-143">You must use an explicit cast to convert one floating-point type to another floating-point type when an implicit conversion isn't defined from the source type to the destination type.</span></span> <span data-ttu-id="47e92-144">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="47e92-144">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="47e92-145">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="47e92-145">The explicit case is required because the conversion can result in data loss.</span></span> <span data-ttu-id="47e92-146">Não há conversão implícita entre outros tipos de ponto flutuante e o tipo `decimal` porque o tipo `decimal` tem maior precisão do que `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="47e92-146">There's no implicit conversion between other floating-point types and the `decimal` type because the `decimal` type has greater precision than either `float` or `double`.</span></span>

<span data-ttu-id="47e92-147">Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="47e92-147">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="47e92-148">Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="47e92-148">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47e92-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47e92-149">See also</span></span>

- [<span data-ttu-id="47e92-150">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="47e92-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47e92-151">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="47e92-151">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="47e92-152">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="47e92-152">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="47e92-153">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="47e92-153">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="47e92-154">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="47e92-154">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="47e92-155">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="47e92-155">Numerics in .NET</span></span>](../../../standard/numerics.md)
- [<span data-ttu-id="47e92-156">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="47e92-156">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="47e92-157">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="47e92-157">Implicit Numeric Conversions Table</span></span>](../keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="47e92-158">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="47e92-158">Explicit Numeric Conversions Table</span></span>](../keywords/explicit-numeric-conversions-table.md)
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
- [<span data-ttu-id="47e92-159">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="47e92-159">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)

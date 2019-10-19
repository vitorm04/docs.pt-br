---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 10/18/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579191"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="a52c3-103">Tipos numéricos integrais (Referência C#)</span><span class="sxs-lookup"><span data-stu-id="a52c3-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="a52c3-104">Os **tipos numéricos integrais** são um subconjunto de **tipos simples** e podem ser inicializados com [*literais*](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="a52c3-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integer-literals).</span></span> <span data-ttu-id="a52c3-105">Todos os tipos integrais também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="a52c3-105">All integral types are also value types.</span></span> <span data-ttu-id="a52c3-106">Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [lógicos](../operators/bitwise-and-shift-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="a52c3-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="a52c3-107">Características dos tipos integrais</span><span class="sxs-lookup"><span data-stu-id="a52c3-107">Characteristics of the integral types</span></span>

<span data-ttu-id="a52c3-108">O C# é compatível com os seguintes tipos integrais predefinidos:</span><span class="sxs-lookup"><span data-stu-id="a52c3-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="a52c3-109">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="a52c3-109">C# type/keyword</span></span>|<span data-ttu-id="a52c3-110">Intervalo</span><span class="sxs-lookup"><span data-stu-id="a52c3-110">Range</span></span>|<span data-ttu-id="a52c3-111">Tamanho</span><span class="sxs-lookup"><span data-stu-id="a52c3-111">Size</span></span>|<span data-ttu-id="a52c3-112">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="a52c3-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="a52c3-113">-128 a 127</span><span class="sxs-lookup"><span data-stu-id="a52c3-113">-128 to 127</span></span>|<span data-ttu-id="a52c3-114">Inteiro de 8 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="a52c3-115">0 a 255</span><span class="sxs-lookup"><span data-stu-id="a52c3-115">0 to 255</span></span>|<span data-ttu-id="a52c3-116">Inteiro de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="a52c3-117">-32.768 a 32.767</span><span class="sxs-lookup"><span data-stu-id="a52c3-117">-32,768 to 32,767</span></span>|<span data-ttu-id="a52c3-118">Inteiro de 16 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="a52c3-119">0 a 65.535</span><span class="sxs-lookup"><span data-stu-id="a52c3-119">0 to 65,535</span></span>|<span data-ttu-id="a52c3-120">Inteiro de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="a52c3-121">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="a52c3-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="a52c3-122">Inteiro de 32 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="a52c3-123">0 a 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="a52c3-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="a52c3-124">Inteiro de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="a52c3-125">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="a52c3-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="a52c3-126">Inteiro de 64 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="a52c3-127">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="a52c3-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="a52c3-128">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="a52c3-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="a52c3-129">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="a52c3-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="a52c3-130">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="a52c3-130">They are interchangeable.</span></span> <span data-ttu-id="a52c3-131">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="a52c3-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="a52c3-132">O valor padrão de cada tipo integral é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="a52c3-133">Cada um dos tipos integrais possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a52c3-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="a52c3-134">Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.</span><span class="sxs-lookup"><span data-stu-id="a52c3-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="a52c3-135">Literais inteiros</span><span class="sxs-lookup"><span data-stu-id="a52c3-135">Integer literals</span></span>

<span data-ttu-id="a52c3-136">Literais inteiros podem ser</span><span class="sxs-lookup"><span data-stu-id="a52c3-136">Integer literals can be</span></span>

- <span data-ttu-id="a52c3-137">*decimal*: sem nenhum prefixo</span><span class="sxs-lookup"><span data-stu-id="a52c3-137">*decimal*: without any prefix</span></span>
- <span data-ttu-id="a52c3-138">*hexadecimal*: com o prefixo de `0x` ou `0X`</span><span class="sxs-lookup"><span data-stu-id="a52c3-138">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="a52c3-139">*Binary*: com o prefixo `0b` ou `0B` (disponível em C# 7,0 e posterior)</span><span class="sxs-lookup"><span data-stu-id="a52c3-139">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="a52c3-140">O código a seguir demonstra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="a52c3-140">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="a52c3-141">O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="a52c3-141">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="a52c3-142">Você pode usar o separador de dígitos com todos os tipos de literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="a52c3-142">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="a52c3-143">O tipo de um inteiro literal é determinado por seu sufixo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a52c3-143">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="a52c3-144">Se o literal não tiver nenhum sufixo, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `int`, `uint`, `long` `ulong`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-144">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="a52c3-145">Se o literal for sufixado por `U` ou `u`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `uint` `ulong`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-145">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="a52c3-146">Se o literal for sufixado por `L` ou `l`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `long` `ulong`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-146">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="a52c3-147">Você pode usar a letra minúscula `l` como um sufixo.</span><span class="sxs-lookup"><span data-stu-id="a52c3-147">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="a52c3-148">No entanto, isso gera um aviso do compilador porque a letra `l` pode ser confundida com o `1` de dígitos.</span><span class="sxs-lookup"><span data-stu-id="a52c3-148">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="a52c3-149">Use `L` para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="a52c3-149">Use `L` for clarity.</span></span>

- <span data-ttu-id="a52c3-150">Se o literal for sufixado por `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` ou `lu`, seu tipo será `ulong`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-150">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="a52c3-151">Se o valor representado por um literal inteiro exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).</span><span class="sxs-lookup"><span data-stu-id="a52c3-151">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="a52c3-152">O valor representado por um inteiro literal pode ser convertido implicitamente em um tipo com um intervalo menor do que o tipo determinado do literal.</span><span class="sxs-lookup"><span data-stu-id="a52c3-152">The value represented by an integer literal can be implicitly converted to a type with a smaller range than the determined type of the literal.</span></span> <span data-ttu-id="a52c3-153">Isso é possível quando o valor está dentro do intervalo do tipo de destino:</span><span class="sxs-lookup"><span data-stu-id="a52c3-153">That's possible when the value is within the range of the destination type:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="a52c3-154">Como mostra o exemplo anterior, se o valor do literal não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031](../../misc/cs0031.md) .</span><span class="sxs-lookup"><span data-stu-id="a52c3-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="a52c3-155">Você também pode usar uma conversão para converter o valor representado por um literal inteiro para o tipo diferente do tipo determinado do literal:</span><span class="sxs-lookup"><span data-stu-id="a52c3-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="a52c3-156">Conversões</span><span class="sxs-lookup"><span data-stu-id="a52c3-156">Conversions</span></span>

<span data-ttu-id="a52c3-157">Há uma conversão implícita (chamada de *conversão de ampliação*) entre quaisquer dois tipos integrais, nos quais o tipo de destino pode armazenar todos os valores do tipo de origem.</span><span class="sxs-lookup"><span data-stu-id="a52c3-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="a52c3-158">Por exemplo, há uma conversão implícita de `int` até `long` porque o intervalo dos valores de `int` é um subconjunto adequado de `long`.</span><span class="sxs-lookup"><span data-stu-id="a52c3-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="a52c3-159">Não há conversões implícitas de um tipo integral sem sinal menor para um tipo integral com sinal maior.</span><span class="sxs-lookup"><span data-stu-id="a52c3-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="a52c3-160">Também há uma conversão implícita de qualquer tipo integral para qualquer tipo de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="a52c3-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="a52c3-161">Não há conversões implícitas de qualquer tipo integral com sinal para qualquer tipo integral sem sinal.</span><span class="sxs-lookup"><span data-stu-id="a52c3-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="a52c3-162">Você deverá usar uma conversão explícita para converter um tipo integral em outro tipo integral quando uma conversão implícita não for definida por meio do tipo de fonte para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="a52c3-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="a52c3-163">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="a52c3-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="a52c3-164">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="a52c3-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a52c3-165">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a52c3-165">C# language specification</span></span>

<span data-ttu-id="a52c3-166">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="a52c3-166">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="a52c3-167">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="a52c3-167">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="a52c3-168">Literais inteiros</span><span class="sxs-lookup"><span data-stu-id="a52c3-168">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="a52c3-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a52c3-169">See also</span></span>

- [<span data-ttu-id="a52c3-170">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a52c3-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a52c3-171">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="a52c3-171">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="a52c3-172">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="a52c3-172">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="a52c3-173">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="a52c3-173">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="a52c3-174">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="a52c3-174">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="a52c3-175">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="a52c3-175">Numerics in .NET</span></span>](../../../standard/numerics.md)

---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 10/22/2019
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
ms.openlocfilehash: 394a809a9a2f45f4aee652d0eca892f62f0f2e54
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093195"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="0e866-103">Tipos numéricos integrais (Referência C#)</span><span class="sxs-lookup"><span data-stu-id="0e866-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="0e866-104">Os *tipos numéricos integrais* representam números inteiros.</span><span class="sxs-lookup"><span data-stu-id="0e866-104">The *integral numeric types* represent integer numbers.</span></span> <span data-ttu-id="0e866-105">Todos os tipos numéricos integrais são [tipos de valor](value-types.md).</span><span class="sxs-lookup"><span data-stu-id="0e866-105">All integral numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="0e866-106">Eles também são [tipos simples](value-types.md#built-in-value-types) e podem ser inicializados com [literais](#integer-literals).</span><span class="sxs-lookup"><span data-stu-id="0e866-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#integer-literals).</span></span> <span data-ttu-id="0e866-107">Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [lógicos](../operators/bitwise-and-shift-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .</span><span class="sxs-lookup"><span data-stu-id="0e866-107">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="0e866-108">Características dos tipos integrais</span><span class="sxs-lookup"><span data-stu-id="0e866-108">Characteristics of the integral types</span></span>

<span data-ttu-id="0e866-109">O C# é compatível com os seguintes tipos integrais predefinidos:</span><span class="sxs-lookup"><span data-stu-id="0e866-109">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="0e866-110">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="0e866-110">C# type/keyword</span></span>|<span data-ttu-id="0e866-111">Intervalo</span><span class="sxs-lookup"><span data-stu-id="0e866-111">Range</span></span>|<span data-ttu-id="0e866-112">Tamanho</span><span class="sxs-lookup"><span data-stu-id="0e866-112">Size</span></span>|<span data-ttu-id="0e866-113">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="0e866-113">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="0e866-114">-128 a 127</span><span class="sxs-lookup"><span data-stu-id="0e866-114">-128 to 127</span></span>|<span data-ttu-id="0e866-115">Inteiro de 8 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-115">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="0e866-116">0 a 255</span><span class="sxs-lookup"><span data-stu-id="0e866-116">0 to 255</span></span>|<span data-ttu-id="0e866-117">Inteiro de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-117">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="0e866-118">-32.768 a 32.767</span><span class="sxs-lookup"><span data-stu-id="0e866-118">-32,768 to 32,767</span></span>|<span data-ttu-id="0e866-119">Inteiro de 16 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-119">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="0e866-120">0 a 65.535</span><span class="sxs-lookup"><span data-stu-id="0e866-120">0 to 65,535</span></span>|<span data-ttu-id="0e866-121">Inteiro de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-121">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="0e866-122">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="0e866-122">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="0e866-123">Inteiro assinado de 32 bits</span><span class="sxs-lookup"><span data-stu-id="0e866-123">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="0e866-124">0 a 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="0e866-124">0 to 4,294,967,295</span></span>|<span data-ttu-id="0e866-125">Inteiro de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-125">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="0e866-126">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="0e866-126">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="0e866-127">Inteiro assinado de 64 bits</span><span class="sxs-lookup"><span data-stu-id="0e866-127">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="0e866-128">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="0e866-128">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="0e866-129">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="0e866-129">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="0e866-130">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="0e866-130">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="0e866-131">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="0e866-131">They are interchangeable.</span></span> <span data-ttu-id="0e866-132">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="0e866-132">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="0e866-133">O valor padrão de cada tipo integral é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="0e866-133">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="0e866-134">Cada um dos tipos integrais possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="0e866-134">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="0e866-135">Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.</span><span class="sxs-lookup"><span data-stu-id="0e866-135">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="0e866-136">Literais inteiros</span><span class="sxs-lookup"><span data-stu-id="0e866-136">Integer literals</span></span>

<span data-ttu-id="0e866-137">Literais inteiros podem ser</span><span class="sxs-lookup"><span data-stu-id="0e866-137">Integer literals can be</span></span>

- <span data-ttu-id="0e866-138">*decimal*: sem nenhum prefixo</span><span class="sxs-lookup"><span data-stu-id="0e866-138">*decimal*: without any prefix</span></span>
- <span data-ttu-id="0e866-139">*hexadecimal*: com o prefixo de `0x` ou `0X`</span><span class="sxs-lookup"><span data-stu-id="0e866-139">*hexadecimal*: with the `0x` or `0X` prefix</span></span>
- <span data-ttu-id="0e866-140">*Binary*: com o prefixo `0b` ou `0B` (disponível em C# 7,0 e posterior)</span><span class="sxs-lookup"><span data-stu-id="0e866-140">*binary*: with the `0b` or `0B` prefix (available in C# 7.0 and later)</span></span>

<span data-ttu-id="0e866-141">O código a seguir demonstra um exemplo de cada um:</span><span class="sxs-lookup"><span data-stu-id="0e866-141">The following code demonstrates an example of each:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="0e866-142">O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0.</span><span class="sxs-lookup"><span data-stu-id="0e866-142">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="0e866-143">Você pode usar o separador de dígitos com todos os tipos de literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="0e866-143">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="0e866-144">O tipo de um inteiro literal é determinado por seu sufixo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0e866-144">The type of an integer literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="0e866-145">Se o literal não tiver nenhum sufixo, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `int`, `uint`, `long``ulong`.</span><span class="sxs-lookup"><span data-stu-id="0e866-145">If the literal has no suffix, its type is the first of the following types in which its value can be represented: `int`, `uint`, `long`, `ulong`.</span></span>
- <span data-ttu-id="0e866-146">Se o literal for sufixado por `U` ou `u`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `uint``ulong`.</span><span class="sxs-lookup"><span data-stu-id="0e866-146">If the literal is suffixed by `U` or `u`, its type is the first of the following types in which its value can be represented: `uint`, `ulong`.</span></span>
- <span data-ttu-id="0e866-147">Se o literal for sufixado por `L` ou `l`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `long``ulong`.</span><span class="sxs-lookup"><span data-stu-id="0e866-147">If the literal is suffixed by `L` or `l`, its type is the first of the following types in which its value can be represented: `long`, `ulong`.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0e866-148">Você pode usar a letra minúscula `l` como um sufixo.</span><span class="sxs-lookup"><span data-stu-id="0e866-148">You can use the lowercase letter `l` as a suffix.</span></span> <span data-ttu-id="0e866-149">No entanto, isso gera um aviso do compilador porque a letra `l` pode ser confundida com o `1`de dígitos.</span><span class="sxs-lookup"><span data-stu-id="0e866-149">However, this generates a compiler warning because the letter `l` can be confused with the digit `1`.</span></span> <span data-ttu-id="0e866-150">Use `L` para maior clareza.</span><span class="sxs-lookup"><span data-stu-id="0e866-150">Use `L` for clarity.</span></span>

- <span data-ttu-id="0e866-151">Se o literal for sufixado por `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`ou `lu`, seu tipo será `ulong`.</span><span class="sxs-lookup"><span data-stu-id="0e866-151">If the literal is suffixed by `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU`, or `lu`, its type is `ulong`.</span></span>

<span data-ttu-id="0e866-152">Se o valor representado por um literal inteiro exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).</span><span class="sxs-lookup"><span data-stu-id="0e866-152">If the value represented by an integer literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span>

<span data-ttu-id="0e866-153">Se o tipo determinado de um literal inteiro for `int` e o valor representado pelo literal estiver dentro do intervalo do tipo de destino, o valor poderá ser convertido implicitamente em `sbyte`, `byte`, `short`, `ushort`, `uint`ou `ulong`:</span><span class="sxs-lookup"><span data-stu-id="0e866-153">If the determined type of an integer literal is `int` and the value represented by the literal is within the range of the destination type, the value can be implicitly converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`:</span></span>

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

<span data-ttu-id="0e866-154">Como mostra o exemplo anterior, se o valor do literal não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031](../../misc/cs0031.md) .</span><span class="sxs-lookup"><span data-stu-id="0e866-154">As the preceding example shows, if the literal's value is not within the range of the destination type, a compiler error [CS0031](../../misc/cs0031.md) occurs.</span></span>

<span data-ttu-id="0e866-155">Você também pode usar uma conversão para converter o valor representado por um literal inteiro para o tipo diferente do tipo determinado do literal:</span><span class="sxs-lookup"><span data-stu-id="0e866-155">You also can use a cast to convert the value represented by an integer literal to the type other than the determined type of the literal:</span></span>

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="0e866-156">Conversões</span><span class="sxs-lookup"><span data-stu-id="0e866-156">Conversions</span></span>

<span data-ttu-id="0e866-157">Você pode converter qualquer tipo numérico integral para qualquer outro tipo numérico integral.</span><span class="sxs-lookup"><span data-stu-id="0e866-157">You can convert any integral numeric type to any other integral numeric type.</span></span> <span data-ttu-id="0e866-158">Se o tipo de destino puder armazenar todos os valores do tipo de origem, a conversão será implícita.</span><span class="sxs-lookup"><span data-stu-id="0e866-158">If the destination type can store all values of the source type, the conversion is implicit.</span></span> <span data-ttu-id="0e866-159">Caso contrário, você precisa usar o [operador cast `()`](../operators/type-testing-and-cast.md#cast-operator-) para invocar uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="0e866-159">Otherwise, you need to use the [cast operator `()`](../operators/type-testing-and-cast.md#cast-operator-) to invoke an explicit conversion.</span></span> <span data-ttu-id="0e866-160">Para obter mais informações, consulte [conversões numéricas internas](numeric-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0e866-160">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0e866-161">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0e866-161">C# language specification</span></span>

<span data-ttu-id="0e866-162">Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="0e866-162">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="0e866-163">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="0e866-163">Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="0e866-164">Literais inteiros</span><span class="sxs-lookup"><span data-stu-id="0e866-164">Integer literals</span></span>](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a><span data-ttu-id="0e866-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="0e866-165">See also</span></span>

- [<span data-ttu-id="0e866-166">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0e866-166">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0e866-167">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="0e866-167">Value types</span></span>](value-types.md)
- [<span data-ttu-id="0e866-168">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="0e866-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="0e866-169">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="0e866-169">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="0e866-170">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="0e866-170">Numerics in .NET</span></span>](../../../standard/numerics.md)

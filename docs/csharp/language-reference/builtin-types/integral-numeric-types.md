---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236085"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="8866a-103">Tipos numéricos integrais (Referência C#)</span><span class="sxs-lookup"><span data-stu-id="8866a-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="8866a-104">Os **tipos numéricos integrais** são um subconjunto de **tipos simples** e podem ser inicializados com [*literais*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="8866a-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="8866a-105">Todos os tipos integrais também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8866a-105">All integral types are also value types.</span></span> <span data-ttu-id="8866a-106">Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [bit a bit lógicos](../operators/bitwise-and-shift-operators.md), de [comparação e igualdade](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="8866a-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-integral-types"></a><span data-ttu-id="8866a-107">Características dos tipos integrais</span><span class="sxs-lookup"><span data-stu-id="8866a-107">Characteristics of the integral types</span></span>

<span data-ttu-id="8866a-108">O C# é compatível com os seguintes tipos integrais predefinidos:</span><span class="sxs-lookup"><span data-stu-id="8866a-108">C# supports the following predefined integral types:</span></span>

|<span data-ttu-id="8866a-109">palavra-chave/tipo C#</span><span class="sxs-lookup"><span data-stu-id="8866a-109">C# type/keyword</span></span>|<span data-ttu-id="8866a-110">Intervalo</span><span class="sxs-lookup"><span data-stu-id="8866a-110">Range</span></span>|<span data-ttu-id="8866a-111">Tamanho</span><span class="sxs-lookup"><span data-stu-id="8866a-111">Size</span></span>|<span data-ttu-id="8866a-112">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="8866a-112">.NET type</span></span>|
|----------|-----------|----------|-------------|
|`sbyte`|<span data-ttu-id="8866a-113">-128 a 127</span><span class="sxs-lookup"><span data-stu-id="8866a-113">-128 to 127</span></span>|<span data-ttu-id="8866a-114">Inteiro de 8 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-114">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|<span data-ttu-id="8866a-115">0 a 255</span><span class="sxs-lookup"><span data-stu-id="8866a-115">0 to 255</span></span>|<span data-ttu-id="8866a-116">Inteiro de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-116">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|<span data-ttu-id="8866a-117">-32.768 a 32.767</span><span class="sxs-lookup"><span data-stu-id="8866a-117">-32,768 to 32,767</span></span>|<span data-ttu-id="8866a-118">Inteiro de 16 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-118">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|<span data-ttu-id="8866a-119">0 a 65.535</span><span class="sxs-lookup"><span data-stu-id="8866a-119">0 to 65,535</span></span>|<span data-ttu-id="8866a-120">Inteiro de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-120">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|<span data-ttu-id="8866a-121">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="8866a-121">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="8866a-122">Inteiro de 32 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-122">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|<span data-ttu-id="8866a-123">0 a 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="8866a-123">0 to 4,294,967,295</span></span>|<span data-ttu-id="8866a-124">Inteiro de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-124">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|<span data-ttu-id="8866a-125">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="8866a-125">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="8866a-126">Inteiro de 64 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-126">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|<span data-ttu-id="8866a-127">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="8866a-127">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="8866a-128">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="8866a-128">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

<span data-ttu-id="8866a-129">Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente.</span><span class="sxs-lookup"><span data-stu-id="8866a-129">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="8866a-130">Eles são intercambiáveis.</span><span class="sxs-lookup"><span data-stu-id="8866a-130">They are interchangeable.</span></span> <span data-ttu-id="8866a-131">Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:</span><span class="sxs-lookup"><span data-stu-id="8866a-131">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="8866a-132">O valor padrão de cada tipo integral é zero, `0`.</span><span class="sxs-lookup"><span data-stu-id="8866a-132">The default value of each integral type is zero, `0`.</span></span> <span data-ttu-id="8866a-133">Cada um dos tipos integrais possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="8866a-133">Each of the integral types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum value of that type.</span></span>

<span data-ttu-id="8866a-134">Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.</span><span class="sxs-lookup"><span data-stu-id="8866a-134">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="8866a-135">Literais integrais</span><span class="sxs-lookup"><span data-stu-id="8866a-135">Integral literals</span></span>

<span data-ttu-id="8866a-136">Os literais integrais podem ser especificados como *literais decimais*, *literais hexadecimais* ou *literais binários*.</span><span class="sxs-lookup"><span data-stu-id="8866a-136">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="8866a-137">Abaixo, um exemplo de cada:</span><span class="sxs-lookup"><span data-stu-id="8866a-137">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="8866a-138">Literais decimais não exigem nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="8866a-138">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="8866a-139">O prefixo `x` ou `X` significa um *literal hexadecimal*.</span><span class="sxs-lookup"><span data-stu-id="8866a-139">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="8866a-140">O prefixo `b` ou `B` significa um *literal binário*.</span><span class="sxs-lookup"><span data-stu-id="8866a-140">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="8866a-141">A declaração de `binaryLiteral` demonstra o uso de `_` como um *separador de dígito*.</span><span class="sxs-lookup"><span data-stu-id="8866a-141">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="8866a-142">O separador de dígito pode ser usado com todos os literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="8866a-142">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="8866a-143">Os literais binários e o separador de dígitos `_` são compatíveis a partir do C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="8866a-143">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="8866a-144">Sufixos literais</span><span class="sxs-lookup"><span data-stu-id="8866a-144">Literal suffixes</span></span>

<span data-ttu-id="8866a-145">O sufixo `l` ou `L` especifica que o literal integral deve ser do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="8866a-145">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="8866a-146">O sufixo `ul` ou `UL` especifica o tipo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8866a-146">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="8866a-147">Se o sufixo `L` for usado em um literal maior que 9.223.372.036.854.775.807 (o valor máximo de `long`), o valor será convertido para o tipo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="8866a-147">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="8866a-148">Se o valor representado por um literal integral exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).</span><span class="sxs-lookup"><span data-stu-id="8866a-148">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="8866a-149">Você pode usar a letra minúscula "l" como sufixo.</span><span class="sxs-lookup"><span data-stu-id="8866a-149">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="8866a-150">No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1".</span><span class="sxs-lookup"><span data-stu-id="8866a-150">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="8866a-151">Use "L" para fins de clareza.</span><span class="sxs-lookup"><span data-stu-id="8866a-151">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="8866a-152">Tipo de um literal integral</span><span class="sxs-lookup"><span data-stu-id="8866a-152">Type of an integral literal</span></span>

<span data-ttu-id="8866a-153">Se um literal integral não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="8866a-153">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="8866a-154">Você pode converter um literal integral em um tipo com um intervalo menor que o padrão usando uma atribuição ou uma conversão:</span><span class="sxs-lookup"><span data-stu-id="8866a-154">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="8866a-155">Você pode converter um literal integral em um tipo com um intervalo maior que o padrão usando uma atribuição, uma conversão ou um sufixo no literal:</span><span class="sxs-lookup"><span data-stu-id="8866a-155">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="8866a-156">Conversões</span><span class="sxs-lookup"><span data-stu-id="8866a-156">Conversions</span></span>

<span data-ttu-id="8866a-157">Há uma conversão implícita (chamada de *conversão de ampliação*) entre quaisquer dois tipos integrais, nos quais o tipo de destino pode armazenar todos os valores do tipo de origem.</span><span class="sxs-lookup"><span data-stu-id="8866a-157">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="8866a-158">Por exemplo, há uma conversão implícita de `int` até `long` porque o intervalo dos valores de `int` é um subconjunto adequado de `long`.</span><span class="sxs-lookup"><span data-stu-id="8866a-158">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="8866a-159">Não há conversões implícitas de um tipo integral sem sinal menor para um tipo integral com sinal maior.</span><span class="sxs-lookup"><span data-stu-id="8866a-159">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="8866a-160">Também há uma conversão implícita de qualquer tipo integral para qualquer tipo de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="8866a-160">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="8866a-161">Não há conversões implícitas de qualquer tipo integral com sinal para qualquer tipo integral sem sinal.</span><span class="sxs-lookup"><span data-stu-id="8866a-161">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="8866a-162">Você deverá usar uma conversão explícita para converter um tipo integral em outro tipo integral quando uma conversão implícita não for definida por meio do tipo de fonte para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="8866a-162">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="8866a-163">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="8866a-163">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="8866a-164">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="8866a-164">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="8866a-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8866a-165">See also</span></span>

- [<span data-ttu-id="8866a-166">Especificação da linguagem C# – Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="8866a-166">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="8866a-167">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8866a-167">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8866a-168">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="8866a-168">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="8866a-169">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="8866a-169">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="8866a-170">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="8866a-170">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="8866a-171">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="8866a-171">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="8866a-172">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="8866a-172">Numerics in .NET</span></span>](../../../standard/numerics.md)

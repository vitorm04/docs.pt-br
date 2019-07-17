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
ms.openlocfilehash: 0a1ed01d9e6cb86ea177e8b947627f9dc02eedae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744222"
---
# <a name="integral-numeric-types--c-reference"></a><span data-ttu-id="64f2b-103">Tipos numéricos integrais (Referência C#)</span><span class="sxs-lookup"><span data-stu-id="64f2b-103">Integral numeric types  (C# reference)</span></span>

<span data-ttu-id="64f2b-104">Os **tipos numéricos integrais** são um subconjunto de **tipos simples** e podem ser inicializados com [*literais*](#integral-literals).</span><span class="sxs-lookup"><span data-stu-id="64f2b-104">The **integral numeric types** are a subset of the **simple types** and can be initialized with [*literals*](#integral-literals).</span></span> <span data-ttu-id="64f2b-105">Todos os tipos integrais também são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="64f2b-105">All integral types are also value types.</span></span>

<span data-ttu-id="64f2b-106">Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [bit a bit lógicos](../operators/bitwise-and-shift-operators.md), de [comparação e igualdade](../operators/equality-operators.md).</span><span class="sxs-lookup"><span data-stu-id="64f2b-106">All integral numeric types support [arithmetic](../operators/arithmetic-operators.md), [bitwise logical](../operators/bitwise-and-shift-operators.md), [comparison, and equality](../operators/equality-operators.md) operators.</span></span>

## <a name="sizes-and-ranges"></a><span data-ttu-id="64f2b-107">Tamanhos e intervalos</span><span class="sxs-lookup"><span data-stu-id="64f2b-107">Sizes and ranges</span></span>

<span data-ttu-id="64f2b-108">A tabela a seguir mostra os tamanhos e os intervalos de tipos integrais:</span><span class="sxs-lookup"><span data-stu-id="64f2b-108">The following table shows the sizes and ranges of the integral types:</span></span>

|<span data-ttu-id="64f2b-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="64f2b-109">Type</span></span>|<span data-ttu-id="64f2b-110">Intervalo</span><span class="sxs-lookup"><span data-stu-id="64f2b-110">Range</span></span>|<span data-ttu-id="64f2b-111">Tamanho</span><span class="sxs-lookup"><span data-stu-id="64f2b-111">Size</span></span>|  
|----------|-----------|----------|  
|`sbyte`|<span data-ttu-id="64f2b-112">-128 a 127</span><span class="sxs-lookup"><span data-stu-id="64f2b-112">-128 to 127</span></span>|<span data-ttu-id="64f2b-113">Inteiro de 8 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-113">Signed 8-bit integer</span></span>|  
|`byte`|<span data-ttu-id="64f2b-114">0 a 255</span><span class="sxs-lookup"><span data-stu-id="64f2b-114">0 to 255</span></span>|<span data-ttu-id="64f2b-115">Inteiro de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-115">Unsigned 8-bit integer</span></span>|  
|`short`|<span data-ttu-id="64f2b-116">-32.768 a 32.767</span><span class="sxs-lookup"><span data-stu-id="64f2b-116">-32,768 to 32,767</span></span>|<span data-ttu-id="64f2b-117">Inteiro de 16 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-117">Signed 16-bit integer</span></span>|  
|`ushort`|<span data-ttu-id="64f2b-118">0 a 65.535</span><span class="sxs-lookup"><span data-stu-id="64f2b-118">0 to 65,535</span></span>|<span data-ttu-id="64f2b-119">Inteiro de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-119">Unsigned 16-bit integer</span></span>|  
|`int`|<span data-ttu-id="64f2b-120">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="64f2b-120">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="64f2b-121">Inteiro de 32 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-121">Signed 32-bit integer</span></span>|  
|`uint`|<span data-ttu-id="64f2b-122">0 a 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="64f2b-122">0 to 4,294,967,295</span></span>|<span data-ttu-id="64f2b-123">Inteiro de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-123">Unsigned 32-bit integer</span></span>|  
|`long`|<span data-ttu-id="64f2b-124">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="64f2b-124">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="64f2b-125">Inteiro de 64 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-125">Signed 64-bit integer</span></span>|  
|`ulong`|<span data-ttu-id="64f2b-126">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="64f2b-126">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="64f2b-127">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="64f2b-127">Unsigned 64-bit integer</span></span>|  

<span data-ttu-id="64f2b-128">O valor padrão para todos os tipos integrais é `0`.</span><span class="sxs-lookup"><span data-stu-id="64f2b-128">The default value for all integral types is `0`.</span></span> <span data-ttu-id="64f2b-129">Cada um dos tipos integrais tem constantes denominadas `MinValue` e `MaxValue` para o valor mínimo e máximo desse tipo.</span><span class="sxs-lookup"><span data-stu-id="64f2b-129">Each of the integral types has constants named `MinValue` and `MaxValue` for the minimum and maximum value for that type.</span></span>

<span data-ttu-id="64f2b-130">Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.</span><span class="sxs-lookup"><span data-stu-id="64f2b-130">Use the <xref:System.Numerics.BigInteger?displayProperty=nameWithType> structure to represent a signed integer with no upper or lower bounds.</span></span>

## <a name="integral-literals"></a><span data-ttu-id="64f2b-131">Literais integrais</span><span class="sxs-lookup"><span data-stu-id="64f2b-131">Integral literals</span></span>

<span data-ttu-id="64f2b-132">Os literais integrais podem ser especificados como *literais decimais*, *literais hexadecimais* ou *literais binários*.</span><span class="sxs-lookup"><span data-stu-id="64f2b-132">Integral literals can be specified as *decimal literals*, *hexadecimal literals*, or *binary literals*.</span></span> <span data-ttu-id="64f2b-133">Abaixo, um exemplo de cada:</span><span class="sxs-lookup"><span data-stu-id="64f2b-133">An example of each is shown below:</span></span>

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

<span data-ttu-id="64f2b-134">Literais decimais não exigem nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="64f2b-134">Decimal literals don't require any prefix.</span></span> <span data-ttu-id="64f2b-135">O prefixo `x` ou `X` significa um *literal hexadecimal*.</span><span class="sxs-lookup"><span data-stu-id="64f2b-135">The `x` or `X` prefix signifies a *hexadecimal literal*.</span></span> <span data-ttu-id="64f2b-136">O prefixo `b` ou `B` significa um *literal binário*.</span><span class="sxs-lookup"><span data-stu-id="64f2b-136">The `b` or `B` prefix signifies a *binary literal*.</span></span> <span data-ttu-id="64f2b-137">A declaração de `binaryLiteral` demonstra o uso de `_` como um *separador de dígito*.</span><span class="sxs-lookup"><span data-stu-id="64f2b-137">The declaration of `binaryLiteral` demonstrates the use of `_` as a *digit separator*.</span></span> <span data-ttu-id="64f2b-138">O separador de dígito pode ser usado com todos os literais numéricos.</span><span class="sxs-lookup"><span data-stu-id="64f2b-138">The digit separator can be used with all numeric literals.</span></span> <span data-ttu-id="64f2b-139">Os literais binários e o separador de dígitos `_` são compatíveis a partir do C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="64f2b-139">Binary literals and the digit separator `_` are supported starting with C# 7.0.</span></span>

### <a name="literal-suffixes"></a><span data-ttu-id="64f2b-140">Sufixos literais</span><span class="sxs-lookup"><span data-stu-id="64f2b-140">Literal suffixes</span></span> 

<span data-ttu-id="64f2b-141">O sufixo `l` ou `L` especifica que o literal integral deve ser do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="64f2b-141">The `l` or `L` suffix specifies that the integral literal should be of the `long` type.</span></span> <span data-ttu-id="64f2b-142">O sufixo `ul` ou `UL` especifica o tipo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="64f2b-142">The `ul` or `UL` suffix specifies the `ulong` type.</span></span> <span data-ttu-id="64f2b-143">Se o sufixo `L` for usado em um literal maior que 9.223.372.036.854.775.807 (o valor máximo de `long`), o valor será convertido para o tipo `ulong`.</span><span class="sxs-lookup"><span data-stu-id="64f2b-143">If the `L` suffix is used on a literal that is greater than 9,223,372,036,854,775,807 (the maximum value of `long`), the value is converted to the `ulong` type.</span></span> <span data-ttu-id="64f2b-144">Se o valor representado por um literal integral exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).</span><span class="sxs-lookup"><span data-stu-id="64f2b-144">If the value represented by an integral literal exceeds <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compiler error [CS1021](../../misc/cs1021.md) occurs.</span></span> 

> [!NOTE]
> <span data-ttu-id="64f2b-145">Você pode usar a letra minúscula "l" como sufixo.</span><span class="sxs-lookup"><span data-stu-id="64f2b-145">You can use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="64f2b-146">No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1".</span><span class="sxs-lookup"><span data-stu-id="64f2b-146">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="64f2b-147">Use "L" para fins de clareza.</span><span class="sxs-lookup"><span data-stu-id="64f2b-147">Use "L" for clarity.</span></span>

### <a name="type-of-an-integral-literal"></a><span data-ttu-id="64f2b-148">Tipo de um literal integral</span><span class="sxs-lookup"><span data-stu-id="64f2b-148">Type of an integral literal</span></span>

<span data-ttu-id="64f2b-149">Se um literal integral não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="64f2b-149">If an integral literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. `int`
1. `uint`
1. `long`
1. `ulong`

<span data-ttu-id="64f2b-150">Você pode converter um literal integral em um tipo com um intervalo menor que o padrão usando uma atribuição ou uma conversão:</span><span class="sxs-lookup"><span data-stu-id="64f2b-150">You can convert an integral literal to a type with a smaller range than the default using either an assignment or a cast:</span></span>

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

<span data-ttu-id="64f2b-151">Você pode converter um literal integral em um tipo com um intervalo maior que o padrão usando uma atribuição, uma conversão ou um sufixo no literal:</span><span class="sxs-lookup"><span data-stu-id="64f2b-151">You can convert an integral literal to a type with a larger range than the default using either assignment, a cast, or a suffix on the literal:</span></span>

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a><span data-ttu-id="64f2b-152">Conversões</span><span class="sxs-lookup"><span data-stu-id="64f2b-152">Conversions</span></span>

<span data-ttu-id="64f2b-153">Há uma conversão implícita (chamada de *conversão de ampliação*) entre quaisquer dois tipos integrais, nos quais o tipo de destino pode armazenar todos os valores do tipo de origem.</span><span class="sxs-lookup"><span data-stu-id="64f2b-153">There's an implicit conversion (called a *widening conversion*) between any two integral types where the destination type can store all values of the source type.</span></span> <span data-ttu-id="64f2b-154">Por exemplo, há uma conversão implícita de `int` até `long` porque o intervalo dos valores de `int` é um subconjunto adequado de `long`.</span><span class="sxs-lookup"><span data-stu-id="64f2b-154">For example, there's an implicit conversion from `int` to `long` because the range of `int` values is a proper subset of `long`.</span></span> <span data-ttu-id="64f2b-155">Não há conversões implícitas de um tipo integral sem sinal menor para um tipo integral com sinal maior.</span><span class="sxs-lookup"><span data-stu-id="64f2b-155">There are implicit conversions from a smaller unsigned integral type to a larger signed integral type.</span></span> <span data-ttu-id="64f2b-156">Também há uma conversão implícita de qualquer tipo integral para qualquer tipo de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="64f2b-156">There's also an implicit conversion from any integral type to any floating-point type.</span></span>  <span data-ttu-id="64f2b-157">Não há conversões implícitas de qualquer tipo integral com sinal para qualquer tipo integral sem sinal.</span><span class="sxs-lookup"><span data-stu-id="64f2b-157">There's no implicit conversion from any signed integral type to any unsigned integral type.</span></span>

<span data-ttu-id="64f2b-158">Você deverá usar uma conversão explícita para converter um tipo integral em outro tipo integral quando uma conversão implícita não for definida por meio do tipo de fonte para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="64f2b-158">You must use an explicit cast to convert one integral type to another integral type when an implicit conversion is not defined from the source type to the destination type.</span></span> <span data-ttu-id="64f2b-159">Isso é chamado de *conversão de estreitamento*.</span><span class="sxs-lookup"><span data-stu-id="64f2b-159">This is called a *narrowing conversion*.</span></span> <span data-ttu-id="64f2b-160">O caso explícito é necessário porque a conversão pode resultar em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="64f2b-160">The explicit case is required because the conversion can result in data loss.</span></span>

## <a name="see-also"></a><span data-ttu-id="64f2b-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64f2b-161">See also</span></span>

- [<span data-ttu-id="64f2b-162">Especificação da linguagem C# – Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="64f2b-162">C# language specification - Integral types</span></span>](~/_csharplang/spec/types.md#integral-types)
- [<span data-ttu-id="64f2b-163">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="64f2b-163">C# reference</span></span>](../index.md)
- [<span data-ttu-id="64f2b-164">Tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="64f2b-164">Floating-point types</span></span>](floating-point-numeric-types.md)
- [<span data-ttu-id="64f2b-165">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="64f2b-165">Default values table</span></span>](../keywords/default-values-table.md)
- [<span data-ttu-id="64f2b-166">Tabela de formatação de resultados numéricos</span><span class="sxs-lookup"><span data-stu-id="64f2b-166">Formatting numeric results table</span></span>](../keywords/formatting-numeric-results-table.md)
- [<span data-ttu-id="64f2b-167">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="64f2b-167">Built-in types table</span></span>](../keywords/built-in-types-table.md)
- [<span data-ttu-id="64f2b-168">Numéricos no .NET</span><span class="sxs-lookup"><span data-stu-id="64f2b-168">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>

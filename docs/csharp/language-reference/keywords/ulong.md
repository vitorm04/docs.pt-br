---
title: Palavra-chave ulong (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: d0c7df4ebda13a59e51e9599699f6abf4bbf1d71
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143422"
---
# <a name="ulong-c-reference"></a><span data-ttu-id="6d1a2-102">ulong (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6d1a2-102">ulong (C# Reference)</span></span>

<span data-ttu-id="6d1a2-103">A palavra-chave `ulong` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="6d1a2-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="6d1a2-104">Type</span></span>|<span data-ttu-id="6d1a2-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="6d1a2-105">Range</span></span>|<span data-ttu-id="6d1a2-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="6d1a2-106">Size</span></span>|<span data-ttu-id="6d1a2-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="6d1a2-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ulong`|<span data-ttu-id="6d1a2-108">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="6d1a2-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="6d1a2-109">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="6d1a2-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="6d1a2-110">Literais</span><span class="sxs-lookup"><span data-stu-id="6d1a2-110">Literals</span></span>

<span data-ttu-id="6d1a2-111">Você pode declarar e inicializar uma variável `ulong` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="6d1a2-112">Se o literal inteiro estiver fora do intervalo de `ulong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="6d1a2-113">No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ulong`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> <span data-ttu-id="6d1a2-114">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="6d1a2-115">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6d1a2-116">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="6d1a2-117">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="6d1a2-118">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="6d1a2-119">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="6d1a2-120">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-120">Some examples are shown below.</span></span>

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="6d1a2-121">Literais inteiros também podem incluir um sufixo que indica o tipo.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="6d1a2-122">O sufixo `UL` ou `ul` identifica inequivocamente um literal numérico como um valor `ulong`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="6d1a2-123">O sufixo `L` denota um `ulong` se o valor literal excede <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d1a2-124">E o sufixo `U` ou `u` denota um `ulong` se o valor literal excede <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d1a2-125">O exemplo a seguir usa o sufixo `ul` para indicar um inteiro longo:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-125">The following example uses the `ul` suffix to denote a long integer:</span></span>

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="6d1a2-126">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="6d1a2-127">int</span><span class="sxs-lookup"><span data-stu-id="6d1a2-127">int</span></span>](int.md)
2. [<span data-ttu-id="6d1a2-128">uint</span><span class="sxs-lookup"><span data-stu-id="6d1a2-128">uint</span></span>](uint.md)
3. [<span data-ttu-id="6d1a2-129">long</span><span class="sxs-lookup"><span data-stu-id="6d1a2-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="6d1a2-130">Resolução de sobrecarga do compilador</span><span class="sxs-lookup"><span data-stu-id="6d1a2-130">Compiler overload resolution</span></span>

<span data-ttu-id="6d1a2-131">Um uso comum do sufixo é a chamada de métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="6d1a2-132">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ulong` e [int](int.md):</span><span class="sxs-lookup"><span data-stu-id="6d1a2-132">Consider, for example, the following overloaded methods that use `ulong` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

<span data-ttu-id="6d1a2-133">Usar o sufixo com o parâmetro `ulong` garante que o tipo correto seja chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a><span data-ttu-id="6d1a2-134">Conversões</span><span class="sxs-lookup"><span data-stu-id="6d1a2-134">Conversions</span></span>

<span data-ttu-id="6d1a2-135">Há uma conversão implícita predefinida de `ulong` para [float](float.md), [double](double.md) ou [decimal](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="6d1a2-135">There is a predefined implicit conversion from `ulong` to [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="6d1a2-136">Não há nenhuma conversão implícita de `ulong` em qualquer tipo integral.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="6d1a2-137">Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

<span data-ttu-id="6d1a2-138">Há uma conversão implícita predefinida de [byte](byte.md), [ushort](ushort.md), [uint](uint.md) ou [char](char.md) em `ulong`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-138">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), [uint](uint.md), or [char](char.md) to `ulong`.</span></span>

<span data-ttu-id="6d1a2-139">Além disso, não há conversão implícita de tipos de ponto flutuante em `ulong`.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="6d1a2-140">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="6d1a2-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

<span data-ttu-id="6d1a2-141">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](float.md) e [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="6d1a2-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="6d1a2-142">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="6d1a2-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6d1a2-143">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6d1a2-143">C# language specification</span></span>

<span data-ttu-id="6d1a2-144">Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d1a2-144">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6d1a2-145">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="6d1a2-145">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d1a2-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d1a2-146">See also</span></span>

- <xref:System.UInt64>
- [<span data-ttu-id="6d1a2-147">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6d1a2-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d1a2-148">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6d1a2-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d1a2-149">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="6d1a2-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6d1a2-150">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="6d1a2-150">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="6d1a2-151">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="6d1a2-151">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="6d1a2-152">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="6d1a2-152">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d1a2-153">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="6d1a2-153">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)

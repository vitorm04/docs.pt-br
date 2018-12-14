---
title: Palavra-chave uint (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 86cbb216bd960251ebd78916fae7865aa10aa5fc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149686"
---
# <a name="uint-c-reference"></a><span data-ttu-id="be6b9-102">uint (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="be6b9-102">uint (C# Reference)</span></span>

<span data-ttu-id="be6b9-103">A palavra-chave `uint` significa um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="be6b9-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="be6b9-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="be6b9-104">Type</span></span>|<span data-ttu-id="be6b9-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="be6b9-105">Range</span></span>|<span data-ttu-id="be6b9-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="be6b9-106">Size</span></span>|<span data-ttu-id="be6b9-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="be6b9-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`uint`|<span data-ttu-id="be6b9-108">0 a 4.294.967.295</span><span class="sxs-lookup"><span data-stu-id="be6b9-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="be6b9-109">Inteiro de 32 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="be6b9-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|

<span data-ttu-id="be6b9-110">**Observação** O tipo `uint` não está em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="be6b9-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="be6b9-111">Use `int` sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="be6b9-111">Use `int` whenever possible.</span></span>

## <a name="literals"></a><span data-ttu-id="be6b9-112">Literais</span><span class="sxs-lookup"><span data-stu-id="be6b9-112">Literals</span></span>

<span data-ttu-id="be6b9-113">Você pode declarar e inicializar uma variável `uint` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="be6b9-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="be6b9-114">Se o literal inteiro estiver fora do intervalo de `uint` (ou seja, se for menor que <xref:System.UInt32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="be6b9-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="be6b9-115">No exemplo a seguir, inteiros iguais a 3.000.000.000 representados como literais decimais, hexadecimais e binários são atribuídos a valores `uint`.</span><span class="sxs-lookup"><span data-stu-id="be6b9-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> <span data-ttu-id="be6b9-116">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="be6b9-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="be6b9-117">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="be6b9-117">Decimal literals have no prefix.</span></span>

<span data-ttu-id="be6b9-118">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade:</span><span class="sxs-lookup"><span data-stu-id="be6b9-118">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="be6b9-119">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="be6b9-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="be6b9-120">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="be6b9-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="be6b9-121">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="be6b9-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="be6b9-122">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="be6b9-122">Some examples are shown below.</span></span>

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

<span data-ttu-id="be6b9-123">Literais inteiros também podem incluir um sufixo que indica o tipo.</span><span class="sxs-lookup"><span data-stu-id="be6b9-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="be6b9-124">O sufixo `U` ou 'u' indica um `uint` ou um `ulong`, dependendo do valor numérico do literal.</span><span class="sxs-lookup"><span data-stu-id="be6b9-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="be6b9-125">O exemplo a seguir usa o sufixo `u` para indicar um inteiro sem sinal dos dois tipos.</span><span class="sxs-lookup"><span data-stu-id="be6b9-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="be6b9-126">Observe que o primeiro literal é um `uint` porque seu valor é menor que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, enquanto o segundo é um `ulong` porque seu valor é maior que <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="be6b9-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

<span data-ttu-id="be6b9-127">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="be6b9-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="be6b9-128">int</span><span class="sxs-lookup"><span data-stu-id="be6b9-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="be6b9-129">long</span><span class="sxs-lookup"><span data-stu-id="be6b9-129">long</span></span>](long.md)
4. [<span data-ttu-id="be6b9-130">ulong</span><span class="sxs-lookup"><span data-stu-id="be6b9-130">ulong</span></span>](ulong.md)

## <a name="conversions"></a><span data-ttu-id="be6b9-131">Conversões</span><span class="sxs-lookup"><span data-stu-id="be6b9-131">Conversions</span></span>

<span data-ttu-id="be6b9-132">Há uma conversão implícita predefinida de `uint` para [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md) ou [decimal](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="be6b9-132">There is a predefined implicit conversion from `uint` to [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span> <span data-ttu-id="be6b9-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="be6b9-133">For example:</span></span>

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

<span data-ttu-id="be6b9-134">Há uma conversão implícita predefinida de [byte](byte.md), [ushort](ushort.md) ou [char](char.md) para `uint`.</span><span class="sxs-lookup"><span data-stu-id="be6b9-134">There is a predefined implicit conversion from [byte](byte.md), [ushort](ushort.md), or [char](char.md) to `uint`.</span></span> <span data-ttu-id="be6b9-135">Caso contrário, você deve usar uma conversão.</span><span class="sxs-lookup"><span data-stu-id="be6b9-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="be6b9-136">Por exemplo, a instrução de atribuição a seguir produzirá um erro de compilação sem uma conversão:</span><span class="sxs-lookup"><span data-stu-id="be6b9-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

<span data-ttu-id="be6b9-137">Observe também que não há conversão implícita de tipos de ponto flutuante em `uint`.</span><span class="sxs-lookup"><span data-stu-id="be6b9-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="be6b9-138">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="be6b9-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

<span data-ttu-id="be6b9-139">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](float.md) e [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="be6b9-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="be6b9-140">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="be6b9-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="be6b9-141">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="be6b9-141">C# language specification</span></span>

<span data-ttu-id="be6b9-142">Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="be6b9-142">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="be6b9-143">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="be6b9-143">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="be6b9-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be6b9-144">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="be6b9-145">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="be6b9-145">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be6b9-146">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="be6b9-146">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be6b9-147">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="be6b9-147">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be6b9-148">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="be6b9-148">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="be6b9-149">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="be6b9-149">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="be6b9-150">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="be6b9-150">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="be6b9-151">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="be6b9-151">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
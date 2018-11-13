---
title: ushort (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: fa7f80f8f0fd6efa92242949ef16963213d0a28e
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744477"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="35200-102">ushort (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="35200-102">ushort (C# Reference)</span></span>

<span data-ttu-id="35200-103">A palavra-chave `ushort` indica um tipo de dados integrais que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="35200-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="35200-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="35200-104">Type</span></span>|<span data-ttu-id="35200-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="35200-105">Range</span></span>|<span data-ttu-id="35200-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="35200-106">Size</span></span>|<span data-ttu-id="35200-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="35200-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="35200-108">0 a 65.535</span><span class="sxs-lookup"><span data-stu-id="35200-108">0 to 65,535</span></span>|<span data-ttu-id="35200-109">Inteiro de 16 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="35200-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="35200-110">Literais</span><span class="sxs-lookup"><span data-stu-id="35200-110">Literals</span></span>  

<span data-ttu-id="35200-111">Você pode declarar e inicializar uma variável `ushort` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="35200-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="35200-112">Se o literal inteiro estiver fora do intervalo de `ushort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="35200-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="35200-113">No exemplo a seguir, inteiros iguais a 65.034 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `ushort`.</span><span class="sxs-lookup"><span data-stu-id="35200-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="35200-114">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="35200-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="35200-115">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="35200-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="35200-116">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="35200-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="35200-117">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="35200-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="35200-118">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="35200-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="35200-119">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="35200-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="35200-120">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="35200-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="35200-121">Resolução de sobrecarga do compilador</span><span class="sxs-lookup"><span data-stu-id="35200-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="35200-122">Uma conversão deve ser usada ao chamar métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="35200-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="35200-123">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ushort` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="35200-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="35200-124">O uso da conversão `ushort` garante que o tipo correto será chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="35200-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="35200-125">Conversões</span><span class="sxs-lookup"><span data-stu-id="35200-125">Conversions</span></span>  
 <span data-ttu-id="35200-126">Há uma conversão implícita predefinida de `ushort` para [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="35200-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="35200-127">Há uma conversão implícita predefinida de [byte](../../../csharp/language-reference/keywords/byte.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `ushort`.</span><span class="sxs-lookup"><span data-stu-id="35200-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="35200-128">Caso contrário, uma conversão deve ser usada para executar uma conversão explícita.</span><span class="sxs-lookup"><span data-stu-id="35200-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="35200-129">Considere, por exemplo, as duas variáveis `ushort` `x` e `y` a seguir:</span><span class="sxs-lookup"><span data-stu-id="35200-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="35200-130">A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.</span><span class="sxs-lookup"><span data-stu-id="35200-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="35200-131">Para corrigir esse problema, use uma conversão:</span><span class="sxs-lookup"><span data-stu-id="35200-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="35200-132">No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:</span><span class="sxs-lookup"><span data-stu-id="35200-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="35200-133">Observe também que não há conversão implícita de tipos de ponto flutuante em `ushort`.</span><span class="sxs-lookup"><span data-stu-id="35200-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="35200-134">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="35200-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="35200-135">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="35200-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="35200-136">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="35200-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="35200-137">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="35200-137">C# Language Specification</span></span>  

<span data-ttu-id="35200-138">Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="35200-138">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="35200-139">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="35200-139">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="35200-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35200-140">See Also</span></span>

- <xref:System.UInt16>  
- [<span data-ttu-id="35200-141">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="35200-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="35200-142">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="35200-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="35200-143">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="35200-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="35200-144">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="35200-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="35200-145">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="35200-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="35200-146">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="35200-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="35200-147">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="35200-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

---
title: sbyte (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: 94968ed61fced9716112740613a4e3a86622e2e3
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028052"
---
# <a name="sbyte-c-reference"></a><span data-ttu-id="7c127-102">sbyte (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7c127-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="7c127-103">`sbyte` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c127-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="7c127-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="7c127-104">Type</span></span>|<span data-ttu-id="7c127-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="7c127-105">Range</span></span>|<span data-ttu-id="7c127-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="7c127-106">Size</span></span>|<span data-ttu-id="7c127-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="7c127-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="7c127-108">-128 a 127</span><span class="sxs-lookup"><span data-stu-id="7c127-108">-128 to 127</span></span>|<span data-ttu-id="7c127-109">Inteiro de 8 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="7c127-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="7c127-110">Literais</span><span class="sxs-lookup"><span data-stu-id="7c127-110">Literals</span></span>  

<span data-ttu-id="7c127-111">Você pode declarar e inicializar uma variável `sbyte` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="7c127-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="7c127-112">No exemplo a seguir, inteiros iguais a -102 representados como literais decimais, hexadecimais e binários são convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="7c127-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> <span data-ttu-id="7c127-113">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="7c127-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="7c127-114">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="7c127-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="7c127-115">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="7c127-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="7c127-116">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="7c127-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="7c127-117">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="7c127-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="7c127-118">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="7c127-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

 <span data-ttu-id="7c127-119">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="7c127-119">Some examples are shown below.</span></span>

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

<span data-ttu-id="7c127-120">Se o literal inteiro estiver fora do intervalo de `sbyte` (ou seja, se for menor que <xref:System.SByte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.SByte.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="7c127-120">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="7c127-121">Quando um literal inteiro não tem sufixo, seu tipo é o primeiro desses tipos em que seu valor pode ser representado: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="7c127-121">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="7c127-122">Isso significa que, neste exemplo, os literais numéricos `0x9A` e `0b10011010` são interpretados como inteiros com sinal de 32 bits com um valor de 156, que excede <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c127-122">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c127-123">Por causa disso, o operador de conversão é necessário e a atribuição deve ocorrer em um contexto [não selecionado](unchecked.md).</span><span class="sxs-lookup"><span data-stu-id="7c127-123">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="7c127-124">Resolução de sobrecarga do compilador</span><span class="sxs-lookup"><span data-stu-id="7c127-124">Compiler overload resolution</span></span>

 <span data-ttu-id="7c127-125">Uma conversão deve ser usada ao chamar métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="7c127-125">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="7c127-126">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `sbyte` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="7c127-126">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="7c127-127">O uso da conversão `sbyte` garante que o tipo correto será chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c127-127">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="7c127-128">Conversões</span><span class="sxs-lookup"><span data-stu-id="7c127-128">Conversions</span></span>  
 <span data-ttu-id="7c127-129">Há uma conversão implícita predefinida de `sbyte` para [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="7c127-129">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="7c127-130">Não é possível converter implicitamente tipos numéricos não literais com tamanho de armazenamento maior em `sbyte` (consulte a [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para ver os tamanhos de armazenamento de tipos integrais).</span><span class="sxs-lookup"><span data-stu-id="7c127-130">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="7c127-131">Considere, por exemplo, as duas variáveis `sbyte` `x` e `y` a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c127-131">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="7c127-132">A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como [int](../../../csharp/language-reference/keywords/int.md) por padrão.</span><span class="sxs-lookup"><span data-stu-id="7c127-132">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="7c127-133">Para corrigir esse problema, converta a expressão como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c127-133">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="7c127-134">No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:</span><span class="sxs-lookup"><span data-stu-id="7c127-134">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="7c127-135">Observe também que não há conversão implícita de tipos de ponto flutuante em `sbyte`.</span><span class="sxs-lookup"><span data-stu-id="7c127-135">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="7c127-136">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="7c127-136">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="7c127-137">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="7c127-137">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="7c127-138">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="7c127-138">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7c127-139">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7c127-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c127-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c127-140">See Also</span></span>  
 <xref:System.SByte>  
 [<span data-ttu-id="7c127-141">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7c127-141">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7c127-142">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7c127-142">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7c127-143">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7c127-143">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7c127-144">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="7c127-144">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="7c127-145">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="7c127-145">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="7c127-146">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="7c127-146">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="7c127-147">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="7c127-147">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

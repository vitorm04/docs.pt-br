---
title: "byte (Referência de C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords: byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 231a491914071b1d43b5a8938e677be531726e75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="byte-c-reference"></a><span data-ttu-id="68d89-102">byte (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="68d89-102">byte (C# Reference)</span></span>

<span data-ttu-id="68d89-103">`byte` indica um tipo integral que armazena valores conforme indicado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="68d89-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="68d89-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="68d89-104">Type</span></span>|<span data-ttu-id="68d89-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="68d89-105">Range</span></span>|<span data-ttu-id="68d89-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="68d89-106">Size</span></span>|<span data-ttu-id="68d89-107">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="68d89-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="68d89-108">0 a 255</span><span class="sxs-lookup"><span data-stu-id="68d89-108">0 to 255</span></span>|<span data-ttu-id="68d89-109">Inteiro de 8 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="68d89-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="68d89-110">Literais</span><span class="sxs-lookup"><span data-stu-id="68d89-110">Literals</span></span>  

 <span data-ttu-id="68d89-111">Você pode declarar e inicializar uma variável `byte` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela.</span><span class="sxs-lookup"><span data-stu-id="68d89-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="68d89-112">Se o literal inteiro estiver fora do intervalo de `byte` (ou seja, se for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="68d89-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="68d89-113">No exemplo a seguir, inteiros iguais a 201 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `byte`.</span><span class="sxs-lookup"><span data-stu-id="68d89-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> <span data-ttu-id="68d89-114">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="68d89-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="68d89-115">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="68d89-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="68d89-116">Iniciando com o c# 7, alguns recursos foram adicionados melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="68d89-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="68d89-117">C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="68d89-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="68d89-118">7.2 c# permite `_` a ser usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="68d89-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="68d89-119">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="68d89-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="68d89-120">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="68d89-120">Some examples are shown below.</span></span>

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a><span data-ttu-id="68d89-121">Conversões</span><span class="sxs-lookup"><span data-stu-id="68d89-121">Conversions</span></span>  
 <span data-ttu-id="68d89-122">Há uma conversão implícita predefinida de `byte` para [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="68d89-122">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="68d89-123">Você não pode converter implicitamente para `byte` os tipos numéricos não literais de tamanho de armazenamento maior.</span><span class="sxs-lookup"><span data-stu-id="68d89-123">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="68d89-124">Para obter mais informações sobre os tamanhos de armazenamento de tipos integrais, consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="68d89-124">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="68d89-125">Considere, por exemplo, as duas variáveis `byte` `x` e `y` a seguir:</span><span class="sxs-lookup"><span data-stu-id="68d89-125">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="68d89-126">A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.</span><span class="sxs-lookup"><span data-stu-id="68d89-126">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="68d89-127">Para corrigir esse problema, use uma conversão:</span><span class="sxs-lookup"><span data-stu-id="68d89-127">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="68d89-128">No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:</span><span class="sxs-lookup"><span data-stu-id="68d89-128">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="68d89-129">Além disso, não há conversão implícita de tipos de ponto flutuante em `byte`.</span><span class="sxs-lookup"><span data-stu-id="68d89-129">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="68d89-130">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="68d89-130">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="68d89-131">Ao chamar métodos sobrecarregados, uma conversão deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="68d89-131">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="68d89-132">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `byte` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="68d89-132">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="68d89-133">O uso da conversão `byte` garante que o tipo correto será chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="68d89-133">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="68d89-134">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="68d89-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="68d89-135">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="68d89-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="68d89-136">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="68d89-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68d89-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68d89-137">See Also</span></span>  
 <xref:System.Byte>  
 [<span data-ttu-id="68d89-138">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="68d89-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="68d89-139">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="68d89-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="68d89-140">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="68d89-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="68d89-141">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="68d89-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="68d89-142">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="68d89-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="68d89-143">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="68d89-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="68d89-144">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="68d89-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

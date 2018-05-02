---
title: short (Referência de C#)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f73189891ecb52b81cfc1861a19194113ab2c32
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="short-c-reference"></a><span data-ttu-id="33e3e-102">short (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="33e3e-102">short (C# Reference)</span></span>

<span data-ttu-id="33e3e-103">`short` indica um tipo de dados integrais que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="33e3e-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="33e3e-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="33e3e-104">Type</span></span>|<span data-ttu-id="33e3e-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="33e3e-105">Range</span></span>|<span data-ttu-id="33e3e-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="33e3e-106">Size</span></span>|<span data-ttu-id="33e3e-107">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="33e3e-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="33e3e-108">-32.768 a 32.767</span><span class="sxs-lookup"><span data-stu-id="33e3e-108">-32,768 to 32,767</span></span>|<span data-ttu-id="33e3e-109">Inteiro de 16 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="33e3e-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="33e3e-110">Literais</span><span class="sxs-lookup"><span data-stu-id="33e3e-110">Literals</span></span>  

<span data-ttu-id="33e3e-111">Você pode declarar e inicializar uma variável `short` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="33e3e-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="33e3e-112">Se o literal inteiro estiver fora do intervalo de `short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="33e3e-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="33e3e-113">No exemplo a seguir, inteiros iguais a 1.034 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `short`.</span><span class="sxs-lookup"><span data-stu-id="33e3e-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> <span data-ttu-id="33e3e-114">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="33e3e-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="33e3e-115">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="33e3e-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="33e3e-116">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="33e3e-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="33e3e-117">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="33e3e-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="33e3e-118">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="33e3e-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="33e3e-119">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="33e3e-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="33e3e-120">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="33e3e-120">Some examples are shown below.</span></span>

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="33e3e-121">Resolução de sobrecarga do compilador</span><span class="sxs-lookup"><span data-stu-id="33e3e-121">Compiler overload resolution</span></span>

 <span data-ttu-id="33e3e-122">Uma conversão deve ser usada ao chamar métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="33e3e-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="33e3e-123">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `short` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="33e3e-123">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="33e3e-124">O uso da conversão `short` garante que o tipo correto será chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="33e3e-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="33e3e-125">Conversões</span><span class="sxs-lookup"><span data-stu-id="33e3e-125">Conversions</span></span>  

 <span data-ttu-id="33e3e-126">Há uma conversão implícita predefinida de `short` em [int](../../../csharp/language-reference/keywords/int.md), [longo](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [duplo](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="33e3e-126">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="33e3e-127">Não é possível converter implicitamente tipos numéricos não literais com tamanho de armazenamento maior em `short` (consulte a [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para ver os tamanhos de armazenamento de tipos integrais).</span><span class="sxs-lookup"><span data-stu-id="33e3e-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="33e3e-128">Considere, por exemplo, as duas variáveis `short` `x` e `y` a seguir:</span><span class="sxs-lookup"><span data-stu-id="33e3e-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="33e3e-129">A instrução de atribuição a seguir produz um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como [int](../../../csharp/language-reference/keywords/int.md) por padrão.</span><span class="sxs-lookup"><span data-stu-id="33e3e-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="33e3e-130">Para corrigir esse problema, use uma conversão:</span><span class="sxs-lookup"><span data-stu-id="33e3e-130">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="33e3e-131">Também é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:</span><span class="sxs-lookup"><span data-stu-id="33e3e-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="33e3e-132">Não há nenhuma conversão implícita de tipos de ponto flutuante para `short`.</span><span class="sxs-lookup"><span data-stu-id="33e3e-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="33e3e-133">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="33e3e-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="33e3e-134">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="33e3e-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="33e3e-135">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="33e3e-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="33e3e-136">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="33e3e-136">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33e3e-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33e3e-137">See Also</span></span>  
 <xref:System.Int16>  
 [<span data-ttu-id="33e3e-138">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="33e3e-138">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="33e3e-139">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="33e3e-139">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33e3e-140">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="33e3e-140">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="33e3e-141">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="33e3e-141">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="33e3e-142">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="33e3e-142">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="33e3e-143">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="33e3e-143">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="33e3e-144">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="33e3e-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

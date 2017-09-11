---
title: "ulong (Referência de C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c2da253e4da7a5d6cfa71116e4fcba7816441e92
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ulong-c-reference"></a><span data-ttu-id="2ae32-102">ulong (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="2ae32-102">ulong (C# Reference)</span></span>

<span data-ttu-id="2ae32-103">A palavra-chave `ulong` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="2ae32-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="2ae32-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="2ae32-104">Type</span></span>|<span data-ttu-id="2ae32-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="2ae32-105">Range</span></span>|<span data-ttu-id="2ae32-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="2ae32-106">Size</span></span>|<span data-ttu-id="2ae32-107">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ae32-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="2ae32-108">0 a 18.446.744.073.709.551.615</span><span class="sxs-lookup"><span data-stu-id="2ae32-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="2ae32-109">Inteiro de 64 bits sem sinal</span><span class="sxs-lookup"><span data-stu-id="2ae32-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="2ae32-110">Literais</span><span class="sxs-lookup"><span data-stu-id="2ae32-110">Literals</span></span>  

<span data-ttu-id="2ae32-111">Você pode declarar e inicializar uma variável `ulong` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela.</span><span class="sxs-lookup"><span data-stu-id="2ae32-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="2ae32-112">Se o literal inteiro estiver fora do intervalo de `ulong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=fullName> ou maior que <xref:System.UInt64.MaxValue?displayProperty=fullName>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="2ae32-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=fullName> or greater than <xref:System.UInt64.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="2ae32-113">No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2ae32-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
<span data-ttu-id="2ae32-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span><span class="sxs-lookup"><span data-stu-id="2ae32-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="2ae32-115">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="2ae32-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="2ae32-116">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="2ae32-116">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="2ae32-117">Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="2ae32-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="2ae32-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span><span class="sxs-lookup"><span data-stu-id="2ae32-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span></span>  
 
 <span data-ttu-id="2ae32-119">Literais inteiros também podem incluir um sufixo que indica o tipo.</span><span class="sxs-lookup"><span data-stu-id="2ae32-119">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="2ae32-120">O sufixo `UL` ou `ul` identifica inequivocamente um literal numérico como um valor `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2ae32-120">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="2ae32-121">O sufixo `L` denota um `ulong` se o valor literal excede <xref:System.Int64.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2ae32-121">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="2ae32-122">E o sufixo `U` ou `u` denota um `ulong` se o valor literal excede <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2ae32-122">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="2ae32-123">O exemplo a seguir usa o sufixo `ul` para indicar um inteiro longo:</span><span class="sxs-lookup"><span data-stu-id="2ae32-123">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
<span data-ttu-id="2ae32-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="2ae32-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span></span>

<span data-ttu-id="2ae32-125">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="2ae32-125">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="2ae32-126">int</span><span class="sxs-lookup"><span data-stu-id="2ae32-126">int</span></span>](int.md)
2. [<span data-ttu-id="2ae32-127">uint</span><span class="sxs-lookup"><span data-stu-id="2ae32-127">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="2ae32-128">long</span><span class="sxs-lookup"><span data-stu-id="2ae32-128">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="2ae32-129">Resolução de sobrecarga do compilador</span><span class="sxs-lookup"><span data-stu-id="2ae32-129">Compiler overload resolution</span></span>
  
 <span data-ttu-id="2ae32-130">Um uso comum do sufixo é a chamada de métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="2ae32-130">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="2ae32-131">Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ulong` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="2ae32-131">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="2ae32-132">Usar o sufixo com o parâmetro `ulong` garante que o tipo correto seja chamado, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2ae32-132">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="2ae32-133">Conversões</span><span class="sxs-lookup"><span data-stu-id="2ae32-133">Conversions</span></span>  
 <span data-ttu-id="2ae32-134">Há uma conversão implícita predefinida de `ulong` para [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="2ae32-134">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="2ae32-135">Não há nenhuma conversão implícita de `ulong` em qualquer tipo integral.</span><span class="sxs-lookup"><span data-stu-id="2ae32-135">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="2ae32-136">Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:</span><span class="sxs-lookup"><span data-stu-id="2ae32-136">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="2ae32-137">Há uma conversão implícita predefinida de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) em `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2ae32-137">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="2ae32-138">Além disso, não há conversão implícita de tipos de ponto flutuante em `ulong`.</span><span class="sxs-lookup"><span data-stu-id="2ae32-138">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="2ae32-139">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="2ae32-139">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="2ae32-140">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="2ae32-140">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="2ae32-141">Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="2ae32-141">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2ae32-142">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="2ae32-142">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2ae32-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ae32-143">See Also</span></span>  
 <span data-ttu-id="2ae32-144"><xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="2ae32-144"><xref:System.UInt64></span></span>   
 <span data-ttu-id="2ae32-145">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-145">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2ae32-146">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-146">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2ae32-147">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-147">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="2ae32-148">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-148">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="2ae32-149">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-149">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="2ae32-150">[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="2ae32-150">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="2ae32-151">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="2ae32-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)


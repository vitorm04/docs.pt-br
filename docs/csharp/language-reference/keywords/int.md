---
title: int (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 95ac267bc70d2e7873593c08e0b10cb50fefd8c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524038"
---
# <a name="int-c-reference"></a><span data-ttu-id="d30b2-102">int (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d30b2-102">int (C# Reference)</span></span>

<span data-ttu-id="d30b2-103">`int` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="d30b2-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="d30b2-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="d30b2-104">Type</span></span>|<span data-ttu-id="d30b2-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="d30b2-105">Range</span></span>|<span data-ttu-id="d30b2-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="d30b2-106">Size</span></span>|<span data-ttu-id="d30b2-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="d30b2-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`int`|<span data-ttu-id="d30b2-108">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="d30b2-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="d30b2-109">Inteiro de 32 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="d30b2-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="d30b2-110">Literais</span><span class="sxs-lookup"><span data-stu-id="d30b2-110">Literals</span></span>  
 
<span data-ttu-id="d30b2-111">Você pode declarar e inicializar uma variável `int` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="d30b2-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="d30b2-112">Se o literal inteiro estiver fora do intervalo de `int` (ou seja, se for menor que <xref:System.Int32.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int32.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="d30b2-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="d30b2-113">No exemplo a seguir, inteiros iguais a 90.946 representados como literais decimais, hexadecimais e binários são atribuídos a valores `int`.</span><span class="sxs-lookup"><span data-stu-id="d30b2-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="d30b2-114">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="d30b2-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="d30b2-115">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="d30b2-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="d30b2-116">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="d30b2-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="d30b2-117">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="d30b2-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="d30b2-118">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="d30b2-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="d30b2-119">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="d30b2-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="d30b2-120">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="d30b2-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="d30b2-121">Literais inteiros também podem incluir um sufixo que denote o tipo, embora não haja nenhum sufixo que indique o tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="d30b2-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="d30b2-122">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="d30b2-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="d30b2-123">uint</span><span class="sxs-lookup"><span data-stu-id="d30b2-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="d30b2-124">long</span><span class="sxs-lookup"><span data-stu-id="d30b2-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="d30b2-125">ulong</span><span class="sxs-lookup"><span data-stu-id="d30b2-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="d30b2-126">Nestes exemplos, o literal 90946 é do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="d30b2-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="d30b2-127">Conversões</span><span class="sxs-lookup"><span data-stu-id="d30b2-127">Conversions</span></span>  
 <span data-ttu-id="d30b2-128">Há uma conversão implícita predefinida de `int` para [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="d30b2-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="d30b2-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d30b2-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="d30b2-130">Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md)ou [char](../../../csharp/language-reference/keywords/char.md) para `int`.</span><span class="sxs-lookup"><span data-stu-id="d30b2-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="d30b2-131">Por exemplo, a instrução de atribuição a seguir produzirá um erro de compilação sem uma conversão:</span><span class="sxs-lookup"><span data-stu-id="d30b2-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="d30b2-132">Observe também que não há conversão implícita de tipos de ponto flutuante em `int`.</span><span class="sxs-lookup"><span data-stu-id="d30b2-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="d30b2-133">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="d30b2-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="d30b2-134">Para obter mais informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="d30b2-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d30b2-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d30b2-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d30b2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d30b2-136">See Also</span></span>

- <xref:System.Int32>  
- [<span data-ttu-id="d30b2-137">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d30b2-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d30b2-138">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d30b2-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d30b2-139">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d30b2-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="d30b2-140">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="d30b2-140">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="d30b2-141">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="d30b2-141">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="d30b2-142">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="d30b2-142">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="d30b2-143">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="d30b2-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

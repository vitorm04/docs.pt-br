---
title: "int (Referência de C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
dev_langs:
- CSharp
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
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
ms.sourcegitcommit: 935428cc9442a3e1d15eeb8942176c237bff4e22
ms.openlocfilehash: 6e87893bcd9800b61297e71b782028fec5116479
ms.contentlocale: pt-br
ms.lasthandoff: 08/22/2017

---
# <a name="int-c-reference"></a><span data-ttu-id="24a58-102">int (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="24a58-102">int (C# Reference)</span></span>

<span data-ttu-id="24a58-103">`int` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="24a58-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="24a58-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="24a58-104">Type</span></span>|<span data-ttu-id="24a58-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="24a58-105">Range</span></span>|<span data-ttu-id="24a58-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="24a58-106">Size</span></span>|<span data-ttu-id="24a58-107">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="24a58-107">.NET Framework type</span></span>|<span data-ttu-id="24a58-108">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="24a58-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="24a58-109">-2.147.483.648 a 2.147.483.647</span><span class="sxs-lookup"><span data-stu-id="24a58-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="24a58-110">Inteiro de 32 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="24a58-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=fullName>|<span data-ttu-id="24a58-111">0</span><span class="sxs-lookup"><span data-stu-id="24a58-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="24a58-112">Literais</span><span class="sxs-lookup"><span data-stu-id="24a58-112">Literals</span></span>  
 
<span data-ttu-id="24a58-113">Você pode declarar e inicializar uma variável `int` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela.</span><span class="sxs-lookup"><span data-stu-id="24a58-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="24a58-114">Se o literal inteiro estiver fora do intervalo de `int` (ou seja, se for menor que <xref:System.Int32.MinValue?displayProperty=fullName> ou maior que <xref:System.Int32.MaxValue?displayProperty=fullName>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="24a58-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=fullName> or greater than <xref:System.Int32.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="24a58-115">No exemplo a seguir, inteiros iguais a 90.946 representados como literais decimais, hexadecimais e binários são atribuídos a valores `int`.</span><span class="sxs-lookup"><span data-stu-id="24a58-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
<span data-ttu-id="24a58-116">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]</span><span class="sxs-lookup"><span data-stu-id="24a58-116">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="24a58-117">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="24a58-117">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="24a58-118">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="24a58-118">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="24a58-119">Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="24a58-119">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="24a58-120">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]</span><span class="sxs-lookup"><span data-stu-id="24a58-120">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]</span></span>  
 
 <span data-ttu-id="24a58-121">Literais inteiros também podem incluir um sufixo que denote o tipo, embora não haja nenhum sufixo que indique o tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="24a58-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="24a58-122">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="24a58-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="24a58-123">uint</span><span class="sxs-lookup"><span data-stu-id="24a58-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="24a58-124">long</span><span class="sxs-lookup"><span data-stu-id="24a58-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="24a58-125">ulong</span><span class="sxs-lookup"><span data-stu-id="24a58-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="24a58-126">Nestes exemplos, o literal 90946 é do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="24a58-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="24a58-127">Conversões</span><span class="sxs-lookup"><span data-stu-id="24a58-127">Conversions</span></span>  
 <span data-ttu-id="24a58-128">Há uma conversão implícita predefinida de `int` para [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="24a58-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="24a58-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="24a58-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="24a58-130">Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md)ou [char](../../../csharp/language-reference/keywords/char.md) para `int`.</span><span class="sxs-lookup"><span data-stu-id="24a58-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="24a58-131">Por exemplo, a instrução de atribuição a seguir produzirá um erro de compilação sem uma conversão:</span><span class="sxs-lookup"><span data-stu-id="24a58-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="24a58-132">Observe também que não há conversão implícita de tipos de ponto flutuante em `int`.</span><span class="sxs-lookup"><span data-stu-id="24a58-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="24a58-133">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="24a58-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="24a58-134">Para obter mais informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="24a58-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="24a58-135">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="24a58-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="24a58-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24a58-136">See Also</span></span>  
 <span data-ttu-id="24a58-137"><xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="24a58-137"><xref:System.Int32></span></span>   
 <span data-ttu-id="24a58-138">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-138">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="24a58-139">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="24a58-140">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-140">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="24a58-141">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-141">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="24a58-142">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-142">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="24a58-143">[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="24a58-143">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="24a58-144">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="24a58-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)


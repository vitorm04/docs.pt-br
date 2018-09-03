---
title: long (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 52755e0914ead3ab61930dd8bfb9ecdd8ced0a14
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400830"
---
# <a name="long-c-reference"></a><span data-ttu-id="f7f28-102">long (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f7f28-102">long (C# Reference)</span></span>

<span data-ttu-id="f7f28-103">`long` indica um tipo integral que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f7f28-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="f7f28-104">Tipo</span><span class="sxs-lookup"><span data-stu-id="f7f28-104">Type</span></span>|<span data-ttu-id="f7f28-105">Intervalo</span><span class="sxs-lookup"><span data-stu-id="f7f28-105">Range</span></span>|<span data-ttu-id="f7f28-106">Tamanho</span><span class="sxs-lookup"><span data-stu-id="f7f28-106">Size</span></span>|<span data-ttu-id="f7f28-107">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="f7f28-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="f7f28-108">-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807</span><span class="sxs-lookup"><span data-stu-id="f7f28-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="f7f28-109">Inteiro de 64 bits com sinal</span><span class="sxs-lookup"><span data-stu-id="f7f28-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="f7f28-110">Literais</span><span class="sxs-lookup"><span data-stu-id="f7f28-110">Literals</span></span> 

<span data-ttu-id="f7f28-111">Você pode declarar e inicializar uma variável `long` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="f7f28-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="f7f28-112">No exemplo a seguir, inteiros iguais a 4.294.967.296 representados como literais decimais, hexadecimais e binários são atribuídos a valores `long`.</span><span class="sxs-lookup"><span data-stu-id="f7f28-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="f7f28-113">Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário.</span><span class="sxs-lookup"><span data-stu-id="f7f28-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="f7f28-114">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="f7f28-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="f7f28-115">Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.</span><span class="sxs-lookup"><span data-stu-id="f7f28-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="f7f28-116">O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.</span><span class="sxs-lookup"><span data-stu-id="f7f28-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="f7f28-117">O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo.</span><span class="sxs-lookup"><span data-stu-id="f7f28-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="f7f28-118">Um literal decimal não pode ter um sublinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="f7f28-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="f7f28-119">Alguns exemplos são mostrados abaixo.</span><span class="sxs-lookup"><span data-stu-id="f7f28-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="f7f28-120">Literais inteiros também podem incluir um sufixo que indica o tipo.</span><span class="sxs-lookup"><span data-stu-id="f7f28-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="f7f28-121">O sufixo `L` indica um `long`.</span><span class="sxs-lookup"><span data-stu-id="f7f28-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="f7f28-122">O exemplo a seguir usa o sufixo `L` para indicar um inteiro longo:</span><span class="sxs-lookup"><span data-stu-id="f7f28-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="f7f28-123">Você também pode usar a letra minúscula "l" como sufixo.</span><span class="sxs-lookup"><span data-stu-id="f7f28-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="f7f28-124">No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1".</span><span class="sxs-lookup"><span data-stu-id="f7f28-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="f7f28-125">Use "L" para fins de clareza.</span><span class="sxs-lookup"><span data-stu-id="f7f28-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="f7f28-126">Quando você usa o sufixo `L`, o tipo do inteiro integral é determinado para ser `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md), dependendo de seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="f7f28-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="f7f28-127">Nesse caso é `long` porque ele menor do que o intervalo de [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="f7f28-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="f7f28-128">Um uso comum do sufixo é para chamar métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="f7f28-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="f7f28-129">Por exemplo, os métodos sobrecarregados a seguir têm parâmetros do tipo `long` e [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="f7f28-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="f7f28-130">O sufixo `L` garante que a sobrecarga correta é chamada:</span><span class="sxs-lookup"><span data-stu-id="f7f28-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="f7f28-131">Se um literal inteiro não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:</span><span class="sxs-lookup"><span data-stu-id="f7f28-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="f7f28-132">int</span><span class="sxs-lookup"><span data-stu-id="f7f28-132">int</span></span>](int.md)
2. [<span data-ttu-id="f7f28-133">uint</span><span class="sxs-lookup"><span data-stu-id="f7f28-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="f7f28-134">ulong</span><span class="sxs-lookup"><span data-stu-id="f7f28-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="f7f28-135">O literal 4294967296 no exemplo anterior é do tipo `long` porque excede o intervalo de [uint](../../../csharp/language-reference/keywords/uint.md) (consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento de tipos integrais).</span><span class="sxs-lookup"><span data-stu-id="f7f28-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="f7f28-136">Se você usar o tipo `long` com outros tipos integrais na mesma expressão, a expressão será avaliada como `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) no caso de expressões relacionais ou boolianas).</span><span class="sxs-lookup"><span data-stu-id="f7f28-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="f7f28-137">Por exemplo, a expressão a seguir é avaliada como `long`:</span><span class="sxs-lookup"><span data-stu-id="f7f28-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="f7f28-138">Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="f7f28-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="f7f28-139">Conversões</span><span class="sxs-lookup"><span data-stu-id="f7f28-139">Conversions</span></span>  
 <span data-ttu-id="f7f28-140">Há uma conversão implícita predefinida de `long` para [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="f7f28-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="f7f28-141">Caso contrário, uma conversão deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="f7f28-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="f7f28-142">Por exemplo, a instrução a seguir produzirá um erro de compilação sem uma conversão explícita:</span><span class="sxs-lookup"><span data-stu-id="f7f28-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int y = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="f7f28-143">Há uma conversão implícita predefinida de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) para `long`.</span><span class="sxs-lookup"><span data-stu-id="f7f28-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="f7f28-144">Observe também que não há conversão implícita de tipos de ponto flutuante em `long`.</span><span class="sxs-lookup"><span data-stu-id="f7f28-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="f7f28-145">Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:</span><span class="sxs-lookup"><span data-stu-id="f7f28-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="f7f28-146">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f7f28-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7f28-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7f28-147">See Also</span></span>

- <xref:System.Int64>  
- [<span data-ttu-id="f7f28-148">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f7f28-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f7f28-149">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f7f28-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f7f28-150">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f7f28-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f7f28-151">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="f7f28-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="f7f28-152">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="f7f28-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="f7f28-153">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="f7f28-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="f7f28-154">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="f7f28-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

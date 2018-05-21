---
title: double (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 3683b51dfd0ef653ab8bfff6705b96a37e21a10a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="double-c-reference"></a><span data-ttu-id="07821-102">double (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="07821-102">double (C# Reference)</span></span>
<span data-ttu-id="07821-103">A palavra-chave `double` indica um tipo simples que armazena valores de ponto flutuante de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="07821-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="07821-104">A tabela a seguir mostra a precisão e o intervalo aproximado do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="07821-104">The following table shows the precision and approximate range for the `double` type.</span></span>  
  
|<span data-ttu-id="07821-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="07821-105">Type</span></span>|<span data-ttu-id="07821-106">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="07821-106">Approximate range</span></span>|<span data-ttu-id="07821-107">Precisão</span><span class="sxs-lookup"><span data-stu-id="07821-107">Precision</span></span>|<span data-ttu-id="07821-108">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="07821-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|<span data-ttu-id="07821-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="07821-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="07821-110">15 a 16 dígitos</span><span class="sxs-lookup"><span data-stu-id="07821-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="07821-111">Literais</span><span class="sxs-lookup"><span data-stu-id="07821-111">Literals</span></span>  
 <span data-ttu-id="07821-112">Por padrão, um literal numérico real no lado direito do operador de atribuição é tratado como `double`.</span><span class="sxs-lookup"><span data-stu-id="07821-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="07821-113">No entanto, se você quiser que um número inteiro seja tratado como `double`, use o sufixo d ou D, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="07821-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>  
  
```csharp  
double x = 3D;  
```  
  
## <a name="conversions"></a><span data-ttu-id="07821-114">Conversões</span><span class="sxs-lookup"><span data-stu-id="07821-114">Conversions</span></span>  
 <span data-ttu-id="07821-115">Você pode misturar tipos integrais numéricos e tipos de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="07821-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="07821-116">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="07821-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="07821-117">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="07821-117">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="07821-118">Se um dos tipos de ponto flutuantes for `double`, a expressão será avaliada como `double` ou [bool](../../../csharp/language-reference/keywords/bool.md) em expressões relacionais ou boolianas.</span><span class="sxs-lookup"><span data-stu-id="07821-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="07821-119">Se não houver um tipo `double` na expressão, ela será avaliada como [float](../../../csharp/language-reference/keywords/float.md) ou [bool](../../../csharp/language-reference/keywords/bool.md) em expressões relacionais ou boolianas.</span><span class="sxs-lookup"><span data-stu-id="07821-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="07821-120">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="07821-120">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="07821-121">Zero positivo e negativo.</span><span class="sxs-lookup"><span data-stu-id="07821-121">Positive and negative zero.</span></span>  
  
-   <span data-ttu-id="07821-122">Infinito positivo e negativo.</span><span class="sxs-lookup"><span data-stu-id="07821-122">Positive and negative infinity.</span></span>  
  
-   <span data-ttu-id="07821-123">Valor diferente de um número (NaN).</span><span class="sxs-lookup"><span data-stu-id="07821-123">Not-a-Number value (NaN).</span></span>  
  
-   <span data-ttu-id="07821-124">O conjunto finito de valores diferentes de zero.</span><span class="sxs-lookup"><span data-stu-id="07821-124">The finite set of nonzero values.</span></span>  
  
 <span data-ttu-id="07821-125">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](http://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="07821-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07821-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07821-126">Example</span></span>  
 <span data-ttu-id="07821-127">No exemplo a seguir, um [int](../../../csharp/language-reference/keywords/int.md), um [short](../../../csharp/language-reference/keywords/short.md), um [float](../../../csharp/language-reference/keywords/float.md) e um `double` são adicionados, levando a um resultado `double`.</span><span class="sxs-lookup"><span data-stu-id="07821-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="07821-128">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="07821-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07821-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07821-129">See Also</span></span>  
 [<span data-ttu-id="07821-130">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="07821-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="07821-131">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="07821-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="07821-132">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="07821-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="07821-133">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="07821-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="07821-134">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="07821-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="07821-135">Tabela de tipos de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="07821-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [<span data-ttu-id="07821-136">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="07821-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="07821-137">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="07821-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

---
title: float (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: edeed59da26c7007b23e1eec8c05fbd2e6d34d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219239"
---
# <a name="float-c-reference"></a><span data-ttu-id="1910f-102">float (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1910f-102">float (C# Reference)</span></span>
<span data-ttu-id="1910f-103">A palavra-chave `float` indica um tipo simples que armazena valores de ponto flutuante de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="1910f-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="1910f-104">A tabela a seguir mostra a precisão e o intervalo aproximado do tipo `float`.</span><span class="sxs-lookup"><span data-stu-id="1910f-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="1910f-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="1910f-105">Type</span></span>|<span data-ttu-id="1910f-106">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="1910f-106">Approximate range</span></span>|<span data-ttu-id="1910f-107">Precisão</span><span class="sxs-lookup"><span data-stu-id="1910f-107">Precision</span></span>|<span data-ttu-id="1910f-108">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1910f-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="1910f-109">-3,4 × 10<sup>38</sup> a +3,4 × 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="1910f-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="1910f-110">7 dígitos</span><span class="sxs-lookup"><span data-stu-id="1910f-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="1910f-111">Literais</span><span class="sxs-lookup"><span data-stu-id="1910f-111">Literals</span></span>  
 <span data-ttu-id="1910f-112">Por padrão, um literal numérico real no lado direito do operador de atribuição é tratado como [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="1910f-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="1910f-113">Portanto, para inicializar uma variável float, use o sufixo `f` ou `F`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1910f-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="1910f-114">Se você não usar o sufixo na declaração anterior, obterá um erro de compilação porque está tentando armazenar um valor [double](double.md) em uma variável `float`.</span><span class="sxs-lookup"><span data-stu-id="1910f-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="1910f-115">Conversões</span><span class="sxs-lookup"><span data-stu-id="1910f-115">Conversions</span></span>  
 <span data-ttu-id="1910f-116">Você pode misturar tipos integrais numéricos e tipos de ponto flutuante em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="1910f-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="1910f-117">Nesse caso, os tipos integrais são convertidos em tipos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="1910f-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="1910f-118">A avaliação da expressão é executada de acordo com as regras a seguir:</span><span class="sxs-lookup"><span data-stu-id="1910f-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="1910f-119">Se um dos tipos de ponto flutuantes for [double](double.md), a expressão será avaliada como [double](double.md) ou [bool](bool.md) em expressões relacionais ou boolianas.</span><span class="sxs-lookup"><span data-stu-id="1910f-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="1910f-120">Se não houver um tipo [double](double.md) na expressão, ela será avaliada como `float` ou [bool](bool.md) em expressões relacionais ou boolianas.</span><span class="sxs-lookup"><span data-stu-id="1910f-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="1910f-121">Uma expressão de ponto flutuante pode conter os seguintes conjuntos de valores:</span><span class="sxs-lookup"><span data-stu-id="1910f-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="1910f-122">Zero positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="1910f-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="1910f-123">Infinito positivo e negativo</span><span class="sxs-lookup"><span data-stu-id="1910f-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="1910f-124">Valor NaN (não é um número)</span><span class="sxs-lookup"><span data-stu-id="1910f-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="1910f-125">O conjunto finito de valores diferentes de zero</span><span class="sxs-lookup"><span data-stu-id="1910f-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="1910f-126">Para obter mais informações sobre esses valores, consulte o padrão IEEE para Aritmética de ponto flutuante binário, disponível no site do [IEEE](http://www.ieee.org).</span><span class="sxs-lookup"><span data-stu-id="1910f-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1910f-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1910f-127">Example</span></span>  
 <span data-ttu-id="1910f-128">No exemplo a seguir, um [int](int.md), um [short](short.md) e um `float` são incluídos em uma expressão matemática dando um resultado `float`.</span><span class="sxs-lookup"><span data-stu-id="1910f-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="1910f-129">(Lembre-se de que `float` é um alias para o tipo <xref:System.Single?displayProperty=nameWithType>.) Observe que não há nenhum [double](double.md) na expressão.</span><span class="sxs-lookup"><span data-stu-id="1910f-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1910f-130">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1910f-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1910f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1910f-131">See Also</span></span>  
 <xref:System.Single>  
 [<span data-ttu-id="1910f-132">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1910f-132">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1910f-133">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1910f-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1910f-134">Transmissões e conversões de tipo</span><span class="sxs-lookup"><span data-stu-id="1910f-134">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="1910f-135">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1910f-135">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="1910f-136">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="1910f-136">Integral Types Table</span></span>](integral-types-table.md)  
 [<span data-ttu-id="1910f-137">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="1910f-137">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="1910f-138">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="1910f-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="1910f-139">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="1910f-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)

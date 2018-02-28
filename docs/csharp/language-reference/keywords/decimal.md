---
title: "decimal (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0da001851c681fe4d698b920d9668b2f6b731e3a
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2018
---
# <a name="decimal-c-reference"></a><span data-ttu-id="3d1d2-102">decimal (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3d1d2-102">decimal (C# Reference)</span></span>
<span data-ttu-id="3d1d2-103">A palavra-chave `decimal` indica um tipo de dados de 128 bits.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="3d1d2-104">Comparado a outros tipos de pontos flutuantes, o tipo `decimal` tem mais precisão e um intervalo menor que o torna apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="3d1d2-105">O intervalo e a precisão aproximados para o tipo `decimal` são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>  
  
|<span data-ttu-id="3d1d2-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="3d1d2-106">Type</span></span>|<span data-ttu-id="3d1d2-107">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="3d1d2-107">Approximate Range</span></span>|<span data-ttu-id="3d1d2-108">Precisão</span><span class="sxs-lookup"><span data-stu-id="3d1d2-108">Precision</span></span>|<span data-ttu-id="3d1d2-109">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3d1d2-109">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|<span data-ttu-id="3d1d2-110">(-7,9 x 10<sup>28</sup> a 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> a 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="3d1d2-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="3d1d2-111">28 a 29 dígitos significativos</span><span class="sxs-lookup"><span data-stu-id="3d1d2-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  

<span data-ttu-id="3d1d2-112">O valor padrão de um `decimal` é 0m.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-112">The default value of a `decimal` is 0m.</span></span>
  
## <a name="literals"></a><span data-ttu-id="3d1d2-113">Literais</span><span class="sxs-lookup"><span data-stu-id="3d1d2-113">Literals</span></span>  
 <span data-ttu-id="3d1d2-114">Se você desejar tratar um literal numérico como `decimal`, use o sufixo m ou M, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3d1d2-114">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 <span data-ttu-id="3d1d2-115">Sem o sufixo m, o número será tratado como [double](../../../csharp/language-reference/keywords/double.md) e gerará um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-115">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="3d1d2-116">Conversões</span><span class="sxs-lookup"><span data-stu-id="3d1d2-116">Conversions</span></span>  
 <span data-ttu-id="3d1d2-117">Os tipos integrais são convertidos implicitamente em `decimal` e o resultado é avaliado como `decimal`.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-117">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="3d1d2-118">Portanto, você pode inicializar uma variável decimal com um literal inteiro sem o sufixo como a seguir:</span><span class="sxs-lookup"><span data-stu-id="3d1d2-118">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>  
  
```csharp
decimal myMoney = 300;  
```  
  
 <span data-ttu-id="3d1d2-119">Não há nenhuma conversão implícita entre outros tipos de pontos flutuantes e o tipo `decimal`. Portanto, uma conversão deve ser usada para converter entre esses dois tipos.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-119">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="3d1d2-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3d1d2-120">For example:</span></span>  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 <span data-ttu-id="3d1d2-121">Você também pode misturar `decimal` e tipos integrais numéricos na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-121">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="3d1d2-122">No entanto, misturar `decimal` e outros tipos de pontos flutuantes sem uma conversão causa um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-122">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>  
  
 <span data-ttu-id="3d1d2-123">Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="3d1d2-123">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="3d1d2-124">Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="3d1d2-124">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
## <a name="formatting-decimal-output"></a><span data-ttu-id="3d1d2-125">Formatando saída decimal</span><span class="sxs-lookup"><span data-stu-id="3d1d2-125">Formatting Decimal Output</span></span>  
 <span data-ttu-id="3d1d2-126">Você pode formatar os resultados ao usar o método `String.Format` ou <xref:System.Console.Write%2A?displayProperty=nameWithType> que chama `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-126">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="3d1d2-127">O formato de moeda é especificado ao usar a cadeia de caracteres de formato de moeda padrão "C" ou "c", como mostrado no segundo exemplo posteriormente neste artigo.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-127">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="3d1d2-128">Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-128">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d1d2-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d1d2-129">Example</span></span>  
 <span data-ttu-id="3d1d2-130">O exemplo a seguir causa um erro do compilador ao tentar adicionar variáveis [double](../../../csharp/language-reference/keywords/double.md) e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-130">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>  
  
```csharp  
decimal dec = 0m;
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 <span data-ttu-id="3d1d2-131">O resultado é o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="3d1d2-131">The result is the following error:</span></span>  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 <span data-ttu-id="3d1d2-132">Neste exemplo, um `decimal` e um [int](../../../csharp/language-reference/keywords/int.md) são misturados na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-132">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="3d1d2-133">O resultado é avaliado como o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-133">The result evaluates to the `decimal` type.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3d1d2-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3d1d2-134">Example</span></span>  
 <span data-ttu-id="3d1d2-135">Neste exemplo, a saída é formatada usando a cadeia de caracteres de formato de moeda.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="3d1d2-136">Observe que `x` é arredondado porque as casas decimais excedem US$ 0,99.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="3d1d2-137">A variável `y`, que representa os dígitos exatos máximos, é exibida exatamente no formato correto.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d1d2-138">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="3d1d2-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d1d2-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d1d2-139">See Also</span></span>  
 <xref:System.Decimal>  
 [<span data-ttu-id="3d1d2-140">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3d1d2-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3d1d2-141">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3d1d2-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d1d2-142">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="3d1d2-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3d1d2-143">Tabela de tipos integrais</span><span class="sxs-lookup"><span data-stu-id="3d1d2-143">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="3d1d2-144">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="3d1d2-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="3d1d2-145">Tabela de conversões numéricas implícitas</span><span class="sxs-lookup"><span data-stu-id="3d1d2-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="3d1d2-146">Tabela de conversões numéricas explícitas</span><span class="sxs-lookup"><span data-stu-id="3d1d2-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="3d1d2-147">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="3d1d2-147">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)

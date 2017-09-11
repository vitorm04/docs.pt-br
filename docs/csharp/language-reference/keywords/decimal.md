---
title: "decimal (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
dev_langs:
- CSharp
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
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
ms.openlocfilehash: 4c06d14f01302a21427845d0269fc8181a380914
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="decimal-c-reference"></a><span data-ttu-id="123e8-102">decimal (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="123e8-102">decimal (C# Reference)</span></span>
<span data-ttu-id="123e8-103">A palavra-chave `decimal` indica um tipo de dados de 128 bits.</span><span class="sxs-lookup"><span data-stu-id="123e8-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="123e8-104">Comparado a outros tipos de pontos flutuantes, o tipo `decimal` tem mais precisão e um intervalo menor que o torna apropriado para cálculos financeiros e monetários.</span><span class="sxs-lookup"><span data-stu-id="123e8-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="123e8-105">O intervalo e a precisão aproximados para o tipo `decimal` são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="123e8-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>  
  
|<span data-ttu-id="123e8-106">Tipo</span><span class="sxs-lookup"><span data-stu-id="123e8-106">Type</span></span>|<span data-ttu-id="123e8-107">Intervalo aproximado</span><span class="sxs-lookup"><span data-stu-id="123e8-107">Approximate Range</span></span>|<span data-ttu-id="123e8-108">Precisão</span><span class="sxs-lookup"><span data-stu-id="123e8-108">Precision</span></span>|<span data-ttu-id="123e8-109">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="123e8-109">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|<span data-ttu-id="123e8-110">(-7,9 x 10<sup>28</sup> a 7,9 x 10<sup>28</sup>) / (10<sup>0</sup> a 10<sup>28</sup>)</span><span class="sxs-lookup"><span data-stu-id="123e8-110">(-7.9 x 10<sup>28</sup> to 7.9 x 10<sup>28</sup>) / (10<sup>0</sup> to 10<sup>28</sup>)</span></span>|<span data-ttu-id="123e8-111">28 a 29 dígitos significativos</span><span class="sxs-lookup"><span data-stu-id="123e8-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="123e8-112">Literais</span><span class="sxs-lookup"><span data-stu-id="123e8-112">Literals</span></span>  
 <span data-ttu-id="123e8-113">Se você desejar tratar um literal numérico como `decimal`, use o sufixo m ou M, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="123e8-113">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>  
  
```csharp
decimal myMoney = 300.5m;  
```  
  
 <span data-ttu-id="123e8-114">Sem o sufixo m, o número será tratado como [double](../../../csharp/language-reference/keywords/double.md) e gerará um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="123e8-114">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="123e8-115">Conversões</span><span class="sxs-lookup"><span data-stu-id="123e8-115">Conversions</span></span>  
 <span data-ttu-id="123e8-116">Os tipos integrais são convertidos implicitamente em `decimal` e o resultado é avaliado como `decimal`.</span><span class="sxs-lookup"><span data-stu-id="123e8-116">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="123e8-117">Portanto, você pode inicializar uma variável decimal com um literal inteiro sem o sufixo como a seguir:</span><span class="sxs-lookup"><span data-stu-id="123e8-117">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>  
  
```csharp
decimal myMoney = 300;  
```  
  
 <span data-ttu-id="123e8-118">Não há nenhuma conversão implícita entre outros tipos de pontos flutuantes e o tipo `decimal`. Portanto, uma conversão deve ser usada para converter entre esses dois tipos.</span><span class="sxs-lookup"><span data-stu-id="123e8-118">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="123e8-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="123e8-119">For example:</span></span>  
  
```csharp
decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 <span data-ttu-id="123e8-120">Você também pode misturar `decimal` e tipos integrais numéricos na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="123e8-120">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="123e8-121">No entanto, misturar `decimal` e outros tipos de pontos flutuantes sem uma conversão causa um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="123e8-121">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>  
  
 <span data-ttu-id="123e8-122">Para obter mais informações sobre as conversões numéricas implícitas, consulte [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="123e8-122">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="123e8-123">Para obter mais informações sobre as conversões numéricas explícitas, consulte [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="123e8-123">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
## <a name="formatting-decimal-output"></a><span data-ttu-id="123e8-124">Formatando saída decimal</span><span class="sxs-lookup"><span data-stu-id="123e8-124">Formatting Decimal Output</span></span>  
 <span data-ttu-id="123e8-125">Você pode formatar os resultados ao usar o método `String.Format` ou <xref:System.Console.Write%2A?displayProperty=fullName> que chama `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="123e8-125">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> method, which calls `String.Format()`.</span></span> <span data-ttu-id="123e8-126">O formato de moeda é especificado ao usar a cadeia de caracteres de formato de moeda padrão "C" ou "c", como mostrado no segundo exemplo posteriormente neste artigo.</span><span class="sxs-lookup"><span data-stu-id="123e8-126">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="123e8-127">Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="123e8-127">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="123e8-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="123e8-128">Example</span></span>  
 <span data-ttu-id="123e8-129">O exemplo a seguir causa um erro do compilador ao tentar adicionar variáveis [double](../../../csharp/language-reference/keywords/double.md) e `decimal`.</span><span class="sxs-lookup"><span data-stu-id="123e8-129">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>  
  
```csharp  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
```  
  
 <span data-ttu-id="123e8-130">O resultado é o seguinte erro:</span><span class="sxs-lookup"><span data-stu-id="123e8-130">The result is the following error:</span></span>  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 <span data-ttu-id="123e8-131">Neste exemplo, um `decimal` e um [int](../../../csharp/language-reference/keywords/int.md) são misturados na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="123e8-131">In this example, a `decimal` and an [int](../../../csharp/language-reference/keywords/int.md) are mixed in the same expression.</span></span> <span data-ttu-id="123e8-132">O resultado é avaliado como o tipo `decimal`.</span><span class="sxs-lookup"><span data-stu-id="123e8-132">The result evaluates to the `decimal` type.</span></span>  
  
 <span data-ttu-id="123e8-133">[!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="123e8-133">[!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="123e8-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="123e8-134">Example</span></span>  
 <span data-ttu-id="123e8-135">Neste exemplo, a saída é formatada usando a cadeia de caracteres de formato de moeda.</span><span class="sxs-lookup"><span data-stu-id="123e8-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="123e8-136">Observe que `x` é arredondado porque as casas decimais excedem US$ 0,99.</span><span class="sxs-lookup"><span data-stu-id="123e8-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="123e8-137">A variável `y`, que representa os dígitos exatos máximos, é exibida exatamente no formato correto.</span><span class="sxs-lookup"><span data-stu-id="123e8-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>  
  
 <span data-ttu-id="123e8-138">[!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="123e8-138">[!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="123e8-139">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="123e8-139">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="123e8-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="123e8-140">See Also</span></span>  
 <span data-ttu-id="123e8-141"><xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="123e8-141"><xref:System.Decimal></span></span>   
 <span data-ttu-id="123e8-142">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="123e8-143">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="123e8-144">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-144">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="123e8-145">[Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-145">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="123e8-146">[Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-146">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="123e8-147">[Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-147">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="123e8-148">[Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="123e8-148">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="123e8-149">Cadeias de Caracteres de Formato Numérico Padrão</span><span class="sxs-lookup"><span data-stu-id="123e8-149">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)


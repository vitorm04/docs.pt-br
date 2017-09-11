---
title: Cadeias de caracteres interpoladas (C#)
ms.date: 2017-02-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 03d1e3f0897713e25be7d7f893861a3eb4dac211
ms.openlocfilehash: ee35da0a008a19ad643fffff64d74485237d716f
ms.contentlocale: pt-br
ms.lasthandoff: 09/11/2017

---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="85b33-102">Cadeias de caracteres interpoladas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="85b33-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="85b33-103">Usado para construir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85b33-103">Used to construct strings.</span></span>  <span data-ttu-id="85b33-104">Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="85b33-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="85b33-105">Uma cadeia de caracteres interpolada retorna uma cadeia de caracteres que substitui as expressões interpoladas que ela contém por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85b33-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span>  

<span data-ttu-id="85b33-106">Os argumentos de uma cadeia de caracteres interpolada são mais fáceis de entender do que uma [cadeia de caracteres de formato composto](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="85b33-106">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="85b33-107">Por exemplo, a cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="85b33-107">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}"); 
```  
<span data-ttu-id="85b33-108">contém duas expressões interpoladas, "{name}" e "{hours:hh}".</span><span class="sxs-lookup"><span data-stu-id="85b33-108">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="85b33-109">A cadeia de caracteres de formato composto equivalente é:</span><span class="sxs-lookup"><span data-stu-id="85b33-109">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);  
```  

<span data-ttu-id="85b33-110">A estrutura de uma cadeia de caracteres interpolada é:</span><span class="sxs-lookup"><span data-stu-id="85b33-110">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="85b33-111">em que:</span><span class="sxs-lookup"><span data-stu-id="85b33-111">where:</span></span> 

- <span data-ttu-id="85b33-112">*field-width* é um inteiro com sinal que indica o número de caracteres no campo.</span><span class="sxs-lookup"><span data-stu-id="85b33-112">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="85b33-113">Se ele for positivo, o campo será alinhado à direita. Se for negativo, será alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="85b33-113">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="85b33-114">*format-string* é uma cadeia de caracteres de formato apropriada para o tipo do objeto que está sendo formatado.</span><span class="sxs-lookup"><span data-stu-id="85b33-114">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="85b33-115">Por exemplo, para um valor @System.DateTime, pode ser uma cadeia de caracteres de formato de data e hora padrão, como "D" ou "d".</span><span class="sxs-lookup"><span data-stu-id="85b33-115">For example, for a @System.DateTime value, it could be a standard date and time format string such as "D" or "d".</span></span>

 <span data-ttu-id="85b33-116">Você pode usar uma cadeia de caracteres interpolada em qualquer lugar em que pode usar um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85b33-116">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="85b33-117">A cadeia de caracteres interpolada é avaliada sempre que o código com a cadeia de caracteres interpolada for executado.</span><span class="sxs-lookup"><span data-stu-id="85b33-117">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="85b33-118">Isso permite que você separe a definição e a avaliação de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="85b33-118">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="85b33-119">Para incluir uma chave ("{" ou "}") em uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="85b33-119">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="85b33-120">Consulte a seção sobre Conversões implícitas para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="85b33-120">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="85b33-121">Se a cadeia de caracteres interpolada contiver outros caracteres com significado especial em uma cadeia de caracteres interpolada, como aspas ("), dois-pontos (:) ou vírgulas (,), eles devem ser substituídos se ocorrerem no texto literal ou devem ser incluídos em uma expressão delimitada por parênteses se forem elementos de linguagem incluídos em uma expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="85b33-121">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="85b33-122">O exemplo a seguir ignora as aspas para incluí-las na cadeia de caracteres de resultado e usa parênteses para delimitar a expressão `(age == 1 ? "" : "s")`, de modo que os dois-pontos não sejam interpretados como o início de uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="85b33-122">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

<span data-ttu-id="85b33-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="85b33-123">[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]</span></span>  

## <a name="implicit-conversions"></a><span data-ttu-id="85b33-124">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="85b33-124">Implicit Conversions</span></span>  

<span data-ttu-id="85b33-125">Há três conversões de tipo implícitas de uma cadeia de caracteres interpolada:</span><span class="sxs-lookup"><span data-stu-id="85b33-125">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="85b33-126">Conversão de uma cadeia de caracteres interpolada em um @System.String.</span><span class="sxs-lookup"><span data-stu-id="85b33-126">Conversion of an interpolated string to a @System.String.</span></span> <span data-ttu-id="85b33-127">O exemplo a seguir retorna uma cadeia de caracteres cujas expressões de cadeia de caracteres interpolada foram substituídas por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85b33-127">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="85b33-128">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="85b33-128">For example:</span></span>

   <span data-ttu-id="85b33-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="85b33-129">[!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]</span></span>  

   <span data-ttu-id="85b33-130">Esse é o resultado final de uma interpretação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85b33-130">This is the final result of a string interpretation.</span></span> <span data-ttu-id="85b33-131">Todas as ocorrências de chaves duplas ("{{" e "}}") serão convertidas em uma chave única.</span><span class="sxs-lookup"><span data-stu-id="85b33-131">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="85b33-132">Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.IFormattable> que permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura de uma única instância <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="85b33-132">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="85b33-133">Isso é útil para incluir itens como os formatos de número e data corretos para culturas individuais.</span><span class="sxs-lookup"><span data-stu-id="85b33-133">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="85b33-134">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até que você formate a cadeia de caracteres explícita ou implicitamente chamando o método @System.Object.ToString.</span><span class="sxs-lookup"><span data-stu-id="85b33-134">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the @System.Object.ToString method.</span></span>  <span data-ttu-id="85b33-135">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="85b33-135">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="85b33-136">O exemplo a seguir usa reflexão para exibir os membros, bem como os valores de campo e propriedade de uma variável <xref:System.IFormattable> criada de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="85b33-136">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="85b33-137">Ela também passa a variável <xref:System.IFormattable> para o método @System.Console(System.String).</span><span class="sxs-lookup"><span data-stu-id="85b33-137">It also passes the <xref:System.IFormattable> variable to the @System.Console(System.String) method.</span></span>

   <span data-ttu-id="85b33-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="85b33-138">[!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]</span></span>  

   <span data-ttu-id="85b33-139">Observe que a cadeia de caracteres interpolada pode ser inspecionada somente usando a reflexão.</span><span class="sxs-lookup"><span data-stu-id="85b33-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="85b33-140">Se ela for passada para um método de formatação de cadeia de caracteres, como @System.Console.WriteLine(System.String), seus itens de formato serão resolvidos e a cadeia de caracteres de resultado será retornada.</span><span class="sxs-lookup"><span data-stu-id="85b33-140">If it is passed to a string formatting method, such as @System.Console.WriteLine(System.String), its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="85b33-141">Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.FormattableString> que representa uma cadeia de caracteres de formato composto.</span><span class="sxs-lookup"><span data-stu-id="85b33-141">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="85b33-142">Inspecionar a cadeia de caracteres de formato composto e como ela é renderizada como uma cadeia de caracteres de resultado pode, por exemplo, ajudar a proteger contra um ataque de injeção se você estiver criando uma consulta.</span><span class="sxs-lookup"><span data-stu-id="85b33-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span>  <span data-ttu-id="85b33-143"><xref:System.FormattableString> também inclui sobrecargas <xref:System.FormattableString.ToString> que permitem que você gere cadeias de caracteres de resultado para a @System.Globalization.InvariantCulture e a @System.Globalization.CurrentCulture.</span><span class="sxs-lookup"><span data-stu-id="85b33-143"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the @System.Globalization.InvariantCulture and @System.Globalization.CurrentCulture.</span></span>  <span data-ttu-id="85b33-144">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas, até você formatar.</span><span class="sxs-lookup"><span data-stu-id="85b33-144">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="85b33-145">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="85b33-145">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="85b33-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="85b33-146">[!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]</span></span>  

## <a name="language-specification"></a><span data-ttu-id="85b33-147">Especificação da linguagem</span><span class="sxs-lookup"><span data-stu-id="85b33-147">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85b33-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85b33-148">See Also</span></span>  
 <span data-ttu-id="85b33-149"><xref:System.IFormattable?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="85b33-149"><xref:System.IFormattable?displayProperty=fullName></span></span>   
 <span data-ttu-id="85b33-150"><xref:System.FormattableString?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="85b33-150"><xref:System.FormattableString?displayProperty=fullName></span></span>   
 <span data-ttu-id="85b33-151">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="85b33-151">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="85b33-152">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="85b33-152">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)


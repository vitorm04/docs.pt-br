---
title: Cadeias de caracteres interpoladas (C#)
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03315a2d9a44405ff520a1c333f56311e2657df6
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="a737d-102">Cadeias de caracteres interpoladas (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a737d-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="a737d-103">Usado para construir cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-103">Used to construct strings.</span></span>  <span data-ttu-id="a737d-104">Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="a737d-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="a737d-105">Uma cadeia de caracteres interpolada retorna uma cadeia de caracteres que substitui as expressões interpoladas que ela contém por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="a737d-106">Este recurso está disponível no C# 6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="a737d-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="a737d-107">Os argumentos de uma cadeia de caracteres interpolada são mais fáceis de entender do que uma [cadeia de caracteres de formato composto](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="a737d-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="a737d-108">Por exemplo, a cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="a737d-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="a737d-109">contém duas expressões interpoladas, "{name}" e "{hours:hh}".</span><span class="sxs-lookup"><span data-stu-id="a737d-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="a737d-110">A cadeia de caracteres de formato composto equivalente é:</span><span class="sxs-lookup"><span data-stu-id="a737d-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="a737d-111">A estrutura de uma cadeia de caracteres interpolada é:</span><span class="sxs-lookup"><span data-stu-id="a737d-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="a737d-112">em que:</span><span class="sxs-lookup"><span data-stu-id="a737d-112">where:</span></span> 

- <span data-ttu-id="a737d-113">*field-width* é um inteiro com sinal que indica o número de caracteres no campo.</span><span class="sxs-lookup"><span data-stu-id="a737d-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="a737d-114">Se ele for positivo, o campo será alinhado à direita. Se for negativo, será alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="a737d-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="a737d-115">*format-string* é uma cadeia de caracteres de formato apropriada para o tipo do objeto que está sendo formatado.</span><span class="sxs-lookup"><span data-stu-id="a737d-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="a737d-116">Por exemplo, para um valor <xref:System.DateTime>, pode ser uma cadeia de caracteres de formato de data e hora padrão, como "D" ou "d".</span><span class="sxs-lookup"><span data-stu-id="a737d-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a737d-117">Você não pode ter nenhum espaço em branco entre o `$` e `"` que iniciam a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="a737d-118">Fazer isso causa um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a737d-118">Doing so causes a compile-time error.</span></span>

 <span data-ttu-id="a737d-119">Você pode usar uma cadeia de caracteres interpolada em qualquer lugar em que pode usar um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="a737d-120">A cadeia de caracteres interpolada é avaliada sempre que o código com a cadeia de caracteres interpolada for executado.</span><span class="sxs-lookup"><span data-stu-id="a737d-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="a737d-121">Isso permite que você separe a definição e a avaliação de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="a737d-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="a737d-122">Para incluir uma chave ("{" ou "}") em uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="a737d-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="a737d-123">Consulte a seção sobre [Conversões Implícitas](#implicit-conversions) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="a737d-123">See the [Implicit Conversions](#implicit-conversions) section for more details.</span></span>  

<span data-ttu-id="a737d-124">Se a cadeia de caracteres interpolada contiver outros caracteres com significado especial em uma cadeia de caracteres interpolada, como aspas ("), dois-pontos (:) ou vírgulas (,), eles devem ser substituídos se ocorrerem no texto literal ou devem ser incluídos em uma expressão delimitada por parênteses se forem elementos de linguagem incluídos em uma expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="a737d-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="a737d-125">O exemplo a seguir ignora as aspas para incluí-las na cadeia de caracteres de resultado e usa parênteses para delimitar a expressão `(age == 1 ? "" : "s")`, de modo que os dois-pontos não sejam interpretados como o início de uma cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="a737d-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="a737d-126">As cadeias de caracteres textuais interpoladas usam o caractere `$` seguido pelo caractere `@`.</span><span class="sxs-lookup"><span data-stu-id="a737d-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="a737d-127">Para obter mais informações sobre cadeias de caracteres textuais, consulte o tópico [cadeia de caracteres](string.md).</span><span class="sxs-lookup"><span data-stu-id="a737d-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="a737d-128">O código a seguir é uma versão modificada do trecho de código anterior usando uma cadeia de caracteres textual interpolada:</span><span class="sxs-lookup"><span data-stu-id="a737d-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="a737d-129">As alterações de formatação são necessárias porque as cadeias de caracteres textuais não obedecem às sequências de escape `\`.</span><span class="sxs-lookup"><span data-stu-id="a737d-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a737d-130">O token `$` deve aparecer antes do token `@` em uma cadeia de caracteres textual interpolada.</span><span class="sxs-lookup"><span data-stu-id="a737d-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="a737d-131">Conversões implícitas</span><span class="sxs-lookup"><span data-stu-id="a737d-131">Implicit Conversions</span></span>  

<span data-ttu-id="a737d-132">Há três conversões de tipo implícitas de uma cadeia de caracteres interpolada:</span><span class="sxs-lookup"><span data-stu-id="a737d-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="a737d-133">Conversão de uma cadeia de caracteres interpolada em um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a737d-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="a737d-134">O exemplo a seguir retorna uma cadeia de caracteres cujas expressões de cadeia de caracteres interpolada foram substituídas por suas representações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="a737d-135">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a737d-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="a737d-136">Esse é o resultado final de uma interpretação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a737d-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="a737d-137">Todas as ocorrências de chaves duplas ("{{" e "}}") serão convertidas em uma chave única.</span><span class="sxs-lookup"><span data-stu-id="a737d-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="a737d-138">Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.IFormattable>, que permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura de uma única instância <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="a737d-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="a737d-139">Isso é útil para incluir itens como os formatos de número e data corretos para culturas individuais.</span><span class="sxs-lookup"><span data-stu-id="a737d-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="a737d-140">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas até que você formate a cadeia de caracteres explícita ou implicitamente chamando o método <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="a737d-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="a737d-141">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a737d-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="a737d-142">O exemplo a seguir usa reflexão para exibir os membros, bem como os valores de campo e propriedade de uma variável <xref:System.IFormattable> criada de uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="a737d-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="a737d-143">Ele também passa a variável <xref:System.IFormattable> para o método <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a737d-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="a737d-144">Observe que a cadeia de caracteres interpolada pode ser inspecionada somente usando a reflexão.</span><span class="sxs-lookup"><span data-stu-id="a737d-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="a737d-145">Se ela for passada para um método de formatação de cadeia de caracteres, como <xref:System.Console.WriteLine(System.String)>, seus itens de formato serão resolvidos e a cadeia de caracteres de resultado será retornada.</span><span class="sxs-lookup"><span data-stu-id="a737d-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="a737d-146">Conversão de uma cadeia de caracteres interpolada em uma variável <xref:System.FormattableString> que representa uma cadeia de caracteres de formato composto.</span><span class="sxs-lookup"><span data-stu-id="a737d-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="a737d-147">Inspecionar a cadeia de caracteres de formato composto e como ela é renderizada como uma cadeia de caracteres de resultado pode, por exemplo, ajudar a proteger contra um ataque de injeção se você estiver criando uma consulta.</span><span class="sxs-lookup"><span data-stu-id="a737d-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="a737d-148"><xref:System.FormattableString> também inclui sobrecargas <xref:System.FormattableString.ToString> que permitem que você gere cadeias de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture> e a <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="a737d-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="a737d-149">Todas as ocorrências de chaves duplas ("{{" e "}}") permanecem como chaves duplas, até você formatar.</span><span class="sxs-lookup"><span data-stu-id="a737d-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="a737d-150">Todas as expressões de interpolação contidas são convertidas em {0}, {1} e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="a737d-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="a737d-151">Especificação da linguagem</span><span class="sxs-lookup"><span data-stu-id="a737d-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a737d-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a737d-152">See also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a737d-153">Interpolação de cadeia de caracteres no C#</span><span class="sxs-lookup"><span data-stu-id="a737d-153">String Interpolation in C#</span></span>](../../../csharp/tutorials/string-interpolation.md)  
 [<span data-ttu-id="a737d-154">Cadeias de caracteres interpoladas em C#</span><span class="sxs-lookup"><span data-stu-id="a737d-154">Interpolated strings in C#</span></span>](../../../csharp/quick-starts/interpolated-strings.yml)  
 [<span data-ttu-id="a737d-155">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a737d-155">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a737d-156">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a737d-156">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

---
title: $ – interpolação de cadeia de caracteres (Referência de C#)
description: A interpolação de cadeia de caracteres oferece uma sintaxe mais legível e conveniente para formatar a saída de cadeia de caracteres de formatação do que a tradicional formatação composta da cadeia de caracteres.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058820"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="253b0-103">$ – interpolação de cadeia de caracteres (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="253b0-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="253b0-104">O caractere especial `$` identifica um literal de cadeia de caracteres como uma *cadeia de caracteres interpolada*.</span><span class="sxs-lookup"><span data-stu-id="253b0-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="253b0-105">Uma cadeia de caracteres interpolada é um literal de cadeia de caracteres que pode conter *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="253b0-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="253b0-106">Quando uma cadeia de caracteres interpolada é resolvida em uma cadeia de caracteres de resultado, itens com expressões interpoladas são substituídos pelas representações de cadeia de caracteres dos resultados da expressão.</span><span class="sxs-lookup"><span data-stu-id="253b0-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="253b0-107">Este recurso está disponível no C# 6 e em versões posteriores da linguagem.</span><span class="sxs-lookup"><span data-stu-id="253b0-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="253b0-108">A interpolação de cadeia de caracteres fornece uma sintaxe mais legível e conveniente para criar cadeias de caracteres formatadas do que o recurso de [formatação composta de cadeia de caracteres](../../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="253b0-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="253b0-109">O exemplo a seguir usa os dois recursos para produzir o mesmo resultado:</span><span class="sxs-lookup"><span data-stu-id="253b0-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="253b0-110">Estrutura de uma cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="253b0-110">Structure of an interpolated string</span></span>

<span data-ttu-id="253b0-111">Para identificar uma literal de cadeia de caracteres como uma cadeia de caracteres interpolada, preceda-a com o símbolo `$`.</span><span class="sxs-lookup"><span data-stu-id="253b0-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="253b0-112">Não pode haver nenhum espaço em branco entre o `$` e `"` que iniciam um literal de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="253b0-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="253b0-113">Fazer isso causa um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="253b0-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="253b0-114">A estrutura de um item com uma expressão interpolada é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="253b0-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="253b0-115">Os elementos entre colchetes são opcionais.</span><span class="sxs-lookup"><span data-stu-id="253b0-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="253b0-116">A seguinte tabela descreve cada elemento:</span><span class="sxs-lookup"><span data-stu-id="253b0-116">The following table describes each element:</span></span>

|<span data-ttu-id="253b0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="253b0-117">Element</span></span>|<span data-ttu-id="253b0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="253b0-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="253b0-119">A expressão que produz um resultado a ser formatado.</span><span class="sxs-lookup"><span data-stu-id="253b0-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="253b0-120">A representação de cadeia de caracteres do resultado `null` é <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="253b0-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="253b0-121">A expressão de constante cujo valor define o número mínimo de caracteres da representação de cadeia de caracteres do resultado da expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="253b0-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="253b0-122">Se for positiva, a representação de cadeia de caracteres será alinhada à direita; se for negativa, será alinhada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="253b0-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="253b0-123">Para obter mais informações, consulte [Componente de alinhamento](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="253b0-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="253b0-124">Uma cadeia de caracteres de formato compatível com o tipo do resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="253b0-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="253b0-125">Para obter mais informações, consulte [Componente da cadeia de caracteres de formato](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="253b0-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="253b0-126">O exemplo a seguir usa os componentes opcionais de formatação descritos acima:</span><span class="sxs-lookup"><span data-stu-id="253b0-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="253b0-127">Caracteres especiais</span><span class="sxs-lookup"><span data-stu-id="253b0-127">Special characters</span></span>

<span data-ttu-id="253b0-128">Para incluir uma chave, "{" ou "}", no texto produzido por uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="253b0-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="253b0-129">Para obter mais informações, consulte [Chaves de escape](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="253b0-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="253b0-130">Como os dois-pontos (":") têm um significado especial em um item de expressão interpolada, para usar um [operador condicional](../operators/conditional-operator.md) em uma expressão interpolada, coloque essa expressão entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="253b0-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="253b0-131">O seguinte exemplo mostra como incluir uma chave em uma cadeia de caracteres de resultado e como usar um operador condicional em uma expressão interpolada:</span><span class="sxs-lookup"><span data-stu-id="253b0-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="253b0-132">Uma cadeia de caracteres interpolada textual começa com o caractere `$` seguido pelo caractere `@`.</span><span class="sxs-lookup"><span data-stu-id="253b0-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="253b0-133">Para obter mais informações sobre cadeias de caracteres textuais, confira os tópicos [cadeia de caracteres](../keywords/string.md) e [identificador textual](verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="253b0-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="253b0-134">O token `$` deve aparecer antes do token `@` em uma cadeia de caracteres textual interpolada.</span><span class="sxs-lookup"><span data-stu-id="253b0-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="253b0-135">Conversões implícitas e especificando a implementação de `IFormatProvider`</span><span class="sxs-lookup"><span data-stu-id="253b0-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="253b0-136">Há três conversões implícitas de uma cadeia de caracteres interpolada:</span><span class="sxs-lookup"><span data-stu-id="253b0-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="253b0-137">Conversão de uma cadeia de caracteres interpolada uma instância <xref:System.String>, que é a resolução da cadeia de caracteres interpolada com os itens da expressão interpolada que estão sendo substituídos pelas representações de seus resultados da cadeia de caracteres corretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="253b0-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="253b0-138">Essa conversão usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="253b0-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="253b0-139">Conversão de uma cadeia de caracteres interpolada em uma instância de <xref:System.FormattableString>, que representa uma cadeia de caracteres de formato composto, juntamente com os resultados da expressão a ser formatada.</span><span class="sxs-lookup"><span data-stu-id="253b0-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="253b0-140">Isso permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="253b0-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="253b0-141">Para fazer isso, chame um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="253b0-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="253b0-142">Uma sobrecarga <xref:System.FormattableString.ToString> que produza uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="253b0-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="253b0-143">Um método <xref:System.FormattableString.Invariant%2A> que produz uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="253b0-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="253b0-144">Um método <xref:System.FormattableString.ToString(System.IFormatProvider)> que produza uma cadeia de caracteres de resultado para uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="253b0-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="253b0-145">Use também o método <xref:System.FormattableString.ToString(System.IFormatProvider)> para fornecer uma implementação definida pelo usuário da interface <xref:System.IFormatProvider> que dá suporte à formatação personalizada.</span><span class="sxs-lookup"><span data-stu-id="253b0-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="253b0-146">Para obter mais informações, confira [Formatação personalizada com ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="253b0-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="253b0-147">Conversão de uma cadeia de caracteres interpolada em uma instância <xref:System.IFormattable>, que também permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="253b0-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="253b0-148">O exemplo a seguir usa a conversão implícita em <xref:System.FormattableString> para a criação de cadeias de caracteres de resultado específicas de cultura:</span><span class="sxs-lookup"><span data-stu-id="253b0-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="253b0-149">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="253b0-149">Additional resources</span></span>

<span data-ttu-id="253b0-150">Se não estiver familiarizado com a interpolação de cadeia de caracteres, confira o guia de início rápido [Interpolação de cadeia de caracteres no C#](../../quick-starts/interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="253b0-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="253b0-151">Para obter mais exemplos, confira o tutorial [Interpolação de cadeia de caracteres no C#](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="253b0-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="253b0-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="253b0-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="253b0-153">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="253b0-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="253b0-154">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="253b0-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="253b0-155">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="253b0-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="253b0-156">Caracteres especiais de C#</span><span class="sxs-lookup"><span data-stu-id="253b0-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="253b0-157">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="253b0-157">C# Reference</span></span>](../index.md)  
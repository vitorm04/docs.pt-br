---
title: $ – interpolação de cadeia de caracteres (Referência de C#)
description: A interpolação de cadeia de caracteres oferece uma sintaxe mais legível e conveniente para formatar a saída de cadeia de caracteres de formatação do que a tradicional formatação composta da cadeia de caracteres.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="dfc52-103">$ – interpolação de cadeia de caracteres (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="dfc52-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="dfc52-104">O caractere especial `$` identifica um literal de cadeia de caracteres como uma *cadeia de caracteres interpolada*.</span><span class="sxs-lookup"><span data-stu-id="dfc52-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="dfc52-105">Uma cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém *expressões interpoladas*.</span><span class="sxs-lookup"><span data-stu-id="dfc52-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="dfc52-106">Quando a cadeia de caracteres interpolada é resolvida para a cadeia de caracteres de resultado, itens com expressões interpoladas são substituídos pelas representações de cadeia de caracteres dos resultados de expressão.</span><span class="sxs-lookup"><span data-stu-id="dfc52-106">When the interpolated string is resolved to the result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="dfc52-107">Este recurso está disponível no C# 6 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="dfc52-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="dfc52-108">A interpolação de cadeia de caracteres fornece uma sintaxe mais legível e conveniente para criar cadeias de caracteres formatadas do que o recurso de [formatação composta de cadeia de caracteres](../../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="dfc52-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="dfc52-109">O exemplo a seguir usa os dois recursos para produzir o mesmo resultado:</span><span class="sxs-lookup"><span data-stu-id="dfc52-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="dfc52-110">Você não pode ter nenhum espaço em branco entre o `$` e `"` que iniciam a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dfc52-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="dfc52-111">Fazer isso causa um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="dfc52-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="dfc52-112">A estrutura de um item com uma expressão interpolada é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="dfc52-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="dfc52-113">Os elementos entre colchetes são opcionais.</span><span class="sxs-lookup"><span data-stu-id="dfc52-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="dfc52-114">A tabela a seguir descreve cada elemento.</span><span class="sxs-lookup"><span data-stu-id="dfc52-114">The following table describes each element.</span></span>

|<span data-ttu-id="dfc52-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfc52-115">Element</span></span>|<span data-ttu-id="dfc52-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfc52-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="dfc52-117">A expressão a ser avaliada para obter um resultado a ser formatado.</span><span class="sxs-lookup"><span data-stu-id="dfc52-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="dfc52-118">A representação de cadeia de caracteres do resultado `null` é <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dfc52-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="dfc52-119">A expressão de constante cujo valor define o número mínimo de caracteres da representação de cadeia de caracteres do resultado da expressão interpolada.</span><span class="sxs-lookup"><span data-stu-id="dfc52-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="dfc52-120">Se for positiva, a representação de cadeia de caracteres é alinhada à direita; se for negativa, será alinhada à esquerda.</span><span class="sxs-lookup"><span data-stu-id="dfc52-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="dfc52-121">Para obter mais informações, consulte [Componente de alinhamento](../../../standard/base-types/composite-formatting.md#alignment-component).</span><span class="sxs-lookup"><span data-stu-id="dfc52-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="dfc52-122">Uma cadeia de caracteres de formato, personalizada ou padrão, que seja compatível com o tipo de resultado da expressão.</span><span class="sxs-lookup"><span data-stu-id="dfc52-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="dfc52-123">Para obter mais informações, consulte [Componente da cadeia de caracteres de formato](../../../standard/base-types/composite-formatting.md#format-string-component).</span><span class="sxs-lookup"><span data-stu-id="dfc52-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="dfc52-124">O exemplo a seguir usa os componentes opcionais de formatação descritos acima:</span><span class="sxs-lookup"><span data-stu-id="dfc52-124">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="dfc52-125">Para incluir uma chave ("{" ou "}") no texto produzido por uma cadeia de caracteres interpolada, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="dfc52-125">To include a brace ("{" or "}") in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="dfc52-126">Para obter mais informações, consulte [Chaves de escape](../../../standard/base-types/composite-formatting.md#escaping-braces).</span><span class="sxs-lookup"><span data-stu-id="dfc52-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="dfc52-127">Como os dois-pontos (:) têm um significado especial em um item de expressão interpolada, para usar um [operador condicional](../operators/conditional-operator.md) em uma expressão interpolada, coloque essa expressão entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="dfc52-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="dfc52-128">O exemplo a seguir mostra como incluir uma chave na cadeia de caracteres de resultado e como usar um operador condicional em uma expressão interpolada:</span><span class="sxs-lookup"><span data-stu-id="dfc52-128">The following example shows how to include a brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="dfc52-129">As cadeias de caracteres textuais interpoladas usam o caractere `$` seguido pelo caractere `@`.</span><span class="sxs-lookup"><span data-stu-id="dfc52-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="dfc52-130">Para obter mais informações sobre cadeias de caracteres textuais, consulte o tópico [cadeia de caracteres](../keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="dfc52-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="dfc52-131">O token `$` deve aparecer antes do token `@` em uma cadeia de caracteres textual interpolada.</span><span class="sxs-lookup"><span data-stu-id="dfc52-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

<span data-ttu-id="dfc52-132">Há três conversões implícitas de uma cadeia de caracteres interpolada:</span><span class="sxs-lookup"><span data-stu-id="dfc52-132">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="dfc52-133">Conversão de uma cadeia de caracteres interpolada uma instância <xref:System.String>, que é a resolução da cadeia de caracteres interpolada com os itens da expressão interpolada que estão sendo substituídos pelas representações de seus resultados da cadeia de caracteres corretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="dfc52-133">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="dfc52-134">Essa conversão usa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dfc52-134">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="dfc52-135">Conversão de uma cadeia de caracteres interpolada em uma instância de <xref:System.FormattableString>, que representa uma cadeia de caracteres de formato composto, juntamente com os resultados da expressão a ser formatada.</span><span class="sxs-lookup"><span data-stu-id="dfc52-135">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="dfc52-136">Isso permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.FormattableString>.</span><span class="sxs-lookup"><span data-stu-id="dfc52-136">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="dfc52-137">Para fazer isso, chame um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="dfc52-137">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="dfc52-138">Uma sobrecarga <xref:System.FormattableString.ToString> que produza uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="dfc52-138">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="dfc52-139">Um método <xref:System.FormattableString.Invariant%2A> que produza uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="dfc52-139">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="dfc52-140">Um método <xref:System.FormattableString.ToString(System.IFormatProvider)> que produza uma cadeia de caracteres de resultado para uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="dfc52-140">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="dfc52-141">Conversão de uma cadeia de caracteres interpolada em uma instância <xref:System.IFormattable>, que também permite criar várias cadeias de caracteres de resultado com conteúdo específico da cultura com base em uma única instância <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="dfc52-141">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="dfc52-142">O exemplo a seguir usa a conversão implícita em <xref:System.FormattableString> para a criação de cadeias de caracteres de resultado específicas de cultura:</span><span class="sxs-lookup"><span data-stu-id="dfc52-142">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

<span data-ttu-id="dfc52-143">Se não estiver familiarizado com a interpolação de cadeia de caracteres, consulte o guia de início rápido [Interpolação de cadeia de caracteres no C#](../../quick-starts/interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="dfc52-143">If you are new to the string interpolation, check the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="dfc52-144">Para obter mais exemplos, consulte o [tutorial de interpolação de cadeia de caracteres](../../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="dfc52-144">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfc52-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfc52-145">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="dfc52-146">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="dfc52-146">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="dfc52-147">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="dfc52-147">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="dfc52-148">Caracteres especiais de C#</span><span class="sxs-lookup"><span data-stu-id="dfc52-148">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="dfc52-149">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="dfc52-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dfc52-150">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="dfc52-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
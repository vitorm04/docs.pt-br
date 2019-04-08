---
title: Interpolação de cadeias de caracteres em C#
description: Saiba como incluir resultados de expressão formatada em uma cadeia de caracteres de resultado em C# com a interpolação de cadeia de caracteres.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 5a66ba9215579a459b543a24ece338ffbbfd9aea
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920708"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="4eadc-103">Interpolação de cadeias de caracteres em C\#</span><span class="sxs-lookup"><span data-stu-id="4eadc-103">String interpolation in C\#</span></span>

<span data-ttu-id="4eadc-104">Este tutorial mostra como usar a [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) para formatar e incluir resultados de expressão em uma cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="4eadc-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="4eadc-105">Os exemplos pressupõem que você esteja familiarizado com os conceitos básicos do C# e a formatação de tipos do .NET.</span><span class="sxs-lookup"><span data-stu-id="4eadc-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="4eadc-106">Se você não estiver familiarizado com a interpolação de cadeia de caracteres ou com a formatação de tipos do .NET, confira primeiro o [tutorial interativo sobre a interpolação de cadeia de caracteres](exploration/interpolated-strings.yml).</span><span class="sxs-lookup"><span data-stu-id="4eadc-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation tutorial](exploration/interpolated-strings.yml) first.</span></span> <span data-ttu-id="4eadc-107">Para obter mais informações sobre como formatar tipos no .NET, confira o tópico [Formatando tipos no .NET](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="4eadc-108">Introdução</span><span class="sxs-lookup"><span data-stu-id="4eadc-108">Introduction</span></span>

<span data-ttu-id="4eadc-109">O recurso [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) baseia-se no recurso [formatação composta](../../standard/base-types/composite-formatting.md) e fornece uma sintaxe mais legível e conveniente para incluir resultados de expressão formatada em uma cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="4eadc-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="4eadc-110">Para identificar uma literal de cadeia de caracteres como uma cadeia de caracteres interpolada, preceda-o com o símbolo `$`.</span><span class="sxs-lookup"><span data-stu-id="4eadc-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="4eadc-111">Você pode inserir qualquer expressão C# válida que retorna um valor em uma cadeia de caracteres interpolada.</span><span class="sxs-lookup"><span data-stu-id="4eadc-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="4eadc-112">No seguinte exemplo, assim que uma expressão é avaliada, o resultado é convertido em uma cadeia de caracteres e incluído em uma cadeia de caracteres de resultado:</span><span class="sxs-lookup"><span data-stu-id="4eadc-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="4eadc-113">Como mostra o exemplo, você inclui uma expressão em uma cadeia de caracteres interpolada colocando-a com chaves:</span><span class="sxs-lookup"><span data-stu-id="4eadc-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="4eadc-114">No tempo de compilação, normalmente uma cadeia de caracteres interpolada é transformada em uma chamada de método <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4eadc-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="4eadc-115">Isso disponibiliza todas as funcionalidades do recurso [formatação composta de cadeia de caracteres](../../standard/base-types/composite-formatting.md) para uso com cadeias de caracteres interpoladas também.</span><span class="sxs-lookup"><span data-stu-id="4eadc-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

<span data-ttu-id="4eadc-116">O compilador poderá substituir um <xref:System.String.Format%2A?displayProperty=nameWithType> por <xref:System.String.Concat%2A?displayProperty=nameWithType> se o comportamento analisado for equivalente à concatenação.</span><span class="sxs-lookup"><span data-stu-id="4eadc-116">The compiler may substitute a <xref:System.String.Format%2A?displayProperty=nameWithType> for <xref:System.String.Concat%2A?displayProperty=nameWithType> if the analyzed behavior would be equivalent to concatenation.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="4eadc-117">Como especificar uma cadeia de caracteres de formato para uma expressão interpolada</span><span class="sxs-lookup"><span data-stu-id="4eadc-117">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="4eadc-118">Especifique uma cadeia de caracteres de formato compatível com o tipo do resultado de expressão seguindo a expressão interpolada com dois-pontos (":") e a cadeia de caracteres de formato:</span><span class="sxs-lookup"><span data-stu-id="4eadc-118">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="4eadc-119">O seguinte exemplo mostra como especificar cadeias de caracteres de formato padrão e personalizadas para expressões que produzem resultados numéricos ou de data e hora:</span><span class="sxs-lookup"><span data-stu-id="4eadc-119">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="4eadc-120">Para obter mais informações, consulte a seção [Componente de cadeia de caracteres de formato](../../standard/base-types/composite-formatting.md#format-string-component) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-120">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="4eadc-121">Esta seção fornece links para tópicos que descrevem cadeias de caracteres de formatos padrão e personalizado compatíveis com os tipos base do .NET.</span><span class="sxs-lookup"><span data-stu-id="4eadc-121">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="4eadc-122">Como controlar a largura do campo e o alinhamento da expressão interpolada formatada</span><span class="sxs-lookup"><span data-stu-id="4eadc-122">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="4eadc-123">Especifique a largura mínima do campo e o alinhamento do resultado de expressão formatada seguindo a expressão interpolada com uma vírgula (",") e a expressão de constante:</span><span class="sxs-lookup"><span data-stu-id="4eadc-123">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="4eadc-124">Se o valor *alignment* for positivo, o resultado da expressão formatada será alinhado à direita; se for negativo, ele será alinhado à esquerda.</span><span class="sxs-lookup"><span data-stu-id="4eadc-124">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="4eadc-125">Caso precise especificar o alinhamento e uma cadeia de caracteres de formato, comece com o componente de alinhamento:</span><span class="sxs-lookup"><span data-stu-id="4eadc-125">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="4eadc-126">O seguinte exemplo mostra como especificar o alinhamento e usa caracteres de barra vertical ("|") para delimitar campos de texto:</span><span class="sxs-lookup"><span data-stu-id="4eadc-126">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="4eadc-127">Como mostra a saída de exemplo, se o tamanho do resultado da expressão formatada exceder a largura de campo especificada, o valor *alignment* será ignorado.</span><span class="sxs-lookup"><span data-stu-id="4eadc-127">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="4eadc-128">Para obter mais informações, consulte a seção [Componente de alinhamento](../../standard/base-types/composite-formatting.md#alignment-component) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-128">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="4eadc-129">Como usar sequências de escape em uma cadeia de caracteres interpolada</span><span class="sxs-lookup"><span data-stu-id="4eadc-129">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="4eadc-130">Cadeias de caracteres interpoladas dão suporte a todas as sequências de escape que podem ser usadas em literais de cadeia de caracteres comuns.</span><span class="sxs-lookup"><span data-stu-id="4eadc-130">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="4eadc-131">Para obter mais informações, consulte [Sequências de escape de cadeia de caracteres](../programming-guide/strings/index.md#string-escape-sequences).</span><span class="sxs-lookup"><span data-stu-id="4eadc-131">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="4eadc-132">Para interpretar sequências de escape literalmente, use um literal de cadeia de caracteres [textual](../language-reference/tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-132">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="4eadc-133">Uma cadeia de caracteres interpolada textual começa com o caractere `$` seguido pelo caractere `@`.</span><span class="sxs-lookup"><span data-stu-id="4eadc-133">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="4eadc-134">Para incluir uma chave, "{" ou "}", em uma cadeia de caracteres de resultado, use duas chaves, "{{" ou "}}".</span><span class="sxs-lookup"><span data-stu-id="4eadc-134">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="4eadc-135">Para obter mais informações, consulte a seção [Chaves de escape](../../standard/base-types/composite-formatting.md#escaping-braces) do tópico [Formatação composta](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-135">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="4eadc-136">O seguinte exemplo mostra como incluir chaves em uma cadeia de caracteres de resultado e construir uma cadeia de caracteres interpolada textual:</span><span class="sxs-lookup"><span data-stu-id="4eadc-136">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="4eadc-137">Como usar um operador condicional ternário `?:` em uma expressão interpolada</span><span class="sxs-lookup"><span data-stu-id="4eadc-137">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="4eadc-138">Como os dois-pontos (:) têm um significado especial em um item com uma expressão interpolada, para usar um [operador condicional](../language-reference/operators/conditional-operator.md) em uma expressão, coloque-a entre parênteses, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="4eadc-138">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="4eadc-139">Como criar uma cadeia de caracteres de resultado específica a uma cultura com a interpolação de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4eadc-139">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="4eadc-140">Por padrão, uma cadeia de caracteres interpolada usa a cultura atual definida pela propriedade <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> para todas as operações de formatação.</span><span class="sxs-lookup"><span data-stu-id="4eadc-140">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="4eadc-141">Use uma conversão implícita de uma cadeia de caracteres interpolada em uma instância <xref:System.FormattableString?displayProperty=nameWithType> e chame seu método <xref:System.FormattableString.ToString(System.IFormatProvider)> para criar uma cadeia de caracteres de resultado específica a uma cultura.</span><span class="sxs-lookup"><span data-stu-id="4eadc-141">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="4eadc-142">O seguinte exemplo mostra como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="4eadc-142">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="4eadc-143">Como mostra o exemplo, você pode usar uma instância <xref:System.FormattableString> para gerar várias cadeias de caracteres de resultado para várias culturas.</span><span class="sxs-lookup"><span data-stu-id="4eadc-143">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="4eadc-144">Como criar uma cadeia de caracteres de resultado usando a cultura invariável</span><span class="sxs-lookup"><span data-stu-id="4eadc-144">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="4eadc-145">Juntamente com o método <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>, você pode usar o método <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> estático para resolver uma cadeia de caracteres interpolada em uma cadeia de caracteres de resultado para a <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="4eadc-145">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="4eadc-146">O seguinte exemplo mostra como fazer isso:</span><span class="sxs-lookup"><span data-stu-id="4eadc-146">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="4eadc-147">Conclusão</span><span class="sxs-lookup"><span data-stu-id="4eadc-147">Conclusion</span></span>

<span data-ttu-id="4eadc-148">Este tutorial descreve cenários comuns de uso da interpolação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4eadc-148">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="4eadc-149">Para obter mais informações sobre a interpolação de cadeia de caracteres, consulte o tópico [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-149">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="4eadc-150">Para obter mais informações sobre como formatar tipos no .NET, confira os tópicos [Formatando tipos no .NET](../../standard/base-types/formatting-types.md) e [Formatação composta](../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4eadc-150">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="4eadc-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4eadc-151">See also</span></span>

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [<span data-ttu-id="4eadc-152">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="4eadc-152">Strings</span></span>](../programming-guide/strings/index.md)

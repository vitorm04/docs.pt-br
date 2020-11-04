---
title: Técnicas de análise de cadeia de caracteres no .NET
description: Saiba mais sobre técnicas diferentes para extrair partes de uma cadeia de caracteres, incluindo String. Split, expressões regulares e String. substring.
ms.date: 10/30/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], breaking up
ms.openlocfilehash: de979b711a850bbb9ce91e1f1704d40a2f78f363
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93343356"
---
# <a name="extract-elements-from-a-string"></a><span data-ttu-id="f81e3-103">Extrair elementos de uma cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f81e3-103">Extract elements from a string</span></span>

<span data-ttu-id="f81e3-104">Este artigo aborda algumas técnicas diferentes para extrair partes de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-104">This article covers some different techniques for extracting parts of a string.</span></span>

- <span data-ttu-id="f81e3-105">Use o [método Split](#stringsplit-method) quando as subcadeias de caracteres desejadas estiverem separadas por um caractere delimitador conhecido (ou caracteres).</span><span class="sxs-lookup"><span data-stu-id="f81e3-105">Use the [Split method](#stringsplit-method) when the substrings you want are separated by a known delimiting character (or characters).</span></span>
- <span data-ttu-id="f81e3-106">As [expressões regulares](#regular-expressions) são úteis quando a cadeia de caracteres está de acordo com um padrão fixo.</span><span class="sxs-lookup"><span data-stu-id="f81e3-106">[Regular expressions](#regular-expressions) are useful when the string conforms to a fixed pattern.</span></span>
- <span data-ttu-id="f81e3-107">Use os [métodos IndexOf e substring](#stringindexof-and-stringsubstring-methods) em conjunto quando você não quiser extrair *todas* as subcadeias de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-107">Use the [IndexOf and Substring methods](#stringindexof-and-stringsubstring-methods) in conjunction when you don't want to extract *all* of the substrings in a string.</span></span>

## <a name="stringsplit-method"></a><span data-ttu-id="f81e3-108">Método String. Split</span><span class="sxs-lookup"><span data-stu-id="f81e3-108">String.Split method</span></span>

<span data-ttu-id="f81e3-109"><xref:System.String.Split%2A?displayProperty=nameWithType> fornece uma série de sobrecargas para ajudá-lo a dividir uma cadeia de caracteres em um grupo de subcadeias de caracteres com base em um ou mais caractere delimitador que você especificar.</span><span class="sxs-lookup"><span data-stu-id="f81e3-109"><xref:System.String.Split%2A?displayProperty=nameWithType> provides a handful of overloads to help you break up a string into a group of substrings based on one or more delimiting characters that you specify.</span></span> <span data-ttu-id="f81e3-110">Você pode optar por limitar o número total de subcadeias de caracteres no resultado final, aparar caracteres de espaço em branco de subcadeias ou excluir subcadeias de caracteres vazias.</span><span class="sxs-lookup"><span data-stu-id="f81e3-110">You can choose to limit the total number of substrings in the final result, trim white-space characters from substrings, or exclude empty substrings.</span></span>

<span data-ttu-id="f81e3-111">Os exemplos a seguir mostram três sobrecargas diferentes de `String.Split()` .</span><span class="sxs-lookup"><span data-stu-id="f81e3-111">The following examples show three different overloads of `String.Split()`.</span></span> <span data-ttu-id="f81e3-112">O primeiro exemplo chama a <xref:System.String.Split(System.Char[])> sobrecarga sem passar nenhum caractere separador.</span><span class="sxs-lookup"><span data-stu-id="f81e3-112">The first example calls the <xref:System.String.Split(System.Char[])> overload without passing any separator characters.</span></span> <span data-ttu-id="f81e3-113">Quando você não especifica nenhum caractere delimitador, `String.Split()` o usa delimitadores padrão, que são caracteres de espaço em branco, para dividir a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-113">When you don't specify any delimiting characters, `String.Split()` uses default delimiters, which are white-space characters, to split up the string.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#1)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="1":::

<span data-ttu-id="f81e3-114">Como você pode ver, os caracteres de ponto ( `.` ) são incluídos em duas das subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-114">As you can see, the period characters (`.`) are included in two of the substrings.</span></span> <span data-ttu-id="f81e3-115">Se você quiser excluir os caracteres de período, poderá adicionar o caractere de ponto como um caractere de delimitação adicional.</span><span class="sxs-lookup"><span data-stu-id="f81e3-115">If you want to exclude the period characters, you can add the period character as an additional delimiting character.</span></span> <span data-ttu-id="f81e3-116">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f81e3-116">The next example shows how to do this.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#2)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="2":::

<span data-ttu-id="f81e3-117">Os períodos foram removidas das subcadeias de caracteres, mas agora duas subcadeias vazias extras foram incluídas.</span><span class="sxs-lookup"><span data-stu-id="f81e3-117">The periods are gone from the substrings, but now two extra empty substrings have been included.</span></span> <span data-ttu-id="f81e3-118">Essas subcadeias de caracteres vazias representam a subcadeia de caracteres entre a palavra e o período que a segue.</span><span class="sxs-lookup"><span data-stu-id="f81e3-118">These empty substring represent the substring between the word and the period that follows it.</span></span> <span data-ttu-id="f81e3-119">Para omitir subcadeias de caracteres vazias da matriz resultante, você pode chamar a <xref:System.String.Split(System.Char[],System.StringSplitOptions)> sobrecarga e especificar <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> para o `options` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f81e3-119">To omit empty substrings from the resulting array, you can call the <xref:System.String.Split(System.Char[],System.StringSplitOptions)> overload and specify <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> for the `options` parameter.</span></span>

[!code-csharp-interactive[Intro#1](snippets/parse-strings/csharp/intro.cs#3)]
:::code language="vb" source="snippets/parse-strings/vb/intro.vb" id="3":::

## <a name="regular-expressions"></a><span data-ttu-id="f81e3-120">Expressões regulares</span><span class="sxs-lookup"><span data-stu-id="f81e3-120">Regular expressions</span></span>

<span data-ttu-id="f81e3-121">Se a cadeia de caracteres estiver em conformidade com um padrão fixo, você poderá usar uma expressão regular para extrair e manipular seus elementos.</span><span class="sxs-lookup"><span data-stu-id="f81e3-121">If your string conforms to a fixed pattern, you can use a regular expression to extract and handle its elements.</span></span> <span data-ttu-id="f81e3-122">Por exemplo, se cadeias de caracteres assumirem o formato " *número* do *operando* de *número* ", você poderá usar uma [expressão regular](regular-expressions.md) para extrair e manipular os elementos da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-122">For example, if strings take the form " *number* *operand* *number* ", you can use a [regular expression](regular-expressions.md) to extract and handle the string's elements.</span></span> <span data-ttu-id="f81e3-123">Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="f81e3-123">Here's an example:</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="1":::

<span data-ttu-id="f81e3-124">O padrão de expressão regular `(\d+)\s+([-+*/])\s+(\d+)` é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f81e3-124">The regular expression pattern `(\d+)\s+([-+*/])\s+(\d+)` is defined like this:</span></span>

|<span data-ttu-id="f81e3-125">Padrão</span><span class="sxs-lookup"><span data-stu-id="f81e3-125">Pattern</span></span>|<span data-ttu-id="f81e3-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f81e3-126">Description</span></span>|
|-------------|-----------------|
|`(\d+)`|<span data-ttu-id="f81e3-127">Corresponde a um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="f81e3-127">Match one or more decimal digits.</span></span> <span data-ttu-id="f81e3-128">Este é o primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="f81e3-128">This is the first capturing group.</span></span>|
|`\s+`|<span data-ttu-id="f81e3-129">Corresponder um ou mais caracteres de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f81e3-129">Match one or more white-space characters.</span></span>|
|`([-+*/])`|<span data-ttu-id="f81e3-130">Corresponder um sinal de operador aritmético (+,-, \* ou/).</span><span class="sxs-lookup"><span data-stu-id="f81e3-130">Match an arithmetic operator sign (+, -, \*, or /).</span></span> <span data-ttu-id="f81e3-131">Este é o segundo grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="f81e3-131">This is the second capturing group.</span></span>|
|`\s+`|<span data-ttu-id="f81e3-132">Corresponder um ou mais caracteres de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f81e3-132">Match one or more white-space characters.</span></span>|
|`(\d+)`|<span data-ttu-id="f81e3-133">Corresponde a um ou mais dígitos decimais.</span><span class="sxs-lookup"><span data-stu-id="f81e3-133">Match one or more decimal digits.</span></span> <span data-ttu-id="f81e3-134">Este é o terceiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="f81e3-134">This is the third capturing group.</span></span>|

<span data-ttu-id="f81e3-135">Você também pode usar uma expressão regular para extrair subseqüências de uma cadeia de caracteres com base em um padrão, em vez de um conjunto fixo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-135">You can also use a regular expression to extract substrings from a string based on a pattern rather than a fixed set of characters.</span></span> <span data-ttu-id="f81e3-136">Esse é um cenário comum quando uma dessas condições ocorre:</span><span class="sxs-lookup"><span data-stu-id="f81e3-136">This is a common scenario when either of these conditions occurs:</span></span>

- <span data-ttu-id="f81e3-137">Um ou mais dos caracteres delimitadores nem *sempre* servem como um delimitador na <xref:System.String> instância.</span><span class="sxs-lookup"><span data-stu-id="f81e3-137">One or more of the delimiter characters does not *always* serve as a delimiter in the <xref:System.String> instance.</span></span>

- <span data-ttu-id="f81e3-138">A sequência e o número de caracteres do delimitador são variáveis ou são desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="f81e3-138">The sequence and number of delimiter characters is variable or unknown.</span></span>

<span data-ttu-id="f81e3-139">Por exemplo, o <xref:System.String.Split%2A> método não pode ser usado para dividir a cadeia de caracteres a seguir, porque o número de `\n` caracteres (nova linha) é variável e nem sempre funciona como delimitadores.</span><span class="sxs-lookup"><span data-stu-id="f81e3-139">For example, the <xref:System.String.Split%2A> method cannot be used to split the following string, because the number of `\n` (newline) characters is variable, and they don't always serve as delimiters.</span></span>

```text
[This is captured\ntext.]\n\n[\n[This is more captured text.]\n]
\n[Some more captured text:\n   Option1\n   Option2][Terse text.]
```

<span data-ttu-id="f81e3-140">Uma expressão regular pode dividir essa cadeia de caracteres facilmente, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f81e3-140">A regular expression can split this string easily, as the following example shows.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="2" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="2":::

<span data-ttu-id="f81e3-141">O padrão de expressão regular `\[([^\[\]]+)\]` é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f81e3-141">The regular expression pattern `\[([^\[\]]+)\]` is defined like this:</span></span>

|<span data-ttu-id="f81e3-142">Padrão</span><span class="sxs-lookup"><span data-stu-id="f81e3-142">Pattern</span></span>|<span data-ttu-id="f81e3-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="f81e3-143">Description</span></span>|
|-------------|-----------------|
|`\[`|<span data-ttu-id="f81e3-144">Corresponde a um colchete de abertura.</span><span class="sxs-lookup"><span data-stu-id="f81e3-144">Match an opening bracket.</span></span>|
|`([^\[\]]+)`|<span data-ttu-id="f81e3-145">Corresponder qualquer caractere que não seja um colchete de abertura ou de fechamento uma ou mais vezes.</span><span class="sxs-lookup"><span data-stu-id="f81e3-145">Match any character that is not an opening or a closing bracket one or more times.</span></span> <span data-ttu-id="f81e3-146">Este é o primeiro grupo de captura.</span><span class="sxs-lookup"><span data-stu-id="f81e3-146">This is the first capturing group.</span></span>|
|`\]`|<span data-ttu-id="f81e3-147">Corresponde a um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="f81e3-147">Match a closing bracket.</span></span>|

<span data-ttu-id="f81e3-148">O <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> método é quase idêntico ao <xref:System.String.Split%2A?displayProperty=nameWithType> , exceto pelo fato de que ele divide uma cadeia de caracteres com base em um padrão de expressão regular em vez de um conjunto de caracteres fixo.</span><span class="sxs-lookup"><span data-stu-id="f81e3-148">The <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method is almost identical to <xref:System.String.Split%2A?displayProperty=nameWithType>, except that it splits a string based on a regular expression pattern instead of a fixed character set.</span></span> <span data-ttu-id="f81e3-149">Por exemplo, o exemplo a seguir usa o <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> método para dividir uma cadeia de caracteres que contém subcadeias de caracteres delimitadas por várias combinações de hifens e outros caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-149">For example, the following example uses the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to split a string that contains substrings delimited by various combinations of hyphens and other characters.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/regex.cs" id="3" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/regex.vb" id="3":::

<span data-ttu-id="f81e3-150">O padrão de expressão regular `\s-\s?[+*]?\s?-\s` é definido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f81e3-150">The regular expression pattern `\s-\s?[+*]?\s?-\s` is defined like this:</span></span>

|<span data-ttu-id="f81e3-151">Padrão</span><span class="sxs-lookup"><span data-stu-id="f81e3-151">Pattern</span></span>|<span data-ttu-id="f81e3-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="f81e3-152">Description</span></span>|
|-------------|-----------------|
|`\s-`|<span data-ttu-id="f81e3-153">Corresponder a um caractere de espaço em branco seguido por um hífen.</span><span class="sxs-lookup"><span data-stu-id="f81e3-153">Match a white-space character followed by a hyphen.</span></span>|
|`\s?`|<span data-ttu-id="f81e3-154">Corresponder a zero ou a um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f81e3-154">Match zero or one white-space character.</span></span>|
|`[+*]?`|<span data-ttu-id="f81e3-155">Corresponder a zero ou uma ocorrência do caractere + ou \*.</span><span class="sxs-lookup"><span data-stu-id="f81e3-155">Match zero or one occurrence of either the + or \* character.</span></span>|
|`\s?`|<span data-ttu-id="f81e3-156">Corresponder a zero ou a um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f81e3-156">Match zero or one white-space character.</span></span>|
|`-\s`|<span data-ttu-id="f81e3-157">Corresponder um hífen seguido por um caractere de espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="f81e3-157">Match a hyphen followed by a white-space character.</span></span>|

## <a name="stringindexof-and-stringsubstring-methods"></a><span data-ttu-id="f81e3-158">Métodos String. IndexOf e String. substring</span><span class="sxs-lookup"><span data-stu-id="f81e3-158">String.IndexOf and String.Substring methods</span></span>

<span data-ttu-id="f81e3-159">Se você não estiver interessado em todas as subcadeias em uma cadeia de caracteres, talvez prefira trabalhar com um dos métodos de comparação de cadeia de caracteres que retorna o índice no qual a correspondência começa.</span><span class="sxs-lookup"><span data-stu-id="f81e3-159">If you aren't interested in all of the substrings in a string, you might prefer to work with one of the string comparison methods that returns the index at which the match begins.</span></span> <span data-ttu-id="f81e3-160">Em seguida, você pode chamar o <xref:System.String.Substring%2A> método para extrair a subcadeia de caracteres desejada.</span><span class="sxs-lookup"><span data-stu-id="f81e3-160">You can then call the <xref:System.String.Substring%2A> method to extract the substring that you want.</span></span> <span data-ttu-id="f81e3-161">Os métodos de comparação de cadeia de caracteres incluem:</span><span class="sxs-lookup"><span data-stu-id="f81e3-161">The string comparison methods include:</span></span>

- <span data-ttu-id="f81e3-162"><xref:System.String.IndexOf%2A>, que retorna o índice de base zero da primeira ocorrência de um caractere ou uma cadeia de caracteres em uma instância de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-162"><xref:System.String.IndexOf%2A>, which returns the zero-based index of the first occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="f81e3-163"><xref:System.String.IndexOfAny%2A>, que retorna o índice de base zero na instância de cadeia de caracteres atual da primeira ocorrência de qualquer caractere em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-163"><xref:System.String.IndexOfAny%2A>, which returns the zero-based index in the current string instance of the first occurrence of any character in a character array.</span></span>

- <span data-ttu-id="f81e3-164"><xref:System.String.LastIndexOf%2A>, que retorna o índice de base zero da última ocorrência de um caractere ou uma cadeia de caracteres em uma instância de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-164"><xref:System.String.LastIndexOf%2A>, which returns the zero-based index of the last occurrence of a character or string in a string instance.</span></span>

- <span data-ttu-id="f81e3-165"><xref:System.String.LastIndexOfAny%2A>, que retorna um índice de base zero na instância de cadeia de caracteres atual da última ocorrência de qualquer caractere em uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-165"><xref:System.String.LastIndexOfAny%2A>, which returns a zero-based index in the current string instance of the last occurrence of any character in a character array.</span></span>

<span data-ttu-id="f81e3-166">O exemplo a seguir usa o <xref:System.String.IndexOf%2A> método para localizar os períodos em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f81e3-166">The following example uses the <xref:System.String.IndexOf%2A> method to find the periods in a string.</span></span> <span data-ttu-id="f81e3-167">Em seguida, ele usa o <xref:System.String.Substring%2A> método para retornar frases completas.</span><span class="sxs-lookup"><span data-stu-id="f81e3-167">It then uses the <xref:System.String.Substring%2A> method to return full sentences.</span></span>

:::code language="csharp" source="snippets/parse-strings/csharp/indexof.cs" id="1" interactive="try-dotnet":::
:::code language="vb" source="snippets/parse-strings/vb/indexof.vb" id="1":::

## <a name="see-also"></a><span data-ttu-id="f81e3-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="f81e3-168">See also</span></span>

- [<span data-ttu-id="f81e3-169">Operações básicas de cadeia de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="f81e3-169">Basic string operations in .NET</span></span>](basic-string-operations.md)
- [<span data-ttu-id="f81e3-170">Expressões regulares do .NET</span><span class="sxs-lookup"><span data-stu-id="f81e3-170">.NET regular expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="f81e3-171">Como analisar cadeias de caracteres usando String. Split em C #</span><span class="sxs-lookup"><span data-stu-id="f81e3-171">How to parse strings using String.Split in C#</span></span>](../../csharp/how-to/parse-strings-using-split.md)

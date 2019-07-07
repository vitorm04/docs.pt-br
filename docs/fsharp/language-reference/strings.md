---
title: Cadeias de caracteres
description: Saiba como o F# tipo 'string' representa texto imutável, como uma sequência de caracteres Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: b252aef7d7e6e299df8282407198714971e80cd5
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610172"
---
# <a name="strings"></a><span data-ttu-id="618f3-103">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="618f3-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="618f3-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="618f3-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="618f3-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="618f3-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="618f3-106">O `string` tipo representa texto imutável, como uma sequência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="618f3-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="618f3-107">`string` é um alias para `System.String` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="618f3-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="618f3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="618f3-108">Remarks</span></span>

<span data-ttu-id="618f3-109">Literais de cadeia de caracteres são delimitados pelo caractere de aspas (").</span><span class="sxs-lookup"><span data-stu-id="618f3-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="618f3-110">O caractere de barra invertida ( \\ ) é usado para codificar determinados caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="618f3-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="618f3-111">A barra invertida e o próximo caractere junto são conhecidos como uma *sequência de escape*.</span><span class="sxs-lookup"><span data-stu-id="618f3-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="618f3-112">Suportada de sequências de escape F# literais de cadeia de caracteres são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="618f3-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="618f3-113">Caractere</span><span class="sxs-lookup"><span data-stu-id="618f3-113">Character</span></span>|<span data-ttu-id="618f3-114">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="618f3-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="618f3-115">Alerta</span><span class="sxs-lookup"><span data-stu-id="618f3-115">Alert</span></span>|`\a`|
|<span data-ttu-id="618f3-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="618f3-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="618f3-117">Avanço de página</span><span class="sxs-lookup"><span data-stu-id="618f3-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="618f3-118">Nova linha</span><span class="sxs-lookup"><span data-stu-id="618f3-118">Newline</span></span>|`\n`|
|<span data-ttu-id="618f3-119">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="618f3-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="618f3-120">Tabulação</span><span class="sxs-lookup"><span data-stu-id="618f3-120">Tab</span></span>|`\t`|
|<span data-ttu-id="618f3-121">Tabulação vertical</span><span class="sxs-lookup"><span data-stu-id="618f3-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="618f3-122">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="618f3-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="618f3-123">Marca de aspas</span><span class="sxs-lookup"><span data-stu-id="618f3-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="618f3-124">Apóstrofe</span><span class="sxs-lookup"><span data-stu-id="618f3-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="618f3-125">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="618f3-125">Unicode character</span></span>|<span data-ttu-id="618f3-126">`\DDD` (onde `D` indica um decimal digit; o intervalo de 000 - 255; por exemplo, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="618f3-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; e.g. `\231` = "ç")</span></span>|
|<span data-ttu-id="618f3-127">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="618f3-127">Unicode character</span></span>|<span data-ttu-id="618f3-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; e.g. `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="618f3-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; e.g. `\xE7` = "ç")</span></span>|
|<span data-ttu-id="618f3-129">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="618f3-129">Unicode character</span></span>|<span data-ttu-id="618f3-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  e.g. `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="618f3-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  e.g. `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="618f3-131">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="618f3-131">Unicode character</span></span>|<span data-ttu-id="618f3-132">`\U00HHHHHH` (UTF-32) (onde `H` indica um dígito hexadecimal; o intervalo de 000000 - 10FFFF;  Por exemplo, `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="618f3-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  e.g. `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="618f3-133">O `\DDD` sequência de escape é a notação decimal, a notação octal não como na maioria das outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="618f3-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="618f3-134">Portanto, os dígitos `8` e `9` sejam válidas e uma sequência de `\032` representa um espaço (u+0020), enquanto esse mesmo ponto de código em notação octal seria `\040`.</span><span class="sxs-lookup"><span data-stu-id="618f3-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="618f3-135">Sendo restrita a um intervalo de 0 – 255 (0xFF), o `\DDD` e `\x` sequências de escape são efetivamente as [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) do conjunto de caracteres, desde que corresponde ao primeiro 256 pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="618f3-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="618f3-136">Se precedido pelo símbolo @, o literal é uma cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="618f3-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="618f3-137">Isso significa que as sequências de escape são ignoradas, exceto que dois caracteres de marca de aspas simples são interpretados como caracteres de uma marca de aspas simples.</span><span class="sxs-lookup"><span data-stu-id="618f3-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="618f3-138">Além disso, uma cadeia de caracteres pode ser delimitada por aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="618f3-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="618f3-139">Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="618f3-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="618f3-140">Para especificar uma cadeia de caracteres que contém um embedded caracteres entre aspas, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="618f3-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="618f3-141">Se você usar uma cadeia de caracteres textual, você deve especificar dois caracteres de aspas para indicar um caractere de aspa simples.</span><span class="sxs-lookup"><span data-stu-id="618f3-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="618f3-142">Se você usar uma cadeia de caracteres entre aspas triplas, você pode usar os caracteres de aspas simples sem que eles que está sendo analisado como o fim da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="618f3-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="618f3-143">Essa técnica pode ser útil ao trabalhar com XML ou outras estruturas que incluem as aspas internas.</span><span class="sxs-lookup"><span data-stu-id="618f3-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="618f3-144">No código, cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida é o último caractere antes da quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="618f3-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="618f3-145">Espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="618f3-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="618f3-146">O código a seguir produz uma cadeia de caracteres `str1` que tem o valor `"abc\ndef"` e uma cadeia de caracteres `str2` que tem o valor `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="618f3-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="618f3-147">Você pode acessar os caracteres individuais em uma cadeia de caracteres usando a sintaxe de matriz, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="618f3-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="618f3-148">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="618f3-148">The output is `b`.</span></span>

<span data-ttu-id="618f3-149">Ou você pode extrair subcadeias de caracteres usando a sintaxe de fatia de matriz, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="618f3-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="618f3-150">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="618f3-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="618f3-151">Cadeias de caracteres ASCII pode ser representado usando matrizes de bytes sem sinal, o tipo `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="618f3-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="618f3-152">Adicione o sufixo `B` para uma cadeia de caracteres literal para indicar que ele é uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="618f3-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="618f3-153">As sequências de escape mesmo como cadeias de caracteres Unicode, exceto para as sequências de escape Unicode dão suporte a literais de cadeia de caracteres ASCII usados com matrizes de bytes.</span><span class="sxs-lookup"><span data-stu-id="618f3-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="618f3-154">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="618f3-154">String Operators</span></span>

<span data-ttu-id="618f3-155">Concatenar cadeias de caracteres de duas maneiras: usando o `+` operador ou usando o `^` operador.</span><span class="sxs-lookup"><span data-stu-id="618f3-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="618f3-156">O `+` operador mantém a compatibilidade com a cadeia de caracteres do .NET Framework que recursos de tratamento.</span><span class="sxs-lookup"><span data-stu-id="618f3-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="618f3-157">O exemplo a seguir ilustra a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="618f3-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="618f3-158">Classe de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="618f3-158">String Class</span></span>

<span data-ttu-id="618f3-159">Porque o tipo de cadeia de caracteres no F# é, na verdade, um .NET Framework `System.String` digitar tudo a `System.String` membros estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="618f3-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="618f3-160">Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, o `Length` propriedade e o `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="618f3-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="618f3-161">Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.</span><span class="sxs-lookup"><span data-stu-id="618f3-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="618f3-162">Usando o `Chars` propriedade de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="618f3-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="618f3-163">Módulo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="618f3-163">String Module</span></span>

<span data-ttu-id="618f3-164">Funcionalidade adicional para a manipulação de cadeia de caracteres está incluída na `String` módulo no `FSharp.Core` namespace.</span><span class="sxs-lookup"><span data-stu-id="618f3-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="618f3-165">Para obter mais informações, consulte [módulo Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="618f3-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="618f3-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="618f3-166">See also</span></span>

- [<span data-ttu-id="618f3-167">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="618f3-167">F# Language Reference</span></span>](index.md)

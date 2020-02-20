---
title: Cadeias de caracteres
description: Saiba como o F# tipo ' String ' representa texto imutável como uma sequência de caracteres Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452812"
---
# <a name="strings"></a><span data-ttu-id="96bab-103">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="96bab-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="96bab-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="96bab-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="96bab-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="96bab-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="96bab-106">O tipo de `string` representa texto imutável como uma sequência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="96bab-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="96bab-107">`string` é um alias para `System.String` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96bab-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="96bab-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="96bab-108">Remarks</span></span>

<span data-ttu-id="96bab-109">Literais de cadeia de caracteres são delimitadas pelo caractere de aspas (").</span><span class="sxs-lookup"><span data-stu-id="96bab-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="96bab-110">O caractere de barra invertida (\\) é usado para codificar determinados caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="96bab-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="96bab-111">A barra invertida e o próximo caractere juntos são conhecidos como uma *sequência de escape*.</span><span class="sxs-lookup"><span data-stu-id="96bab-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="96bab-112">As sequências de F# escape com suporte em literais de cadeia de caracteres são mostradas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="96bab-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="96bab-113">Caractere</span><span class="sxs-lookup"><span data-stu-id="96bab-113">Character</span></span>|<span data-ttu-id="96bab-114">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="96bab-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="96bab-115">Alerta</span><span class="sxs-lookup"><span data-stu-id="96bab-115">Alert</span></span>|`\a`|
|<span data-ttu-id="96bab-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="96bab-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="96bab-117">Avanço de formulário</span><span class="sxs-lookup"><span data-stu-id="96bab-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="96bab-118">Nova linha</span><span class="sxs-lookup"><span data-stu-id="96bab-118">Newline</span></span>|`\n`|
|<span data-ttu-id="96bab-119">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="96bab-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="96bab-120">Tab</span><span class="sxs-lookup"><span data-stu-id="96bab-120">Tab</span></span>|`\t`|
|<span data-ttu-id="96bab-121">Guia vertical</span><span class="sxs-lookup"><span data-stu-id="96bab-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="96bab-122">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="96bab-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="96bab-123">Aspas</span><span class="sxs-lookup"><span data-stu-id="96bab-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="96bab-124">Apóstrofo</span><span class="sxs-lookup"><span data-stu-id="96bab-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="96bab-125">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="96bab-125">Unicode character</span></span>|<span data-ttu-id="96bab-126">`\DDD` (em que `D` indica um dígito decimal; intervalo de 000-255; por exemplo, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="96bab-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="96bab-127">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="96bab-127">Unicode character</span></span>|<span data-ttu-id="96bab-128">`\xHH` (em que `H` indica um dígito hexadecimal; intervalo de 00-FF; por exemplo, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="96bab-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="96bab-129">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="96bab-129">Unicode character</span></span>|<span data-ttu-id="96bab-130">`\uHHHH` (UTF-16) (em que `H` indica um dígito hexadecimal; intervalo de 0000-FFFF;  por exemplo, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="96bab-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="96bab-131">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="96bab-131">Unicode character</span></span>|<span data-ttu-id="96bab-132">`\U00HHHHHH` (UTF-32) (em que `H` indica um dígito hexadecimal; intervalo de 000000-10FFFF;  por exemplo, `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="96bab-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="96bab-133">A sequência de escape `\DDD` é notação decimal, não notação octal, como na maioria das outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="96bab-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="96bab-134">Portanto, os dígitos `8` e `9` são válidos e uma sequência de `\032` representa um espaço (U + 0020), enquanto que o mesmo ponto de código na notação octal seria `\040`.</span><span class="sxs-lookup"><span data-stu-id="96bab-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="96bab-135">Sendo restrito a um intervalo de 0-255 (0xFF), as sequências de escape `\DDD` e `\x` são efetivamente o conjunto de caracteres [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , pois isso corresponde aos primeiros 256 pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="96bab-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="96bab-136">Cadeias de caracteres textuais</span><span class="sxs-lookup"><span data-stu-id="96bab-136">Verbatim Strings</span></span>

<span data-ttu-id="96bab-137">Se for precedido pelo símbolo @, o literal é uma cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="96bab-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="96bab-138">Isso significa que todas as sequências de escape são ignoradas, exceto que dois caracteres de aspas são interpretados como um caractere de aspas.</span><span class="sxs-lookup"><span data-stu-id="96bab-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="96bab-139">Cadeias de caracteres entre aspas triplas</span><span class="sxs-lookup"><span data-stu-id="96bab-139">Triple Quoted Strings</span></span>

<span data-ttu-id="96bab-140">Além disso, uma cadeia de caracteres pode estar entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="96bab-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="96bab-141">Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="96bab-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="96bab-142">Para especificar uma cadeia de caracteres que contenha uma cadeia de caracteres entre aspas incorporada, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="96bab-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="96bab-143">Se você usar uma cadeia de caracteres textual, deverá especificar dois caracteres de aspas para indicar um caractere de aspas simples.</span><span class="sxs-lookup"><span data-stu-id="96bab-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="96bab-144">Se você usar uma cadeia de caracteres entre aspas triplas, poderá usar os caracteres de aspas simples sem que eles sejam analisados como o final da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="96bab-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="96bab-145">Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.</span><span class="sxs-lookup"><span data-stu-id="96bab-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="96bab-146">No código, as cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida seja o último caractere antes da quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="96bab-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="96bab-147">O espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="96bab-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="96bab-148">O código a seguir produz uma cadeia de caracteres `str1` com valor `"abc\ndef"` e uma `str2` de cadeia de caracteres com valor `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="96bab-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="96bab-149">Indexação e divisão de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="96bab-149">String Indexing and Slicing</span></span>

<span data-ttu-id="96bab-150">Você pode acessar caracteres individuais em uma cadeia de caracteres usando a sintaxe do tipo matriz, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="96bab-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="96bab-151">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="96bab-151">The output is `b`.</span></span>

<span data-ttu-id="96bab-152">Ou você pode extrair subcadeias de caracteres usando a sintaxe da fatia de matriz, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="96bab-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="96bab-153">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="96bab-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="96bab-154">Você pode representar cadeias de caracteres ASCII por matrizes de bytes não assinados, digite `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="96bab-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="96bab-155">Você adiciona o sufixo `B` a uma cadeia de caracteres literal para indicar que é uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="96bab-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="96bab-156">Literais de cadeia de caracteres ASCII usados com matrizes de bytes dão suporte às mesmas sequências de escape que as cadeias de caracteres Unicode, exceto as sequências de escape Unicode</span><span class="sxs-lookup"><span data-stu-id="96bab-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="96bab-157">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="96bab-157">String Operators</span></span>

<span data-ttu-id="96bab-158">Há duas maneiras de concatenar cadeias de caracteres: usando o operador `+` ou usando o operador `^`.</span><span class="sxs-lookup"><span data-stu-id="96bab-158">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="96bab-159">O operador `+` mantém a compatibilidade com os recursos de manipulação de cadeia de caracteres .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96bab-159">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="96bab-160">O exemplo a seguir ilustra a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="96bab-160">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="96bab-161">Classe String</span><span class="sxs-lookup"><span data-stu-id="96bab-161">String Class</span></span>

<span data-ttu-id="96bab-162">Como o tipo de cadeia F# de caracteres no é, na verdade, um .NET Framework tipo de `System.String`, todos os membros `System.String` estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="96bab-162">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="96bab-163">Isso inclui o operador de `+`, que é usado para concatenar cadeias de caracteres, a propriedade `Length` e a propriedade `Chars`, que retorna a cadeia como uma matriz de caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="96bab-163">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="96bab-164">Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.</span><span class="sxs-lookup"><span data-stu-id="96bab-164">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="96bab-165">Usando a propriedade `Chars` de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="96bab-165">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="96bab-166">Módulo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="96bab-166">String Module</span></span>

<span data-ttu-id="96bab-167">A funcionalidade adicional para manipulação de cadeia de caracteres está incluída no módulo `String` no namespace `FSharp.Core`.</span><span class="sxs-lookup"><span data-stu-id="96bab-167">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="96bab-168">Para obter mais informações, consulte [Core. String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="96bab-168">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="96bab-169">Confira também</span><span class="sxs-lookup"><span data-stu-id="96bab-169">See also</span></span>

- [<span data-ttu-id="96bab-170">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="96bab-170">F# Language Reference</span></span>](index.md)

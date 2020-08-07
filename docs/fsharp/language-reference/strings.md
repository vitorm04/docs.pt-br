---
title: Cadeias de caracteres
description: 'Saiba como o tipo de cadeia de caracteres F # representa um texto imutável como uma sequência de caracteres Unicode.'
ms.date: 07/05/2019
ms.openlocfilehash: 67a6506b4b8c479da1022c069a7f53402f904b4d
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855407"
---
# <a name="strings"></a><span data-ttu-id="552e4-103">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="552e4-103">Strings</span></span>

<span data-ttu-id="552e4-104">O `string` tipo representa texto imutável como uma sequência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="552e4-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="552e4-105">`string` é um alias de `System.String` no .NET.</span><span class="sxs-lookup"><span data-stu-id="552e4-105">`string` is an alias for `System.String` in .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="552e4-106">A referência da API docs.microsoft.com para F # não está completa.</span><span class="sxs-lookup"><span data-stu-id="552e4-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="552e4-107">Se você encontrar links desfeitos, consulte a [documentação da biblioteca principal F #](https://fsharp.github.io/fsharp-core-docs/) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="552e4-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="remarks"></a><span data-ttu-id="552e4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="552e4-108">Remarks</span></span>

<span data-ttu-id="552e4-109">Literais de cadeia de caracteres são delimitadas pelo caractere de aspas (").</span><span class="sxs-lookup"><span data-stu-id="552e4-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="552e4-110">O caractere de barra invertida ( \\ ) é usado para codificar determinados caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="552e4-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="552e4-111">A barra invertida e o próximo caractere juntos são conhecidos como uma *sequência de escape*.</span><span class="sxs-lookup"><span data-stu-id="552e4-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="552e4-112">As sequências de escape com suporte em literais de cadeia de caracteres F # são mostradas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="552e4-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="552e4-113">Caractere</span><span class="sxs-lookup"><span data-stu-id="552e4-113">Character</span></span>|<span data-ttu-id="552e4-114">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="552e4-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="552e4-115">Alerta</span><span class="sxs-lookup"><span data-stu-id="552e4-115">Alert</span></span>|`\a`|
|<span data-ttu-id="552e4-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="552e4-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="552e4-117">Avanço de formulário</span><span class="sxs-lookup"><span data-stu-id="552e4-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="552e4-118">Nova linha</span><span class="sxs-lookup"><span data-stu-id="552e4-118">Newline</span></span>|`\n`|
|<span data-ttu-id="552e4-119">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="552e4-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="552e4-120">Tab</span><span class="sxs-lookup"><span data-stu-id="552e4-120">Tab</span></span>|`\t`|
|<span data-ttu-id="552e4-121">Guia vertical</span><span class="sxs-lookup"><span data-stu-id="552e4-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="552e4-122">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="552e4-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="552e4-123">Aspas</span><span class="sxs-lookup"><span data-stu-id="552e4-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="552e4-124">Apóstrofo</span><span class="sxs-lookup"><span data-stu-id="552e4-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="552e4-125">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="552e4-125">Unicode character</span></span>|<span data-ttu-id="552e4-126">`\DDD`(onde `D` indica um dígito decimal; intervalo de 000-255; por exemplo, `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="552e4-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="552e4-127">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="552e4-127">Unicode character</span></span>|<span data-ttu-id="552e4-128">`\xHH`(onde `H` indica um dígito hexadecimal; intervalo de 00-FF; por exemplo, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="552e4-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="552e4-129">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="552e4-129">Unicode character</span></span>|<span data-ttu-id="552e4-130">`\uHHHH`(UTF-16) (onde `H` indica um dígito hexadecimal; intervalo de 0000-ffff;  por exemplo, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="552e4-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="552e4-131">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="552e4-131">Unicode character</span></span>|<span data-ttu-id="552e4-132">`\U00HHHHHH`(UTF-32) (onde `H` indica um dígito hexadecimal; intervalo de 000000-10FFFF;  por exemplo, `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="552e4-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="552e4-133">A `\DDD` sequência de escape é notação decimal, não notação octal, como na maioria das outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="552e4-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="552e4-134">Portanto, os dígitos `8` e `9` são válidos, e uma sequência de `\032` representa um espaço (U + 0020), enquanto que o mesmo ponto de código na notação octal seria `\040` .</span><span class="sxs-lookup"><span data-stu-id="552e4-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="552e4-135">Sendo restrito a um intervalo de 0-255 (0xFF), as `\DDD` `\x` sequências de escape e são efetivamente o conjunto de caracteres [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , pois isso corresponde aos primeiros 256 pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="552e4-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="552e4-136">Cadeias de caracteres textuais</span><span class="sxs-lookup"><span data-stu-id="552e4-136">Verbatim Strings</span></span>

<span data-ttu-id="552e4-137">Se for precedido pelo símbolo @, o literal é uma cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="552e4-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="552e4-138">Isso significa que todas as sequências de escape são ignoradas, exceto que dois caracteres de aspas são interpretados como um caractere de aspas.</span><span class="sxs-lookup"><span data-stu-id="552e4-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="552e4-139">Cadeias de caracteres entre aspas triplas</span><span class="sxs-lookup"><span data-stu-id="552e4-139">Triple Quoted Strings</span></span>

<span data-ttu-id="552e4-140">Além disso, uma cadeia de caracteres pode estar entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="552e4-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="552e4-141">Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="552e4-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="552e4-142">Para especificar uma cadeia de caracteres que contenha uma cadeia de caracteres entre aspas incorporada, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="552e4-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="552e4-143">Se você usar uma cadeia de caracteres textual, deverá especificar dois caracteres de aspas para indicar um caractere de aspas simples.</span><span class="sxs-lookup"><span data-stu-id="552e4-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="552e4-144">Se você usar uma cadeia de caracteres entre aspas triplas, poderá usar os caracteres de aspas simples sem que eles sejam analisados como o final da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="552e4-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="552e4-145">Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.</span><span class="sxs-lookup"><span data-stu-id="552e4-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="552e4-146">No código, as cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida seja o último caractere antes da quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="552e4-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="552e4-147">O espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="552e4-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="552e4-148">O código a seguir produz uma cadeia de caracteres `str1` com valor `"abc\ndef"` e uma cadeia de caracteres `str2` com valor `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="552e4-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="552e4-149">Indexação e divisão de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="552e4-149">String Indexing and Slicing</span></span>

<span data-ttu-id="552e4-150">Você pode acessar caracteres individuais em uma cadeia de caracteres usando a sintaxe do tipo matriz, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="552e4-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="552e4-151">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="552e4-151">The output is `b`.</span></span>

<span data-ttu-id="552e4-152">Ou você pode extrair subcadeias de caracteres usando a sintaxe da fatia de matriz, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="552e4-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="552e4-153">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="552e4-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="552e4-154">Você pode representar cadeias de caracteres ASCII por matrizes de bytes não assinados, digite `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="552e4-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="552e4-155">Você adiciona o sufixo `B` a um literal de cadeia de caracteres para indicar que é uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="552e4-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="552e4-156">Literais de cadeia de caracteres ASCII usados com matrizes de bytes dão suporte às mesmas sequências de escape que as cadeias de caracteres Unicode, exceto as sequências de escape Unicode</span><span class="sxs-lookup"><span data-stu-id="552e4-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="552e4-157">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="552e4-157">String Operators</span></span>

<span data-ttu-id="552e4-158">O `+` operador pode ser usado para concatenar cadeias de caracteres, mantendo a compatibilidade com os recursos de manipulação de cadeia de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="552e4-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="552e4-159">O exemplo a seguir ilustra a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="552e4-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="552e4-160">Classe String</span><span class="sxs-lookup"><span data-stu-id="552e4-160">String Class</span></span>

<span data-ttu-id="552e4-161">Como o tipo de cadeia de caracteres em F # é, na verdade, um tipo de .NET Framework `System.String` , todos os `System.String` Membros estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="552e4-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="552e4-162">Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, a `Length` propriedade e a `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caractere Unicode.</span><span class="sxs-lookup"><span data-stu-id="552e4-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="552e4-163">Para obter mais informações sobre cadeias de caracteres, consulte `System.String` .</span><span class="sxs-lookup"><span data-stu-id="552e4-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="552e4-164">Usando a `Chars` propriedade de `System.String` , você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="552e4-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="552e4-165">Módulo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="552e4-165">String Module</span></span>

<span data-ttu-id="552e4-166">A funcionalidade adicional para manipulação de cadeia de caracteres está incluída no `String` módulo no `FSharp.Core` namespace.</span><span class="sxs-lookup"><span data-stu-id="552e4-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="552e4-167">Para obter mais informações, consulte [Core. String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="552e4-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="552e4-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="552e4-168">See also</span></span>

- [<span data-ttu-id="552e4-169">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="552e4-169">F# Language Reference</span></span>](index.md)

---
title: Cadeias de caracteres
description: Saiba como o tipo F# 'string' representa o texto imutável como uma seqüência de caracteres Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739564"
---
# <a name="strings"></a><span data-ttu-id="af130-103">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="af130-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="af130-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="af130-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="af130-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="af130-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="af130-106">O `string` tipo representa texto imutável como uma seqüência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="af130-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="af130-107">`string` é um alias para `System.String` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af130-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="af130-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="af130-108">Remarks</span></span>

<span data-ttu-id="af130-109">Os literais das cordas são delimitados pelo caractere de marcação (").</span><span class="sxs-lookup"><span data-stu-id="af130-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="af130-110">O caractere barra \\ invertida () é usado para codificar certos caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="af130-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="af130-111">A barra invertida e o próximo personagem juntos são conhecidos como uma *seqüência de fuga.*</span><span class="sxs-lookup"><span data-stu-id="af130-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="af130-112">Sequências de escape suportadas em literais de seqüência f# são mostradas na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="af130-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="af130-113">Caractere</span><span class="sxs-lookup"><span data-stu-id="af130-113">Character</span></span>|<span data-ttu-id="af130-114">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="af130-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="af130-115">Alerta</span><span class="sxs-lookup"><span data-stu-id="af130-115">Alert</span></span>|`\a`|
|<span data-ttu-id="af130-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="af130-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="af130-117">Avanço de formulário</span><span class="sxs-lookup"><span data-stu-id="af130-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="af130-118">Nova linha</span><span class="sxs-lookup"><span data-stu-id="af130-118">Newline</span></span>|`\n`|
|<span data-ttu-id="af130-119">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="af130-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="af130-120">Tab</span><span class="sxs-lookup"><span data-stu-id="af130-120">Tab</span></span>|`\t`|
|<span data-ttu-id="af130-121">Guia vertical</span><span class="sxs-lookup"><span data-stu-id="af130-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="af130-122">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="af130-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="af130-123">Aspas</span><span class="sxs-lookup"><span data-stu-id="af130-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="af130-124">Apóstrofo</span><span class="sxs-lookup"><span data-stu-id="af130-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="af130-125">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="af130-125">Unicode character</span></span>|<span data-ttu-id="af130-126">`\DDD`(onde `D` indica um dígito decimal; intervalo de 000 `\231` - 255; por exemplo, = "ç")</span><span class="sxs-lookup"><span data-stu-id="af130-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="af130-127">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="af130-127">Unicode character</span></span>|<span data-ttu-id="af130-128">`\xHH`(onde `H` indica um dígito hexadecimal; intervalo de 00 - FF; por exemplo, `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="af130-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="af130-129">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="af130-129">Unicode character</span></span>|<span data-ttu-id="af130-130">`\uHHHH`(UTF-16) (onde `H` indica um dígito hexadecimal; intervalo de 0000 - FFFF;  por exemplo, `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="af130-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="af130-131">Caractere unicode</span><span class="sxs-lookup"><span data-stu-id="af130-131">Unicode character</span></span>|<span data-ttu-id="af130-132">`\U00HHHHHH`(UTF-32) (onde `H` indica um dígito hexadecimal; intervalo de 000000 - 10FFFF;  por exemplo, `\U0001F47D` 👽= "")</span><span class="sxs-lookup"><span data-stu-id="af130-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="af130-133">A `\DDD` seqüência de fuga é notação decimal, não notação octal como na maioria das outras línguas.</span><span class="sxs-lookup"><span data-stu-id="af130-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="af130-134">Portanto, dígitos `8` `9` e são válidos, `\032` e uma seqüência de representa um espaço (U+0020), `\040`enquanto que o mesmo ponto de código na notação octal seria .</span><span class="sxs-lookup"><span data-stu-id="af130-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="af130-135">Sendo constrangidos a um intervalo de 0 `\DDD` - `\x` 255 (0xFF), as seqüências e fuga são efetivamente o conjunto de caracteres [ISO-8859-1,](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) uma vez que corresponde aos primeiros 256 pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="af130-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="af130-136">Cordas Verbatim</span><span class="sxs-lookup"><span data-stu-id="af130-136">Verbatim Strings</span></span>

<span data-ttu-id="af130-137">Se precedido pelo símbolo @, o literal é uma seqüência verbatim.</span><span class="sxs-lookup"><span data-stu-id="af130-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="af130-138">Isso significa que todas as seqüências de fuga são ignoradas, exceto que dois caracteres de marca de citação são interpretados como um caractere de marca de citação.</span><span class="sxs-lookup"><span data-stu-id="af130-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="af130-139">Cordas tríplices citadas</span><span class="sxs-lookup"><span data-stu-id="af130-139">Triple Quoted Strings</span></span>

<span data-ttu-id="af130-140">Além disso, uma seqüência pode ser fechada por cotações triplas.</span><span class="sxs-lookup"><span data-stu-id="af130-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="af130-141">Neste caso, todas as seqüências de escape são ignoradas, incluindo caracteres de marca ção dupla.</span><span class="sxs-lookup"><span data-stu-id="af130-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="af130-142">Para especificar uma seqüência que contém uma seqüência de string incorporada, você pode usar uma seqüência verbatim ou uma seqüência de três citações.</span><span class="sxs-lookup"><span data-stu-id="af130-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="af130-143">Se você usar uma seqüência de caracteres verbatim, você deve especificar dois caracteres de marca de citação para indicar um único caractere de marca de citação.</span><span class="sxs-lookup"><span data-stu-id="af130-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="af130-144">Se você usar uma seqüência de caracteres de citação tripla, você pode usar os caracteres de marca de cotação única sem que eles sejam analisados como o final da seqüência.</span><span class="sxs-lookup"><span data-stu-id="af130-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="af130-145">Esta técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.</span><span class="sxs-lookup"><span data-stu-id="af130-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="af130-146">Em código, as strings que têm quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como linhas novas, a menos que um caractere de barra invertida seja o último caractere antes da linha quebrar.</span><span class="sxs-lookup"><span data-stu-id="af130-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="af130-147">O espaço em branco líder na próxima linha é ignorado quando o caractere barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="af130-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="af130-148">O código a seguir `str1` produz `"abc\ndef"` uma string `str2` que `"abcdef"`tem valor e uma string que tem valor .</span><span class="sxs-lookup"><span data-stu-id="af130-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="af130-149">Indexação e Corte de Cordas</span><span class="sxs-lookup"><span data-stu-id="af130-149">String Indexing and Slicing</span></span>

<span data-ttu-id="af130-150">Você pode acessar caracteres individuais em uma seqüência usando sintaxe semelhante a matriz, da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="af130-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="af130-151">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="af130-151">The output is `b`.</span></span>

<span data-ttu-id="af130-152">Ou você pode extrair substrings usando a sintaxe de fatia de matriz, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="af130-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="af130-153">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="af130-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="af130-154">Você pode representar strings ASCII por matrizes de `byte[]`bytes não assinados, digite .</span><span class="sxs-lookup"><span data-stu-id="af130-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="af130-155">Você adiciona o `B` sufixo a um literal de seqüência para indicar que é uma seqüência ASCII.</span><span class="sxs-lookup"><span data-stu-id="af130-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="af130-156">Os literais de seqüência ASCII usados com matrizes de byte suportam as mesmas seqüências de escape que as seqüências Unicode, exceto as seqüências de fuga Unicode.</span><span class="sxs-lookup"><span data-stu-id="af130-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="af130-157">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="af130-157">String Operators</span></span>

<span data-ttu-id="af130-158">O `+` operador pode ser usado para concatenar strings, mantendo a compatibilidade com os recursos de manuseio de strings .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af130-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="af130-159">O exemplo a seguir ilustra a concatenação de cordas.</span><span class="sxs-lookup"><span data-stu-id="af130-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="af130-160">Classe cordas</span><span class="sxs-lookup"><span data-stu-id="af130-160">String Class</span></span>

<span data-ttu-id="af130-161">Como o tipo de string em F# é na verdade um tipo de Framework `System.String` .NET, todos os `System.String` membros estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="af130-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="af130-162">Isso inclui `+` o operador, que é usado para `Length` concatenar `Chars` strings, a propriedade e a propriedade, que retorna a string como uma matriz de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="af130-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="af130-163">Para obter mais informações `System.String`sobre strings, consulte .</span><span class="sxs-lookup"><span data-stu-id="af130-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="af130-164">Usando a `Chars` propriedade `System.String`de , você pode acessar os caracteres individuais em uma seqüência especificando um índice, como é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="af130-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="af130-165">Módulo de cordas</span><span class="sxs-lookup"><span data-stu-id="af130-165">String Module</span></span>

<span data-ttu-id="af130-166">A funcionalidade adicional para o manuseio `String` de `FSharp.Core` cordas está incluída no módulo no namespace.</span><span class="sxs-lookup"><span data-stu-id="af130-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="af130-167">Para obter mais informações, consulte [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="af130-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="af130-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="af130-168">See also</span></span>

- [<span data-ttu-id="af130-169">Referência de idioma F#</span><span class="sxs-lookup"><span data-stu-id="af130-169">F# Language Reference</span></span>](index.md)

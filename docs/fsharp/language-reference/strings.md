---
title: Cadeias de caracteres (F#)
description: "Saiba como o tipo 'string' F # representa texto imutável como uma sequência de caracteres Unicode."
ms.date: 05/16/2016
ms.openlocfilehash: 21971602093bc84b0df47d4ae46a14fb936c28bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43799337"
---
# <a name="strings"></a><span data-ttu-id="36de4-103">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="36de4-103">Strings</span></span>

> [!NOTE]
<span data-ttu-id="36de4-104">Os links de referência da API neste artigo levarão você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="36de4-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="36de4-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="36de4-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="36de4-106">O `string` tipo representa texto imutável, como uma sequência de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="36de4-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="36de4-107">`string` é um alias para `System.String` no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36de4-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="36de4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="36de4-108">Remarks</span></span>

<span data-ttu-id="36de4-109">Literais de cadeia de caracteres são delimitados pelo caractere de aspas (").</span><span class="sxs-lookup"><span data-stu-id="36de4-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="36de4-110">O caractere de barra invertida ( \\ ) é usado para codificar determinados caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="36de4-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="36de4-111">A barra invertida e o próximo caractere junto são conhecidos como uma *sequência de escape*.</span><span class="sxs-lookup"><span data-stu-id="36de4-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="36de4-112">Com suporte em F # de cadeia de caracteres literais são mostrados na tabela a seguir de sequências de escape.</span><span class="sxs-lookup"><span data-stu-id="36de4-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="36de4-113">Caractere</span><span class="sxs-lookup"><span data-stu-id="36de4-113">Character</span></span>|<span data-ttu-id="36de4-114">Sequência de escape</span><span class="sxs-lookup"><span data-stu-id="36de4-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="36de4-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="36de4-115">Backspace</span></span>|`\b`|
|<span data-ttu-id="36de4-116">Nova linha</span><span class="sxs-lookup"><span data-stu-id="36de4-116">Newline</span></span>|`\n`|
|<span data-ttu-id="36de4-117">Retorno de carro</span><span class="sxs-lookup"><span data-stu-id="36de4-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="36de4-118">Tabulação</span><span class="sxs-lookup"><span data-stu-id="36de4-118">Tab</span></span>|`\t`|
|<span data-ttu-id="36de4-119">Barra invertida</span><span class="sxs-lookup"><span data-stu-id="36de4-119">Backslash</span></span>|`\\`|
|<span data-ttu-id="36de4-120">Marca de aspas</span><span class="sxs-lookup"><span data-stu-id="36de4-120">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="36de4-121">Apóstrofe</span><span class="sxs-lookup"><span data-stu-id="36de4-121">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="36de4-122">caractere Unicode</span><span class="sxs-lookup"><span data-stu-id="36de4-122">Unicode character</span></span>|<span data-ttu-id="36de4-123">`\uXXXX` ou `\UXXXX` (onde `X` indica um dígito hexadecimal)</span><span class="sxs-lookup"><span data-stu-id="36de4-123">`\uXXXX` or `\UXXXX` (where `X` indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="36de4-124">Se precedido pelo símbolo @, o literal é uma cadeia de caracteres textual.</span><span class="sxs-lookup"><span data-stu-id="36de4-124">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="36de4-125">Isso significa que as sequências de escape são ignoradas, exceto que dois caracteres de marca de aspas simples são interpretados como caracteres de uma marca de aspas simples.</span><span class="sxs-lookup"><span data-stu-id="36de4-125">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="36de4-126">Além disso, uma cadeia de caracteres pode ser delimitada por aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="36de4-126">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="36de4-127">Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="36de4-127">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="36de4-128">Para especificar uma cadeia de caracteres que contém um embedded caracteres entre aspas, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas.</span><span class="sxs-lookup"><span data-stu-id="36de4-128">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="36de4-129">Se você usar uma cadeia de caracteres textual, você deve especificar dois caracteres de aspas para indicar um caractere de aspa simples.</span><span class="sxs-lookup"><span data-stu-id="36de4-129">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="36de4-130">Se você usar uma cadeia de caracteres entre aspas triplas, você pode usar os caracteres de aspas simples sem que eles que está sendo analisado como o fim da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="36de4-130">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="36de4-131">Essa técnica pode ser útil ao trabalhar com XML ou outras estruturas que incluem as aspas internas.</span><span class="sxs-lookup"><span data-stu-id="36de4-131">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="36de4-132">No código, cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida é o último caractere antes da quebra de linha.</span><span class="sxs-lookup"><span data-stu-id="36de4-132">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="36de4-133">Espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado.</span><span class="sxs-lookup"><span data-stu-id="36de4-133">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="36de4-134">O código a seguir produz uma cadeia de caracteres `str1` que tem o valor `"abc\ndef"` e uma cadeia de caracteres `str2` que tem o valor `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="36de4-134">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="36de4-135">Você pode acessar os caracteres individuais em uma cadeia de caracteres usando a sintaxe de matriz, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="36de4-135">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="36de4-136">A saída é `b`.</span><span class="sxs-lookup"><span data-stu-id="36de4-136">The output is `b`.</span></span>

<span data-ttu-id="36de4-137">Ou você pode extrair subcadeias de caracteres usando a sintaxe de fatia de matriz, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="36de4-137">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="36de4-138">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="36de4-138">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="36de4-139">Cadeias de caracteres ASCII pode ser representado usando matrizes de bytes sem sinal, o tipo `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="36de4-139">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="36de4-140">Adicione o sufixo `B` para uma cadeia de caracteres literal para indicar que ele é uma cadeia de caracteres ASCII.</span><span class="sxs-lookup"><span data-stu-id="36de4-140">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="36de4-141">As sequências de escape mesmo como cadeias de caracteres Unicode, exceto para as sequências de escape Unicode dão suporte a literais de cadeia de caracteres ASCII usados com matrizes de bytes.</span><span class="sxs-lookup"><span data-stu-id="36de4-141">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="36de4-142">Operadores da cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="36de4-142">String Operators</span></span>

<span data-ttu-id="36de4-143">Concatenar cadeias de caracteres de duas maneiras: usando o `+` operador ou usando o `^` operador.</span><span class="sxs-lookup"><span data-stu-id="36de4-143">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="36de4-144">O `+` operador mantém a compatibilidade com a cadeia de caracteres do .NET Framework que recursos de tratamento.</span><span class="sxs-lookup"><span data-stu-id="36de4-144">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="36de4-145">O exemplo a seguir ilustra a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="36de4-145">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="36de4-146">Classe de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="36de4-146">String Class</span></span>

<span data-ttu-id="36de4-147">Porque o tipo de cadeia de caracteres no F #, na verdade, um .NET Framework `System.String` digitar, todo o `System.String` membros estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="36de4-147">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="36de4-148">Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, o `Length` propriedade e o `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="36de4-148">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="36de4-149">Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.</span><span class="sxs-lookup"><span data-stu-id="36de4-149">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="36de4-150">Usando o `Chars` propriedade de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="36de4-150">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="36de4-151">Módulo de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="36de4-151">String Module</span></span>

<span data-ttu-id="36de4-152">Funcionalidade adicional para a manipulação de cadeia de caracteres está incluída na `String` módulo no `FSharp.Core` namespace.</span><span class="sxs-lookup"><span data-stu-id="36de4-152">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="36de4-153">Para obter mais informações, consulte [módulo Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="36de4-153">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="36de4-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36de4-154">See also</span></span>

- [<span data-ttu-id="36de4-155">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="36de4-155">F# Language Reference</span></span>](index.md)

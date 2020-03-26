---
title: Introdução à codificação de caracteres em .NET
description: Aprenda sobre codificação de caracteres e decodificação em .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134425"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="7af50-103">Codificação de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="7af50-103">Character encoding in .NET</span></span>

<span data-ttu-id="7af50-104">Este artigo fornece uma introdução aos sistemas de codificação de caracteres que são usados pelo .NET.</span><span class="sxs-lookup"><span data-stu-id="7af50-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="7af50-105">O artigo explica <xref:System.String> <xref:System.Char>como <xref:System.Text.Rune>os <xref:System.Globalization.StringInfo> tipos funcionam com Unicode, UTF-16 e UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7af50-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="7af50-106">O termo *caractere* é usado aqui no sentido geral do *que um leitor percebe como um único elemento de exibição*.</span><span class="sxs-lookup"><span data-stu-id="7af50-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="7af50-107">Exemplos comuns são a letra "a", o símbolo🐂"@" e o emoji " ".</span><span class="sxs-lookup"><span data-stu-id="7af50-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="7af50-108">Às vezes, o que parece um caractere é na verdade composto de múltiplos elementos de exibição independentes, como explica a seção em [clusters de grafeme.](#grapheme-clusters)</span><span class="sxs-lookup"><span data-stu-id="7af50-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="7af50-109">Os tipos de string e char</span><span class="sxs-lookup"><span data-stu-id="7af50-109">The string and char types</span></span>

<span data-ttu-id="7af50-110">Um exemplo da classe [string](xref:System.String) representa algum texto.</span><span class="sxs-lookup"><span data-stu-id="7af50-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="7af50-111">A `string` é logicamente uma seqüência de valores de 16 bits, cada um dos quais é uma instância da estrutura de [char.](xref:System.Char)</span><span class="sxs-lookup"><span data-stu-id="7af50-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="7af50-112">A [corda. A](xref:System.String.Length) propriedade de `char` comprimento retorna `string` o número de instâncias na instância.</span><span class="sxs-lookup"><span data-stu-id="7af50-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="7af50-113">A função de amostra a seguir imprime os valores `char` na notação hexadecimal de todas as instâncias em a: `string`</span><span class="sxs-lookup"><span data-stu-id="7af50-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="7af50-114">Passe a seqüência "Olá" para esta função e obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="7af50-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="7af50-115">Cada personagem é representado `char` por um único valor.</span><span class="sxs-lookup"><span data-stu-id="7af50-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="7af50-116">Esse padrão vale para a maioria das línguas do mundo.</span><span class="sxs-lookup"><span data-stu-id="7af50-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="7af50-117">Por exemplo, aqui está a saída para dois caracteres chineses que soam *como nə həo* e significa *Olá*:</span><span class="sxs-lookup"><span data-stu-id="7af50-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="7af50-118">No entanto, para algumas línguas e para `char` alguns símbolos e emojis, é preciso duas instâncias para representar um único personagem.</span><span class="sxs-lookup"><span data-stu-id="7af50-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="7af50-119">Por exemplo, compare `char` os caracteres e instâncias na palavra que significa *Osage* na língua Osage:</span><span class="sxs-lookup"><span data-stu-id="7af50-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="7af50-120">No exemplo anterior, cada caractere, exceto `char` o espaço, é representado por duas instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="7af50-121">Um único emoji Unicode também `char`é representado por dois s, como visto no exemplo a seguir mostrando um emoji de boi:</span><span class="sxs-lookup"><span data-stu-id="7af50-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="7af50-122">Esses exemplos mostram que `string.Length`o valor de `char` , que indica o número de instâncias, não necessariamente indica o número de caracteres exibidos.</span><span class="sxs-lookup"><span data-stu-id="7af50-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="7af50-123">Uma `char` única instância por si só não representa necessariamente um personagem.</span><span class="sxs-lookup"><span data-stu-id="7af50-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="7af50-124">Os `char` pares que mapeiam para um único caractere são chamados *pares de substitutos*.</span><span class="sxs-lookup"><span data-stu-id="7af50-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="7af50-125">Para entender como eles funcionam, você precisa entender a codificação Unicode e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="7af50-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="7af50-126">Pontos de código Unicode</span><span class="sxs-lookup"><span data-stu-id="7af50-126">Unicode code points</span></span>

<span data-ttu-id="7af50-127">Unicode é um padrão internacional de codificação para uso em várias plataformas e com vários idiomas e scripts.</span><span class="sxs-lookup"><span data-stu-id="7af50-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="7af50-128">O Padrão Unicode define mais de 1,1 milhão de [pontos de código](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="7af50-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="7af50-129">Um ponto de código é um valor inteiro `U+10FFFF` que pode variar de 0 a (decimal 1.114.111).</span><span class="sxs-lookup"><span data-stu-id="7af50-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="7af50-130">Alguns pontos de código são atribuídos a letras, símbolos ou emojis.</span><span class="sxs-lookup"><span data-stu-id="7af50-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="7af50-131">Outros são atribuídos a ações que controlam como texto ou caracteres são exibidos, como avançar para uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="7af50-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="7af50-132">Muitos pontos de código ainda não foram atribuídos.</span><span class="sxs-lookup"><span data-stu-id="7af50-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="7af50-133">Aqui estão alguns exemplos de atribuições de pontos de código, com links para gráficos Unicode em que eles aparecem:</span><span class="sxs-lookup"><span data-stu-id="7af50-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="7af50-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="7af50-134">Decimal</span></span>|<span data-ttu-id="7af50-135">Hex</span><span class="sxs-lookup"><span data-stu-id="7af50-135">Hex</span></span>       |<span data-ttu-id="7af50-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7af50-136">Example</span></span>|<span data-ttu-id="7af50-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="7af50-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="7af50-138">10</span><span class="sxs-lookup"><span data-stu-id="7af50-138">10</span></span>     | `U+000A` |<span data-ttu-id="7af50-139">N/D</span><span class="sxs-lookup"><span data-stu-id="7af50-139">N/A</span></span>| [<span data-ttu-id="7af50-140">ALIMENTAÇÃO DE LINHA</span><span class="sxs-lookup"><span data-stu-id="7af50-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="7af50-141">65</span><span class="sxs-lookup"><span data-stu-id="7af50-141">65</span></span>     | `U+0061` | <span data-ttu-id="7af50-142">a</span><span class="sxs-lookup"><span data-stu-id="7af50-142">a</span></span> | [<span data-ttu-id="7af50-143">LATIN PEQUENA LETRA A</span><span class="sxs-lookup"><span data-stu-id="7af50-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="7af50-144">562</span><span class="sxs-lookup"><span data-stu-id="7af50-144">562</span></span>    | `U+0232` | <span data-ttu-id="7af50-145">Em 1998</span><span class="sxs-lookup"><span data-stu-id="7af50-145">Ȳ</span></span> | [<span data-ttu-id="7af50-146">CARTA CAPITAL LATINA E COM MACRON</span><span class="sxs-lookup"><span data-stu-id="7af50-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="7af50-147">68,675</span><span class="sxs-lookup"><span data-stu-id="7af50-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="7af50-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="7af50-148">𐱃</span></span> | [<span data-ttu-id="7af50-149">VELHA CARTA TURCA ORKHON EM</span><span class="sxs-lookup"><span data-stu-id="7af50-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="7af50-150">127,801</span><span class="sxs-lookup"><span data-stu-id="7af50-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="7af50-151">🌹</span><span class="sxs-lookup"><span data-stu-id="7af50-151">🌹</span></span> | [<span data-ttu-id="7af50-152">Emoji ROSE</span><span class="sxs-lookup"><span data-stu-id="7af50-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="7af50-153">Os pontos de código são normalmente referidos usando a sintaxe, `U+xxxx`onde `xxxx` está o valor inteiro codificado por hexa.</span><span class="sxs-lookup"><span data-stu-id="7af50-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="7af50-154">Dentro da gama completa de pontos de código há dois subintervalos:</span><span class="sxs-lookup"><span data-stu-id="7af50-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="7af50-155">O **plano multilíngüe básico (BMP)** na faixa `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="7af50-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="7af50-156">Esta faixa de 16 bits fornece 65.536 pontos de código, o suficiente para cobrir a maioria dos sistemas de escrita do mundo.</span><span class="sxs-lookup"><span data-stu-id="7af50-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="7af50-157">**Pontos de código** suplementar `U+10000..U+10FFFF`na faixa .</span><span class="sxs-lookup"><span data-stu-id="7af50-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="7af50-158">Este intervalo de 21 bits fornece mais de um milhão de pontos de código adicionais que podem ser usados para idiomas menos conhecidos e outros propósitos, como emojis.</span><span class="sxs-lookup"><span data-stu-id="7af50-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="7af50-159">O diagrama a seguir ilustra a relação entre o BMP e os pontos de código complementar.</span><span class="sxs-lookup"><span data-stu-id="7af50-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP e pontos de código suplementar":::

## <a name="utf-16-code-units"></a><span data-ttu-id="7af50-161">Unidades de código UTF-16</span><span class="sxs-lookup"><span data-stu-id="7af50-161">UTF-16 code units</span></span>

<span data-ttu-id="7af50-162">O Formato de Transformação unicode de 16 bits[(UTF-16)](https://www.unicode.org/faq/utf_bom.html#UTF16)é um sistema de codificação de caracteres que usa unidades de código de 16 *bits* para representar pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="7af50-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="7af50-163">.NET usa UTF-16 para codificar `string`o texto em um .</span><span class="sxs-lookup"><span data-stu-id="7af50-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="7af50-164">Uma `char` instância representa uma unidade de código de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="7af50-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="7af50-165">Uma única unidade de código de 16 bits pode representar qualquer ponto de código na faixa de 16 bits do Plano Multilíngue Básico.</span><span class="sxs-lookup"><span data-stu-id="7af50-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="7af50-166">Mas para um ponto de código `char` na faixa suplementar, duas instâncias são necessárias.</span><span class="sxs-lookup"><span data-stu-id="7af50-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="7af50-167">Pares substitutos</span><span class="sxs-lookup"><span data-stu-id="7af50-167">Surrogate pairs</span></span>

<span data-ttu-id="7af50-168">A tradução de dois valores de 16 bits para um único valor de 21 `U+D800` `U+DFFF` bits é facilitada por uma faixa especial chamada pontos de *código substituto,* de para (decimal 55.296 a 57.343), inclusive.</span><span class="sxs-lookup"><span data-stu-id="7af50-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="7af50-169">O diagrama a seguir ilustra a relação entre o BMP e os pontos de código substitutos.</span><span class="sxs-lookup"><span data-stu-id="7af50-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="Pontos de código BMP e substituto":::

<span data-ttu-id="7af50-171">Quando um ponto de`U+D800..U+DBFF`código de substituto *alto* ( )`U+DC00..U+DFFF`é imediatamente seguido por um ponto de código de substituto *baixo* (), o par é interpretado como um ponto de código suplementar usando a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="7af50-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="7af50-172">Aqui está a mesma fórmula usando notação decimal:</span><span class="sxs-lookup"><span data-stu-id="7af50-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="7af50-173">Um ponto de código de substituto *alto* não tem um valor numérico maior do que um ponto de código de substituto *baixo.*</span><span class="sxs-lookup"><span data-stu-id="7af50-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="7af50-174">O ponto de código de substituto alto é chamado de "alto" porque é usado para calcular os 11 bits de ordem mais alta da faixa completa de ponto de código de 21 bits.</span><span class="sxs-lookup"><span data-stu-id="7af50-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="7af50-175">O ponto de código de substituto baixo é usado para calcular os 10 bits de ordem inferior.</span><span class="sxs-lookup"><span data-stu-id="7af50-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="7af50-176">Por exemplo, o ponto de código real `0xD83C` `0xDF39` que corresponde ao par substituto e é calculado da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="7af50-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="7af50-177">Aqui está o mesmo cálculo usando notação decimal:</span><span class="sxs-lookup"><span data-stu-id="7af50-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="7af50-178">O exemplo anterior `"\ud83c\udf39"` demonstra que é a codificação `U+1F339 ROSE ('🌹')` UTF-16 do ponto de código mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7af50-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="7af50-179">Valores escalares unicode</span><span class="sxs-lookup"><span data-stu-id="7af50-179">Unicode scalar values</span></span>

<span data-ttu-id="7af50-180">O termo [valor escalar Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) refere-se a todos os pontos de código que não os pontos de código substituto.</span><span class="sxs-lookup"><span data-stu-id="7af50-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="7af50-181">Em outras palavras, um valor escalar é qualquer ponto de código que é atribuído a um caractere ou pode ser atribuído um caractere no futuro.</span><span class="sxs-lookup"><span data-stu-id="7af50-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="7af50-182">"Caractere" aqui refere-se a qualquer coisa que possa ser atribuída a um ponto de código, que inclui coisas como ações que controlam como texto ou caracteres são exibidos.</span><span class="sxs-lookup"><span data-stu-id="7af50-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="7af50-183">O diagrama a seguir ilustra os pontos de código de valor escalar.</span><span class="sxs-lookup"><span data-stu-id="7af50-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Valores escalares":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="7af50-185">O Rune tipo como um valor escalar</span><span class="sxs-lookup"><span data-stu-id="7af50-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="7af50-186">Começando com .NET Core 3.0, o <xref:System.Text.Rune?displayProperty=fullName> tipo representa um valor escalar Unicode.</span><span class="sxs-lookup"><span data-stu-id="7af50-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="7af50-187">**`Rune`não está disponível em .NET Core 2.x ou .NET Framework 4.x.**</span><span class="sxs-lookup"><span data-stu-id="7af50-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="7af50-188">Os `Rune` construtores validam que a instância resultante é um valor escalar Unicode válido, caso contrário, eles lançam uma exceção.</span><span class="sxs-lookup"><span data-stu-id="7af50-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="7af50-189">O exemplo a seguir mostra `Rune` o código que instancia as instâncias com sucesso porque a entrada representa valores escalares válidos:</span><span class="sxs-lookup"><span data-stu-id="7af50-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="7af50-190">O exemplo a seguir lança uma exceção porque o ponto de código está na faixa de substituto e não faz parte de um par de substitutos:</span><span class="sxs-lookup"><span data-stu-id="7af50-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="7af50-191">O exemplo a seguir abre uma exceção porque o ponto de código está além da faixa suplementar:</span><span class="sxs-lookup"><span data-stu-id="7af50-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="7af50-192">exemplo de uso: alteração do caso da letra</span><span class="sxs-lookup"><span data-stu-id="7af50-192"> usage example: changing letter case</span></span>

<span data-ttu-id="7af50-193">Uma API que `char` pega a e assume que está trabalhando com um ponto de `char` código que é um valor escalar não funciona corretamente se for de um par de substitutos.</span><span class="sxs-lookup"><span data-stu-id="7af50-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="7af50-194">Por exemplo, considere o <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> seguinte char método stringque chama cada um em um :</span><span class="sxs-lookup"><span data-stu-id="7af50-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="7af50-195">Se `input` string contiver a letra `er` minúscula de`𐑉`Deseret (), este código`𐐡`não a converterá em maiúsculas ().</span><span class="sxs-lookup"><span data-stu-id="7af50-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="7af50-196">O código `char.ToUpperInvariant` chama separadamente em `U+D801` cada `U+DC49`ponto de código substituto, e .</span><span class="sxs-lookup"><span data-stu-id="7af50-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="7af50-197">Mas `U+D801` não tem informação suficiente por si só para identificá-la como uma letra minúscula, então `char.ToUpperInvariant` deixe-a em paz.</span><span class="sxs-lookup"><span data-stu-id="7af50-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="7af50-198">E ele `U+DC49` lida da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="7af50-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="7af50-199">O resultado é que o ''''' minúsculo no `input` string não é convertido em maiúsculas ''.'.</span><span class="sxs-lookup"><span data-stu-id="7af50-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="7af50-200">Aqui estão duas opções para string converter corretamente a em maiúsculas:</span><span class="sxs-lookup"><span data-stu-id="7af50-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="7af50-201">Ligue <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> para string a entrada em `char`vez`char`de iterar -por- .</span><span class="sxs-lookup"><span data-stu-id="7af50-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="7af50-202">O `string.ToUpperInvariant` método tem acesso a ambas as partes de cada par de substitutos, para que ele possa lidar com todos os pontos de código Unicode corretamente.</span><span class="sxs-lookup"><span data-stu-id="7af50-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="7af50-203">Iterar através dos valores `Rune` escalares `char` Unicode como instâncias em vez de instâncias, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7af50-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="7af50-204">Uma `Rune` vez que uma instância é um valor escalar Unicode válido, ele pode ser passado para APIs que esperam operar em um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="7af50-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="7af50-205">Por exemplo, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> chamar como mostrado no exemplo a seguir dá resultados corretos:</span><span class="sxs-lookup"><span data-stu-id="7af50-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="7af50-206">Outras Rune APIs</span><span class="sxs-lookup"><span data-stu-id="7af50-206">Other Rune APIs</span></span>

<span data-ttu-id="7af50-207">O `Rune` tipo expõe análogos `char` de muitas das APIs.</span><span class="sxs-lookup"><span data-stu-id="7af50-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="7af50-208">Por exemplo, os seguintes métodos `char` espelham APIs estáticas no tipo:</span><span class="sxs-lookup"><span data-stu-id="7af50-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="7af50-209">Para obter o valor escalonado bruto de uma `Rune` instância, use a <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="7af50-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="7af50-210">Para converter `Rune` uma instância de `char`volta <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> a <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> uma seqüência de s, use ou o método.</span><span class="sxs-lookup"><span data-stu-id="7af50-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7af50-211">Uma vez que qualquer valor escalar Unicode é representado por um único `char` ou por um par substituto, qualquer `Rune` instância pode ser representada por no máximo 2 `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="7af50-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> para ver `char` quantas instâncias `Rune` são necessárias para representar uma instância.</span><span class="sxs-lookup"><span data-stu-id="7af50-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="7af50-213">Para obter mais informações `Rune` sobre o tipo .NET, consulte a [ `Rune` referência a API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="7af50-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="7af50-214">Clusters de grafeme</span><span class="sxs-lookup"><span data-stu-id="7af50-214">Grapheme clusters</span></span>

<span data-ttu-id="7af50-215">O que parece um caractere pode resultar de uma combinação de múltiplos pontos de código, de modo que um termo mais descritivo que é frequentemente usado no lugar de "caractere" é [o cluster de grafeme](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="7af50-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="7af50-216">O termo equivalente em .NET é [elemento de texto](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="7af50-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="7af50-217">Considere `string` as instâncias "a", "á".</span><span class="sxs-lookup"><span data-stu-id="7af50-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="7af50-218">"á", e`👩🏽‍🚒`"" ".</span><span class="sxs-lookup"><span data-stu-id="7af50-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="7af50-219">Se o sistema operacional manuseá-los conforme especificado `string` pelo padrão Unicode, cada uma dessas instâncias será exibida como um único elemento de texto ou cluster de grafeme.</span><span class="sxs-lookup"><span data-stu-id="7af50-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="7af50-220">Mas os dois últimos são representados por mais de um ponto de código de valor escalar.</span><span class="sxs-lookup"><span data-stu-id="7af50-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="7af50-221">O string "a" é representado por um `char` valor escalar e contém uma instância.</span><span class="sxs-lookup"><span data-stu-id="7af50-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="7af50-222">O string "á" é representado por um `char` valor escalar e contém uma instância.</span><span class="sxs-lookup"><span data-stu-id="7af50-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* <span data-ttu-id="7af50-223">O string "á" parece o mesmo que "á", mas é `char` representado por dois valores escalares e contém duas instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="7af50-224">Finalmente, string o`👩🏽‍🚒`" " é representado por `char` quatro valores escalares e contém sete instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="7af50-225">`U+1F469 WOMAN`(faixa suplementar, requer um par de substitutos)</span><span class="sxs-lookup"><span data-stu-id="7af50-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="7af50-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(faixa suplementar, requer um par de substitutos)</span><span class="sxs-lookup"><span data-stu-id="7af50-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="7af50-227">`U+1F692 FIRE ENGINE`(faixa suplementar, requer um par de substitutos)</span><span class="sxs-lookup"><span data-stu-id="7af50-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="7af50-228">Em alguns dos exemplos anteriores - como o modificador de acento combinado ou o modificador de tom de pele - o ponto de código não é exibido como um elemento autônomo na tela.</span><span class="sxs-lookup"><span data-stu-id="7af50-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="7af50-229">Em vez disso, serve para modificar a aparência de um elemento de texto que veio antes dele.</span><span class="sxs-lookup"><span data-stu-id="7af50-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="7af50-230">Esses exemplos mostram que pode ser necessário múltiplos valores escalares para compor o que pensamos como um único "caractere", ou "cluster de grafeme".</span><span class="sxs-lookup"><span data-stu-id="7af50-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="7af50-231">Para enumerar os clusters de `string`grafeme de a, use a <xref:System.Globalization.StringInfo> classe como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7af50-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="7af50-232">Se você está familiarizado com swift, o tipo .NET `StringInfo` é conceitualmente semelhante ao tipo de [ `character` Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="7af50-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="7af50-233">Exemplo: charcontagem Runee instâncias de elemento de texto</span><span class="sxs-lookup"><span data-stu-id="7af50-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="7af50-234">Em .NET APIs, um cluster de grafeme é chamado de *elemento de texto*.</span><span class="sxs-lookup"><span data-stu-id="7af50-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="7af50-235">O método a seguir `char` `Rune`demonstra as diferenças entre `string`, e instâncias de elemento de texto em a :</span><span class="sxs-lookup"><span data-stu-id="7af50-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="7af50-236">Se você executar esse código no .NET Framework ou no .NET Core 3.1 ou anterior, a contagem de elementos de texto para os emojis será mostrada `4`.</span><span class="sxs-lookup"><span data-stu-id="7af50-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="7af50-237">Isso é devido a `StringInfo` um bug na classe que é corrigido em .NET 5.</span><span class="sxs-lookup"><span data-stu-id="7af50-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="7af50-238">Exemplo: string instâncias de divisão</span><span class="sxs-lookup"><span data-stu-id="7af50-238">Example: splitting string instances</span></span>

<span data-ttu-id="7af50-239">Ao `string` dividir instâncias, evite dividir pares de substitutos e clusters de grafeme.</span><span class="sxs-lookup"><span data-stu-id="7af50-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="7af50-240">Considere o seguinte exemplo de código incorreto, que pretende stringinserir quebras de linha a cada 10 caracteres em um :</span><span class="sxs-lookup"><span data-stu-id="7af50-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="7af50-241">Como este código enumera instâncias, `char` um par de substitutos`char` que acontece de straddle um limite de 10-limite será dividido e uma nova linha injetada entre eles.</span><span class="sxs-lookup"><span data-stu-id="7af50-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="7af50-242">Essa inserção introduz corrupção de dados, porque os pontos de código substitutos são significativos apenas como pares.</span><span class="sxs-lookup"><span data-stu-id="7af50-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="7af50-243">O potencial de corrupção de dados não é `Rune` eliminado se você enumerar instâncias (valores escalares) em vez de `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="7af50-244">Um conjunto `Rune` de instâncias pode compor um cluster de`char` grafeme que atravessa um limite de 10.</span><span class="sxs-lookup"><span data-stu-id="7af50-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="7af50-245">Se o conjunto de cluster de grafeme for dividido, não poderá ser interpretado corretamente.</span><span class="sxs-lookup"><span data-stu-id="7af50-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="7af50-246">Uma abordagem melhor string é quebrar o clusters de grafeme ou elementos de texto, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7af50-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="7af50-247">Como observado anteriormente, no entanto, em implementações `StringInfo` de .NET diferente do .NET 5, a classe pode lidar com alguns clusters de grafeme incorretamente.</span><span class="sxs-lookup"><span data-stu-id="7af50-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="7af50-248">UTF-8 e UTF-32</span><span class="sxs-lookup"><span data-stu-id="7af50-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="7af50-249">As seções anteriores se concentraram no UTF-16 porque `string` é isso que o .NET usa para codificar instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="7af50-250">Existem outros sistemas de codificação para Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) e [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="7af50-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="7af50-251">Essas codificações usam unidades de código de 8 bits e unidades de código de 32 bits, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7af50-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="7af50-252">Como o UTF-16, o UTF-8 requer várias unidades de código para representar alguns valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="7af50-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="7af50-253">O UTF-32 pode representar qualquer valor escalar em uma única unidade de código de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="7af50-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="7af50-254">Aqui estão alguns exemplos mostrando como o mesmo ponto de código Unicode é representado em cada um desses três sistemas de codificação Unicode:</span><span class="sxs-lookup"><span data-stu-id="7af50-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="7af50-255">Como observado anteriormente, uma única unidade de código UTF-16 de um par de [substitutos](#surrogate-pairs) não tem sentido por si só.</span><span class="sxs-lookup"><span data-stu-id="7af50-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="7af50-256">Da mesma forma, uma única unidade de código UTF-8 não tem sentido por si só se estiver em uma seqüência de dois, três ou quatro usados para calcular um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="7af50-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="7af50-257">Endianness</span><span class="sxs-lookup"><span data-stu-id="7af50-257">Endianness</span></span>

<span data-ttu-id="7af50-258">Em .NET, as unidades de código string UTF-16 de a são armazenadas em memória contígua como uma seqüência de inteiros de 16 bits (instâncias).`char`</span><span class="sxs-lookup"><span data-stu-id="7af50-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="7af50-259">Os pedaços de unidades de código individuais são dispostos de acordo com a [finalidade](https://en.wikipedia.org/wiki/Endianness) da arquitetura atual.</span><span class="sxs-lookup"><span data-stu-id="7af50-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="7af50-260">Em uma arquitetura pouco endiana, os string pontos `[ D801 DCCC ]` de código UTF-16 seriam dispostos `[ 0x01, 0xD8, 0xCC, 0xDC ]`na memória como os bytes .</span><span class="sxs-lookup"><span data-stu-id="7af50-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="7af50-261">Em uma arquitetura de grande string endiana, o mesmo seria `[ 0xD8, 0x01, 0xDC, 0xCC ]`disposto na memória como os bytes.</span><span class="sxs-lookup"><span data-stu-id="7af50-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="7af50-262">Os sistemas de computador que se comunicam entre si devem concordar com a representação de dados cruzando o fio.</span><span class="sxs-lookup"><span data-stu-id="7af50-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="7af50-263">A maioria dos protocolos de rede usa o UTF-8 como padrão ao transmitir texto, em parte para evitar problemas que podem resultar de uma máquina de grande endiana se comunicando com uma máquina pouco endiana.</span><span class="sxs-lookup"><span data-stu-id="7af50-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="7af50-264">Os string pontos `[ F0 90 93 8C ]` de código UTF-8 serão sempre representados `[ 0xF0, 0x90, 0x93, 0x8C ]` como bytes, independentemente da endianidade.</span><span class="sxs-lookup"><span data-stu-id="7af50-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="7af50-265">Para usar o UTF-8 para transmitir texto, os aplicativos .NET geralmente usam código como o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="7af50-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="7af50-266">No exemplo anterior, o método [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodifica o `string` UTF-16 de volta em uma série de valores unicodecalar, em seguida, ele recodifica `byte` esses valores escalares em UTF-8 e coloca a seqüência resultante em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7af50-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="7af50-267">O método [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) realiza a transformação oposta, `byte` convertendo uma matriz `string`UTF-8 em um UTF-16 .</span><span class="sxs-lookup"><span data-stu-id="7af50-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="7af50-268">Como o UTF-8 é comum na internet, pode ser tentador ler bytes brutos do fio e tratar os dados como se fossem UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7af50-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="7af50-269">No entanto, você deve validar que ele é realmente bem formado.</span><span class="sxs-lookup"><span data-stu-id="7af50-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="7af50-270">Um cliente mal-intencionado pode enviar UTF-8 mal formado ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="7af50-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="7af50-271">Se você operar esses dados como se fossem bem formados, isso poderia causar erros ou falhas de segurança em sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="7af50-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="7af50-272">Para validar os dados utf-8, `Encoding.UTF8.GetString`você pode usar um método como , `string`que executará a validação ao converter os dados de entrada em um .</span><span class="sxs-lookup"><span data-stu-id="7af50-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="7af50-273">Codificação bem formada</span><span class="sxs-lookup"><span data-stu-id="7af50-273">Well-formed encoding</span></span>

<span data-ttu-id="7af50-274">Uma codificação Unicode bem string formada é uma das unidades de código que podem ser decodificadas de forma inequívoca e sem erro em uma seqüência de valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="7af50-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="7af50-275">Os dados bem formados podem ser transcodificados livremente entre UTF-8, UTF-16 e UTF-32.</span><span class="sxs-lookup"><span data-stu-id="7af50-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="7af50-276">A questão de saber se uma seqüência de codificação é bem formada ou não não está relacionada com a finalidade da arquitetura de uma máquina.</span><span class="sxs-lookup"><span data-stu-id="7af50-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="7af50-277">Uma sequência UTF-8 mal formada é mal formada da mesma forma em máquinas de grande endian e pouco endian.</span><span class="sxs-lookup"><span data-stu-id="7af50-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="7af50-278">Aqui estão alguns exemplos de codificações mal formadas:</span><span class="sxs-lookup"><span data-stu-id="7af50-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="7af50-279">No UTF-8, `[ 6C C2 61 ]` a seqüência `C2` é mal `61`formada porque não pode ser seguida por .</span><span class="sxs-lookup"><span data-stu-id="7af50-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="7af50-280">Na UTF-16, `[ DC00 DD00 ]` a seqüência (ou, em C#, string `"\udc00\udd00"`a `DC00` ) é mal `DD00`formada porque o substituto baixo não pode ser seguido por outro substituto baixo .</span><span class="sxs-lookup"><span data-stu-id="7af50-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="7af50-281">No UTF-32, `[ 0011ABCD ]` a seqüência `0011ABCD` é mal formada porque está fora do intervalo de valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="7af50-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="7af50-282">No .NET, `string` as instâncias quase sempre contêm dados UTF-16 bem formados, mas isso não é garantido.</span><span class="sxs-lookup"><span data-stu-id="7af50-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="7af50-283">Os exemplos a seguir mostram código C# válido que cria `string` dados UTF-16 mal formados em instâncias.</span><span class="sxs-lookup"><span data-stu-id="7af50-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="7af50-284">Um literal mal formado:</span><span class="sxs-lookup"><span data-stu-id="7af50-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="7af50-285">Uma substring que divide um par de substitutos:</span><span class="sxs-lookup"><span data-stu-id="7af50-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="7af50-286">APIs [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) como nunca retornam `string` instâncias mal formadas.</span><span class="sxs-lookup"><span data-stu-id="7af50-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="7af50-287">`Encoding.GetString`e `Encoding.GetBytes` os métodos detectam seqüências mal formadas na entrada e executam a substituição de caracteres ao gerar a saída.</span><span class="sxs-lookup"><span data-stu-id="7af50-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="7af50-288">Por exemplo, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) se vir um byte não-ASCII na entrada (fora do intervalo U+0000.U+007F), ele `string` insere um '?' na instância retornada.</span><span class="sxs-lookup"><span data-stu-id="7af50-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="7af50-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)substitui sequências UTF-8 mal `U+FFFD REPLACEMENT CHARACTER ('�')` formadas com `string` na instância retornada.</span><span class="sxs-lookup"><span data-stu-id="7af50-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="7af50-290">Para obter mais informações, consulte [o Padrão Unicode](https://www.unicode.org/versions/latest/), seções 5.22 e 3.9.</span><span class="sxs-lookup"><span data-stu-id="7af50-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="7af50-291">As classes `Encoding` incorporadas também podem ser configuradas para lançar uma exceção em vez de executar a substituição de caracteres quando seqüências mal formadas são vistas.</span><span class="sxs-lookup"><span data-stu-id="7af50-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="7af50-292">Essa abordagem é frequentemente usada em aplicativos sensíveis à segurança, onde a substituição de caracteres pode não ser aceitável.</span><span class="sxs-lookup"><span data-stu-id="7af50-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="7af50-293">Para obter informações sobre como `Encoding` usar as classes incorporadas, consulte [Como usar classes de codificação de caracteres em .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="7af50-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7af50-294">Confira também</span><span class="sxs-lookup"><span data-stu-id="7af50-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="7af50-295">Globalização e Localização</span><span class="sxs-lookup"><span data-stu-id="7af50-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)

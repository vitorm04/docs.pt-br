---
title: 'Introdução à char codificação acter no .net'
description: 'Saiba mais sobre char codificação e decodificação de acter no .net.'
ms.date: 03/09/2020
no-loc:
- 'Rune'
- 'char'
- 'string'
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 572fcd289eea720873d94e7fc71f3b4a030d1d70
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282310"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="5281a-103">Codificação de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="5281a-103">Character encoding in .NET</span></span>

<span data-ttu-id="5281a-104">Este artigo fornece uma introdução aos char sistemas de codificação acter que são usados pelo .net.</span><span class="sxs-lookup"><span data-stu-id="5281a-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="5281a-105">O artigo explica como os <xref:System.String> tipos,, <xref:System.Char> <xref:System.Text.Rune> e <xref:System.Globalization.StringInfo> funcionam com Unicode, UTF-16 e UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5281a-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="5281a-106">O termo *char acter* é usado aqui no sentido geral do *que um leitor percebe como um único elemento de exibição*.</span><span class="sxs-lookup"><span data-stu-id="5281a-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="5281a-107">Exemplos comuns são a letra "a", o símbolo "@" e o Emoji " 🐂 ".</span><span class="sxs-lookup"><span data-stu-id="5281a-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="5281a-108">Às vezes, o que parece um char acter é, na verdade, composto por vários elementos de exibição independentes, como explica a seção sobre [clusters grafemas](#grapheme-clusters) .</span><span class="sxs-lookup"><span data-stu-id="5281a-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-no-locstring-and-no-locchar-types"></a><span data-ttu-id="5281a-109">Os string char tipos e</span><span class="sxs-lookup"><span data-stu-id="5281a-109">The string and char types</span></span>

<span data-ttu-id="5281a-110">Uma instância da [string](xref:System.String) classe representa algum texto.</span><span class="sxs-lookup"><span data-stu-id="5281a-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="5281a-111">Um `string` é logicamente uma sequência de valores de 16 bits, cada um deles é uma instância da [char](xref:System.Char) estrutura.</span><span class="sxs-lookup"><span data-stu-id="5281a-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="5281a-112">O [ string . Propriedade Length](xref:System.String.Length) retorna o número de `char` instâncias na `string` instância.</span><span class="sxs-lookup"><span data-stu-id="5281a-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="5281a-113">A função de exemplo a seguir imprime os valores em notação hexadecimal de todas as `char` instâncias em um `string` :</span><span class="sxs-lookup"><span data-stu-id="5281a-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

<span data-ttu-id="5281a-114">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/PrintStringChars. cs" ID = "SnippetPrintChars":::</span><span class="sxs-lookup"><span data-stu-id="5281a-114">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::</span></span>

<span data-ttu-id="5281a-115">Passe string "Olá" para essa função e obtenha a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="5281a-115">Pass the string "Hello" to this function, and you get the following output:</span></span>

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

<span data-ttu-id="5281a-116">Cada char acter é representado por um único `char` valor.</span><span class="sxs-lookup"><span data-stu-id="5281a-116">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="5281a-117">Esse padrão é verdadeiro para a maioria dos idiomas do mundo.</span><span class="sxs-lookup"><span data-stu-id="5281a-117">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="5281a-118">Por exemplo, aqui está a saída de dois char Acters chineses que parece *nǐ hǎo* e Mean *Hello* :</span><span class="sxs-lookup"><span data-stu-id="5281a-118">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello* :</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="5281a-119">No entanto, para alguns idiomas e para alguns símbolos e Emoji, são necessárias duas `char` instâncias para representar um único char acter.</span><span class="sxs-lookup"><span data-stu-id="5281a-119">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="5281a-120">Por exemplo, compare o char acters e as `char` instâncias na palavra que significa *Osage* na linguagem Osage:</span><span class="sxs-lookup"><span data-stu-id="5281a-120">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

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

<span data-ttu-id="5281a-121">No exemplo anterior, cada char acter, exceto o espaço, é representado por duas `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-121">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="5281a-122">Um único Emoji Unicode também é representado por dois `char` s, como visto no exemplo a seguir, mostrando um Emoji Ox:</span><span class="sxs-lookup"><span data-stu-id="5281a-122">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```output
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="5281a-123">Esses exemplos mostram que o valor de `string.Length` , que indica o número de `char` instâncias, não indica necessariamente o número de char acters exibidas.</span><span class="sxs-lookup"><span data-stu-id="5281a-123">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="5281a-124">Uma única `char` instância por si só não representa necessariamente um char acter.</span><span class="sxs-lookup"><span data-stu-id="5281a-124">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="5281a-125">Os `char` pares que mapeiam para um único char acter são chamados de *pares substitutos*.</span><span class="sxs-lookup"><span data-stu-id="5281a-125">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="5281a-126">Para entender como eles funcionam, você precisa entender a codificação Unicode e UTF-16.</span><span class="sxs-lookup"><span data-stu-id="5281a-126">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="5281a-127">Pontos de código Unicode</span><span class="sxs-lookup"><span data-stu-id="5281a-127">Unicode code points</span></span>

<span data-ttu-id="5281a-128">O Unicode é um padrão de codificação internacional para uso em várias plataformas e em vários idiomas e scripts.</span><span class="sxs-lookup"><span data-stu-id="5281a-128">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="5281a-129">O padrão Unicode define mais de 1,1 milhões [pontos de código](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="5281a-129">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="5281a-130">Um ponto de código é um valor inteiro que pode variar de 0 a `U+10FFFF` (decimal 1.114.111).</span><span class="sxs-lookup"><span data-stu-id="5281a-130">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="5281a-131">Alguns pontos de código são atribuídos a letras, símbolos ou Emoji.</span><span class="sxs-lookup"><span data-stu-id="5281a-131">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="5281a-132">Outras são atribuídas a ações que controlam como Text ou char acters são exibidas, como avançar para uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="5281a-132">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="5281a-133">Muitos pontos de código ainda não foram atribuídos.</span><span class="sxs-lookup"><span data-stu-id="5281a-133">Many code points are not yet assigned.</span></span>

<span data-ttu-id="5281a-134">Aqui estão alguns exemplos de atribuições de ponto de código, com links para char TS Unicode em que aparecem:</span><span class="sxs-lookup"><span data-stu-id="5281a-134">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="5281a-135">Decimal</span><span class="sxs-lookup"><span data-stu-id="5281a-135">Decimal</span></span>|<span data-ttu-id="5281a-136">Hex</span><span class="sxs-lookup"><span data-stu-id="5281a-136">Hex</span></span>       |<span data-ttu-id="5281a-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5281a-137">Example</span></span>|<span data-ttu-id="5281a-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="5281a-138">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="5281a-139">10</span><span class="sxs-lookup"><span data-stu-id="5281a-139">10</span></span>     | `U+000A` |<span data-ttu-id="5281a-140">N/D</span><span class="sxs-lookup"><span data-stu-id="5281a-140">N/A</span></span>| <span data-ttu-id="5281a-141">[ALIMENTAÇÃO DE LINHA](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="5281a-141">[LINE FEED](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="5281a-142">97</span><span class="sxs-lookup"><span data-stu-id="5281a-142">97</span></span>     | `U+0061` | <span data-ttu-id="5281a-143">um</span><span class="sxs-lookup"><span data-stu-id="5281a-143">a</span></span> | <span data-ttu-id="5281a-144">[LETRA LATINA MINÚSCULA A](https://www.unicode.org/charts/PDF/U0000.pdf)</span><span class="sxs-lookup"><span data-stu-id="5281a-144">[LATIN SMALL LETTER A](https://www.unicode.org/charts/PDF/U0000.pdf)</span></span> |
|<span data-ttu-id="5281a-145">562</span><span class="sxs-lookup"><span data-stu-id="5281a-145">562</span></span>    | `U+0232` | <span data-ttu-id="5281a-146">Ȳ</span><span class="sxs-lookup"><span data-stu-id="5281a-146">Ȳ</span></span> | <span data-ttu-id="5281a-147">[LETRA LATINA MAIÚSCULA Y COM MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span><span class="sxs-lookup"><span data-stu-id="5281a-147">[LATIN CAPITAL LETTER Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf)</span></span> |
|<span data-ttu-id="5281a-148">68.675</span><span class="sxs-lookup"><span data-stu-id="5281a-148">68,675</span></span> | `U+10C43`| <span data-ttu-id="5281a-149">𐱃</span><span class="sxs-lookup"><span data-stu-id="5281a-149">𐱃</span></span> | <span data-ttu-id="5281a-150">[ANTIGA LETRA TURCO ORKHON EM](https://www.unicode.org/charts/PDF/U10C00.pdf)</span><span class="sxs-lookup"><span data-stu-id="5281a-150">[OLD TURKIC LETTER ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf)</span></span> |
|<span data-ttu-id="5281a-151">127.801</span><span class="sxs-lookup"><span data-stu-id="5281a-151">127,801</span></span>| `U+1F339`| <span data-ttu-id="5281a-152">🌹</span><span class="sxs-lookup"><span data-stu-id="5281a-152">🌹</span></span> | <span data-ttu-id="5281a-153">[Emoji rosa](https://www.unicode.org/charts/PDF/U1F300.pdf)</span><span class="sxs-lookup"><span data-stu-id="5281a-153">[ROSE emoji](https://www.unicode.org/charts/PDF/U1F300.pdf)</span></span> |

<span data-ttu-id="5281a-154">Os pontos de código são normalmente referenciados usando a sintaxe `U+xxxx` , em que `xxxx` é o valor inteiro codificado em hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="5281a-154">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="5281a-155">Dentro de todo o intervalo de pontos de código, há dois subintervalos:</span><span class="sxs-lookup"><span data-stu-id="5281a-155">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="5281a-156">O **BMP (plano multilíngüe básico)** no intervalo `U+0000..U+FFFF` .</span><span class="sxs-lookup"><span data-stu-id="5281a-156">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="5281a-157">Esse intervalo de 16 bits fornece 65.536 pontos de código, o suficiente para abranger a maioria dos sistemas de escrita do mundo.</span><span class="sxs-lookup"><span data-stu-id="5281a-157">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="5281a-158">**Pontos de código suplementares** no intervalo `U+10000..U+10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="5281a-158">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="5281a-159">Esse intervalo de 21 bits fornece mais de um milhão de pontos de código adicionais que podem ser usados para linguagens menos conhecidas e outras finalidades, como emojis.</span><span class="sxs-lookup"><span data-stu-id="5281a-159">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="5281a-160">O diagrama a seguir ilustra a relação entre o BMP e os pontos de código suplementares.</span><span class="sxs-lookup"><span data-stu-id="5281a-160">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/:::no-Loc (Char)::: acter-Encoding-Introduction/BMP-and-Supplementary. svg "alt-text =" BMP e pontos de código suplementares ":::

## <a name="utf-16-code-units"></a><span data-ttu-id="5281a-162">Unidades de código UTF-16</span><span class="sxs-lookup"><span data-stu-id="5281a-162">UTF-16 code units</span></span>

<span data-ttu-id="5281a-163">o formato de transformação Unicode de 16 bits ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) é um char sistema de codificação acter que usa *unidades de código* de 16 bits para representar pontos de código Unicode.</span><span class="sxs-lookup"><span data-stu-id="5281a-163">16-bit Unicode Transformation Format ( [UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="5281a-164">O .NET usa UTF-16 para codificar o texto em um `string` .</span><span class="sxs-lookup"><span data-stu-id="5281a-164">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="5281a-165">Uma `char` instância representa uma unidade de código de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="5281a-165">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="5281a-166">Uma única unidade de código de 16 bits pode representar qualquer ponto de código no intervalo de 16 bits do plano multilíngüe básico.</span><span class="sxs-lookup"><span data-stu-id="5281a-166">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="5281a-167">Mas, para um ponto de código no intervalo suplementar, `char` são necessárias duas instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-167">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="5281a-168">Pares substitutos</span><span class="sxs-lookup"><span data-stu-id="5281a-168">Surrogate pairs</span></span>

<span data-ttu-id="5281a-169">A conversão de valores de 2 16 bits em um único valor de 21 bits é facilitada por um intervalo especial denominado *pontos de código substitutos* , de `U+D800` até `U+DFFF` (decimal 55.296 a 57.343), inclusive.</span><span class="sxs-lookup"><span data-stu-id="5281a-169">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points* , from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="5281a-170">O diagrama a seguir ilustra a relação entre o BMP e os pontos de código substitutos.</span><span class="sxs-lookup"><span data-stu-id="5281a-170">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/:::no-Loc (Char)::: acter-Encoding-Introduction/BMP-and-Surrogate. svg "alt-text =" BMP e pontos de código substitutos ":::

<span data-ttu-id="5281a-172">Quando um ponto de código *substituto alto* ( `U+D800..U+DBFF` ) é imediatamente seguido por um ponto de código *substituto baixo* ( `U+DC00..U+DFFF` ), o par é interpretado como um ponto de código suplementar usando a seguinte fórmula:</span><span class="sxs-lookup"><span data-stu-id="5281a-172">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="5281a-173">Esta é a mesma fórmula usando a notação decimal:</span><span class="sxs-lookup"><span data-stu-id="5281a-173">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="5281a-174">Um ponto de código substituto *alto* não tem um valor de número mais alto que um ponto de código substituto *baixo* .</span><span class="sxs-lookup"><span data-stu-id="5281a-174">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="5281a-175">O ponto de código substituto alto é chamado de "alta" porque é usado para calcular os 11 bits de ordem superior do intervalo completo de pontos de código de 21 bits.</span><span class="sxs-lookup"><span data-stu-id="5281a-175">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="5281a-176">O ponto de código substituto baixo é usado para calcular os 10 bits de ordem inferior.</span><span class="sxs-lookup"><span data-stu-id="5281a-176">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="5281a-177">Por exemplo, o ponto de código real que corresponde ao par substituto `0xD83C` e `0xDF39`  é calculado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5281a-177">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="5281a-178">Aqui está o mesmo cálculo usando a notação decimal:</span><span class="sxs-lookup"><span data-stu-id="5281a-178">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="5281a-179">O exemplo anterior demonstra que `"\ud83c\udf39"` é a codificação UTF-16 do `U+1F339 ROSE ('🌹')` ponto de código mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="5281a-179">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="5281a-180">Valores escalares Unicode</span><span class="sxs-lookup"><span data-stu-id="5281a-180">Unicode scalar values</span></span>

<span data-ttu-id="5281a-181">O termo [valor escalar Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) refere-se a todos os pontos de código que não sejam os pontos de código substitutos.</span><span class="sxs-lookup"><span data-stu-id="5281a-181">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="5281a-182">Em outras palavras, um valor escalar é qualquer ponto de código atribuído a um char acter ou pode ser atribuído a um char acter no futuro.</span><span class="sxs-lookup"><span data-stu-id="5281a-182">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="5281a-183">"Caractere" aqui refere-se a qualquer coisa que possa ser atribuída a um ponto de código, que inclui itens como ações que controlam como o texto ou char acters são exibidos.</span><span class="sxs-lookup"><span data-stu-id="5281a-183">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="5281a-184">O diagrama a seguir ilustra os pontos de código de valor escalar.</span><span class="sxs-lookup"><span data-stu-id="5281a-184">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/:::no-Loc (Char)::: acter-Encoding-Introduction/Scalar-Values. svg "alt-text =" valores escalares ":::

### <a name="the-no-locrune-type-as-a-scalar-value"></a><span data-ttu-id="5281a-186">O Rune tipo como um valor escalar</span><span class="sxs-lookup"><span data-stu-id="5281a-186">The Rune type as a scalar value</span></span>

<span data-ttu-id="5281a-187">A partir do .NET Core 3,0, o <xref:System.Text.Rune?displayProperty=fullName> tipo representa um valor escalar Unicode.</span><span class="sxs-lookup"><span data-stu-id="5281a-187">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="5281a-188">**`Rune` Não está disponível no .NET Core 2. x ou .NET Framework 4. x.**</span><span class="sxs-lookup"><span data-stu-id="5281a-188">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="5281a-189">Os `Rune` construtores validam que a instância resultante é um valor escalar Unicode válido; caso contrário, elas geram uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5281a-189">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="5281a-190">O exemplo a seguir mostra o código que instancia instâncias com êxito `Rune` porque a entrada representa valores escalares válidos:</span><span class="sxs-lookup"><span data-stu-id="5281a-190">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

<span data-ttu-id="5281a-191">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/instancie Rune s.cs" ID = "SnippetValid":::</span><span class="sxs-lookup"><span data-stu-id="5281a-191">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::</span></span>

<span data-ttu-id="5281a-192">O exemplo a seguir gera uma exceção porque o ponto de código está no intervalo substituto e não faz parte de um par substituto:</span><span class="sxs-lookup"><span data-stu-id="5281a-192">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

<span data-ttu-id="5281a-193">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/instancie Rune s.cs" ID = "SnippetInvalidSurrogate":::</span><span class="sxs-lookup"><span data-stu-id="5281a-193">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::</span></span>

<span data-ttu-id="5281a-194">O exemplo a seguir gera uma exceção porque o ponto de código está além do intervalo suplementar:</span><span class="sxs-lookup"><span data-stu-id="5281a-194">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

<span data-ttu-id="5281a-195">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/instancie Rune s.cs" ID = "SnippetInvalidHigh":::</span><span class="sxs-lookup"><span data-stu-id="5281a-195">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::</span></span>

### <a name="no-locrune-usage-example-changing-letter-case"></a><span data-ttu-id="5281a-196">Rune exemplo de uso: alterando o caso da letra</span><span class="sxs-lookup"><span data-stu-id="5281a-196">Rune usage example: changing letter case</span></span>

<span data-ttu-id="5281a-197">Uma API que usa `char` e pressupõe que está trabalhando com um ponto de código que é um valor escalar não funciona corretamente se `char` for de um par substituto.</span><span class="sxs-lookup"><span data-stu-id="5281a-197">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="5281a-198">Por exemplo, considere o seguinte método que chama <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> em cada char um string :</span><span class="sxs-lookup"><span data-stu-id="5281a-198">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

<span data-ttu-id="5281a-199">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/ConvertToUpper. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="5281a-199">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="5281a-200">Se o `input` string contiver a letra minúscula Deseret `er` ( `𐑉` ), esse código não o converterá em letras maiúsculas ( `𐐡` ).</span><span class="sxs-lookup"><span data-stu-id="5281a-200">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="5281a-201">O código chama `char.ToUpperInvariant` separadamente em cada ponto de código substituto `U+D801` e `U+DC49` .</span><span class="sxs-lookup"><span data-stu-id="5281a-201">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="5281a-202">Mas `U+D801` não tem informações suficientes para identificá-lo como uma letra minúscula, portanto, `char.ToUpperInvariant` deixa-o sozinho.</span><span class="sxs-lookup"><span data-stu-id="5281a-202">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="5281a-203">E ele lida `U+DC49` da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="5281a-203">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="5281a-204">O resultado é que ' 𐑉 ' minúsculas em `input` string não é convertido em letras maiúsculas ' 𐑉 '.</span><span class="sxs-lookup"><span data-stu-id="5281a-204">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="5281a-205">Aqui estão duas opções para converter corretamente um string em maiúsculas:</span><span class="sxs-lookup"><span data-stu-id="5281a-205">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="5281a-206">Chame <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na entrada em string vez de iterar `char` por- `char` .</span><span class="sxs-lookup"><span data-stu-id="5281a-206">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="5281a-207">O `string.ToUpperInvariant` método tem acesso a ambas as partes de cada par alternativo, portanto, ele pode manipular todos os pontos de código Unicode corretamente.</span><span class="sxs-lookup"><span data-stu-id="5281a-207">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="5281a-208">Itere pelos valores escalares Unicode como `Rune` instâncias em vez de `char` instâncias, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5281a-208">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="5281a-209">Como uma `Rune` instância é um valor escalar Unicode válido, ela pode ser passada para APIs que esperam operar em um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="5281a-209">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="5281a-210">Por exemplo, chamar, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> conforme mostrado no exemplo a seguir, fornece os resultados corretos:</span><span class="sxs-lookup"><span data-stu-id="5281a-210">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  <span data-ttu-id="5281a-211">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/ConvertToUpper. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="5281a-211">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::</span></span>

### <a name="other-no-locrune-apis"></a><span data-ttu-id="5281a-212">Outras Rune APIs</span><span class="sxs-lookup"><span data-stu-id="5281a-212">Other Rune APIs</span></span>

<span data-ttu-id="5281a-213">O `Rune` tipo expõe as analogias de muitas das `char` APIs.</span><span class="sxs-lookup"><span data-stu-id="5281a-213">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="5281a-214">Por exemplo, os métodos a seguir espelham APIs estáticas no `char` tipo:</span><span class="sxs-lookup"><span data-stu-id="5281a-214">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="5281a-215">Para obter o valor escalar bruto de uma `Rune` instância, use a <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5281a-215">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="5281a-216">Para converter uma `Rune` instância de volta em uma sequência de `char` s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> ou o <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="5281a-216">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5281a-217">Como qualquer valor escalar Unicode é representável por um único `char` ou por um par alternativo, qualquer `Rune` instância pode ser representada por no máximo 2 `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-217">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="5281a-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> para ver quantas `char` instâncias são necessárias para representar uma `Rune` instância.</span><span class="sxs-lookup"><span data-stu-id="5281a-218">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="5281a-219">Para obter mais informações sobre o `Rune` tipo .net, consulte a [ `Rune` referência da API](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="5281a-219">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="5281a-220">Clusters grafemas</span><span class="sxs-lookup"><span data-stu-id="5281a-220">Grapheme clusters</span></span>

<span data-ttu-id="5281a-221">O que parece um char acter pode resultar de uma combinação de vários pontos de código, portanto, um termo mais descritivo que é geralmente usado no lugar de " char acter" é o [cluster grafemas](https://www.unicode.org/glossary/#grapheme_cluster).</span><span class="sxs-lookup"><span data-stu-id="5281a-221">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="5281a-222">O termo equivalente no .NET é o [elemento de texto](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="5281a-222">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="5281a-223">Considere as `string` instâncias "a", "á", "á" e " `👩🏽‍🚒` ".</span><span class="sxs-lookup"><span data-stu-id="5281a-223">Consider the `string` instances "a", "á", "á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="5281a-224">Se seu sistema operacional os tratar como especificado pelo padrão Unicode, cada `string` uma dessas instâncias aparecerá como um único elemento de texto ou cluster grafemas.</span><span class="sxs-lookup"><span data-stu-id="5281a-224">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="5281a-225">Mas os dois últimos são representados por mais de um ponto de código de valor escalar.</span><span class="sxs-lookup"><span data-stu-id="5281a-225">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="5281a-226">O string "a" é representado por um valor escalar e contém uma `char` instância.</span><span class="sxs-lookup"><span data-stu-id="5281a-226">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="5281a-227">O string "á" é representado por um valor escalar e contém uma `char` instância.</span><span class="sxs-lookup"><span data-stu-id="5281a-227">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="5281a-228">O string "á" tem a mesma aparência de "á", mas é representado por dois valores escalares e contém duas `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-228">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="5281a-229">Por fim, o string " `👩🏽‍🚒` " é representado por quatro valores escalares e contém sete `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-229">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="5281a-230">`U+1F469 WOMAN` (intervalo suplementar, requer um par alternativo)</span><span class="sxs-lookup"><span data-stu-id="5281a-230">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="5281a-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (intervalo suplementar, requer um par alternativo)</span><span class="sxs-lookup"><span data-stu-id="5281a-231">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="5281a-232">`U+1F692 FIRE ENGINE` (intervalo suplementar, requer um par alternativo)</span><span class="sxs-lookup"><span data-stu-id="5281a-232">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="5281a-233">Em alguns dos exemplos anteriores, como o modificador de acentuação de acento ou o modificador de Tom de pele, o ponto de código não é exibido como um elemento autônomo na tela.</span><span class="sxs-lookup"><span data-stu-id="5281a-233">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="5281a-234">Em vez disso, ele serve para modificar a aparência de um elemento de texto que veio antes dele.</span><span class="sxs-lookup"><span data-stu-id="5281a-234">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="5281a-235">Esses exemplos mostram que pode ser necessário usar vários valores escalares para criar o que achamos como um único " char acter", ou "cluster grafemas".</span><span class="sxs-lookup"><span data-stu-id="5281a-235">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="5281a-236">Para enumerar os clusters grafemas de um `string` , use a <xref:System.Globalization.StringInfo> classe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5281a-236">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="5281a-237">Se você estiver familiarizado com o Swift, o `StringInfo` tipo .net será conceitualmente semelhante ao [ `character` tipo de Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="5281a-237">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a><span data-ttu-id="5281a-238">Exemplo: contagem char , Rune e instâncias de elemento de texto</span><span class="sxs-lookup"><span data-stu-id="5281a-238">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="5281a-239">Em APIs do .NET, um cluster grafemas é chamado de *elemento de texto*.</span><span class="sxs-lookup"><span data-stu-id="5281a-239">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="5281a-240">O método a seguir demonstra as diferenças entre o `char` , o `Rune` e as instâncias de elemento de texto em um `string` :</span><span class="sxs-lookup"><span data-stu-id="5281a-240">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

<span data-ttu-id="5281a-241">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/CountTextElements. cs" ID = "SnippetCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="5281a-241">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::</span></span>

<span data-ttu-id="5281a-242">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/CountTextElements. cs" ID = "SnippetCallCountMethod":::</span><span class="sxs-lookup"><span data-stu-id="5281a-242">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::</span></span>

<span data-ttu-id="5281a-243">Se você executar esse código no .NET Framework ou no .NET Core 3,1 ou anterior, a contagem de elementos de texto para o emoji será mostrada `4` .</span><span class="sxs-lookup"><span data-stu-id="5281a-243">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="5281a-244">Isso ocorre devido a um bug na `StringInfo` classe que é corrigido no .NET 5.</span><span class="sxs-lookup"><span data-stu-id="5281a-244">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-no-locstring-instances"></a><span data-ttu-id="5281a-245">Exemplo: dividindo string instâncias</span><span class="sxs-lookup"><span data-stu-id="5281a-245">Example: splitting string instances</span></span>

<span data-ttu-id="5281a-246">Ao dividir `string` instâncias, evite dividir pares substitutos e clusters grafemas.</span><span class="sxs-lookup"><span data-stu-id="5281a-246">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="5281a-247">Considere o seguinte exemplo de código incorreto, que pretende inserir quebras de linha a cada 10 char acters em um string :</span><span class="sxs-lookup"><span data-stu-id="5281a-247">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

<span data-ttu-id="5281a-248">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/InsertNewlines. cs" ID = "SnippetBadExample":::</span><span class="sxs-lookup"><span data-stu-id="5281a-248">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::</span></span>

<span data-ttu-id="5281a-249">Como esse código enumera `char` instâncias, um par substituto que ocorre em cima de 10 `char` limites será dividido e uma nova linha injetada entre eles.</span><span class="sxs-lookup"><span data-stu-id="5281a-249">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="5281a-250">Essa inserção apresenta dados corrompidos, pois os pontos de código substitutos são significativos apenas como pares.</span><span class="sxs-lookup"><span data-stu-id="5281a-250">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="5281a-251">O potencial de corrupção de dados não será eliminado se você enumerar `Rune` instâncias (valores escalares) em vez de `char` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-251">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="5281a-252">Um conjunto de `Rune` instâncias pode criar um cluster grafemas que se espalha por 10 `char` limites.</span><span class="sxs-lookup"><span data-stu-id="5281a-252">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="5281a-253">Se o conjunto de clusters grafemas for dividido, ele não poderá ser interpretado corretamente.</span><span class="sxs-lookup"><span data-stu-id="5281a-253">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="5281a-254">Uma abordagem melhor é quebrar o string ao contar os clusters grafemas, ou elementos de texto, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5281a-254">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

<span data-ttu-id="5281a-255">::: código Language = "CSharp" origem = "Snippets/ char acter-Encoding-Introduction/Csharp/InsertNewlines. cs" ID = "SnippetGoodExample":::</span><span class="sxs-lookup"><span data-stu-id="5281a-255">:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::</span></span>

<span data-ttu-id="5281a-256">Como observado anteriormente, no entanto, em implementações do .NET que não seja o .NET 5, a `StringInfo` classe pode lidar com alguns clusters do grafemas incorretamente.</span><span class="sxs-lookup"><span data-stu-id="5281a-256">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="5281a-257">UTF-8 e UTF-32</span><span class="sxs-lookup"><span data-stu-id="5281a-257">UTF-8 and UTF-32</span></span>

<span data-ttu-id="5281a-258">As seções anteriores se concentram em UTF-16 porque é isso que o .NET usa para codificar `string` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-258">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="5281a-259">Há outros sistemas de codificação para Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) e [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="5281a-259">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="5281a-260">Essas codificações usam unidades de código de 8 bits e unidades de código de 32 bits, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5281a-260">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="5281a-261">Como o UTF-16, o UTF-8 requer várias unidades de código para representar alguns valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="5281a-261">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="5281a-262">O UTF-32 pode representar qualquer valor escalar em uma única unidade de código de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="5281a-262">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="5281a-263">Aqui estão alguns exemplos que mostram como o mesmo ponto de código Unicode é representado em cada um desses três sistemas de codificação Unicode:</span><span class="sxs-lookup"><span data-stu-id="5281a-263">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

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

<span data-ttu-id="5281a-264">Conforme observado anteriormente, uma única unidade de código UTF-16 de um [par substituto](#surrogate-pairs) não faz sentido por si só.</span><span class="sxs-lookup"><span data-stu-id="5281a-264">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="5281a-265">Da mesma forma, uma única unidade de código UTF-8 não faz sentido por si só, se estiver em uma sequência de dois, três ou quatro usadas para calcular um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="5281a-265">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="5281a-266">Endianness</span><span class="sxs-lookup"><span data-stu-id="5281a-266">Endianness</span></span>

<span data-ttu-id="5281a-267">No .NET, as unidades de código UTF-16 de um string são armazenadas em memória contígua como uma sequência de inteiros de 16 bits ( `char` instâncias).</span><span class="sxs-lookup"><span data-stu-id="5281a-267">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="5281a-268">Os bits de unidades de código individuais são dispostos de acordo com a [endian](https://en.wikipedia.org/wiki/Endianness) da arquitetura atual.</span><span class="sxs-lookup"><span data-stu-id="5281a-268">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="5281a-269">Em uma arquitetura little-endian, a string consistir dos pontos de código UTF-16 `[ D801 DCCC ]` seria disposta na memória como os bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]` .</span><span class="sxs-lookup"><span data-stu-id="5281a-269">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="5281a-270">Em uma arquitetura big endian string , a mesma seria disposta na memória como os bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]` .</span><span class="sxs-lookup"><span data-stu-id="5281a-270">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="5281a-271">Sistemas de computador que se comunicam entre si devem concordar com a representação de dados que cruzam a conexão.</span><span class="sxs-lookup"><span data-stu-id="5281a-271">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="5281a-272">A maioria dos protocolos de rede usa UTF-8 como padrão ao transmitir texto, parcialmente para evitar problemas que podem resultar de um computador big endian se comunicando com um computador little-endian.</span><span class="sxs-lookup"><span data-stu-id="5281a-272">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="5281a-273">Os string pontos de código UTF-8 `[ F0 90 93 8C ]` sempre serão representados como bytes, `[ 0xF0, 0x90, 0x93, 0x8C ]` independentemente da endian.</span><span class="sxs-lookup"><span data-stu-id="5281a-273">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="5281a-274">Para usar UTF-8 para transmissão de texto, os aplicativos .NET geralmente usam um código como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5281a-274">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="5281a-275">No exemplo anterior, o método [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) DECODIFICA o UTF-16 de `string` volta em uma série de valores escalares Unicode e, em seguida, ele codifica novamente esses valores escalares em UTF-8 e coloca a sequência resultante em uma `byte` matriz.</span><span class="sxs-lookup"><span data-stu-id="5281a-275">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="5281a-276">O método [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) executa a transformação oposta, convertendo uma matriz UTF-8 `byte` em um UTF-16 `string` .</span><span class="sxs-lookup"><span data-stu-id="5281a-276">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="5281a-277">Como o UTF-8 é comum na Internet, pode ser tentador ler bytes brutos da transmissão e tratá-los como se fossem UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5281a-277">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="5281a-278">No entanto, você deve validar que ele está realmente bem formado.</span><span class="sxs-lookup"><span data-stu-id="5281a-278">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="5281a-279">Um cliente mal-intencionado pode enviar UTF-8 mal formado para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="5281a-279">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="5281a-280">Se você operar nesses dados como se eles estivessem bem formados, isso poderá causar erros ou brechas de segurança em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5281a-280">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="5281a-281">Para validar dados UTF-8, você pode usar um método como `Encoding.UTF8.GetString` , que executará a validação durante a conversão dos dados de entrada em um `string` .</span><span class="sxs-lookup"><span data-stu-id="5281a-281">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="5281a-282">Codificação bem formada</span><span class="sxs-lookup"><span data-stu-id="5281a-282">Well-formed encoding</span></span>

<span data-ttu-id="5281a-283">Uma codificação Unicode bem formada é uma string das unidades de código que podem ser decodificadas inequivocadamente e sem erro em uma sequência de valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="5281a-283">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="5281a-284">Os dados bem formados podem ser transcodificados livremente entre UTF-8, UTF-16 e UTF-32.</span><span class="sxs-lookup"><span data-stu-id="5281a-284">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="5281a-285">A questão de uma sequência de codificação estar bem formada ou não não está relacionada à endian da arquitetura de uma máquina.</span><span class="sxs-lookup"><span data-stu-id="5281a-285">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="5281a-286">Uma sequência UTF-8 mal formada é mal formada da mesma forma em computadores big endian e little-endian.</span><span class="sxs-lookup"><span data-stu-id="5281a-286">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="5281a-287">Aqui estão alguns exemplos de codificações mal formadas:</span><span class="sxs-lookup"><span data-stu-id="5281a-287">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="5281a-288">Em UTF-8, a sequência `[ 6C C2 61 ]` está mal formada porque `C2` não pode ser seguida por `61` .</span><span class="sxs-lookup"><span data-stu-id="5281a-288">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="5281a-289">Em UTF-16, a sequência `[ DC00 DD00 ]` (ou, em C#, a string `"\udc00\udd00"` ) está mal formada porque o substituto baixo `DC00` não pode ser seguido por outro substituto baixo `DD00` .</span><span class="sxs-lookup"><span data-stu-id="5281a-289">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="5281a-290">Em UTF-32, a sequência `[ 0011ABCD ]` está mal formada porque `0011ABCD` está fora do intervalo de valores escalares Unicode.</span><span class="sxs-lookup"><span data-stu-id="5281a-290">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="5281a-291">No .NET, as `string` instâncias quase sempre contêm dados UTF-16 bem formados, mas isso não é garantido.</span><span class="sxs-lookup"><span data-stu-id="5281a-291">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="5281a-292">Os exemplos a seguir mostram um código C# válido que cria dados UTF-16 mal formados em `string` instâncias.</span><span class="sxs-lookup"><span data-stu-id="5281a-292">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="5281a-293">Um literal mal formado:</span><span class="sxs-lookup"><span data-stu-id="5281a-293">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="5281a-294">Um sub string que divide um par substituto:</span><span class="sxs-lookup"><span data-stu-id="5281a-294">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="5281a-295">APIs como [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) nunca retornam instâncias mal formadas `string` .</span><span class="sxs-lookup"><span data-stu-id="5281a-295">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="5281a-296">`Encoding.GetString` e os `Encoding.GetBytes` métodos detectam sequências mal formadas na entrada e executam char a substituição de acter ao gerar a saída.</span><span class="sxs-lookup"><span data-stu-id="5281a-296">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="5281a-297">Por exemplo, se [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) o vê um byte não-ASCII na entrada (fora do intervalo U + 0000.. U + 007F), ele insere um '? ' na instância retornada `string` .</span><span class="sxs-lookup"><span data-stu-id="5281a-297">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="5281a-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) Substitui sequências UTF-8 mal formadas por `U+FFFD REPLACEMENT CHARACTER ('�')` na `string` instância retornada.</span><span class="sxs-lookup"><span data-stu-id="5281a-298">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="5281a-299">Para obter mais informações, consulte [o padrão Unicode, as](https://www.unicode.org/versions/latest/)seções 5,22 e 3,9.</span><span class="sxs-lookup"><span data-stu-id="5281a-299">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="5281a-300">As `Encoding` classes internas também podem ser configuradas para lançar uma exceção em vez de executar a char substituição de acter quando seqüências mal formadas são vistas.</span><span class="sxs-lookup"><span data-stu-id="5281a-300">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="5281a-301">Essa abordagem é geralmente usada em aplicativos sensíveis à segurança em que a char substituição acter pode não ser aceitável.</span><span class="sxs-lookup"><span data-stu-id="5281a-301">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="5281a-302">Para obter informações sobre como usar as `Encoding` classes internas, consulte [como usar char classes de codificação acter no .net](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="5281a-302">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5281a-303">Veja também</span><span class="sxs-lookup"><span data-stu-id="5281a-303">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="5281a-304">Globalização e localização</span><span class="sxs-lookup"><span data-stu-id="5281a-304">Globalization and Localization</span></span>](../globalization-localization/index.md)

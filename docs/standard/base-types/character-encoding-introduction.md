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
# <a name="character-encoding-in-net"></a>Codificação de caracteres no .NET

Este artigo fornece uma introdução aos sistemas de codificação de caracteres que são usados pelo .NET. O artigo explica <xref:System.String> <xref:System.Char>como <xref:System.Text.Rune>os <xref:System.Globalization.StringInfo> tipos funcionam com Unicode, UTF-16 e UTF-8.

O termo *caractere* é usado aqui no sentido geral do *que um leitor percebe como um único elemento de exibição*. Exemplos comuns são a letra "a", o símbolo🐂"@" e o emoji " ". Às vezes, o que parece um caractere é na verdade composto de múltiplos elementos de exibição independentes, como explica a seção em [clusters de grafeme.](#grapheme-clusters)

## <a name="the-string-and-char-types"></a>Os tipos de string e char

Um exemplo da classe [string](xref:System.String) representa algum texto. A `string` é logicamente uma seqüência de valores de 16 bits, cada um dos quais é uma instância da estrutura de [char.](xref:System.Char) A [corda. A](xref:System.String.Length) propriedade de `char` comprimento retorna `string` o número de instâncias na instância.

A função de amostra a seguir imprime os valores `char` na notação hexadecimal de todas as instâncias em a: `string`

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Passe a seqüência "Olá" para esta função e obtenha a seguinte saída:

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

Cada personagem é representado `char` por um único valor. Esse padrão vale para a maioria das línguas do mundo. Por exemplo, aqui está a saída para dois caracteres chineses que soam *como nə həo* e significa *Olá*:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

No entanto, para algumas línguas e para `char` alguns símbolos e emojis, é preciso duas instâncias para representar um único personagem. Por exemplo, compare `char` os caracteres e instâncias na palavra que significa *Osage* na língua Osage:

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

No exemplo anterior, cada caractere, exceto `char` o espaço, é representado por duas instâncias.

Um único emoji Unicode também `char`é representado por dois s, como visto no exemplo a seguir mostrando um emoji de boi:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Esses exemplos mostram que `string.Length`o valor de `char` , que indica o número de instâncias, não necessariamente indica o número de caracteres exibidos. Uma `char` única instância por si só não representa necessariamente um personagem.

Os `char` pares que mapeiam para um único caractere são chamados *pares de substitutos*. Para entender como eles funcionam, você precisa entender a codificação Unicode e UTF-16.

## <a name="unicode-code-points"></a>Pontos de código Unicode

Unicode é um padrão internacional de codificação para uso em várias plataformas e com vários idiomas e scripts.

O Padrão Unicode define mais de 1,1 milhão de [pontos de código](https://www.unicode.org/glossary/#code_point). Um ponto de código é um valor inteiro `U+10FFFF` que pode variar de 0 a (decimal 1.114.111). Alguns pontos de código são atribuídos a letras, símbolos ou emojis. Outros são atribuídos a ações que controlam como texto ou caracteres são exibidos, como avançar para uma nova linha. Muitos pontos de código ainda não foram atribuídos.

Aqui estão alguns exemplos de atribuições de pontos de código, com links para gráficos Unicode em que eles aparecem:

|Decimal|Hex       |Exemplo|Descrição|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/D| [ALIMENTAÇÃO DE LINHA](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [LATIN PEQUENA LETRA A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Em 1998 | [CARTA CAPITAL LATINA E COM MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [VELHA CARTA TURCA ORKHON EM](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [Emoji ROSE](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Os pontos de código são normalmente referidos usando a sintaxe, `U+xxxx`onde `xxxx` está o valor inteiro codificado por hexa.

Dentro da gama completa de pontos de código há dois subintervalos:

* O **plano multilíngüe básico (BMP)** na faixa `U+0000..U+FFFF`. Esta faixa de 16 bits fornece 65.536 pontos de código, o suficiente para cobrir a maioria dos sistemas de escrita do mundo.
* **Pontos de código** suplementar `U+10000..U+10FFFF`na faixa . Este intervalo de 21 bits fornece mais de um milhão de pontos de código adicionais que podem ser usados para idiomas menos conhecidos e outros propósitos, como emojis.

O diagrama a seguir ilustra a relação entre o BMP e os pontos de código complementar.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP e pontos de código suplementar":::

## <a name="utf-16-code-units"></a>Unidades de código UTF-16

O Formato de Transformação unicode de 16 bits[(UTF-16)](https://www.unicode.org/faq/utf_bom.html#UTF16)é um sistema de codificação de caracteres que usa unidades de código de 16 *bits* para representar pontos de código Unicode. .NET usa UTF-16 para codificar `string`o texto em um . Uma `char` instância representa uma unidade de código de 16 bits.

Uma única unidade de código de 16 bits pode representar qualquer ponto de código na faixa de 16 bits do Plano Multilíngue Básico. Mas para um ponto de código `char` na faixa suplementar, duas instâncias são necessárias.

## <a name="surrogate-pairs"></a>Pares substitutos

A tradução de dois valores de 16 bits para um único valor de 21 `U+D800` `U+DFFF` bits é facilitada por uma faixa especial chamada pontos de *código substituto,* de para (decimal 55.296 a 57.343), inclusive.

O diagrama a seguir ilustra a relação entre o BMP e os pontos de código substitutos.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="Pontos de código BMP e substituto":::

Quando um ponto de`U+D800..U+DBFF`código de substituto *alto* ( )`U+DC00..U+DFFF`é imediatamente seguido por um ponto de código de substituto *baixo* (), o par é interpretado como um ponto de código suplementar usando a seguinte fórmula:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Aqui está a mesma fórmula usando notação decimal:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

Um ponto de código de substituto *alto* não tem um valor numérico maior do que um ponto de código de substituto *baixo.* O ponto de código de substituto alto é chamado de "alto" porque é usado para calcular os 11 bits de ordem mais alta da faixa completa de ponto de código de 21 bits. O ponto de código de substituto baixo é usado para calcular os 10 bits de ordem inferior.

Por exemplo, o ponto de código real `0xD83C` `0xDF39` que corresponde ao par substituto e é calculado da seguinte forma:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Aqui está o mesmo cálculo usando notação decimal:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

O exemplo anterior `"\ud83c\udf39"` demonstra que é a codificação `U+1F339 ROSE ('🌹')` UTF-16 do ponto de código mencionado anteriormente.

## <a name="unicode-scalar-values"></a>Valores escalares unicode

O termo [valor escalar Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) refere-se a todos os pontos de código que não os pontos de código substituto. Em outras palavras, um valor escalar é qualquer ponto de código que é atribuído a um caractere ou pode ser atribuído um caractere no futuro. "Caractere" aqui refere-se a qualquer coisa que possa ser atribuída a um ponto de código, que inclui coisas como ações que controlam como texto ou caracteres são exibidos.

O diagrama a seguir ilustra os pontos de código de valor escalar.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Valores escalares":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>O Rune tipo como um valor escalar

Começando com .NET Core 3.0, o <xref:System.Text.Rune?displayProperty=fullName> tipo representa um valor escalar Unicode. **`Rune`não está disponível em .NET Core 2.x ou .NET Framework 4.x.**

Os `Rune` construtores validam que a instância resultante é um valor escalar Unicode válido, caso contrário, eles lançam uma exceção. O exemplo a seguir mostra `Rune` o código que instancia as instâncias com sucesso porque a entrada representa valores escalares válidos:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

O exemplo a seguir lança uma exceção porque o ponto de código está na faixa de substituto e não faz parte de um par de substitutos:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

O exemplo a seguir abre uma exceção porque o ponto de código está além da faixa suplementar:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Runeexemplo de uso: alteração do caso da letra

Uma API que `char` pega a e assume que está trabalhando com um ponto de `char` código que é um valor escalar não funciona corretamente se for de um par de substitutos. Por exemplo, considere o <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> seguinte char método stringque chama cada um em um :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

Se `input` string contiver a letra `er` minúscula de`𐑉`Deseret (), este código`𐐡`não a converterá em maiúsculas (). O código `char.ToUpperInvariant` chama separadamente em `U+D801` cada `U+DC49`ponto de código substituto, e . Mas `U+D801` não tem informação suficiente por si só para identificá-la como uma letra minúscula, então `char.ToUpperInvariant` deixe-a em paz. E ele `U+DC49` lida da mesma maneira. O resultado é que o ''''' minúsculo no `input` string não é convertido em maiúsculas ''.'.

Aqui estão duas opções para string converter corretamente a em maiúsculas:

* Ligue <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> para string a entrada em `char`vez`char`de iterar -por- . O `string.ToUpperInvariant` método tem acesso a ambas as partes de cada par de substitutos, para que ele possa lidar com todos os pontos de código Unicode corretamente.
* Iterar através dos valores `Rune` escalares `char` Unicode como instâncias em vez de instâncias, como mostrado no exemplo a seguir. Uma `Rune` vez que uma instância é um valor escalar Unicode válido, ele pode ser passado para APIs que esperam operar em um valor escalar. Por exemplo, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> chamar como mostrado no exemplo a seguir dá resultados corretos:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Outras Rune APIs

O `Rune` tipo expõe análogos `char` de muitas das APIs. Por exemplo, os seguintes métodos `char` espelham APIs estáticas no tipo:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Para obter o valor escalonado bruto de uma `Rune` instância, use a <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> propriedade.

Para converter `Rune` uma instância de `char`volta <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> a <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> uma seqüência de s, use ou o método.

Uma vez que qualquer valor escalar Unicode é representado por um único `char` ou por um par substituto, qualquer `Rune` instância pode ser representada por no máximo 2 `char` instâncias. Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> para ver `char` quantas instâncias `Rune` são necessárias para representar uma instância.

Para obter mais informações `Rune` sobre o tipo .NET, consulte a [ `Rune` referência a API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Clusters de grafeme

O que parece um caractere pode resultar de uma combinação de múltiplos pontos de código, de modo que um termo mais descritivo que é frequentemente usado no lugar de "caractere" é [o cluster de grafeme](https://www.unicode.org/glossary/#grapheme_cluster). O termo equivalente em .NET é [elemento de texto](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Considere `string` as instâncias "a", "á". "á", e`👩🏽‍🚒`"" ". Se o sistema operacional manuseá-los conforme especificado `string` pelo padrão Unicode, cada uma dessas instâncias será exibida como um único elemento de texto ou cluster de grafeme. Mas os dois últimos são representados por mais de um ponto de código de valor escalar.

* O string "a" é representado por um `char` valor escalar e contém uma instância.

  * `U+0061 LATIN SMALL LETTER A`

* O string "á" é representado por um `char` valor escalar e contém uma instância.

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* O string "á" parece o mesmo que "á", mas é `char` representado por dois valores escalares e contém duas instâncias.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Finalmente, string o`👩🏽‍🚒`" " é representado por `char` quatro valores escalares e contém sete instâncias.

  * `U+1F469 WOMAN`(faixa suplementar, requer um par de substitutos)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(faixa suplementar, requer um par de substitutos)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(faixa suplementar, requer um par de substitutos)

Em alguns dos exemplos anteriores - como o modificador de acento combinado ou o modificador de tom de pele - o ponto de código não é exibido como um elemento autônomo na tela. Em vez disso, serve para modificar a aparência de um elemento de texto que veio antes dele. Esses exemplos mostram que pode ser necessário múltiplos valores escalares para compor o que pensamos como um único "caractere", ou "cluster de grafeme".

Para enumerar os clusters de `string`grafeme de a, use a <xref:System.Globalization.StringInfo> classe como mostrado no exemplo a seguir. Se você está familiarizado com swift, o tipo .NET `StringInfo` é conceitualmente semelhante ao tipo de [ `character` Swift](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Exemplo: charcontagem Runee instâncias de elemento de texto

Em .NET APIs, um cluster de grafeme é chamado de *elemento de texto*. O método a seguir `char` `Rune`demonstra as diferenças entre `string`, e instâncias de elemento de texto em a :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Se você executar esse código no .NET Framework ou no .NET Core 3.1 ou anterior, a contagem de elementos de texto para os emojis será mostrada `4`. Isso é devido a `StringInfo` um bug na classe que é corrigido em .NET 5.

### <a name="example-splitting-opno-locstring-instances"></a>Exemplo: string instâncias de divisão

Ao `string` dividir instâncias, evite dividir pares de substitutos e clusters de grafeme. Considere o seguinte exemplo de código incorreto, que pretende stringinserir quebras de linha a cada 10 caracteres em um :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Como este código enumera instâncias, `char` um par de substitutos`char` que acontece de straddle um limite de 10-limite será dividido e uma nova linha injetada entre eles. Essa inserção introduz corrupção de dados, porque os pontos de código substitutos são significativos apenas como pares.

O potencial de corrupção de dados não é `Rune` eliminado se você enumerar instâncias (valores escalares) em vez de `char` instâncias. Um conjunto `Rune` de instâncias pode compor um cluster de`char` grafeme que atravessa um limite de 10. Se o conjunto de cluster de grafeme for dividido, não poderá ser interpretado corretamente.

Uma abordagem melhor string é quebrar o clusters de grafeme ou elementos de texto, como no exemplo a seguir:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Como observado anteriormente, no entanto, em implementações `StringInfo` de .NET diferente do .NET 5, a classe pode lidar com alguns clusters de grafeme incorretamente.

## <a name="utf-8-and-utf-32"></a>UTF-8 e UTF-32

As seções anteriores se concentraram no UTF-16 porque `string` é isso que o .NET usa para codificar instâncias. Existem outros sistemas de codificação para Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) e [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Essas codificações usam unidades de código de 8 bits e unidades de código de 32 bits, respectivamente.

Como o UTF-16, o UTF-8 requer várias unidades de código para representar alguns valores escalares Unicode. O UTF-32 pode representar qualquer valor escalar em uma única unidade de código de 32 bits.

Aqui estão alguns exemplos mostrando como o mesmo ponto de código Unicode é representado em cada um desses três sistemas de codificação Unicode:

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

Como observado anteriormente, uma única unidade de código UTF-16 de um par de [substitutos](#surrogate-pairs) não tem sentido por si só. Da mesma forma, uma única unidade de código UTF-8 não tem sentido por si só se estiver em uma seqüência de dois, três ou quatro usados para calcular um valor escalar.

### <a name="endianness"></a>Endianness

Em .NET, as unidades de código string UTF-16 de a são armazenadas em memória contígua como uma seqüência de inteiros de 16 bits (instâncias).`char` Os pedaços de unidades de código individuais são dispostos de acordo com a [finalidade](https://en.wikipedia.org/wiki/Endianness) da arquitetura atual.

Em uma arquitetura pouco endiana, os string pontos `[ D801 DCCC ]` de código UTF-16 seriam dispostos `[ 0x01, 0xD8, 0xCC, 0xDC ]`na memória como os bytes . Em uma arquitetura de grande string endiana, o mesmo seria `[ 0xD8, 0x01, 0xDC, 0xCC ]`disposto na memória como os bytes.

Os sistemas de computador que se comunicam entre si devem concordar com a representação de dados cruzando o fio. A maioria dos protocolos de rede usa o UTF-8 como padrão ao transmitir texto, em parte para evitar problemas que podem resultar de uma máquina de grande endiana se comunicando com uma máquina pouco endiana. Os string pontos `[ F0 90 93 8C ]` de código UTF-8 serão sempre representados `[ 0xF0, 0x90, 0x93, 0x8C ]` como bytes, independentemente da endianidade.

Para usar o UTF-8 para transmitir texto, os aplicativos .NET geralmente usam código como o seguinte exemplo:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

No exemplo anterior, o método [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodifica o `string` UTF-16 de volta em uma série de valores unicodecalar, em seguida, ele recodifica `byte` esses valores escalares em UTF-8 e coloca a seqüência resultante em uma matriz. O método [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) realiza a transformação oposta, `byte` convertendo uma matriz `string`UTF-8 em um UTF-16 .

> [!WARNING]
> Como o UTF-8 é comum na internet, pode ser tentador ler bytes brutos do fio e tratar os dados como se fossem UTF-8. No entanto, você deve validar que ele é realmente bem formado. Um cliente mal-intencionado pode enviar UTF-8 mal formado ao seu serviço. Se você operar esses dados como se fossem bem formados, isso poderia causar erros ou falhas de segurança em sua aplicação. Para validar os dados utf-8, `Encoding.UTF8.GetString`você pode usar um método como , `string`que executará a validação ao converter os dados de entrada em um .

### <a name="well-formed-encoding"></a>Codificação bem formada

Uma codificação Unicode bem string formada é uma das unidades de código que podem ser decodificadas de forma inequívoca e sem erro em uma seqüência de valores escalares Unicode. Os dados bem formados podem ser transcodificados livremente entre UTF-8, UTF-16 e UTF-32.

A questão de saber se uma seqüência de codificação é bem formada ou não não está relacionada com a finalidade da arquitetura de uma máquina. Uma sequência UTF-8 mal formada é mal formada da mesma forma em máquinas de grande endian e pouco endian.

Aqui estão alguns exemplos de codificações mal formadas:

* No UTF-8, `[ 6C C2 61 ]` a seqüência `C2` é mal `61`formada porque não pode ser seguida por .

* Na UTF-16, `[ DC00 DD00 ]` a seqüência (ou, em C#, string `"\udc00\udd00"`a `DC00` ) é mal `DD00`formada porque o substituto baixo não pode ser seguido por outro substituto baixo .

* No UTF-32, `[ 0011ABCD ]` a seqüência `0011ABCD` é mal formada porque está fora do intervalo de valores escalares Unicode.

No .NET, `string` as instâncias quase sempre contêm dados UTF-16 bem formados, mas isso não é garantido. Os exemplos a seguir mostram código C# válido que cria `string` dados UTF-16 mal formados em instâncias.

* Um literal mal formado:

  ```csharp
  const string s = "\ud800";
  ```

* Uma substring que divide um par de substitutos:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

APIs [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) como nunca retornam `string` instâncias mal formadas. `Encoding.GetString`e `Encoding.GetBytes` os métodos detectam seqüências mal formadas na entrada e executam a substituição de caracteres ao gerar a saída. Por exemplo, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) se vir um byte não-ASCII na entrada (fora do intervalo U+0000.U+007F), ele `string` insere um '?' na instância retornada. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)substitui sequências UTF-8 mal `U+FFFD REPLACEMENT CHARACTER ('�')` formadas com `string` na instância retornada. Para obter mais informações, consulte [o Padrão Unicode](https://www.unicode.org/versions/latest/), seções 5.22 e 3.9.

As classes `Encoding` incorporadas também podem ser configuradas para lançar uma exceção em vez de executar a substituição de caracteres quando seqüências mal formadas são vistas. Essa abordagem é frequentemente usada em aplicativos sensíveis à segurança, onde a substituição de caracteres pode não ser aceitável.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Para obter informações sobre como `Encoding` usar as classes incorporadas, consulte [Como usar classes de codificação de caracteres em .NET](character-encoding.md).

## <a name="see-also"></a>Confira também

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalização e Localização](../../../docs/standard/globalization-localization/index.md)

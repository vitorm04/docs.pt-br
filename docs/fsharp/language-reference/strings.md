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
# <a name="strings"></a>Cadeias de caracteres

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O `string` tipo representa texto imutável como uma seqüência de caracteres Unicode. `string` é um alias para `System.String` no .NET Framework.

## <a name="remarks"></a>Comentários

Os literais das cordas são delimitados pelo caractere de marcação ("). O caractere barra \\ invertida () é usado para codificar certos caracteres especiais. A barra invertida e o próximo personagem juntos são conhecidos como uma *seqüência de fuga.* Sequências de escape suportadas em literais de seqüência f# são mostradas na tabela a seguir.

|Caractere|Sequência de escape|
|---------|---------------|
|Alerta|`\a`|
|Backspace|`\b`|
|Avanço de formulário|`\f`|
|Nova linha|`\n`|
|Retorno de carro|`\r`|
|Tab|`\t`|
|Guia vertical|`\v`|
|Barra invertida|`\\`|
|Aspas|`\"`|
|Apóstrofo|`\'`|
|Caractere unicode|`\DDD`(onde `D` indica um dígito decimal; intervalo de 000 `\231` - 255; por exemplo, = "ç")|
|Caractere unicode|`\xHH`(onde `H` indica um dígito hexadecimal; intervalo de 00 - FF; por exemplo, `\xE7` = "ç")|
|Caractere unicode|`\uHHHH`(UTF-16) (onde `H` indica um dígito hexadecimal; intervalo de 0000 - FFFF;  por exemplo, `\u00E7` = "ç")|
|Caractere unicode|`\U00HHHHHH`(UTF-32) (onde `H` indica um dígito hexadecimal; intervalo de 000000 - 10FFFF;  por exemplo, `\U0001F47D` 👽= "")|

> [!IMPORTANT]
> A `\DDD` seqüência de fuga é notação decimal, não notação octal como na maioria das outras línguas. Portanto, dígitos `8` `9` e são válidos, `\032` e uma seqüência de representa um espaço (U+0020), `\040`enquanto que o mesmo ponto de código na notação octal seria .

> [!NOTE]
> Sendo constrangidos a um intervalo de 0 `\DDD` - `\x` 255 (0xFF), as seqüências e fuga são efetivamente o conjunto de caracteres [ISO-8859-1,](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) uma vez que corresponde aos primeiros 256 pontos de código Unicode.

## <a name="verbatim-strings"></a>Cordas Verbatim

Se precedido pelo símbolo @, o literal é uma seqüência verbatim. Isso significa que todas as seqüências de fuga são ignoradas, exceto que dois caracteres de marca de citação são interpretados como um caractere de marca de citação.

## <a name="triple-quoted-strings"></a>Cordas tríplices citadas

Além disso, uma seqüência pode ser fechada por cotações triplas. Neste caso, todas as seqüências de escape são ignoradas, incluindo caracteres de marca ção dupla. Para especificar uma seqüência que contém uma seqüência de string incorporada, você pode usar uma seqüência verbatim ou uma seqüência de três citações. Se você usar uma seqüência de caracteres verbatim, você deve especificar dois caracteres de marca de citação para indicar um único caractere de marca de citação. Se você usar uma seqüência de caracteres de citação tripla, você pode usar os caracteres de marca de cotação única sem que eles sejam analisados como o final da seqüência. Esta técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Em código, as strings que têm quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como linhas novas, a menos que um caractere de barra invertida seja o último caractere antes da linha quebrar. O espaço em branco líder na próxima linha é ignorado quando o caractere barra invertida é usado. O código a seguir `str1` produz `"abc\ndef"` uma string `str2` que `"abcdef"`tem valor e uma string que tem valor .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexação e Corte de Cordas

Você pode acessar caracteres individuais em uma seqüência usando sintaxe semelhante a matriz, da seguinte forma.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

A saída é `b`.

Ou você pode extrair substrings usando a sintaxe de fatia de matriz, como mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

A saída é a seguinte.

```console
abc
def
```

Você pode representar strings ASCII por matrizes de `byte[]`bytes não assinados, digite . Você adiciona o `B` sufixo a um literal de seqüência para indicar que é uma seqüência ASCII. Os literais de seqüência ASCII usados com matrizes de byte suportam as mesmas seqüências de escape que as seqüências Unicode, exceto as seqüências de fuga Unicode.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operadores da cadeia de caracteres

O `+` operador pode ser usado para concatenar strings, mantendo a compatibilidade com os recursos de manuseio de strings .NET Framework. O exemplo a seguir ilustra a concatenação de cordas.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe cordas

Como o tipo de string em F# é na verdade um tipo de Framework `System.String` .NET, todos os `System.String` membros estão disponíveis. Isso inclui `+` o operador, que é usado para `Length` concatenar `Chars` strings, a propriedade e a propriedade, que retorna a string como uma matriz de caracteres Unicode. Para obter mais informações `System.String`sobre strings, consulte .

Usando a `Chars` propriedade `System.String`de , você pode acessar os caracteres individuais em uma seqüência especificando um índice, como é mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Módulo de cordas

A funcionalidade adicional para o manuseio `String` de `FSharp.Core` cordas está incluída no módulo no namespace. Para obter mais informações, consulte [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Confira também

- [Referência de idioma F#](index.md)

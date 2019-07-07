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
# <a name="strings"></a>Cadeias de caracteres

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O `string` tipo representa texto imutável, como uma sequência de caracteres Unicode. `string` é um alias para `System.String` no .NET Framework.

## <a name="remarks"></a>Comentários

Literais de cadeia de caracteres são delimitados pelo caractere de aspas ("). O caractere de barra invertida ( \\ ) é usado para codificar determinados caracteres especiais. A barra invertida e o próximo caractere junto são conhecidos como uma *sequência de escape*. Suportada de sequências de escape F# literais de cadeia de caracteres são mostrados na tabela a seguir.

|Caractere|Sequência de escape|
|---------|---------------|
|Alerta|`\a`|
|Backspace|`\b`|
|Avanço de página|`\f`|
|Nova linha|`\n`|
|Retorno de carro|`\r`|
|Tabulação|`\t`|
|Tabulação vertical|`\v`|
|Barra invertida|`\\`|
|Marca de aspas|`\"`|
|Apóstrofe|`\'`|
|caractere Unicode|`\DDD` (onde `D` indica um decimal digit; o intervalo de 000 - 255; por exemplo, `\231` = "ç")|
|caractere Unicode|`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; e.g. `\xE7` = "ç")|
|caractere Unicode|`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  e.g. `\u00E7` = "ç")|
|caractere Unicode|`\U00HHHHHH` (UTF-32) (onde `H` indica um dígito hexadecimal; o intervalo de 000000 - 10FFFF;  Por exemplo, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> O `\DDD` sequência de escape é a notação decimal, a notação octal não como na maioria das outras linguagens. Portanto, os dígitos `8` e `9` sejam válidas e uma sequência de `\032` representa um espaço (u+0020), enquanto esse mesmo ponto de código em notação octal seria `\040`.

> [!NOTE]
> Sendo restrita a um intervalo de 0 – 255 (0xFF), o `\DDD` e `\x` sequências de escape são efetivamente as [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) do conjunto de caracteres, desde que corresponde ao primeiro 256 pontos de código Unicode.

Se precedido pelo símbolo @, o literal é uma cadeia de caracteres textual. Isso significa que as sequências de escape são ignoradas, exceto que dois caracteres de marca de aspas simples são interpretados como caracteres de uma marca de aspas simples.

Além disso, uma cadeia de caracteres pode ser delimitada por aspas triplas. Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas. Para especificar uma cadeia de caracteres que contém um embedded caracteres entre aspas, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas. Se você usar uma cadeia de caracteres textual, você deve especificar dois caracteres de aspas para indicar um caractere de aspa simples. Se você usar uma cadeia de caracteres entre aspas triplas, você pode usar os caracteres de aspas simples sem que eles que está sendo analisado como o fim da cadeia de caracteres. Essa técnica pode ser útil ao trabalhar com XML ou outras estruturas que incluem as aspas internas.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

No código, cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida é o último caractere antes da quebra de linha. Espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado. O código a seguir produz uma cadeia de caracteres `str1` que tem o valor `"abc\ndef"` e uma cadeia de caracteres `str2` que tem o valor `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Você pode acessar os caracteres individuais em uma cadeia de caracteres usando a sintaxe de matriz, da seguinte maneira.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

A saída é `b`.

Ou você pode extrair subcadeias de caracteres usando a sintaxe de fatia de matriz, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

A saída é a seguinte.

```
abc
def
```

Cadeias de caracteres ASCII pode ser representado usando matrizes de bytes sem sinal, o tipo `byte[]`. Adicione o sufixo `B` para uma cadeia de caracteres literal para indicar que ele é uma cadeia de caracteres ASCII. As sequências de escape mesmo como cadeias de caracteres Unicode, exceto para as sequências de escape Unicode dão suporte a literais de cadeia de caracteres ASCII usados com matrizes de bytes.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operadores da cadeia de caracteres

Concatenar cadeias de caracteres de duas maneiras: usando o `+` operador ou usando o `^` operador. O `+` operador mantém a compatibilidade com a cadeia de caracteres do .NET Framework que recursos de tratamento.

O exemplo a seguir ilustra a concatenação de cadeia de caracteres.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe de cadeia de caracteres

Porque o tipo de cadeia de caracteres no F# é, na verdade, um .NET Framework `System.String` digitar tudo a `System.String` membros estão disponíveis. Isso inclui o `+` operador, que é usado para concatenar cadeias de caracteres, o `Length` propriedade e o `Chars` propriedade, que retorna a cadeia de caracteres como uma matriz de caracteres Unicode. Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.

Usando o `Chars` propriedade de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, conforme mostrado no código a seguir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Módulo de cadeia de caracteres

Funcionalidade adicional para a manipulação de cadeia de caracteres está incluída na `String` módulo no `FSharp.Core` namespace. Para obter mais informações, consulte [módulo Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)

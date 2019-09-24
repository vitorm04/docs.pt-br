---
title: Cadeias de caracteres
description: Saiba como o F# tipo ' String ' representa texto imutável como uma sequência de caracteres Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 25f5d7ce5059ba5ddb4e938313c511734c2d7320
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216738"
---
# <a name="strings"></a>Cadeias de caracteres

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O `string` tipo representa texto imutável como uma sequência de caracteres Unicode. `string` é um alias para `System.String` no .NET Framework.

## <a name="remarks"></a>Comentários

Literais de cadeia de caracteres são delimitadas pelo caractere de aspas ("). O caractere de barra invertida ( \\ ) é usado para codificar determinados caracteres especiais. A barra invertida e o próximo caractere juntos são conhecidos como uma *sequência de escape*. As sequências de F# escape com suporte em literais de cadeia de caracteres são mostradas na tabela a seguir.

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
|Aspas|`\"`|
|Apóstrofo|`\'`|
|caractere Unicode|`\DDD`(onde `D` indica um dígito decimal; intervalo de 000-255; por exemplo, `\231` = "ç")|
|caractere Unicode|`\xHH`(onde `H` indica um dígito hexadecimal; intervalo de 00-FF; por exemplo, `\xE7` = "ç")|
|caractere Unicode|`\uHHHH`(UTF-16) (onde `H` indica um dígito hexadecimal; intervalo de 0000-ffff;  por exemplo, `\u00E7` = "ç")|
|caractere Unicode|`\U00HHHHHH`(UTF-32) (onde `H` indica um dígito hexadecimal; intervalo de 000000-10FFFF;  por exemplo, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> A `\DDD` sequência de escape é notação decimal, não notação octal, como na maioria das outras linguagens. Portanto, os `8` dígitos `9` e são válidos, e uma sequência `\032` de representa um espaço (U + 0020), enquanto que o `\040`mesmo ponto de código na notação octal seria.

> [!NOTE]
> Sendo restrito a um intervalo de 0-255 (0xFF), as `\DDD` sequências de escape e `\x` são efetivamente o conjunto de caracteres [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , pois isso corresponde aos primeiros 256 pontos de código Unicode.

Se for precedido pelo símbolo @, o literal é uma cadeia de caracteres textual. Isso significa que todas as sequências de escape são ignoradas, exceto que dois caracteres de aspas são interpretados como um caractere de aspas.

Além disso, uma cadeia de caracteres pode estar entre aspas triplas. Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas. Para especificar uma cadeia de caracteres que contenha uma cadeia de caracteres entre aspas incorporada, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas. Se você usar uma cadeia de caracteres textual, deverá especificar dois caracteres de aspas para indicar um caractere de aspas simples. Se você usar uma cadeia de caracteres entre aspas triplas, poderá usar os caracteres de aspas simples sem que eles sejam analisados como o final da cadeia de caracteres. Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

No código, as cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida seja o último caractere antes da quebra de linha. O espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado. O código a seguir produz uma `str1` cadeia de caracteres `"abc\ndef"` com valor e `str2` uma cadeia de `"abcdef"`caracteres com valor.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Você pode acessar caracteres individuais em uma cadeia de caracteres usando a sintaxe do tipo matriz, da seguinte maneira.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

A saída é `b`.

Ou você pode extrair subcadeias de caracteres usando a sintaxe da fatia de matriz, conforme mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

A saída é a seguinte.

```console
abc
def
```

Você pode representar cadeias de caracteres ASCII por matrizes de bytes não `byte[]`assinados, digite. Você adiciona o sufixo `B` a um literal de cadeia de caracteres para indicar que é uma cadeia de caracteres ASCII. Literais de cadeia de caracteres ASCII usados com matrizes de bytes dão suporte às mesmas sequências de escape que as cadeias de caracteres Unicode, exceto as sequências de escape Unicode

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operadores da cadeia de caracteres

Há duas maneiras de concatenar cadeias de caracteres: usando `+` o operador ou usando o `^` operador. O `+` operador mantém a compatibilidade com os recursos de manipulação de cadeia de caracteres .NET Framework.

O exemplo a seguir ilustra a concatenação de cadeia de caracteres.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe String

Como o tipo de cadeia F# de caracteres no é `System.String` , na verdade, `System.String` um tipo de .NET Framework, todos os membros estão disponíveis. Isso inclui o `+` operador, que é usado para concatenar cadeias de `Length` caracteres, a propriedade `Chars` e a propriedade, que retorna a cadeia de caracteres como uma matriz de caractere Unicode. Para obter mais informações sobre cadeias `System.String`de caracteres, consulte.

Usando a `Chars` propriedade de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Módulo de cadeia de caracteres

A funcionalidade adicional para manipulação de cadeia de caracteres `String` está incluída no `FSharp.Core` módulo no namespace. Para obter mais informações, consulte [Core. String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Consulte também

- [Referência da Linguagem F#](index.md)

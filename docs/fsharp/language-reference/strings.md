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
# <a name="strings"></a>Cadeias de caracteres

> [!NOTE]
> Os links de referência da API neste artigo levarão você até o MSDN.  A referência da API docs.microsoft.com não está completa.

O tipo de `string` representa texto imutável como uma sequência de caracteres Unicode. `string` é um alias para `System.String` no .NET Framework.

## <a name="remarks"></a>Comentários

Literais de cadeia de caracteres são delimitadas pelo caractere de aspas ("). O caractere de barra invertida (\\) é usado para codificar determinados caracteres especiais. A barra invertida e o próximo caractere juntos são conhecidos como uma *sequência de escape*. As sequências de F# escape com suporte em literais de cadeia de caracteres são mostradas na tabela a seguir.

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
|Caractere unicode|`\DDD` (em que `D` indica um dígito decimal; intervalo de 000-255; por exemplo, `\231` = "ç")|
|Caractere unicode|`\xHH` (em que `H` indica um dígito hexadecimal; intervalo de 00-FF; por exemplo, `\xE7` = "ç")|
|Caractere unicode|`\uHHHH` (UTF-16) (em que `H` indica um dígito hexadecimal; intervalo de 0000-FFFF;  por exemplo, `\u00E7` = "ç")|
|Caractere unicode|`\U00HHHHHH` (UTF-32) (em que `H` indica um dígito hexadecimal; intervalo de 000000-10FFFF;  por exemplo, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> A sequência de escape `\DDD` é notação decimal, não notação octal, como na maioria das outras linguagens. Portanto, os dígitos `8` e `9` são válidos e uma sequência de `\032` representa um espaço (U + 0020), enquanto que o mesmo ponto de código na notação octal seria `\040`.

> [!NOTE]
> Sendo restrito a um intervalo de 0-255 (0xFF), as sequências de escape `\DDD` e `\x` são efetivamente o conjunto de caracteres [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , pois isso corresponde aos primeiros 256 pontos de código Unicode.

## <a name="verbatim-strings"></a>Cadeias de caracteres textuais

Se for precedido pelo símbolo @, o literal é uma cadeia de caracteres textual. Isso significa que todas as sequências de escape são ignoradas, exceto que dois caracteres de aspas são interpretados como um caractere de aspas.

## <a name="triple-quoted-strings"></a>Cadeias de caracteres entre aspas triplas

Além disso, uma cadeia de caracteres pode estar entre aspas triplas. Nesse caso, todas as sequências de escape são ignoradas, incluindo caracteres de aspas duplas. Para especificar uma cadeia de caracteres que contenha uma cadeia de caracteres entre aspas incorporada, você pode usar uma cadeia de caracteres textual ou uma cadeia de caracteres entre aspas triplas. Se você usar uma cadeia de caracteres textual, deverá especificar dois caracteres de aspas para indicar um caractere de aspas simples. Se você usar uma cadeia de caracteres entre aspas triplas, poderá usar os caracteres de aspas simples sem que eles sejam analisados como o final da cadeia de caracteres. Essa técnica pode ser útil quando você trabalha com XML ou outras estruturas que incluem aspas incorporadas.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

No código, as cadeias de caracteres com quebras de linha são aceitas e as quebras de linha são interpretadas literalmente como novas linhas, a menos que um caractere de barra invertida seja o último caractere antes da quebra de linha. O espaço em branco à esquerda na próxima linha é ignorado quando o caractere de barra invertida é usado. O código a seguir produz uma cadeia de caracteres `str1` com valor `"abc\ndef"` e uma `str2` de cadeia de caracteres com valor `"abcdef"`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Indexação e divisão de cadeia de caracteres

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

Você pode representar cadeias de caracteres ASCII por matrizes de bytes não assinados, digite `byte[]`. Você adiciona o sufixo `B` a uma cadeia de caracteres literal para indicar que é uma cadeia de caracteres ASCII. Literais de cadeia de caracteres ASCII usados com matrizes de bytes dão suporte às mesmas sequências de escape que as cadeias de caracteres Unicode, exceto as sequências de escape Unicode

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Operadores da cadeia de caracteres

Há duas maneiras de concatenar cadeias de caracteres: usando o operador `+` ou usando o operador `^`. O operador `+` mantém a compatibilidade com os recursos de manipulação de cadeia de caracteres .NET Framework.

O exemplo a seguir ilustra a concatenação de cadeia de caracteres.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Classe String

Como o tipo de cadeia F# de caracteres no é, na verdade, um .NET Framework tipo de `System.String`, todos os membros `System.String` estão disponíveis. Isso inclui o operador de `+`, que é usado para concatenar cadeias de caracteres, a propriedade `Length` e a propriedade `Chars`, que retorna a cadeia como uma matriz de caractere Unicode. Para obter mais informações sobre cadeias de caracteres, consulte `System.String`.

Usando a propriedade `Chars` de `System.String`, você pode acessar os caracteres individuais em uma cadeia de caracteres especificando um índice, como é mostrado no código a seguir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Módulo de cadeia de caracteres

A funcionalidade adicional para manipulação de cadeia de caracteres está incluída no módulo `String` no namespace `FSharp.Core`. Para obter mais informações, consulte [Core. String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Confira também

- [Referência da Linguagem F#](index.md)

---
title: Literais
description: Saiba mais sobre os tipos de literais no F# linguagem de programação.
ms.date: 06/28/2019
ms.openlocfilehash: 0c9ced0b505817a161ca39c6c9f853f94cedf410
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610148"
---
# <a name="literals"></a>Literais

> [!NOTE]
> Os links de referência de API neste artigo você será levado ao MSDN (por enquanto).

Este tópico fornece uma tabela que mostra como especificar o tipo de um literal em F#.

## <a name="literal-types"></a>Tipos literais

A tabela a seguir mostra os tipos de literais no F#. Caracteres que representam dígitos em notação hexadecimal não diferenciam maiusculas de minúsculas; caracteres que identifica o tipo diferenciam maiusculas de minúsculas.

|Tipo|Descrição|Prefixo ou sufixo|Exemplos|
|----|-----------|----------------|--------|
|sbyte|inteiro com sinal de 8 bits|y|`86y`<br /><br />`0b00000101y`|
|byte|número de natural de 8 bits sem sinal|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|inteiro com sinal de 16 bits|s|`86s`|
|uint16|número de natural de 16 bits sem sinal|us|`86us`|
|int<br /><br />int32|inteiro com sinal de 32 bits|l ou none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|número de natural de 32 bits sem sinal|u ou ul|`86u`<br /><br />`86ul`|
|nativeint|ponteiro nativo para um número natural assinado|n|`123n`|
|unativeint|ponteiro nativo como um número natural sem sinal|Cancelar|`0x00002D3Fun`|
|int64|inteiro com sinal de 64 bits|L|`86L`|
|uint64|número de natural de 64 bits sem sinal|UL|`86UL`|
|simples, float32|número de ponto flutuante de 32 bits|F ou f|`4.14F` ou `4.14f`|
|||LF|`0x00000000lf`|
|float; Double|número de ponto flutuante de 64 bits|nenhum|`4.14`, `2.3E+32` ou `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|inteiro não limitado a representação de 64 bits|I|`9999999999999999999999999999I`|
|decimal|número fracionário representado como um ponto fixo ou um número racional|M ou m|`0.7833M` ou `0.7833m`|
|Char|caractere Unicode|nenhum|`'a'`|
|Cadeia de Caracteres|Cadeia de caracteres Unicode|nenhum|`"text\n"`<br /><br />ou<br /><br />`@"c:\filename"`<br /><br />ou<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />ou<br /><br />`"string1" + "string2"`<br /><br />Consulte também [cadeias de caracteres](Strings.md).|
|byte|Caractere ASCII|B|`'a'B`|
|byte[]|Cadeia de caracteres ASCII|B|`"text"B`|
|Cadeia de caracteres ou byte]|cadeia de caracteres textual|@ prefix|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Literais nomeados

Os valores que devem ser constantes podem ser marcados com o [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atributo. Este atributo tem o efeito de causar um valor a ser compilado como uma constante.

Em expressões de correspondência, identificadores que começam com caracteres minúsculos sempre são tratados como variáveis a serem associadas, em vez de como literais, portanto, você deve geralmente usar iniciais maiusculas ao definir literais.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Comentários

Cadeias de caracteres Unicode podem conter as codificações explícitas que você pode especificar usando `\u` seguido por um código hexadecimal de 16 bits (0000 - FFFF) ou codificações UTF-32 que você pode especificar usando `\U` seguido por um código hexadecimal de 32 bits que representa qualquer ponto de código Unicode (00000000 - 0010FFFF).

O uso de outros operadores bit a bit diferente de `|||` não é permitido.

## <a name="integers-in-other-bases"></a>Números inteiros em outras bases

Inteiros com sinal de 32 bits também podem ser especificados em octal, hexadecimal ou binário usando um `0x`, `0o` ou `0b` do prefixo, respectivamente.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Sublinhados em literais numéricos

Você pode separar dígitos com o caractere de sublinhado (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Consulte também

- [Classe Core. literalattribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)

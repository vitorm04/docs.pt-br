---
title: tipo char - referência C#
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: c4e29e6437edfe549b36a04a2050f63caa0d3d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846516"
---
# <a name="char-c-reference"></a>char (referência C#)

A `char` palavra-chave tipo é um <xref:System.Char?displayProperty=nameWithType> alias para o tipo de estrutura .NET que representa um caractere Unicode UTF-16.

|Type|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 a U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

O valor padrão `char` do `\0`tipo é, ou seja, U+0000.

O tipo [de string](reference-types.md#the-string-type) representa `char` o texto como uma seqüência de valores.

## <a name="literals"></a>Literais

Você pode `char` especificar um valor com:

- um personagem literal.
- uma seqüência de `\u` fuga Unicode, que é seguida pela representação hexadecimal de quatro símbolos de um código de caractere.
- uma seqüência de fuga hexadecimal, que é `\x` seguida pela representação hexadecimal de um código de caractere.

[!code-csharp-interactive[char literals](snippets/CharType.cs#Literals)]

Como o exemplo anterior mostra, você também pode lançar `char` o valor de um código de caractere no valor correspondente.

> [!NOTE]
> No caso de uma seqüência de fuga Unicode, você deve especificar todos os quatro dígitos hexadecimais. Ou seja, `\u006A` é uma sequência `\u06A` `\u6A` de fuga válida, enquanto e não são válidos.
>
> No caso de uma seqüência de fuga hexadecimal, você pode omiti-lo os zeros principais. Ou seja, `\x006A` `\x06A`as `\x6A` seqüências de fuga são válidas e correspondem ao mesmo caractere.

## <a name="conversions"></a>Conversões

O `char` tipo é implicitamente conversível `int`para `uint` `long`os `ulong`seguintes tipos [integrais:](integral-numeric-types.md) `ushort`, , , e . . Também é implicitamente conversível para os tipos numéricos `double`de `decimal` [ponto flutuante](floating-point-numeric-types.md) embutidos: `float`, e . É explicitamente conversível `sbyte`para, `byte` `short` e tipos integrais.

Não há conversões implícitas de `char` outros tipos para o tipo. No entanto, qualquer tipo numérico [integral](integral-numeric-types.md) `char`ou de ponto [flutuante](floating-point-numeric-types.md) é explicitamente conversível para .

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [Tipos Integrais](~/_csharplang/spec/types.md#integral-types) da especificação do [idioma C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de valor](value-types.md)
- [Cadeias de caracteres](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>

---
title: tipo de caractere C# -referência
ms.date: 11/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 3b2eec4f0e17aa329fe3865fb3ef453ee030c6a7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451160"
---
# <a name="char-c-reference"></a>Char (C# referência)

A palavra-chave Type de `char` é um alias para o tipo de estrutura .NET <xref:System.Char?displayProperty=nameWithType> que representa um caractere Unicode UTF-16.

|Tipo|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 a U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

O tipo de [cadeia de caracteres](reference-types.md#the-string-type) representa o texto como uma sequência de valores de `char`.

## <a name="literals"></a>{1&gt;Literais&lt;1}

Você pode especificar um valor de `char` com:

- um literal de caractere.
- uma sequência de escape Unicode, que é `\u` seguida pela representação hexadecimal de quatro símbolos de um código de caractere.
- uma sequência de escape hexadecimal, que é `\x` seguida pela representação hexadecimal de um código de caractere.

[!code-csharp-interactive[char literals](~/samples/csharp/language-reference/builtin-types/CharType.cs#Literals)]

Como mostra o exemplo anterior, você também pode converter o valor de um código de caractere no valor de `char` correspondente.

> [!NOTE]
> No caso de uma sequência de escape Unicode, você deve especificar todos os quatro dígitos hexadecimais. Ou seja, `\u006A` é uma sequência de escape válida, enquanto `\u06A` e `\u6A` não são válidos.
>
> No caso de uma sequência de escape hexadecimal, você pode omitir os zeros à esquerda. Ou seja, as sequências de escape `\x006A`, `\x06A`e `\x6A` são válidas e correspondem ao mesmo caractere.

## <a name="conversions"></a>Conversões

O tipo de `char` é implicitamente conversível para os seguintes tipos [integral](integral-numeric-types.md) : `ushort`, `int`, `uint`, `long`e `ulong`. Ele também é implicitamente conversível para os tipos numéricos de [ponto flutuante](floating-point-numeric-types.md) internos: `float`, `double`e `decimal`. Ele é explicitamente conversível para `sbyte`, `byte`e `short` tipos integrais.

Não há conversões implícitas de outros tipos para o tipo de `char`. No entanto, qualquer tipo [integral](integral-numeric-types.md) ou numérico [de ponto flutuante](floating-point-numeric-types.md) é explicitamente conversível para `char`.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [tipos integrais](~/_csharplang/spec/types.md#integral-types) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tabela de tipos internos](../keywords/built-in-types-table.md)
- [Cadeias de Caracteres](../../programming-guide/strings/index.md)

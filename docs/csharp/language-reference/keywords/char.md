---
title: palavra-chave C# Char-referência
ms.custom: seodec18
ms.date: 10/22/2019
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1b9f8d1bb205a6cbfe521830a11bd8878ccde991
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771795"
---
# <a name="char-c-reference"></a>Char (C# referência)

A palavra-chave Type de `char` é um alias para o tipo de estrutura .NET <xref:System.Char?displayProperty=nameWithType> que representa um caractere Unicode UTF-16:

|Digite|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 a U+FFFF|16 bits|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literais

As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode. Você também pode converter um código de caractere integral no valor de `char` correspondente. No exemplo a seguir, os quatro elementos de uma matriz de `char` são inicializados com o mesmo caractere `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Conversões

O tipo de `char` é implicitamente conversível para os seguintes tipos [integral](../builtin-types/integral-numeric-types.md) : `ushort`, `int`, `uint`, `long` e `ulong`. Ele também é implicitamente conversível para os tipos numéricos de [ponto flutuante](../builtin-types/floating-point-numeric-types.md) internos: `float`, `double` e `decimal`. Ele é explicitamente conversível para `sbyte`, `byte` e `short` tipos integrais.

Não há conversões implícitas de outros tipos para o tipo de `char`. No entanto, qualquer tipo [integral](../builtin-types/integral-numeric-types.md) ou numérico [de ponto flutuante](../builtin-types/floating-point-numeric-types.md) é explicitamente conversível para `char`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, consulte a seção [tipos integrais](~/_csharplang/spec/types.md#integral-types) da [ C# especificação da linguagem](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Palavras-chave do C#](./index.md)
- [Tabela de tipos internos](./built-in-types-table.md)
- [Cadeias de Caracteres](../../programming-guide/strings/index.md)
- <xref:System.Char?displayProperty=nameWithType>

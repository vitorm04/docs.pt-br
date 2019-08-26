---
title: Palavra-chave char – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 754c04bfc3b4090906420d55d55e51606b72f187
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605952"
---
# <a name="char-c-reference"></a>char (Referência de C#)

A palavra-chave `char` é usada para declarar uma instância da estrutura <xref:System.Char?displayProperty=nameWithType> que o .NET Framework usa para representar um caractere Unicode. O valor de um objeto `Char` é um valor numérico de 16 bits (ordinal).

 Os caracteres Unicode são usados para representar a maioria dos idiomas escritos em todo o mundo.

|Tipo|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`char`|U+0000 a U+FFFF|Caractere Unicode de 16 bits|<xref:System.Char?displayProperty=nameWithType>|

## <a name="literals"></a>Literais

As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode. Você também pode converter os códigos de caracteres integrais. No exemplo a seguir, quatro variáveis `char` são inicializadas com o mesmo caractere `X`:

[!code-csharp[csrefKeywordsTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#19)]

## <a name="conversions"></a>Conversões

Um `char` pode ser implicitamente convertido em [ushort](../builtin-types/integral-numeric-types.md), [int](../builtin-types/integral-numeric-types.md), [uint](../builtin-types/integral-numeric-types.md), [double](../builtin-types/floating-point-numeric-types.md) ou [decimal](../builtin-types/floating-point-numeric-types.md). No entanto, não há conversões implícitas de outros tipos para o tipo `char`.

O tipo <xref:System.Char?displayProperty=nameWithType> fornece vários métodos estáticos para trabalhar com valores `char`.

## <a name="c-language-specification"></a>Especificação da linguagem C#  

Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- <xref:System.Char>
- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [Tipos integrais](../builtin-types/integral-numeric-types.md)
- [Tabela de tipos internos](./built-in-types-table.md)
- [Tabela de conversões numéricas implícitas](./implicit-numeric-conversions-table.md)
- [Tabela de conversões numéricas explícitas](./explicit-numeric-conversions-table.md)
- [Tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md)
- [Cadeias de Caracteres](../../programming-guide/strings/index.md)

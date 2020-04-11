---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 10/22/2019
f1_keywords:
- byte
- byte_CSharpKeyword
- sbyte_CSharpKeyword
- sbyte
- short
- short_CSharpKeyword
- ushort
- ushort_CSharpKeyword
- int_CSharpKeyword
- int
- uint
- uint_CSharpKeyword
- long_CSharpKeyword
- long
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
- byte keyword [C#]
- sbyte keyword [C#]
- short keyword [C#]
- ushort keyword [C#]
- int keyword [C#]
- uint keyword [C#]
- long keyword [C#]
- ulong keyword [C#]
ms.openlocfilehash: 4b2506f48c3e72ff838a07087c8c5d9ea63bb46c
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121463"
---
# <a name="integral-numeric-types--c-reference"></a>Tipos numéricos integrais (Referência C#)

Os *tipos numéricos integrais* representam números inteiros. Todos os tipos numéricos integrais são [tipos de valor](value-types.md). Eles também são [tipos simples](value-types.md#built-in-value-types) e podem ser inicializados com [literais](#integer-literals). Todos os tipos numéricos integrais suportam [operadores aritméticos,](../operators/arithmetic-operators.md) [bitwise lógicos,](../operators/bitwise-and-shift-operators.md) [de comparação](../operators/comparison-operators.md)e [de igualdade.](../operators/equality-operators.md)

## <a name="characteristics-of-the-integral-types"></a>Características dos tipos integrais

O C# é compatível com os seguintes tipos integrais predefinidos:

|palavra-chave/tipo C#|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 a 127|Inteiro de 8 bits com sinal|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 a 255|Inteiro de 8 bits sem sinal|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32.768 a 32.767|Inteiro de 16 bits com sinal|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 a 65.535|Inteiro de 16 bits sem sinal|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648 a 2.147.483.647|Inteiro assinado de 32 bits|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 a 4.294.967.295|Inteiro de 32 bits sem sinal|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|Inteiro assinado de 64 bits|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 a 18.446.744.073.709.551.615|Inteiro de 64 bits sem sinal|<xref:System.UInt64?displayProperty=nameWithType>|

Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente. Eles são intercambiáveis. Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:

```csharp
int a = 123;
System.Int32 b = 123;
```

O valor padrão de cada tipo integral é zero, `0`. Cada um dos tipos integrais possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.

Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.

## <a name="integer-literals"></a>Literals inteiros

Literais inteiros podem ser

- *decimal*: sem qualquer prefixo
- *hexadecimal*: `0x` com `0X` o prefixo ou prefixo
- *binário*: `0b` com `0B` o prefixo ou (disponível em C# 7.0 e posterior)

O código a seguir demonstra um exemplo de cada um:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

O exemplo anterior também `_` mostra o uso de como *separador de dígitos,* que é suportado a partir de C# 7.0. Você pode usar o separador de dígitos com todos os tipos de literais numéricos.

O tipo de um inteiro literal é determinado pelo seu sufixo da seguinte forma:

- Se o literal não tiver sufixo, seu tipo é o primeiro dos `int` `uint`seguintes tipos em que seu valor pode ser representado: , , `long`. `ulong`
- Se o literal for `U` sufixo por ou `u`, seu tipo é o primeiro `uint` `ulong`dos seguintes tipos em que seu valor pode ser representado: , .
- Se o literal for `L` sufixo por ou `l`, seu tipo é o primeiro `long` `ulong`dos seguintes tipos em que seu valor pode ser representado: , .

  > [!NOTE]
  > Você pode usar a `l` letra minúscula como um sufixo. No entanto, isso gera um `l` aviso compilador porque `1`a letra pode ser confundida com o dígito . Use `L` para clareza.

- Se o literal for `UL`sufixo por `Lu` `lU`, `Ul` `uL`, `ul`, , `LU`, , , , ou `lu`, seu tipo é `ulong`.

Se o valor representado por um literal inteiro exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).

Se o tipo determinado de um `int` inteiro literal é e o valor representado pelo literal está dentro do `sbyte`intervalo `byte` `short`do `ushort`tipo de destino, o valor pode ser implicitamente convertido para, , , , , `uint`, ou `ulong`:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Como o exemplo anterior mostra, se o valor do literal não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031.](../../misc/cs0031.md)

Você também pode usar um elenco para converter o valor representado por um inteiro literal para o tipo diferente do determinado tipo do literal:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Conversões

Você pode converter qualquer tipo numérico integral para qualquer outro tipo numérico integral. Se o tipo de destino pode armazenar todos os valores do tipo de origem, a conversão está implícita. Caso contrário, você precisa usar uma [expressão de elenco](../operators/type-testing-and-cast.md#cast-expression) para realizar uma conversão explícita. Para obter mais informações, consulte [conversões numéricas incorporadas](numeric-conversions.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos integrais](~/_csharplang/spec/types.md#integral-types)
- [Literals inteiros](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Tipos de valor](value-types.md)
- [Tipos de pontos flutuantes](floating-point-numeric-types.md)
- [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md)
- [Numéricos no .NET](../../../standard/numerics.md)

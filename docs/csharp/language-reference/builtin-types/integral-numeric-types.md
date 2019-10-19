---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 10/18/2019
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
ms.openlocfilehash: 3d4f3164d67a000123417619f3be6be455d5ab87
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579191"
---
# <a name="integral-numeric-types--c-reference"></a>Tipos numéricos integrais (Referência C#)

Os **tipos numéricos integrais** são um subconjunto de **tipos simples** e podem ser inicializados com [*literais*](#integer-literals). Todos os tipos integrais também são tipos de valor. Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [lógicos](../operators/bitwise-and-shift-operators.md), de [comparação](../operators/comparison-operators.md)e de [igualdade](../operators/equality-operators.md) .

## <a name="characteristics-of-the-integral-types"></a>Características dos tipos integrais

O C# é compatível com os seguintes tipos integrais predefinidos:

|palavra-chave/tipo C#|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------|
|`sbyte`|-128 a 127|Inteiro de 8 bits com sinal|<xref:System.SByte?displayProperty=nameWithType>|
|`byte`|0 a 255|Inteiro de 8 bits sem sinal|<xref:System.Byte?displayProperty=nameWithType>|
|`short`|-32.768 a 32.767|Inteiro de 16 bits com sinal|<xref:System.Int16?displayProperty=nameWithType>|
|`ushort`|0 a 65.535|Inteiro de 16 bits sem sinal|<xref:System.UInt16?displayProperty=nameWithType>|
|`int`|-2.147.483.648 a 2.147.483.647|Inteiro de 32 bits com sinal|<xref:System.Int32?displayProperty=nameWithType>|
|`uint`|0 a 4.294.967.295|Inteiro de 32 bits sem sinal|<xref:System.UInt32?displayProperty=nameWithType>|
|`long`|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807|Inteiro de 64 bits com sinal|<xref:System.Int64?displayProperty=nameWithType>|
|`ulong`|0 a 18.446.744.073.709.551.615|Inteiro de 64 bits sem sinal|<xref:System.UInt64?displayProperty=nameWithType>|

Na tabela anterior, cada palavra-chave do tipo C# da coluna mais à esquerda é um alias do tipo .NET correspondente. Eles são intercambiáveis. Por exemplo, as declarações a seguir declaram variáveis do mesmo tipo:

```csharp
int a = 123;
System.Int32 b = 123;
```

O valor padrão de cada tipo integral é zero, `0`. Cada um dos tipos integrais possui as constantes `MinValue` e `MaxValue` que fornecem o valor mínimo e máximo desse tipo.

Use a estrutura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> para representar um inteiro com sinal sem nenhum limite superior ou inferior.

## <a name="integer-literals"></a>Literais inteiros

Literais inteiros podem ser

- *decimal*: sem nenhum prefixo
- *hexadecimal*: com o prefixo de `0x` ou `0X`
- *Binary*: com o prefixo `0b` ou `0B` (disponível em C# 7,0 e posterior)

O código a seguir demonstra um exemplo de cada um:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

O exemplo anterior também mostra o uso de `_` como um *separador de dígito*, que tem C# suporte a partir de 7,0. Você pode usar o separador de dígitos com todos os tipos de literais numéricos.

O tipo de um inteiro literal é determinado por seu sufixo da seguinte maneira:

- Se o literal não tiver nenhum sufixo, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `int`, `uint`, `long` `ulong`.
- Se o literal for sufixado por `U` ou `u`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `uint` `ulong`.
- Se o literal for sufixado por `L` ou `l`, seu tipo será o primeiro dos seguintes tipos em que seu valor pode ser representado: `long` `ulong`.

  > [!NOTE]
  > Você pode usar a letra minúscula `l` como um sufixo. No entanto, isso gera um aviso do compilador porque a letra `l` pode ser confundida com o `1` de dígitos. Use `L` para maior clareza.

- Se o literal for sufixado por `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` ou `lu`, seu tipo será `ulong`.

Se o valor representado por um literal inteiro exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md).

O valor representado por um inteiro literal pode ser convertido implicitamente em um tipo com um intervalo menor do que o tipo determinado do literal. Isso é possível quando o valor está dentro do intervalo do tipo de destino:

```csharp
byte a = 17;
byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
```

Como mostra o exemplo anterior, se o valor do literal não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031](../../misc/cs0031.md) .

Você também pode usar uma conversão para converter o valor representado por um literal inteiro para o tipo diferente do tipo determinado do literal:

```csharp
var signedByte = (sbyte)42;
var longVariable = (long)42;
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita (chamada de *conversão de ampliação*) entre quaisquer dois tipos integrais, nos quais o tipo de destino pode armazenar todos os valores do tipo de origem. Por exemplo, há uma conversão implícita de `int` até `long` porque o intervalo dos valores de `int` é um subconjunto adequado de `long`. Não há conversões implícitas de um tipo integral sem sinal menor para um tipo integral com sinal maior. Também há uma conversão implícita de qualquer tipo integral para qualquer tipo de ponto flutuante.  Não há conversões implícitas de qualquer tipo integral com sinal para qualquer tipo integral sem sinal.

Você deverá usar uma conversão explícita para converter um tipo integral em outro tipo integral quando uma conversão implícita não for definida por meio do tipo de fonte para o tipo de destino. Isso é chamado de *conversão de estreitamento*. O caso explícito é necessário porque a conversão pode resultar em perda de dados.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Tipos integrais](~/_csharplang/spec/types.md#integral-types)
- [Literais inteiros](~/_csharplang/spec/lexical-structure.md#integer-literals)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Tipos de ponto flutuante](floating-point-numeric-types.md)
- [Tabela de valores padrão](../keywords/default-values-table.md)
- [Tabela de formatação de resultados numéricos](../keywords/formatting-numeric-results-table.md)
- [Tabela de tipos internos](../keywords/built-in-types-table.md)
- [Numéricos no .NET](../../../standard/numerics.md)

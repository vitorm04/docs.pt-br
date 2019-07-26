---
title: Tipos numéricos integrais – Referência C#
description: Saiba o intervalo, o tamanho de armazenamento e os usos para cada um dos tipos numéricos integrais.
ms.date: 06/25/2019
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
ms.openlocfilehash: dfb1298abaff0cfe8eae7536f94511a30012a4a9
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236085"
---
# <a name="integral-numeric-types--c-reference"></a>Tipos numéricos integrais (Referência C#)

Os **tipos numéricos integrais** são um subconjunto de **tipos simples** e podem ser inicializados com [*literais*](#integral-literals). Todos os tipos integrais também são tipos de valor. Todos os tipos numéricos integrais dão suporte a operadores [aritméticos](../operators/arithmetic-operators.md), [bit a bit lógicos](../operators/bitwise-and-shift-operators.md), de [comparação e igualdade](../operators/equality-operators.md).

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

## <a name="integral-literals"></a>Literais integrais

Os literais integrais podem ser especificados como *literais decimais*, *literais hexadecimais* ou *literais binários*. Abaixo, um exemplo de cada:

```csharp
var decimalLiteral = 42;
var hexLiteral = 0x2A;
var binaryLiteral = 0b_0010_1010;
```

Literais decimais não exigem nenhum prefixo. O prefixo `x` ou `X` significa um *literal hexadecimal*. O prefixo `b` ou `B` significa um *literal binário*. A declaração de `binaryLiteral` demonstra o uso de `_` como um *separador de dígito*. O separador de dígito pode ser usado com todos os literais numéricos. Os literais binários e o separador de dígitos `_` são compatíveis a partir do C# 7.0.

### <a name="literal-suffixes"></a>Sufixos literais

O sufixo `l` ou `L` especifica que o literal integral deve ser do tipo `long`. O sufixo `ul` ou `UL` especifica o tipo `ulong`. Se o sufixo `L` for usado em um literal maior que 9.223.372.036.854.775.807 (o valor máximo de `long`), o valor será convertido para o tipo `ulong`. Se o valor representado por um literal integral exceder <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilador [CS1021](../../misc/cs1021.md). 

> [!NOTE]
> Você pode usar a letra minúscula "l" como sufixo. No entanto, isso gera um aviso do compilador porque a letra "l" é facilmente confundida com o dígito "1". Use "L" para fins de clareza.

### <a name="type-of-an-integral-literal"></a>Tipo de um literal integral

Se um literal integral não tiver sufixo, seu tipo será o primeiro dos tipos a seguir em que seu valor pode ser representado:

1. `int`
1. `uint`
1. `long`
1. `ulong`

Você pode converter um literal integral em um tipo com um intervalo menor que o padrão usando uma atribuição ou uma conversão:

```csharp
byte byteVariable = 42; // type is byte
var signedByte = (sbyte)42; // type is sbyte.
```

Você pode converter um literal integral em um tipo com um intervalo maior que o padrão usando uma atribuição, uma conversão ou um sufixo no literal:

```csharp
var unsignedLong = 42UL;
var longVariable = 42L;
ulong anotherUnsignedLong = 42;
var anotherLong = (long)42;
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita (chamada de *conversão de ampliação*) entre quaisquer dois tipos integrais, nos quais o tipo de destino pode armazenar todos os valores do tipo de origem. Por exemplo, há uma conversão implícita de `int` até `long` porque o intervalo dos valores de `int` é um subconjunto adequado de `long`. Não há conversões implícitas de um tipo integral sem sinal menor para um tipo integral com sinal maior. Também há uma conversão implícita de qualquer tipo integral para qualquer tipo de ponto flutuante.  Não há conversões implícitas de qualquer tipo integral com sinal para qualquer tipo integral sem sinal.

Você deverá usar uma conversão explícita para converter um tipo integral em outro tipo integral quando uma conversão implícita não for definida por meio do tipo de fonte para o tipo de destino. Isso é chamado de *conversão de estreitamento*. O caso explícito é necessário porque a conversão pode resultar em perda de dados.

## <a name="see-also"></a>Consulte também

- [Especificação da linguagem C# – Tipos integrais](~/_csharplang/spec/types.md#integral-types)
- [Referência de C#](../index.md)
- [Tipos de ponto flutuante](floating-point-numeric-types.md)
- [Tabela de valores padrão](../keywords/default-values-table.md)
- [Tabela de formatação de resultados numéricos](../keywords/formatting-numeric-results-table.md)
- [Tabela de tipos internos](../keywords/built-in-types-table.md)
- [Numéricos no .NET](../../../standard/numerics.md)

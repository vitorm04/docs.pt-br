---
title: Palavra-chave ushort – Referência de C#
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614448"
---
# <a name="ushort-c-reference"></a>ushort (Referência de C#)

A palavra-chave `ushort` indica um tipo de dados integrais que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.

|Tipo|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`ushort`|0 a 65.535|Inteiro de 16 bits sem sinal|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a>Literais

Você pode declarar e inicializar uma variável `ushort` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário. Se o literal inteiro estiver fora do intervalo de `ushort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 65.034 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](int.md) para `ushort`.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade:

- O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.
- O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo. Um literal decimal não pode ter um sublinhado à esquerda.

Alguns exemplos são mostrados abaixo.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a>Resolução de sobrecarga do compilador

Uma conversão deve ser usada ao chamar métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `ushort` e [int](int.md):

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

O uso da conversão `ushort` garante que o tipo correto será chamado, por exemplo:

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita predefinida de `ushort` para [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md) ou [decimal](decimal.md).

Há uma conversão implícita predefinida de [byte](byte.md) ou [char](char.md) para `ushort`. Caso contrário, uma conversão deve ser usada para executar uma conversão explícita. Considere, por exemplo, as duas variáveis `ushort` `x` e `y` a seguir:

```csharp
ushort x = 5, y = 12;
```

A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

Para corrigir esse problema, use uma conversão:

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:

```csharp
int m = x + y;
long n = x + y;
```

Observe também que não há conversão implícita de tipos de ponto flutuante em `ushort`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](float.md) e [double](double.md).

Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, veja [Tipos integrais](~/_csharplang/spec/types.md#integral-types) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- <xref:System.UInt16>
- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tabela de tipos integrais](integral-types-table.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md)
- [Tabela de conversões numéricas explícitas](explicit-numeric-conversions-table.md)

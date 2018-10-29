---
title: short (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0d90f31da49b94eee490e95f0cdf1d582bb0b059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184147"
---
# <a name="short-c-reference"></a>short (Referência de C#)

`short` indica um tipo de dados integrais que armazena valores de acordo com o tamanho e o intervalo mostrados na tabela a seguir.

|Tipo|Intervalo|Tamanho|Tipo .NET|
|----------|-----------|----------|-------------------------|
|`short`|-32.768 a 32.767|Inteiro de 16 bits com sinal|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a>Literais

Você pode declarar e inicializar uma variável `short` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário.  Se o literal inteiro estiver fora do intervalo de `short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 1.034 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](int.md) para `short`.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade.

- O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.
- O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo. Um literal decimal não pode ter um sublinhado à esquerda.

Alguns exemplos são mostrados abaixo.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a>Resolução de sobrecarga do compilador

Uma conversão deve ser usada ao chamar métodos sobrecarregados. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `short` e [int](int.md):

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

O uso da conversão `short` garante que o tipo correto será chamado, por exemplo:

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a>Conversões

Há uma conversão implícita predefinida de `short` em [int](int.md), [longo](long.md), [float](float.md), [duplo](double.md) ou [decimal](decimal.md).

Não é possível converter implicitamente tipos numéricos não literais com tamanho de armazenamento maior em `short` (consulte a [Tabela de tipos integrais](integral-types-table.md) para ver os tamanhos de armazenamento de tipos integrais). Considere, por exemplo, as duas variáveis `short` `x` e `y` a seguir:

```csharp
short x = 5, y = 12;
```

A instrução de atribuição a seguir produz um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como [int](int.md) por padrão.

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

Para corrigir esse problema, use uma conversão:

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

Também é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:

```csharp
int m = x + y;
long n = x + y;
```

Não há nenhuma conversão implícita de tipos de ponto flutuante para `short`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](float.md) e [double](double.md).

Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- <xref:System.Int16>
- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tabela de tipos integrais](integral-types-table.md)
- [Tabela de tipos internos](built-in-types-table.md)
- [Tabela de conversões numéricas implícitas](implicit-numeric-conversions-table.md)
- [Tabela de conversões numéricas explícitas](explicit-numeric-conversions-table.md)
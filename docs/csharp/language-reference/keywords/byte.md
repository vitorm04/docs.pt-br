---
title: byte (Referência de C#)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 28acbe67b85637550fdb1f5e290a9abb60bf5c65
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027883"
---
# <a name="byte-c-reference"></a>byte (Referência de C#)

`byte` indica um tipo integral que armazena valores conforme indicado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 a 255|Inteiro de 8 bits sem sinal|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literais  

 Você pode declarar e inicializar uma variável `byte` atribuindo a ela um literal decimal, um literal hexadecimal ou (começando com o C# 7.0) um literal binário. Se o literal inteiro estiver fora do intervalo de `byte` (ou seja, se for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 201 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `byte`.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7.0, alguns recursos foram adicionados para melhorar a legibilidade. 
 - O C# 7.0 permite o uso do caractere de sublinhado, `_`, como um separador de dígito.
 - O C# 7.2 permite que `_` seja usado como separador de dígito de um literal binário ou hexadecimal, após o prefixo. Um literal decimal não pode ter um sublinhado à esquerda.

Alguns exemplos são mostrados abaixo.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `byte` para [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Você não pode converter implicitamente para `byte` os tipos numéricos não literais de tamanho de armazenamento maior. Para obter mais informações sobre os tamanhos de armazenamento de tipos integrais, consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md). Considere, por exemplo, as duas variáveis `byte` `x` e `y` a seguir:  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Para corrigir esse problema, use uma conversão:  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Além disso, não há conversão implícita de tipos de ponto flutuante em `byte`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Ao chamar métodos sobrecarregados, uma conversão deve ser usada. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `byte` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 O uso da conversão `byte` garante que o tipo correto será chamado, por exemplo:  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Byte>  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

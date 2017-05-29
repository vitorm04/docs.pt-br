---
title: "byte (Referência de C#) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 57c4b1c7ead9386ff4067da5915a55a79f5e562e
ms.openlocfilehash: fce94687cbf055219913758d49642c8e4a999db3
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="byte-c-reference"></a>byte (Referência de C#)

`byte` indica um tipo integral que armazena valores conforme indicado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 a 255|Inteiro de 8 bits sem sinal|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a>Literais  

 Você pode declarar e inicializar uma variável `byte` atribuindo um literal decimal, um literal hexadecimal ou (começando com C# 7) um literal binário a ela. Se o literal inteiro estiver fora do intervalo de `byte` (ou seja, se ele for menor que <xref:System.Byte.MinValue?displayProperty=fullName> ou maior que <xref:System.Byte.MaxValue?displayProperty=fullName>, ocorrerá um erro de compilação.

No exemplo a seguir, inteiros iguais a 201 representados como literais decimais, hexadecimais e binários são implicitamente convertidos de valores [int](../../../csharp/language-reference/keywords/int.md) para `byte`.    
  
[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Use o prefixo `0x` ou `0X` para indicar um literal hexadecimal e o prefixo `0b` ou `0B` para indicar um literal binário. Literais decimais não têm nenhum prefixo.

Começando com o C# 7, você também pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.

[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Conversões  
 Há uma conversão implícita predefinida de `byte` para [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Você não pode converter implicitamente para `byte` os tipos numéricos não literais de tamanho de armazenamento maior. Para obter mais informações sobre os tamanhos de armazenamento de tipos integrais, consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md). Considere, por exemplo, as duas variáveis `byte` `x` e `y` a seguir:  
  
```  
  
byte x = 10, y = 20;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Para corrigir esse problema, use uma conversão:  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 No entanto, é possível usar as instruções a seguir, em que a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Além disso, não há conversão implícita de tipos de ponto flutuante em `byte`. Por exemplo, a instrução a seguir gerará um erro de compilador, a menos que uma conversão explícita seja usada:  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Ao chamar métodos sobrecarregados, uma conversão deve ser usada. Considere, por exemplo, os seguintes métodos sobrecarregados que usam os parâmetros `byte` e [int](../../../csharp/language-reference/keywords/int.md):  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 O uso da conversão `byte` garante que o tipo correto será chamado, por exemplo:  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Para obter informações sobre expressões aritméticas com tipos de ponto flutuante mistos e tipos integrais, consulte [float](../../../csharp/language-reference/keywords/float.md) e [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre as regras de conversão numérica implícita, consulte a [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Byte>   
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

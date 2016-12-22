---
title: "byte (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "byte"
  - "byte_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave byte [C#]"
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# byte (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `byte` palavra\-chave denota um tipo integral que armazena valores conforme indicado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`byte`|0 a 255|Inteiro de 8 bits sem\-sinal|<xref:System.Byte?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `byte` variável semelhante ao exemplo:  
  
```  
byte myByte = 255;  
```  
  
 Na declaração precedente, a literal inteira `255` é convertido implicitamente de  [int](../../../csharp/language-reference/keywords/int.md) para `byte`.  Se a literal inteira excede o intervalo de `byte`, ocorrerá um erro de compilação.  
  
## Conversões  
 Há uma conversão implícita predefinida de `byte` para  [curto](../../../csharp/language-reference/keywords/short.md),  [ushort](../../../csharp/language-reference/keywords/ushort.md),  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md),  [longo](../../../csharp/language-reference/keywords/long.md),  [ulong](../../../csharp/language-reference/keywords/ulong.md),  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Você não pode converter implicitamente não literal tipos numéricos de maior tamanho de armazenamento para `byte`.  Para obter mais informações sobre os tamanhos de armazenamento de tipos integrais, consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md).  Considere, por exemplo, os dois seguintes `byte` variáveis de `x` e `y`:  
  
```  
  
byte x = 10, y = 20;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Para corrigir esse problema, use um cast:  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 É possível no entanto, usar as instruções a seguir onde a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho de armazenamento maior:  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Além disso, não há nenhuma conversão implícita de tipos de ponto flutuante para `byte`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Ao chamar métodos sobrecarregados um cast deve ser usado.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `byte` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Usando o `byte` cast garante que o tipo correto é chamado, por exemplo:  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Byte>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
---
title: "ushort (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "ushort"
  - "ushort_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave ushort [C#]"
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ushort (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `ushort` palavra\-chave indica um tipo de dados integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`ushort`|0 a 65,535|Inteiro de 16 bits sem\-sinal|<xref:System.UInt16?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `ushort` variável, como neste exemplo:  
  
```  
  
ushort myShort = 65535;  
```  
  
 Na declaração anterior, o inteiro literal `65535` é convertido implicitamente de  [int](../../../csharp/language-reference/keywords/int.md) para `ushort`.  Se a literal inteira excede o intervalo de `ushort`, ocorrerá um erro de compilação.  
  
 Uma conversão deve ser usada ao chamar métodos sobrecarregados.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `ushort` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
  
 Usando o `ushort` cast garante que o tipo correto é chamado, por exemplo:  
  
```  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## Conversões  
 Há uma conversão implícita predefinida de `ushort` para  [int](../../../csharp/language-reference/keywords/int.md),  [uint](../../../csharp/language-reference/keywords/uint.md),  [longo](../../../csharp/language-reference/keywords/long.md),  [ulong](../../../csharp/language-reference/keywords/ulong.md),  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Há uma conversão implícita predefinida de  [bytes](../../../csharp/language-reference/keywords/byte.md) ou  [char](../../../csharp/language-reference/keywords/char.md) para `ushort`.  Caso contrário, a projeção de deve ser usada para executar uma conversão explícita.  Considere, por exemplo, os dois seguintes `ushort` variáveis de `x` e `y`:  
  
```  
  
ushort x = 5, y = 12;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como `int` por padrão.  
  
```  
  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Para corrigir esse problema, use um cast:  
  
```  
  
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 No entanto é possível usar as instruções a seguir, onde a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho maior de armazenamento:  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 Observe também que não há nenhuma conversão implícita de tipos de ponto flutuante para `ushort`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.UInt16>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
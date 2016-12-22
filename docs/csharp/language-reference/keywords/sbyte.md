---
title: "sbyte (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "sbyte_CSharpKeyword"
  - "sbyte"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave sbyte [C#]"
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# sbyte (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `sbyte` palavra\-chave indica o tipo integral que armazena valores de acordo com o tamanho e o intervalo, mostrado na tabela a seguir.  
  
|Tipo|Intervalo|Tamanho|Tipo .NET Framework|  
|----------|---------------|-------------|-------------------------|  
|`sbyte`|\-128 a 127|Inteiro assinado de 8 bits|<xref:System.SByte?displayProperty=fullName>|  
  
## Literais  
 Você pode declarar e inicializar um `sbyte` variável dessa maneira:  
  
```  
  
sbyte sByte1 = 127;  
```  
  
 A declaração anterior, o inteiro literal 127 implicitamente é convertido de  [int](../../../csharp/language-reference/keywords/int.md) para `sbyte`.  Se a literal inteira excede o intervalo de `sbyte`, ocorrerá um erro de compilação.  
  
 Uma conversão deve ser usada quando chamada sobrecarregado métodos.  Considere, por exemplo, o seguinte sobrecarregado métodos que usam `sbyte` e  [int](../../../csharp/language-reference/keywords/int.md) parâmetros:  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Usando o `sbyte` cast garante que o tipo correto é chamado, por exemplo:  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## Conversões  
 Há uma conversão implícita predefinida de `sbyte` para  [curto](../../../csharp/language-reference/keywords/short.md),  [int](../../../csharp/language-reference/keywords/int.md),  [longo](../../../csharp/language-reference/keywords/long.md),  [float](../../../csharp/language-reference/keywords/float.md),  [double](../../../csharp/language-reference/keywords/double.md), ou  [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Você não pode converter implicitamente nonliteral tipos numéricos de maior tamanho de armazenamento para `sbyte` \(consulte [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md) para os tamanhos de armazenamento dos tipos integrais\).  Considere, por exemplo, os dois seguintes `sbyte` variáveis de `x` e `y`:  
  
```  
  
sbyte x = 10, y = 20;  
```  
  
 A seguinte instrução de atribuição produzirá um erro de compilação, porque a expressão aritmética no lado direito do operador de atribuição é avaliada como  [int](../../../csharp/language-reference/keywords/int.md) por padrão.  
  
```  
  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Para corrigir esse problema, converta a expressão, como no exemplo a seguir:  
  
```  
  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 No entanto é possível usar as instruções a seguir, onde a variável de destino tem o mesmo tamanho de armazenamento ou um tamanho maior de armazenamento:  
  
```  
  
        sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Observe também que não há nenhuma conversão implícita de tipos de ponto flutuante para `sbyte`.  Por exemplo, a instrução a seguir gera um erro do compilador, a menos que seja usada uma conversão explícita:  
  
```  
  
        sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Para obter informações sobre expressões aritméticas com tipos mistos de ponto flutuante e tipos integrais, consulte  [float](../../../csharp/language-reference/keywords/float.md) e  [double](../../../csharp/language-reference/keywords/double.md).  
  
 Para obter mais informações sobre regras de conversão numérica implícito, consulte o [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.SByte>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
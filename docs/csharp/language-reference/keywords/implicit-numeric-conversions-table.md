---
title: "Tabela de convers&#245;es num&#233;ricas impl&#237;citas (Refer&#234;ncia de C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversões [C#], numéricas implícitas"
  - "conversões numéricas implícitas [C#]"
  - "conversões numéricas [C#], implícito"
  - "tipos [C#], conversões numéricas implícitas"
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tabela de convers&#245;es num&#233;ricas impl&#237;citas (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir mostra as conversões de numéricas implícitas predefinidas.  Podem ocorrer conversões implícitas em muitas situações, incluindo instruções de atribuição e invocar o método.  
  
|From|Para|  
|----------|----------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, or`decimal`|  
|[Byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or`decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, ou `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, or`decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, ou `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, ou `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, ou `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or`decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, or`decimal`|  
  
## Comentários  
  
-   Precisão, mas não a magnitude pode ser perdido em conversões de `int`, `uint`, `long`, ou `ulong` para `float` de `long` ou `ulong` para `double`.  
  
-   Não há nenhum conversões implícitas para o `char` tipo.  
  
-   Não há nenhuma conversão implícita entre tipos de ponto flutuante e o `decimal` tipo.  
  
-   Uma expressão constante do tipo `int` pode ser convertido em `sbyte`, `byte`, `short`, `ushort`, `uint`, ou `ulong`, desde que o valor da expressão constante está dentro do intervalo do tipo de destino.  
  
## Especificação de linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Conversões cast e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
---
title: "char (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "char"
  - "char_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tipo de dados char [C#]"
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# char (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A palavra\-chave de `char` é usada para declarar uma instância da estrutura de <xref:System.Char?displayProperty=fullName> que o.NET Framework usa para representar um caractere Unicode.  O valor de um objeto de `Char` é um valor numérico de 16 bits \(de ordinal\).  
  
 Os caracteres Unicode são usados para representar em todo o mundo a maioria dos idiomas gravados.  
  
|Tipo|Intervalo|Size \(Tamanho\)|tipo do .NET Framework|  
|----------|---------------|----------------------|----------------------------|  
|`char`|Desde U\+FFFF a|Caractere de 16 bits Unicode|<xref:System.Char?displayProperty=fullName>|  
  
## Literais  
 Constantes de tipo de `char` podem ser gravadas como literais de caracteres, a sequência de escape a representação hexadecimal, ou Unicode.  Você também pode converter os códigos de caracteres inteiros.  Nas variáveis de `char` de exemplo quatro são inicializados com o mesmo caractere `X`:  
  
 [!CODE [csrefKeywordsTypes#19](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#19)]  
  
## Conversões  
 `char` pode ser convertida implicitamente para [ushort](../../../csharp/language-reference/keywords/ushort.md), a [int](../../../csharp/language-reference/keywords/int.md), a [uint](../../../csharp/language-reference/keywords/uint.md), a [long](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md), a [float](../../../csharp/language-reference/keywords/float.md), a [double](../../../csharp/language-reference/keywords/double.md), ou a [decimal](../../../csharp/language-reference/keywords/decimal.md).  No entanto, não há nenhuma conversão implícita de outros tipos para o tipo de `char` .  
  
 O tipo de <xref:System.Char?displayProperty=fullName> fornece vários métodos estáticos para trabalhar com valores de `char` .  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 <xref:System.Char>   
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Tipos anuláveis](../../../csharp/programming-guide/nullable-types/index.md)   
 [Cadeias de caracteres](../../../csharp/programming-guide/strings/index.md)
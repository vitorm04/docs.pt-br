---
title: "Tabela de tipos internos (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "tipos C# internos"
  - "tipos [C#], internos"
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tabela de tipos internos (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir mostra as palavras\-chave para C\# tipos internos, que são aliases dos tipos predefinidos na <xref:System> espaço para nome.  
  
|Tipo de C\#|.NET Framework tipo|  
|-----------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[Byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## Comentários  
 Todos os tipos na tabela, exceto `object` e `string`, são conhecidas como tipos simples.  
  
 As palavras\-chave C\# tipo e seus aliases são intercambiáveis.  Por exemplo, você pode declarar uma variável integer, usando uma das seguintes declarações:  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Para exibir o tipo real para qualquer tipo de C\#, use o método de sistema `GetType()`.  Por exemplo, a instrução a seguir exibe o alias do sistema que representa o tipo de `myVariable`:  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Você também pode usar o  [typeof](../../../csharp/language-reference/keywords/typeof.md) operador.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tabela de formatação de resultados numéricos](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
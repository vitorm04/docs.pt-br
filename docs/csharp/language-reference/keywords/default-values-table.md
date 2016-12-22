---
title: "Tabela de valores padr&#227;o (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "construtores [c#], valores de retorno"
  - "palavras-chave [c#], novas"
  - "construtor padrão [C#]"
  - "padrões [C#]"
  - "tipos de valor [c#], inicializando"
  - "variáveis [c#], tipos de valor"
  - "construtores [c#], o construtor padrão"
  - "valores de retorno de tipos [c#], o construtor padrão"
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tabela de valores padr&#227;o (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir mostra os valores padrão dos tipos de valores retornados pelos construtores padrão.  Os construtores padrão são chamados usando o operador de `new` , como segue:  
  
```  
int myInt = new int();  
```  
  
 A declaração anterior tem o mesmo efeito que a instrução a seguir:  
  
```  
int myInt = 0;  
```  
  
 Lembre\-se que usar variáveis não inicializada em C\# não é concedida.  
  
|Tipos de valor|Valor padrão|  
|--------------------|------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`false`|  
|[Byte](../../../csharp/language-reference/keywords/byte.md)|0|  
|[char](../../../csharp/language-reference/keywords/char.md)|'\\0'|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|0.0M|  
|[double](../../../csharp/language-reference/keywords/double.md)|0.0D|  
|[enum](../../../csharp/language-reference/keywords/enum.md)|O valor gerado pela expressão E \(0\), E onde é o identificador enum.|  
|[float](../../../csharp/language-reference/keywords/float.md)|0.0F|  
|[int](../../../csharp/language-reference/keywords/int.md)|0|  
|[long](../../../csharp/language-reference/keywords/long.md)|0L|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|0|  
|[short](../../../csharp/language-reference/keywords/short.md)|0|  
|[estrutura](../../../csharp/language-reference/keywords/struct.md)|O valor gerado definindo todos os campos de tipo de valor para seus valores padrão e todos os campos de tipo da `null`.|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|0|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|0|  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Tabela de tipos de valor](../../../csharp/language-reference/keywords/value-types-table.md)   
 [Tipos de valor](../../../csharp/language-reference/keywords/value-types.md)   
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
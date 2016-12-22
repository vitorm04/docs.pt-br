---
title: "Como determinar se uma cadeia de caracteres representa um valor num&#233;rico (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "cadeias de caracteres numéricas [C#]"
  - "cadeias de caracteres [C#], numérico"
  - "validando entrada numérica [C#]"
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como determinar se uma cadeia de caracteres representa um valor num&#233;rico (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Para determinar se uma seqüência de caracteres é uma representação válida de um tipo numérico especificado, use estática `TryParse` método que é implementado por todos os tipos numéricos primitivos e também por tipos como <xref:System.DateTime> e <xref:System.Net.IPAddress>.  O exemplo a seguir mostra como determinar se "108" é um válido  [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Se a seqüência de caracteres contém caracteres não numéricos ou o valor numérico é muito grande ou muito pequeno para o tipo específico que você especificou, `TryParse` retorna false e define o parâmetro de saída como zero.  Caso contrário, ele retorna true e define o parâmetro de saída para o valor numérico da seqüência de caracteres.  
  
> [!NOTE]
>  Uma seqüência pode conter somente caracteres numéricos e ainda não seja válido para o tipo cuja `TryParse` método que você usar.  Por exemplo, "256" não é um valor válido para `byte` , mas ele é válido para `int`. "  98,6 "não é um valor válido para `int` , mas ele é válido `decimal`.  
  
## Exemplo  
 Os exemplos a seguir mostram como usar `TryParse` com representações de strings de `long`, `byte`, e `decimal` valores.  
  
 [!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## Programação robusta  
 Tipos de primitivo numérico também implementar a `Parse` método estático, que lança uma exceção se a seqüência de caracteres não é um número válido.  `TryParse`é geralmente mais eficiente porque ele simplesmente retornará false se o número não é válido.  
  
## Segurança do .NET Framework  
 Sempre use o `TryParse` ou `Parse` métodos para validar entrada do usuário de controles como caixas de texto e caixas de combinação.  
  
## Consulte também  
 [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)   
 [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)   
 [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)   
 [Analisando cadeias de caracteres numéricas](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)   
 [Formatando tipos](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)
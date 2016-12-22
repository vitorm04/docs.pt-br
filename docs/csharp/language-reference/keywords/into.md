---
title: "into (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "into_CSharpKeyword"
  - "into"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "palavra-chave into [C#]"
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# into (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O `into` palavra\-chave contextual que pode ser usado para criar um identificador temporário para armazenar os resultados de uma  [grupo](../../../csharp/language-reference/keywords/group-clause.md),  [associação](../../../csharp/language-reference/keywords/join-clause.md) ou  [Selecionar](../../../csharp/language-reference/keywords/select-clause.md) cláusula em um novo identificador.  Esse identificador pode ser um gerador para comandos de consulta adicionais.  Quando usado em um `group` ou `select` cláusula, o uso de um novo identificador é às vezes chamado de um  *continuação*.  
  
## Exemplo  
 O exemplo a seguir mostra o uso da `into` palavra\-chave para permitir que um identificador temporário `fruitGroup` que tem um tipo inferido do `IGrouping`.  Usando o identificador, você pode chamar o <xref:System.Linq.Enumerable.Count%2A> método em cada grupo e selecione apenas os grupos que contêm duas ou mais palavras.  
  
 [!CODE [cscsrefQueryKeywords#18](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#18)]  
  
 O uso de `into` em um `group` cláusula só é necessária quando você deseja realizar operações de consulta adicionais em cada grupo.  Para obter mais informações, consulte [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Para obter um exemplo do uso de `into` em um `join` cláusula, consulte [Cláusula join](../../../csharp/language-reference/keywords/join-clause.md).  
  
## Consulte também  
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)
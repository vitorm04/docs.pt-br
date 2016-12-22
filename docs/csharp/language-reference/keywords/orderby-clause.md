---
title: "Cl&#225;usula orderby (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "orderby"
  - "orderby_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cláusula orderby [C#]"
  - "palavra-chave orderby [C#]"
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cl&#225;usula orderby (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em uma expressão de consulta, o `orderby` cláusula faz com que a seqüência retornada ou o subsequence \(grupo\) a ser classificado em crescente ou decrescente.  Várias chaves podem ser especificadas para realizar uma ou mais operações de classificação secundária.  A classificação é realizada pelo comparador padrão para o tipo do elemento.  A ordem de classificação padrão é crescente.  Você também pode especificar um comparador personalizado.  No entanto, ele só está disponível usando a sintaxe do método.  Para obter mais informações, consulte [Classificando dados](../../../visual-basic/programming-guide/concepts/linq/sorting-data.md).  
  
## Exemplo  
 No exemplo a seguir, a primeira consulta classifica as palavras em ordem alfabética, a partir de um e segunda consulta classifica as mesmas palavras em ordem decrescente.  \(O `ascending` palavra\-chave é o valor de classificação padrão e pode ser omitido.\)  
  
 [!CODE [cscsrefQueryKeywords#20](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#20)]  
  
## Exemplo  
 O exemplo a seguir executa uma classificação primária no sobrenomes dos alunos e, em seguida, uma ordenação secundária em seus nomes.  
  
 [!CODE [cscsrefQueryKeywords#22](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#22)]  
  
## Comentários  
 Em tempo de compilação, o `orderby` cláusula é traduzida como uma chamada para o <xref:System.Linq.Enumerable.OrderBy%2A> método.  Várias chaves de `orderby` cláusula se traduzem em <xref:System.Linq.Enumerable.ThenBy%2A> chamadas de método.  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Cláusula group](../../../csharp/language-reference/keywords/group-clause.md)   
 [Introdução a LINQ em C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
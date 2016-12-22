---
title: "Cl&#225;usula let (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "let_CSharpKeyword"
  - "let"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "cláusula let [C#]"
  - "palavra-chave let [C#]"
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cl&#225;usula let (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em uma expressão de consulta, às vezes é útil armazenar o resultado de uma subexpressão para usá\-lo em cláusulas subseqüentes.  Você pode fazer isso com o `let` palavra\-chave, que cria uma nova variável de intervalo e o inicializa com o resultado da expressão você fornecer.  Uma vez inicializado com um valor, a variável de intervalo não pode ser usada para armazenar o valor de outro.  No entanto, se a variável de intervalo contém um tipo que podem ser consultado, ele pode ser consultado.  
  
## Exemplo  
 No exemplo a seguir `let` é usado de duas maneiras:  
  
1.  Para criar um tipo de enumerable propriamente dito pode ser consultado.  
  
2.  Para habilitar a consulta chamar `ToLower` somente uma vez na variável de intervalo `word`.  Sem usar `let`, você teria chame `ToLower` em cada predicado na `where` cláusula.  
  
 [!CODE [cscsrefQueryKeywords#28](../CodeSnippet/VS_Snippets_VBCSharp/CsCsrefQueryKeywords#28)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Palavras\-chave de consulta \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressões de consulta LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Introdução a LINQ em C\#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Como manipular exceções em expressões de consulta](../Topic/How%20to:%20Handle%20Exceptions%20in%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md)
---
title: "A vari&#225;vel de intervalo &lt;variable&gt; oculta uma vari&#225;vel em um bloco delimitador, uma vari&#225;vel de intervalo definida anteriormente ou uma vari&#225;vel declarada implicitamente em uma express&#227;o de consulta | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36633"
  - "vbc36633"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36633"
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel de intervalo &lt;variable&gt; oculta uma vari&#225;vel em um bloco delimitador, uma vari&#225;vel de intervalo definida anteriormente ou uma vari&#225;vel declarada implicitamente em uma express&#227;o de consulta
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um nome de variável de intervalo especificado cláusula `Select`, `From`, `Aggregate` ou `Let` duplica o nome de uma variável já especificado na consulta, ou o nome de uma variável que é declarada implicitamente pela consulta, como um nome de campo ou o nome de uma função agregada.  
  
 **Identificação do erro:**  BC36633  
  
### Para corrigir este erro  
  
-   Garanta que todas as variáveis de intervalo num escopo de consulta em particular têm nomes únicos.  Você pode delimitar a consulta entre parênteses para garantir que consultas aninhadas têm um escopo único.  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Cláusula From](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Cláusula Let](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Cláusula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
---
title: "&#39;&lt;keyword&gt;&#39; s&#243; &#233; valido dentro de um m&#233;todo de inst&#226;ncia | Microsoft Docs"
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
  - "bc30043"
  - "vbc30043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30043"
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;keyword&gt;&#39; s&#243; &#233; valido dentro de um m&#233;todo de inst&#226;ncia
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

As palavras\-chave `Me`, `MyClass` e `MyBase` referem\-se a instâncias de classe específicas.  Você não pode usá\-las dentro de um procedimento compartilhado `Function` ou `Sub`.  
  
 **Identificação do erro:**  BC30043  
  
### Para corrigir este erro  
  
-   Remova a palavra\-chave do procedimento, ou remova a palavra\-chave `Shared` da declaração de procedimento.  
  
## Consulte também  
 [Atribuição de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
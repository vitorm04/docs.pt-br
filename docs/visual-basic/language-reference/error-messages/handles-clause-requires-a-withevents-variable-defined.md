---
title: "A cl&#225;usula de identificadores requer uma vari&#225;vel WithEvents definida no tipo recipiente ou em um de seus tipos base | Microsoft Docs"
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
  - "vbc30506"
  - "bc30506"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30506"
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A cl&#225;usula de identificadores requer uma vari&#225;vel WithEvents definida no tipo recipiente ou em um de seus tipos base
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você não forneceu uma variável `WithEvents` na sua cláusula `Handles`.  A palavra\-chave `Handles` no fim da declaração de um procedimento faz com que ele manipule eventos causados por uma variável de objeto declarada usando a palavra\-chave `WithEvents`.  
  
 **Identificação do erro:**  BC30506  
  
### Para corrigir este erro  
  
-   Forneça a variável `WithEvents` necessária.  
  
## Consulte também  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
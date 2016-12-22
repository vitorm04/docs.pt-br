---
title: "Instru&#231;&#227;o &#39;Class&#39; deve finalizar com &#39;End Class&#39; correspondente | Microsoft Docs"
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
  - "vbc30481"
  - "bc30481"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30481"
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o &#39;Class&#39; deve finalizar com &#39;End Class&#39; correspondente
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Class` é usado para iniciar um bloco `Class`; portanto, ele só pode aparecer no início do bloco, com uma instrução `End Class` correspondente terminando o bloco.  Ou você tem uma instrução `Class` redundante, ou você não encerrou seu bloco `Class` com `End Class`.  
  
 **Identificação do erro:**  BC30481  
  
### Para corrigir este erro  
  
-   Localize e remova a instrução `Class` desnecessária.  
  
-   Conclua o bloco `Class` com um `End Class` correspondente.  
  
## Consulte também  
 [Instrução End \<keyword\>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
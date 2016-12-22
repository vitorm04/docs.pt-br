---
title: "As classes derivadas n&#227;o podem acionar eventos de classe base | Microsoft Docs"
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
  - "vbc30029"
  - "bc30029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30029"
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As classes derivadas n&#227;o podem acionar eventos de classe base
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um evento pode ser gerado apenas a partir do espaço de declaração na qual ele é declarado.  Portanto, uma classe não pode disparar eventos de qualquer outra classe, até mesmo uma da qual ela é derivado.  
  
 **Identificação do erro:**  BC30029  
  
### Para corrigir este erro  
  
-   Mova a declaração `Event` ou a declaração `RaiseEvent`, de modo que elas fiquem na mesma classe.  
  
## Consulte também  
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
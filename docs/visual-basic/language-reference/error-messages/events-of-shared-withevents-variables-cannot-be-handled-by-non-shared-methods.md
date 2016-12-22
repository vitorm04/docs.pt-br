---
title: "Eventos de vari&#225;veis WithEvents compartilhadas n&#227;o podem ser identificados por m&#233;todos n&#227;o compartilhados | Microsoft Docs"
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
  - "bc30594"
  - "vbc30594"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30594"
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eventos de vari&#225;veis WithEvents compartilhadas n&#227;o podem ser identificados por m&#233;todos n&#227;o compartilhados
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma variável declarada com o modificador `Shared` é uma variável compartilhada.  Uma variável compartilhada identifica exatamente um local de armazenamento.  Uma variável declarada com o modificador `WithEvents` expressa que aquele tipo ao qual a variavel pertence manipula o conjunto de eventos que a variável causa.  Quando um valor é atribuído à variável, a propriedade criada pela declaração `WithEvents` desengancha qualquer tratador de eventos e engancha o novo tratador de eventos através do método `Add`.  
  
 **Identificação do erro:**  BC30594  
  
### Para corrigir este erro  
  
-   Declare seu tratador de eventos `Shared`.  
  
## Consulte também  
 [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)   
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
---
title: "&#39;Optional&#39; esperado | Microsoft Docs"
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
  - "bc30202"
  - "vbc30202"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30202"
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; esperado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um argumento opcional em um procedimento declaração é seguido por um argumento necessário.  Cada argumento após um argumento opcional também deve ser opcional.  
  
 **Identificação do erro:**  BC30202  
  
### Para corrigir este erro  
  
1.  Se o argumento destina\-se a ser necessários, movê\-lo a preceda o primeiro argumento opcional na lista de argumentos.  
  
2.  Se o argumento destina\-se a ser opcional, use a `Optional` palavra\-chave.  
  
## Consulte também  
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
---
title: "Express&#227;o de subscrito de matriz ausente | Microsoft Docs"
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
  - "bc30306"
  - "vbc30306"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30306"
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o de subscrito de matriz ausente
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma inicialização de matriz omite um ou mais dos subscritos que definem os limites da matriz.  Por exemplo, a instrução pode conter a expressão `myArray (5,5,,10)`, que omite o terceiro subscrito.  
  
 **Identificação do erro:**  BC30306  
  
### Para corrigir este erro  
  
-   Forneça o subscrito que falta.  
  
## Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
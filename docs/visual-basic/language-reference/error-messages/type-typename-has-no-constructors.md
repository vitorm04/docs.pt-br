---
title: "O tipo &#39;&lt;typename&gt;&#39; n&#227;o tem construtores | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30251"
  - "vbc30251"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30251"
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt;typename&gt;&#39; n&#227;o tem construtores
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um tipo não suporta uma chamada para `Sub New()`.  Uma possível causa é um compilador corrompido ou arquivo binário.  
  
 **Identificação do erro:** BC30251  
  
### Para corrigir este erro  
  
1.  Se o tipo estiver em um projeto diferente ou em um arquivo referenciado, reinstale o projeto ou arquivo.  
  
2.  Se o tipo estiver no mesmo projeto, recompile o assembly que contém o tipo.  
  
3.  Se o erro persistir, reinstale o compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
4.  Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.  
  
## Consulte também  
 [Objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Fale conosco](/visual-studio/ide/talk-to-us)
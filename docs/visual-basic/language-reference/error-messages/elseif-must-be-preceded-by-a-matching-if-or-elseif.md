---
title: "&#39;#ElseIf&#39; deve ser precedido por um &#39;#If&#39; ou &#39;#ElseIf&#39; correspondente | Microsoft Docs"
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
  - "vbc30014"
  - "bc30014"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30014"
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#ElseIf&#39; deve ser precedido por um &#39;#If&#39; ou &#39;#ElseIf&#39; correspondente
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#ElseIf` é uma diretiva de compilação condicional.  Uma cláusula `#ElseIf` deve ser precedida por uma cláusula `#If` ou `#ElseIf` correspondente.  
  
 **Identificação do erro:**  BC30014  
  
### Para corrigir este erro  
  
1.  Verifique se um `#If`  ou `#ElseIf` anterior não foi separado deste `#ElseIf` por um bloco intermediário de compilação condicional  ou um `#End If` posicionado incorretamente.  
  
2.  Se o `#ElseIf` é precedido por uma diretriz `#Else`, remova o `#Else` ou altere\-o para um `#ElseIf`.  
  
3.  Se todo o restante estiver em ordem, adicione a diretiva `#If` no início do bloco de compilação condicional.  
  
## Consulte também  
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
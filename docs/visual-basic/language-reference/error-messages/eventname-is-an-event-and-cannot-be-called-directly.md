---
title: "&#39;&lt;eventname&gt;&#39; &#233; um evento, e n&#227;o pode ser chamado diretamente | Microsoft Docs"
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
  - "bc32022"
  - "vbc32022"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32022"
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;eventname&gt;&#39; &#233; um evento, e n&#227;o pode ser chamado diretamente
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

' \<`eventname`\>' é um evento e, portanto, não pode ser chamado diretamente.  Use uma declaração `RaiseEvent` para disparar um evento.  
  
 Uma chamada de procedimento especifica um evento para o nome do procedimento.  Um manipulador de eventos é um procedimento, mas o evento em si é um dispositivo sinalizador, que seve disparado e tratado.  
  
 **Identificação do erro:**  BC32022  
  
### Para corrigir este erro  
  
1.  Use uma declaração `RaiseEvent` para sinalizar um evento e chamar o procedimento ou procedimentos que lidam com ele.  
  
## Consulte também  
 [Instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
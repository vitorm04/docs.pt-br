---
title: "Arquivo j&#225; aberto | Microsoft Docs"
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
  - "vbrID55"
dev_langs: 
  - "VB"
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arquivo j&#225; aberto
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer.  Dentre as causas possíveis desse erro, estão:  
  
-   Um modo de saída seqüencial `FileOpen` operação foi executada para um arquivo que já está aberto  
  
-   Uma declaração se refere a um arquivo aberto.  
  
### Para corrigir este erro  
  
1.  Feche o arquivo antes de executar a instrução.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
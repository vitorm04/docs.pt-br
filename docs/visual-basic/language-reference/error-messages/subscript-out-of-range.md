---
title: "Subscrito fora do intervalo (Visual Basic) | Microsoft Docs"
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
  - "vbrID9"
dev_langs: 
  - "VB"
ms.assetid: d0344a65-ec02-4caf-8d3c-9977392ca353
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Subscrito fora do intervalo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma matriz subscrita não é válida porque ela está fora do intervalo permitido.  O menor valor subscrito para uma dimensão é sempre 0 e o maior valor subscrito retornado pelo `GetUpperBound` método para essa dimensão.  
  
### Para corrigir este erro  
  
-   Altere a subscrição para que ele esteja dentro do intervalo válido.  
  
## Consulte também  
 <xref:System.Array.GetUpperBound%2A?displayProperty=fullName>   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
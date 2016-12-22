---
title: "A fun&#231;&#227;o &#39;Dir&#39; deve ser chamada primeiro com um argumento &#39;PathName&#39; | Microsoft Docs"
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
  - "vbrDIR_IllegalCall"
dev_langs: 
  - "VB"
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A fun&#231;&#227;o &#39;Dir&#39; deve ser chamada primeiro com um argumento &#39;PathName&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma chamada inicial para a função `Dir` não inclui o argumento `PathName`.  A primeira chamada para `Dir` deve incluir um `PathName`,mas chamadas subsequentes para `Dir` não precisa incluir parâmetros para recuperar o próximo item.  
  
### Para corrigir este erro  
  
1.  Forneça um argumento `PathName` in a chamada de função.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
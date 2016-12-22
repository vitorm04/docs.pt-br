---
title: "A vari&#225;vel usa um tipo de automa&#231;&#227;o sem suporte no Visual Basic | Microsoft Docs"
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
  - "vbrID458"
dev_langs: 
  - "VB"
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel usa um tipo de automa&#231;&#227;o sem suporte no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você tentou usar uma variável definida em uma biblioteca de tipos ou biblioteca de objetos que tem um tipo de dados não oferece suporte para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Para corrigir este erro  
  
-   Usar uma variável de um tipo reconhecido pelo [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
     \- ou \-  
  
-   Se você encontrar esse erro enquanto estiver usando `FileGet` ou `FileGetOBject`, verifique se o arquivo que você está tentando usar foi gravado com `FilePut` ou `FilePutObject`.  
  
## Consulte também  
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)
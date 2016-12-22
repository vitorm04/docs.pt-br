---
title: "As constantes devem ser do tipo intr&#237;nseco ou enumerado, e n&#227;o classe, estrutura, tipo de par&#226;metro ou tipo de matriz | Microsoft Docs"
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
  - "vbc30424"
  - "bc30424"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30424"
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As constantes devem ser do tipo intr&#237;nseco ou enumerado, e n&#227;o classe, estrutura, tipo de par&#226;metro ou tipo de matriz
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você tentou declarar uma constante como uma classe, estrutura ou matriz, ou um parâmetro de tipo definido por um tipo genérico.  
  
 Constantes devem ser de um tipo intrínseco \(`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`\),  ou um tipo `Enum` baseado nos tipos integrais.  
  
 **Identificação do erro:**  BC30424  
  
### Para corrigir este erro  
  
1.  Declare a constante como um tipo intrínseco ou `Enum`.  
  
2.  A constante pode também ser de um valor especial como `True`, `False`, ou `Nothing`.  O compilador considera esses valores predefinidos como do tipo intrínseco apropriado.  
  
## Consulte também  
 [Constantes e enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)
---
title: "A estrutura &#39;&lt;structurename&gt;&#39; deve conter pelos menos uma vari&#225;vel membro da inst&#226;ncia ou pelo menos uma declara&#231;&#227;o de evento da inst&#226;ncia n&#227;o marcada como &#39;Personalizada&#39; | Microsoft Docs"
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
  - "bc30941"
  - "vbc30941"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30941"
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A estrutura &#39;&lt;structurename&gt;&#39; deve conter pelos menos uma vari&#225;vel membro da inst&#226;ncia ou pelo menos uma declara&#231;&#227;o de evento da inst&#226;ncia n&#227;o marcada como &#39;Personalizada&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.  
  
 Toda estrutura deve ter ou uma variável ou um evento que se aplica a cada instância específica \(não compartilhada\) ao invés de todas as instâncias coletivamente \([Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)\).  Constante, propriedades e procedimentos não compartilhados não satisfazem esta exigência.  Adicionalmente, se não há variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um evento `Custom`.  
  
 **Identificação do erro:**  BC30941  
  
### Para corrigir este erro  
  
-   Defina pelo menos uma variável ou evento que não é `Shared`.  Se você definir apenas um evento, deve ser não personalizado assim como não compartilhado.  
  
## Consulte também  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
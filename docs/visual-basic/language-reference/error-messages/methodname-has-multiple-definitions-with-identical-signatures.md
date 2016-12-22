---
title: "&#39;&lt;methodname&gt;&#39; tem v&#225;rias defini&#231;&#245;es com assinaturas id&#234;nticas | Microsoft Docs"
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
  - "vbc30269"
  - "bc30269"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30269"
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methodname&gt;&#39; tem v&#225;rias defini&#231;&#245;es com assinaturas id&#234;nticas
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração de procedimento `Function` ou `Sub`usa o nome do procedimento e lista de argumentos idênticos dos de uma declaração anterior.  Uma causa possível é uma tentativa para sobrecarregar o procedimento original.  Procedimentos sobrecarregados devem ter listas diferentes de argumentos.  
  
 **Identificação do erro:**  BC30269  
  
### Para corrigir este erro  
  
-   Altere o nome do procedimento ou o lista de argumentos, ou remova a declaração duplicada.  
  
## Consulte também  
 [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Considerações sobre procedimentos de sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
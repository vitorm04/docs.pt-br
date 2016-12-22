---
title: "Procedimento let de propriedade n&#227;o definido e procedimento get de propriedade n&#227;o retornou um objeto | Microsoft Docs"
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
  - "vbrID451"
dev_langs: 
  - "VB"
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedimento let de propriedade n&#227;o definido e procedimento get de propriedade n&#227;o retornou um objeto
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Certas propriedades, métodos e operações só podem aplicar a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva a coleções, mas o objeto não é uma coleção.  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia do nome do objeto ou uma propriedade, ou verifique se o objeto é uma `Collection` objeto.  
  
2.  Examinar o `Add`método usado para adicionar o objeto à coleção para certificar\-se de que a sintaxe está correto e que quaisquer identificadores foram grafados corretamente.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Collection>
---
title: "&#39;&lt;attribute&gt;&#39; n&#227;o pode ser aplicado porque o formato da GUID &#39;&lt;number&gt;&#39; n&#227;o est&#225; correto | Microsoft Docs"
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
  - "vbc32500"
  - "bc32500"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32500"
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;attribute&gt;&#39; n&#227;o pode ser aplicado porque o formato da GUID &#39;&lt;number&gt;&#39; n&#227;o est&#225; correto
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A `COMClassAttribute` bloco de atributo especifica um identificador globalmente exclusivo \(GUID\) que não obedece para o formato adequado para um GUID.  `COMClassAttribute`usa os GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Um GUID consiste de 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários.  Ele é gerado por utilitários Microsoft como Uuidgen.exe e é garantido como sendo exclusivo no espaço e tempo.  
  
 **Identificação do erro:**  BC32500  
  
### Para corrigir este erro  
  
1.  Determine o GUID correto ou GUIDs necessários para identificar o objeto COM.  
  
2.  Certifique\-se de que as cadeias GUID apresentadas ao bloco de atributos `COMClassAttribute` são copiadas corretamente.  
  
## Consulte também  
 <xref:System.Guid>   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)
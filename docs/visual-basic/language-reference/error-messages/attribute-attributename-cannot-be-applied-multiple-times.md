---
title: "O atributo &#39;&lt;attributename&gt;&#39; n&#227;o pode ser aplicado v&#225;rias vezes | Microsoft Docs"
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
  - "bc30663"
  - "vbc30663"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30663"
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O atributo &#39;&lt;attributename&gt;&#39; n&#227;o pode ser aplicado v&#225;rias vezes
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O atributo só pode ser aplicado uma vez.  O atributo `AttributeUsage` determina se um atributo pode ser aplicado mais de uma vez.  
  
 **Identificação do erro:**  BC30663  
  
### Para corrigir este erro  
  
1.  Verifique se que o atributo é aplicado somente uma vez.  
  
2.  Se você está usando atributos personalizados que você desenvolveu, considere alterar o atributo `AttributeUsage` para permitir que vários usos de atributo, como ocorre com o exemplo a seguir.  
  
    ```  
    <AttributeUsage(AllowMultiple := True)>  
    ```  
  
## Consulte também  
 <xref:System.AttributeUsageAttribute>   
 [Criando atributos personalizados](../Topic/Creating%20Custom%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [AttributeUsage](../Topic/AttributeUsage%20\(C%23%20and%20Visual%20Basic\).md)
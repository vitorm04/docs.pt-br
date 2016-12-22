---
title: "A exce&#231;&#227;o de coment&#225;rio XML deve ter um atributo &#39;cref&#39; | Microsoft Docs"
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
  - "bc42319"
  - "vbc42319"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42319"
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A exce&#231;&#227;o de coment&#225;rio XML deve ter um atributo &#39;cref&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tag \< exception \> fornece uma maneira para documentar as exceções que podem ser geradas por um método.  O atributo necessário `cref`designa o nome de um membro, que é verificado pelo gerador de documentação.  Se o membro existe, ele é convertido para o nome canônico do elemento no arquivo de documentação.  
  
 **Identificação do erro:**  BC42319  
  
### Para corrigir este erro  
  
-   Adicione o atributo `cref` à exceção da seguinte maneira:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## Consulte também  
 [\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md)   
 [Como criar documentação XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
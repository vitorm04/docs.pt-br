---
title: "As refer&#234;ncias de entidade XML n&#227;o s&#227;o suportadas | Microsoft Docs"
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
  - "vbc31180"
  - "bc31180"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31180"
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As refer&#234;ncias de entidade XML n&#227;o s&#227;o suportadas
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma referência de entidade \(por exemplo, `©`\) que não está definido no XML 1.0 especificação está incluída como um valor para um literal XML.  Somente as referências a entidades XML `&`, `"`, `<`, `>`, `'` são suportadas em literais XML.  
  
 **Identificação do erro:**  BC31180  
  
### Para corrigir este erro  
  
-   Remover a referência de entidade não suportadas.  
  
## Consulte também  
 [Especificação dos literais XML e do XML 1.0](../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
---
title: "Declara&#231;&#227;o esperada | Microsoft Docs"
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
  - "vbc30188"
  - "bc30188"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30188"
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declara&#231;&#227;o esperada
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma instrução nondeclarative, como, por exemplo, uma atribuição ou a instrução loop, ocorre fora de qualquer procedimento.  Declarações só são permitidas procedimentos externos.  
  
 Como alternativa, um elemento de programação é declarado sem uma palavra\-chave da declaração, como `Dim` ou `Const`.  
  
 **Identificação do erro:**  BC30188  
  
### Para corrigir este erro  
  
-   Mova a instrução de nondeclarative para o corpo de um procedimento.  
  
-   Comece a declaração com uma palavra\-chave da declaração apropriado.  
  
-   Certifique\-se de que não está digitado incorretamente uma palavra\-chave da declaração.  
  
## Consulte também  
 [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
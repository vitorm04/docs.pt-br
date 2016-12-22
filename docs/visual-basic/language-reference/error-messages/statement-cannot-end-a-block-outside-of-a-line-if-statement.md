---
title: "A instru&#231;&#227;o n&#227;o pode finalizar um bloco fora de uma instru&#231;&#227;o &#39;If&#39; de linha | Microsoft Docs"
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
  - "vbc32005"
  - "bc32005"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32005"
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A instru&#231;&#227;o n&#227;o pode finalizar um bloco fora de uma instru&#231;&#227;o &#39;If&#39; de linha
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma instrução `If` de linha única contém várias instruções separadas por dois\-pontos \(:\), uma delas é uma instrução `End` para um bloco de controle fora da única linha `If`.  Instruções `If` de linha única não usam a instrução `End If`.  
  
 **Identificação do erro:**  BC32005  
  
### Para corrigir este erro  
  
-   Mova a instrução `If`de única linha para fora do bloco de controle que contém a instrução `End If`.  
  
## Consulte também  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
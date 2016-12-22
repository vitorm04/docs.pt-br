---
title: "&#39;.&#39; ou &#39;!&#39; &#224; esquerda s&#243; podem aparecer dentro de uma instru&#231;&#227;o &#39;With&#39; | Microsoft Docs"
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
  - "vbc30157"
  - "bc30157"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30157"
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;.&#39; ou &#39;!&#39; &#224; esquerda s&#243; podem aparecer dentro de uma instru&#231;&#227;o &#39;With&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um ponto \(.\) ou ponto de exclamação \(\!\) que não está dentro de um bloco `With` não ocorre sem uma expressão no lado esquerdo.  Membro de acesso \(`.`\) e dicionário membro de acesso \(`!`\) requerem uma expressão especificando o elemento que contém o membro.  Isso deve aparecer imediatamente à esquerda do acessador ou como o destino de um bloco `With` contendo o acesso membro.  
  
 **Identificação do erro:**  BC30157  
  
### Para corrigir este erro  
  
1.  Certifique\-sede que o bloco `With` está formatado corretamente.  
  
2.  Se não houver nenhum bloco`With` , adicione uma expressão à esquerda do acessador que avalia para um elemento definido que contém o membro.  
  
## Consulte também  
 [Caracteres especiais no código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)   
 [Instrução With ... End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
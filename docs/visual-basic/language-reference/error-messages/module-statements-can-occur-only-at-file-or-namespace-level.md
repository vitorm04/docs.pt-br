---
title: "Instru&#231;&#245;es &#39;Module&#39; s&#243; podem ocorrer no n&#237;vel de namespace ou arquivo | Microsoft Docs"
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
  - "bc30617"
  - "vbc30617"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30617"
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;Module&#39; s&#243; podem ocorrer no n&#237;vel de namespace ou arquivo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declarações `Module` devem aparecer no topo do seu arquivo fonte imediatamente após as declarações `Option` e `Imports`, atributos globais, e declarações de namespace, mas antes das outras declarações.  
  
 **Identificação do erro:**  BC30617  
  
### Para corrigir este erro  
  
-   Mova a declaração `Module` para o topo da sua declaração de namespace ou arquivo fonte.  
  
## Consulte também  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
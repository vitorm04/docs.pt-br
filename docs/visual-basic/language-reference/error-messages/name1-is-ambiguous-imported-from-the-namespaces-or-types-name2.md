---
title: "&#39;&lt;name1&gt;&#39; &#233; amb&#237;guo, importado dos namespaces ou tipos &#39;&lt;name2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30561"
  - "bc30561"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30561"
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;name1&gt;&#39; &#233; amb&#237;guo, importado dos namespaces ou tipos &#39;&lt;name2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você forneceu um nome que é ambíguo e portanto conflitante com outro nome.  O compilador [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não tem nenhuma regra de resolução de conflitos; você mesmo deve eliminar a ambiguidade.  
  
 **Identificação do erro:**  BC30561  
  
### Para corrigir este erro  
  
1.  Torne o nome não ambíguo removendo imports de namespace.  
  
2.  Determine totalmente o nome.  
  
## Consulte também  
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)
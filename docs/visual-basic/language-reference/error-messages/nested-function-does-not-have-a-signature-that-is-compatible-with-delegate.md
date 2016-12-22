---
title: "A fun&#231;&#227;o aninhada n&#227;o tem uma assinatura que seja compat&#237;vel com o delegado &#39;&lt;delegatename&gt;&#39; | Microsoft Docs"
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
  - "vbc36532"
  - "bc36532"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36532"
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A fun&#231;&#227;o aninhada n&#227;o tem uma assinatura que seja compat&#237;vel com o delegado &#39;&lt;delegatename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um expressão lambda foi atribuída a um delegado que tem uma assinatura incompatível.  Por exemplo, no código a seguir, o delegado `Del` tem dois parâmetros inteiros.  
  
```vb#  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:  
  
```vb#  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **Identificação do erro:**  BC36532  
  
### Para corrigir este erro  
  
-   Ajuste a definição de representante ou o expressão lambda atribuído para que as assinaturas sejam compatíveis.  
  
## Consulte também  
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
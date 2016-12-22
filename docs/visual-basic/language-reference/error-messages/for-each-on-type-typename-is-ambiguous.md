---
title: "&#39;For Each&#39; no tipo &#39;&lt;typename&gt;&#39; &#233; amb&#237;guo porque o tipo implementa v&#225;rias inst&#226;ncias de &#39;System.Collections.Generic.IEnumerable(Of T)&#39; | Microsoft Docs"
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
  - "vbc32096"
  - "bc32096"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32096"
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;For Each&#39; no tipo &#39;&lt;typename&gt;&#39; &#233; amb&#237;guo porque o tipo implementa v&#225;rias inst&#226;ncias de &#39;System.Collections.Generic.IEnumerable(Of T)&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A `For Each` declaração especifica uma variável do iterador que tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.  
  
 A variável do iterador deve ser de um tipo que implementa o <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface da `Collections` namespaces da [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  É possível que uma classe implementar a mais de uma interface genérica construída, usando um argumento de tipo diferente para cada construção.  Se uma classe que faz isso é usada para a variável do iterador, essa variável tem mais de um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método.  Nesse caso, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não é possível escolher qual método de chamada.  
  
 **Identificação do erro:**  BC32096  
  
### Para corrigir este erro  
  
-   Use [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) para converter o tipo de variável do iterador para a definição de interface do <xref:System.Collections.IEnumerable.GetEnumerator%2A> método você deseja usar.  
  
## Consulte também  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)
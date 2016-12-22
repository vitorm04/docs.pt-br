---
title: "A matriz declarada para a vari&#225;vel de controle do loop n&#227;o pode ser declarada com um tamanho inicial | Microsoft Docs"
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
  - "vbc32039"
  - "bc32039"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32039"
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A matriz declarada para a vari&#225;vel de controle do loop n&#227;o pode ser declarada com um tamanho inicial
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um loop `For Each` usa uma matriz como sua variável de iteração de *element* mas inicializa essa matriz.  
  
 As instruções a seguir mostram como esse erro pode ser gerado.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 A primeira instrução `For Each` é a maneira correta de acessar elementos de `arrayList`.  A segunda instrução `For Each` gera esse erro.  
  
 **Identificação do erro:**  BC32039  
  
### Para corrigir este erro  
  
-   Remova a inicialização da declaração da variável de iteração do *element*.  
  
## Consulte também  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)
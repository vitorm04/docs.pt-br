---
title: "Matrizes declaradas como membros de estrutura n&#227;o podem ser declaradas com um tamanho inicial | Microsoft Docs"
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
  - "vbc31043"
  - "bc31043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31043"
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Matrizes declaradas como membros de estrutura n&#227;o podem ser declaradas com um tamanho inicial
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma matriz numa estrutura é declarada com um tamanho inicial.  Você não pode inicializar nenhum elemento de uma estrutura, e declarar o tamanho de uma matriz é uma forma de inicialização.  
  
 **Identificação do erro:**  BC31043  
  
### Para corrigir este erro  
  
1.  Defina a matriz na sua estrutura como dinâmica \(sem tamanho inicial\).  
  
2.  Se você necessita de um certo tamanho de matriz, você pode redimensionar uma matriz dinâmica com uma declaração [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) quando seu código está sendo executado.  O exemplo a seguir ilustra isto:  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Como declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
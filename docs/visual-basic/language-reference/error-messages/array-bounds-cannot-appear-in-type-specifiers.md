---
title: "Os limites de matriz n&#227;o podem ser exibidos em especificadores de tipo | Microsoft Docs"
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
  - "vbc30638"
  - "bc30638"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30638"
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Os limites de matriz n&#227;o podem ser exibidos em especificadores de tipo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.  
  
 **Identificação do erro:**  BC30638  
  
### Para corrigir este erro  
  
-   Especifique o tamanho da matriz imediatamente após o nome de variável em vez de colocar o tamanho da matriz após o tipo, conforme mostrado no exemplo o seguir.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Defina uma matriz e inicialize\-a com o número desejado de elementos, como mostrado no exemplo o seguir.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
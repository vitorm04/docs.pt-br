---
title: "O n&#250;mero de &#237;ndices excede o n&#250;mero de dimens&#245;es da matriz indexada | Microsoft Docs"
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
  - "bc30106"
  - "vbc30106"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30106"
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O n&#250;mero de &#237;ndices excede o n&#250;mero de dimens&#245;es da matriz indexada
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O número de índices usado para acessar um elemento de matriz deve ser exatamente o mesmo da classificação da matriz, ou seja, o número de dimensões declarada para ela.  
  
 **Identificação do erro:**  BC30106  
  
### Para corrigir este erro  
  
-   Remova subscrições da referência de matriz até que o número total de subscrições se iguale à classificação da matriz.  Por exemplo:  
  
    ```  
    [Visual Basic]  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
---
title: "Como fazer refer&#234;ncia &#224; inst&#226;ncia atual de um objeto (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instância atual"
  - "instâncias, referindo-se a atual"
  - "variáveis de objeto"
  - "objetos [Visual Basic], referindo-se à instância atual"
  - "variáveis [Visual Basic], Objeto "
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como fazer refer&#234;ncia &#224; inst&#226;ncia atual de um objeto (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A  *instância atual*  de um objeto é a instância na qual o código está em execução atualmente.  
  
 Você pode usar o `Me` palavra\-chave para se referir à instância atual.  
  
### Para referir\-se a instância atual  
  
-   Use a `Me` palavra\-chave em que você normalmente seria usar o nome de um variável de objeto.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Embora `Me` se comporta como um objeto variável, você não pode declará\-lo ou atribuir nada a ela.  `Me`sempre se refere à instância atual.  
  
## Consulte também  
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
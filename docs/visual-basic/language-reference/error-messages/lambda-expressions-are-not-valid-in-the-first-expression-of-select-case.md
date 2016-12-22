---
title: "As express&#245;es lambda n&#227;o s&#227;o v&#225;lidas na primeira express&#227;o de uma instru&#231;&#227;o &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc36635"
  - "vbc36635"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36635"
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As express&#245;es lambda n&#227;o s&#227;o v&#225;lidas na primeira express&#227;o de uma instru&#231;&#227;o &#39;Select Case&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você não pode usar uma expressão lambda para a expressão numa declaração `Select Case`.  Definições de expressão lambda retornam funções, e a expressão de teste de uma declaração `Select Case` deve ser um tipo de dados elementar.  
  
 O código a seguir causa este erro:  
  
```vb#  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Identificação do erro:**  BC36635  
  
### Para corrigir este erro  
  
-   Examine seu código para determinar se uma construção condicional diferente, como declaração `If...Then...Else`, funcionaria para você.  
  
-   Você pode ter pretendido chamar a função, como mostrado no código a seguir:  
  
    ```vb#  
    Dim num? As Integer  
    Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
        ' List of the cases  
    End Select  
    ```  
  
## Consulte também  
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
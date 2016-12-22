---
title: "Infer&#234;ncia de tipo que permite valor nulo n&#227;o suportada neste contexto | Microsoft Docs"
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
  - "vbc36629"
  - "bc36629"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36629"
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Infer&#234;ncia de tipo que permite valor nulo n&#227;o suportada neste contexto
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Tipos de valor e estruturas podem ser declarados anuláveis.  
  
```vb#  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Entretanto, você não pode usar a declaração anulável em conjunto com inferência de tipos.  Os exemplos a seguir causam este erro.  
  
```vb#  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Identificação do erro:**  BC36629  
  
### Para corrigir este erro  
  
-   Us uma cláusula `As` para declarar a variável como anulável.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
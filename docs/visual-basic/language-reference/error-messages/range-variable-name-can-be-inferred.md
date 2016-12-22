---
title: "O nome da vari&#225;vel de intervalo s&#243; pode ser inferido a partir de um nome simples ou qualificado sem argumentos | Microsoft Docs"
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
  - "vbc36599"
  - "bc36599"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36599"
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O nome da vari&#225;vel de intervalo s&#243; pode ser inferido a partir de um nome simples ou qualificado sem argumentos
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um elemento de programação que leva um ou mais argumentos está incluído em uma consulta LINQ.  O compilador não consegue interpretar uma variável de intervalo a partir do elemento de programação.  
  
 **Identificação do erro:**  BC36599  
  
### Para corrigir este erro  
  
1.  Forneça um nome de variável explícito para o elemento de programação, como mostrado no código a seguir:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias = SampleFunction(var1), var1  
```  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)
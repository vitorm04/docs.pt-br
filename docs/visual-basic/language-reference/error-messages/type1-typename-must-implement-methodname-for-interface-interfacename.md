---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; deve implementar &#39;&lt;methodname&gt;&#39; para interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
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
  - "vbc30149"
  - "bc30149"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30149"
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; deve implementar &#39;&lt;methodname&gt;&#39; para interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento definido pela interface.  Cada membro da interface deve ser implementado.  
  
 **Identificação do erro:**  BC30149  
  
### Para corrigir este erro  
  
1.  Declare um procedimento com o mesmo nome e assinatura, conforme definido na interface.  Não se esqueça incluir pelo menos a declaração `End Function` ou `End Sub`.  
  
2.  Adicionar uma cláusula `Implements` ao final da declaração `Function` ou `Sub` .  Por exemplo:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)
---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; deve implementar &#39;&lt;membername&gt;&#39; para interface &#39;&lt;interfacename&gt;&#39; | Microsoft Docs"
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
  - "vbc30154"
  - "bc30154"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30154"
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt;&#39;&lt;typename&gt;&#39; deve implementar &#39;&lt;membername&gt;&#39; para interface &#39;&lt;interfacename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\< tipodenome\>' deve implementar '\< nomedomembro \>' para interface '\< nomedainterface \>' .Implementação de propriedade deve ter especificadores 'ReadOnly' \/ 'WriteOnly' correspondentes.  
  
 Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento, propriedade ou evento definido pela interface.  Cada membro da interface deve ser implementado.  
  
 **Identificação do erro:**  BC30154  
  
### Para corrigir este erro  
  
1.  Declare um membro com o mesmo nome e assinatura, conforme definido na interface.  Não se esqueça de incluir pelo menos a declaração `End Function`, `End Sub`, ou `End Property`.  
  
2.  Adicione uma cláusula `Implements` ao final da declaração `Function`, `Sub`, `Property`, ou `Event`.  Por exemplo:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Quando estiver implementando uma propriedade, certifique\-se que `ReadOnly` ou `WriteOnly` é usado da mesma forma como na definição de interface.  
  
4.  Quando estiver implementando uma propriedade, declare procedimentos `Get` e `Set`, conforme apropriado.  
  
## Consulte também  
 [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)   
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)
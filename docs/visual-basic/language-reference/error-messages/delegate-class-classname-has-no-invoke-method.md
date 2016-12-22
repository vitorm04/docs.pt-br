---
title: "Classe Delegate &#39;&lt;classname&gt;&#39; n&#227;o tem nenhum m&#233;todo Invoke. Portanto, uma express&#227;o desse tipo n&#227;o pode ser o destino de uma chamada de m&#233;todo | Microsoft Docs"
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
  - "vbc30220"
  - "bc30220"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30220"
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classe Delegate &#39;&lt;classname&gt;&#39; n&#227;o tem nenhum m&#233;todo Invoke. Portanto, uma express&#227;o desse tipo n&#227;o pode ser o destino de uma chamada de m&#233;todo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma chamada para o `Invoke` através de um delegado falhou devido ao fato de o `Invoke` não estar implementado na classe de delegado.  
  
 **Identificação do erro:**  BC30220  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que um exemplo da classe delegada foi criada com uma declaração `Dim` e que um procedimento foi designado para o exemplo delegado com o operador `AddressOf`.  
  
2.  Localize o código que implementa a classe delegada e certifique\-se de que ele implementa o procedimento `Invoke`.  
  
## Consulte também  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
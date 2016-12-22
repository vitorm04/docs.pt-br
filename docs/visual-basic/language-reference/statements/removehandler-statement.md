---
title: "Instru&#231;&#227;o RemoveHandler | Microsoft Docs"
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
  - "vb.RemoveHandlerMethod"
  - "vb.RemoveHandler"
  - "RemoveHandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave RemoveHandler"
  - "Instrução RemoveHandler"
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o RemoveHandler
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Remove a associação entre um evento e um manipulador de eventos.  
  
## Sintaxe  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`event`|O nome do evento que está sendo tratado.|  
|`eventhandler`|O nome do procedimento que no momento estiver manipulando o evento.|  
  
## Comentários  
 As instruções `AddHandler` e  `RemoveHandler` permitem que você inicie e pare a manipulação de eventos para um evento específico a qualquer momento durante a execução do programa.  
  
> [!NOTE]
>  Para eventos personalizados, a instrução `RemoveHandler` chama o evento do acessador `RemoveHandler`.  Para obter mais informações sobre eventos personalizados, consulte [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## Exemplo  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## Consulte também  
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Eventos](../../../visual-basic/programming-guide/language-features/events/events.md)
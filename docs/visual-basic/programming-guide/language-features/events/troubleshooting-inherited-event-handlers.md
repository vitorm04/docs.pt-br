---
title: "Solucionando problemas de manipuladores de eventos herdados no Visual Basic | Microsoft Docs"
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
  - "manipuladores de eventos, solucionando problemas"
  - "manipulação de eventos, solucionando problemas"
  - "eventos herdados"
  - "solucionando problemas de eventos"
  - "solucionando problemas do Visual Basic, manipuladores de eventos"
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Solucionando problemas de manipuladores de eventos herdados no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico lista os problemas comuns que surgem com manipuladores de eventos em componentes herdados.  
  
## Procedimentos  
  
#### O código no manipulador de eventos é executado duas vezes para cada chamada  
  
-   Um manipulador de eventos herdadas não deve incluir um [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.  O método na classe base já está associado ao evento e será acionado apropriadamente.  Remover o `Handles` cláusula do método herdado.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Se o método herdado não tem um `Handles` palavra\-chave, verifique se seu código não contém um extra [Instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou todos os métodos adicionais que lidam com o mesmo evento.  
  
## Consulte também  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)
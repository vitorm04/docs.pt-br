---
title: "Como declarar eventos personalizados para evitar bloqueio (Visual Basic) | Microsoft Docs"
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
  - "eventos personalizados"
  - "declarando eventos, personalizado"
  - "eventos [Visual Basic], personalizado"
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar eventos personalizados para evitar bloqueio (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Há várias circunstâncias quando é importante que um manipulador de eventos não bloqueie os manipuladores de eventos subsequentes.  Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.  
  
 Por padrão, o campo de armazenamento reverso para uma declaração de evento é um representante de difusão seletiva que serialmente combina todos os manipuladores de eventos.  Isso significa que se um manipulador levar um longo tempo para concluir, ele bloqueia os outros manipuladores até que ela seja concluída.  \(Os manipuladores de eventos bem comportados nunca devem executar operações longas ou possivelmente de bloqueio.\)  
  
 Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.  
  
## Exemplo  
 Nesse exemplo, o acessador `AddHandler` adiciona o representante para cada manipulador de evento `Click` para um <xref:System.Collections.ArrayList> armazenado no campo `EventHandlerList`.  
  
 Quando o código dispara o evento `Click`, o acessador `RaiseEvent` chama todos os representantes de manipulador de eventos de forma assíncrona usando o método <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>.  Esse método chama cada manipulador em um segmento de trabalho e retorna imediatamente, portanto, manipuladores não podem bloquear um ao outro.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## Consulte também  
 <xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
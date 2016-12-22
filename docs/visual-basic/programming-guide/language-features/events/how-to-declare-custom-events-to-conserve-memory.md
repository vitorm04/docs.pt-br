---
title: "Como declarar eventos personalizados para conservar mem&#243;ria (Visual Basic) | Microsoft Docs"
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
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar eventos personalizados para conservar mem&#243;ria (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Há várias circunstâncias quando ele é importante que um aplicativo mantenha seu uso de memória baixa.  Eventos personalizados permitem que o aplicativo use memória somente para os eventos que ele gerencia.  
  
 Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo para armazenar as informações de evento.  Se uma classe tem muitos eventos não utilizados, eles desnecessariamente ocupam memória.  
  
 Em vez de usar a implementação de padrão de eventos que Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória mais cuidadosamente.  
  
## Exemplo  
 Nesse exemplo, a classe usa uma instância da classe <xref:System.ComponentModel.EventHandlerList>, armazenada no campo `Events`, para armazenar informações sobre os eventos em uso.  A classe <xref:System.ComponentModel.EventHandlerList> é uma classe lista otimizada projetada para armazenar representantes.  
  
 Todos os eventos na classe usam o campo `Events` para manter controle de quais métodos estão manipulando cada evento.  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## Consulte também  
 <xref:System.ComponentModel.EventHandlerList>   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
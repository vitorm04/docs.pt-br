---
title: "Como: declarar eventos personalizados para conservar memória (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4f8ce32a3b4da411a73010119283ce9661b82a6c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Como declarar eventos personalizados para conservar memória (Visual Basic)
Há várias circunstâncias quando é importante que um aplicativo mantenha seu uso de memória baixa. Eventos personalizados permitem que o aplicativo use memória somente para os eventos que ele gerencia.  
  
 Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo armazenar as informações do evento. Se uma classe tem muitos eventos não utilizados, eles desnecessariamente ocupam de memória.  
  
 Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória mais cuidadosamente.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe usa uma instância da <xref:System.ComponentModel.EventHandlerList>classe, armazenado no `Events` campo para armazenar informações sobre os eventos em uso.</xref:System.ComponentModel.EventHandlerList> O <xref:System.ComponentModel.EventHandlerList>classe é uma classe lista otimizada projetada para armazenar representantes.</xref:System.ComponentModel.EventHandlerList>  
  
 Todos os eventos na classe usam o `Events` campo para controlar quais métodos estão manipulando cada evento.  
  
 [!code-vb[VbVbalrEvents&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList>   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)

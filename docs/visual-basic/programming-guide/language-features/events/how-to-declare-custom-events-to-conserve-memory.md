---
title: 'Como: Declarar eventos personalizados para conservar memória (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973154"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Como: Declarar eventos personalizados para conservar memória (Visual Basic)
Há várias circunstâncias quando é importante que um aplicativo mantenha seu uso de memória baixa. Eventos personalizados permitem que o aplicativo para usar a memória somente para os eventos que ele manipula.  
  
 Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo para armazenar as informações do evento. Se uma classe tem muitos eventos não utilizados, eles desnecessariamente ocupam de memória.  
  
 Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória mais cuidadosamente.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe usa uma instância das <xref:System.ComponentModel.EventHandlerList> classe, armazenado no `Events` campo para armazenar informações sobre os eventos em uso. O <xref:System.ComponentModel.EventHandlerList> é uma classe de lista otimizada projetada para armazenar representantes.  
  
 Todos os eventos na classe usam o `Events` campo para controlar quais métodos estão manipulando cada evento.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.EventHandlerList>
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Como: Declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)

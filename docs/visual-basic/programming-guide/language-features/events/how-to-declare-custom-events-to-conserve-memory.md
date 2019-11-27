---
title: Como declarar eventos personalizados para conservar memória
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345124"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a>Como declarar eventos personalizados para conservar memória (Visual Basic)
Há várias circunstâncias em que é importante que um aplicativo Mantenha seu uso de memória baixo. Os eventos personalizados permitem que o aplicativo use a memória apenas para os eventos que ele manipula.  
  
 Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo para armazenar as informações do evento. Se uma classe tiver muitos eventos não utilizados, eles ocupam desnecessariamente a memória.  
  
 Em vez de usar a implementação padrão de eventos que Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória com mais cuidado.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe usa uma instância da classe <xref:System.ComponentModel.EventHandlerList>, armazenada no campo `Events`, para armazenar informações sobre os eventos em uso. A classe <xref:System.ComponentModel.EventHandlerList> é uma classe de lista otimizada projetada para manter delegados.  
  
 Todos os eventos na classe usam o campo `Events` para controlar quais métodos estão manipulando cada evento.  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.EventHandlerList>
- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)

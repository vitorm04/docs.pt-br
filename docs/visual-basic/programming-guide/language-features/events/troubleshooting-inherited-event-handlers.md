---
title: Solucionando problemas de manipuladores de eventos herdados no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Solucionando problemas de manipuladores de eventos herdados no Visual Basic
Este tópico lista os problemas comuns que surgem com manipuladores de evento nos componentes herdados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Código no manipulador de eventos é executado duas vezes para cada chamada  
  
-   Um manipulador de eventos herdados não deve incluir um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula. O método na classe base já está associado ao evento e disparam adequadamente. Remover o `Handles` cláusula do método herdado.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Se o método herdado não tem um `Handles` palavra-chave, verifique se seu código não contém um extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou todos os métodos adicionais que lidam com o mesmo evento.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)

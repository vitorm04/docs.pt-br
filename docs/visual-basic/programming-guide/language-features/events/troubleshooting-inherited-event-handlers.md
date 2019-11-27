---
title: Solução de problemas de manipuladores de eventos herdados
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345100"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Solucionando problemas de manipuladores de eventos herdados no Visual Basic
Este tópico lista os problemas comuns que surgem com manipuladores de eventos em componentes herdados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>O código no manipulador de eventos é executado duas vezes para cada chamada  
  
- Um manipulador de eventos herdado não deve incluir uma cláusula [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) . O método na classe base já está associado ao evento e será acionado de acordo. Remova a cláusula `Handles` do método herdado.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Se o método herdado não tiver uma palavra-chave `Handles`, verifique se o seu código não contém uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) extra ou quaisquer métodos adicionais que manipulem o mesmo evento.  
  
## <a name="see-also"></a>Consulte também

- [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)

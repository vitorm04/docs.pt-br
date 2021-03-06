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
ms.openlocfilehash: d228e916e45054bc088aa633afd9d591e592210d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057995"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Solucionando problemas de manipuladores de eventos herdados no Visual Basic

Este tópico lista os problemas comuns que surgem com manipuladores de eventos em componentes herdados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>O código no manipulador de eventos é executado duas vezes para cada chamada  
  
- Um manipulador de eventos herdado não deve incluir uma cláusula [Handles](../../../language-reference/statements/handles-clause.md) . O método na classe base já está associado ao evento e será acionado de acordo. Remova a `Handles` cláusula do método herdado.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Se o método herdado não tiver uma `Handles` palavra-chave, verifique se o seu código não contém uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) extra ou quaisquer métodos adicionais que manipulem o mesmo evento.  
  
## <a name="see-also"></a>Confira também

- [Eventos](index.md)

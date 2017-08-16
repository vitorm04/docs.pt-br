---
title: "Solução de problemas de manipuladores de eventos no Visual Basic herdados | Documentos do Microsoft"
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
- troubleshooting events
- inherited events
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 0dae6b48b1885a52b99ae3e7328340cac7b2d7d4
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Solucionando problemas de manipuladores de eventos herdados no Visual Basic
Este tópico lista problemas comuns que surgem com manipuladores de evento nos componentes herdados.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>O código no manipulador de eventos é executado duas vezes para cada chamada  
  
-   Um manipulador de eventos herdados não deve incluir uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula. O método na classe base já está associado ao evento e acionará adequadamente. Remover o `Handles` cláusula do método herdado.  
  
     [!code-vb[32 VbVbalrEvents](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Se o método herdado não tem um `Handles` palavra-chave, verifique se seu código não contém um arquivo extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou quaisquer métodos adicionais que tratam o mesmo evento.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)

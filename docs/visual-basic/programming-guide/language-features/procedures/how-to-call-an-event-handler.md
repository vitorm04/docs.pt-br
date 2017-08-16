---
title: 'Como: chamar um manipulador de eventos no Visual Basic | Documentos do Microsoft'
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
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
ms.openlocfilehash: c5b300feca3415d1283d24179795a4ae92c61e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Como chamar um manipulador de eventos no Visual Basic
Um *evento* é uma ação ou ocorrência — como um mouse clique ou um limite de crédito excedido — que é reconhecida pelo componente algum programa, e para o qual você pode escrever código para responder. Um *manipulador de eventos* é o código que você escreve para responder a um evento.  
  
 Um manipulador de eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é uma `Sub` procedimento. No entanto, você não chamá-lo normalmente a mesma maneira que outras `Sub` procedimentos. Em vez disso, você deve identificar o procedimento como um manipulador para o evento. Você pode fazer isso com um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula e um [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variável, ou com um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Usando um `Handles` cláusula é a maneira padrão para declarar um manipulador de eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Essa é a maneira que os manipuladores de eventos são gravados pelos designers quando você programa no ambiente de desenvolvimento integrado (IDE). O `AddHandler` instrução é adequada para elevar eventos dinamicamente em tempo de execução.  
  
 Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente chama o procedimento de manipulador de eventos. Qualquer código que tenha acesso ao evento pode fazer com que ele ocorrer ao executar uma [instrução RaiseEvent](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Você pode associar mais de um manipulador de eventos com o mesmo evento. Em alguns casos você pode dissociar um manipulador de um evento. Para obter mais informações, consulte [eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Para chamar um manipulador de eventos usando identificadores e WithEvents  
  
1.  Verifique se o evento é declarado com um [declaração de evento](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Declare uma variável de objeto no módulo ou classe de nível, usando o [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) palavra-chave. O `As` cláusula para esta variável deve especificar a classe que gera o evento.  
  
3.  Na declaração do manipulador de eventos `Sub` procedimento, adicione uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula que especifica o `WithEvents` variável e o nome do evento.  
  
4.  Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama automaticamente o `Sub` procedimento. Seu código pode usar uma `RaiseEvent` instrução para fazer com que o evento ocorrer.  
  
     O exemplo a seguir define um evento e um `WithEvents` variável que faz referência à classe que gera o evento. A manipulação de eventos `Sub` procedimento usa um `Handles` cláusula para especificar a classe e o evento manipula.  
  
     [!code-vb[VbVbcnProcedures n º&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Para chamar um manipulador de eventos usando AddHandler  
  
1.  Verifique se o evento é declarado com um `Event` instrução.  
  
2.  Executar uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) conectem dinamicamente a manipulação de eventos `Sub` procedimento com o evento.  
  
3.  Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama automaticamente o `Sub` procedimento. Seu código pode usar uma `RaiseEvent` instrução para fazer com que o evento ocorrer.  
  
     O exemplo a seguir define uma `Sub` procedimento para manipular o <xref:System.Windows.Forms.Form.Closing>evento de um formulário.</xref:System.Windows.Forms.Form.Closing> Ele usa o [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) para associar o `catchClose` procedimento como um manipulador de eventos <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>  
  
     [!code-vb[VbVbcnProcedures n º&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Você pode dissociar um manipulador de eventos de um evento executando o [Instrução RemoveHandler](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Como: criar um procedimento](./how-to-create-a-procedure.md)   
 [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)

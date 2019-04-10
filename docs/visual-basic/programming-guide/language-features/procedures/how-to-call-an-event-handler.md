---
title: 'Como: Chamar um manipulador de eventos no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3690d1c2eb8ece9059b8b25b5a14bef2021bc8f6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320165"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Como: Chamar um manipulador de eventos no Visual Basic
Uma *evento* é uma ação ou ocorrência — como um mouse clique ou um limite de crédito excedido — que é reconhecida pelo componente algum programa, e para o qual você pode escrever código para responder. Uma *manipulador de eventos* é o código que você escreve para responder a um evento.  
  
 Um manipulador de eventos no Visual Basic é uma `Sub` procedimento. No entanto, você não chamá-lo normalmente a mesma maneira que outras `Sub` procedimentos. Em vez disso, você deve identificar o procedimento como um manipulador para o evento. Você pode fazer isso com uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula e um [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variável, ou com um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Usando um `Handles` cláusula é a maneira padrão para declarar um manipulador de eventos no Visual Basic. Essa é a maneira que os manipuladores de eventos são gravados pelos designers ao programar no ambiente de desenvolvimento integrado (IDE). O `AddHandler` instrução é adequada para gerar eventos dinamicamente em tempo de execução.  
  
 Quando o evento ocorre, o Visual Basic chama automaticamente o procedimento de manipulador de eventos. Qualquer código que tenha acesso ao evento pode fazer com que ele ocorrer ao executar uma [instrução RaiseEvent](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Você pode associar mais de um manipulador de eventos com o mesmo evento. Em alguns casos, você pode desassociar um manipulador de um evento. Para obter mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Para chamar um manipulador de eventos usando identificadores e WithEvents  
  
1. Certifique-se de que o evento é declarado com um [declaração de evento](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2. Declarar uma variável de objeto no módulo ou classe de nível, usando o [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) palavra-chave. O `As` cláusula para essa variável deve especificar a classe que gera o evento.  
  
3. Na declaração de manipulação de eventos `Sub` procedimento, adicione uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula que especifica o `WithEvents` variável e o nome do evento.  
  
4. Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento. Seu código pode usar um `RaiseEvent` instrução para fazer com que o evento ocorrer.  
  
     O exemplo a seguir define um evento e um `WithEvents` variável que faz referência à classe que gera o evento. A manipulação de eventos `Sub` procedimento usa um `Handles` cláusula para especificar a classe e eventos que ele manipula.  
  
     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Para chamar um manipulador de eventos usando AddHandler  
  
1. Certifique-se de que o evento é declarado com um `Event` instrução.  
  
2. Executar uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) conectem-se dinamicamente a manipulação do evento `Sub` procedimento com o evento.  
  
3. Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento. Seu código pode usar um `RaiseEvent` instrução para fazer com que o evento ocorrer.  
  
     O exemplo a seguir define uma `Sub` procedimento para manipular o <xref:System.Windows.Forms.Form.Closing> evento de um formulário. Ele usa o [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) para associar a `catchClose` procedimento como um manipulador de eventos <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]  
  
     Você pode desassociar um manipulador de eventos de um evento executando o [Instrução RemoveHandler](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Subprocedimentos](./sub-procedures.md)
- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Como: criar um procedimento](./how-to-create-a-procedure.md)
- [Como: chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)

---
title: "Como chamar um manipulador de eventos no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "manipuladores de eventos"
  - "manipuladores de eventos, Chamando "
  - "procedimentos, Chamando "
  - "procedimentos, manipuladores de eventos"
  - "código do Visual Basic, procedimentos"
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como chamar um manipulador de eventos no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Um *evento* é uma ação ou ocorrência — como um mouse clique ou um limite de crédito excedido — que é reconhecida pelo componente algum de programa, e para o qual você pode escrever código para responder.  Um  *manipulador de eventos*  é o código que você escreve para responder a um evento.  
  
 Um manipulador de eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é um  procedimento `Sub`.  No entanto, você não pode chamá\-lo normalmente da mesma maneira que outros procedimentos `Sub`.  Em vez disso, você identificar o procedimento como um manipulador para o evento.  Você pode fazer isso com uma  cláusula [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) e uma variável [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md), ou com um [Instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).  Usando uma cláusula `Handles` é a maneira padrão para declarar um manipulador de eventos no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Essa é a maneira que os manipuladores de eventos são gravados pelos designers quando você programa in a ambiente de desenvolvimento integrado \(IDE\).  A instrução `AddHandler` é adequada para elevar eventos dinamicamente em tempo de execução.  
  
 Quando o evento ocorrer, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente chama o procedimento manipulador de eventos.  Qualquer código que tenha acesso ao evento pode fazer com que ele ocorrer ao executar uma [Instrução RaiseEvent](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Você pode associar mais de um manipulador de eventos com o mesmo evento.  Em alguns casos, você pode dissociar um manipulador de um evento.  Para obter mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md).  
  
### Para chamar um manipulador de eventos Usando identificadores e WithEvents  
  
1.  Certifique\-se de que o evento é declarado com um [Instrução Event](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Declare um variável de objeto no nível de classe ou Módulo, usando a palavra\-chave [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).  A cláusula `As` para esta variável deve especificar a classe que gera o evento.  
  
3.  Na declaração do procedimento `Sub` de manipulação de eventos, adicione uma cláusula [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) que especifica a variável `WithEvents` e o nome do evento.  
  
4.  Quando o evento ocorrer, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente chama o procedimento `Sub`.  Seu código pode usar uma declaração `RaiseEvent` para fazer o evento ocorrer.  
  
     O exemplo a seguir define um evento e uma variável `WithEvents`que faz referência à classe que gera o evento.  O procedimento de tratamento de eventos `Sub` usa uma cláusula `Handles` para especificar a classe e o evento que a cláusula manipula.  
  
     [!code-vb[VbVbcnProcedures#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### Para chamar um manipulador de eventos usando AddHandler  
  
1.  Certifique\-se de que o evento é declarado com uma declaração `Event`.  
  
2.  Execute uma [Instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) para conectar dinamicamente o procedimento de tratamento de eventos `Sub` com o evento.  
  
3.  Quando o evento ocorrer, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente chama o procedimento `Sub`.  Seu código pode usar uma declaração `RaiseEvent` para fazer o evento ocorrer.  
  
     O exemplo a seguir define um procedimento `Sub` para manipular o evento <xref:System.Windows.Forms.Form.Closing> de um formulário.  Ele usa, então, o [Instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) para associar o procedimento `catchClose` como um manipulador de eventos de <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Você pode dissociar um manipulador de eventos de um evento executando o [Instrução RemoveHandler](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Como criar um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [Como chamar um procedimento que não retorne um valor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)
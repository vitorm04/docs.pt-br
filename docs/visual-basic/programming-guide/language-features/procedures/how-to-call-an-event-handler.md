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
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216619"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Como: Chamar um manipulador de eventos no Visual Basic

Um *evento* é uma ação ou ocorrência — como um clique do mouse ou um limite de crédito excedido — que é reconhecido por algum componente do programa e para o qual você pode escrever código para responder. Um *manipulador de eventos* é o código que você escreve para responder a um evento.

 Um manipulador de eventos no Visual Basic é `Sub` um procedimento. No entanto, você normalmente não o chama da mesma maneira que `Sub` outros procedimentos. Em vez disso, você identifica o procedimento como um manipulador para o evento. Isso pode ser feito com uma cláusula [Handles](../../../language-reference/statements/handles-clause.md) e uma variável [WithEvents](../../../language-reference/modifiers/withevents.md) , ou com uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md). O uso `Handles` de uma cláusula é a maneira padrão de declarar um manipulador de eventos em Visual Basic. Essa é a maneira como os manipuladores de eventos são escritos pelos designers quando você programa no ambiente de desenvolvimento integrado (IDE). A `AddHandler` instrução é adequada para gerar eventos dinamicamente em tempo de execução.

 Quando o evento ocorre, Visual Basic chama automaticamente o procedimento do manipulador de eventos. Qualquer código que tenha acesso ao evento pode fazer com que ele ocorra executando uma [instrução RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Você pode associar mais de um manipulador de eventos com o mesmo evento. Em alguns casos, você pode dissociar um manipulador de um evento. Para obter mais informações, consulte [Eventos](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Para chamar um manipulador de eventos usando Handles e WithEvents

1. Verifique se o evento é declarado com uma [instrução de evento](../../../language-reference/statements/event-statement.md).

2. Declare uma variável de objeto no nível de módulo ou classe, usando a palavra-chave [WithEvents](../../../language-reference/modifiers/withevents.md) . A `As` cláusula para essa variável deve especificar a classe que gera o evento.

3. Na declaração do procedimento de manipulação `Sub` de eventos, adicione uma cláusula [Handles](../../../language-reference/statements/handles-clause.md) que especifica a `WithEvents` variável e o nome do evento.

4. Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento. Seu código pode usar uma `RaiseEvent` instrução para fazer o evento ocorrer.

     O exemplo a seguir define um evento e `WithEvents` uma variável que se refere à classe que gera o evento. O procedimento de manipulação `Sub` de eventos usa `Handles` uma cláusula para especificar a classe e o evento que ele manipula.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Para chamar um manipulador de eventos usando AddHandler

1. Verifique se o evento é declarado com uma `Event` instrução.

2. Execute uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) para conectar dinamicamente o procedimento de manipulação `Sub` de eventos com o evento.

3. Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento. Seu código pode usar uma `RaiseEvent` instrução para fazer o evento ocorrer.

     O exemplo a seguir define `Sub` um procedimento para manipular <xref:System.Windows.Forms.Form.Closing> o evento de um formulário. Em seguida, ele usa a [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) para `catchClose` associar o procedimento como um manipulador <xref:System.Windows.Forms.Form.Closing>de eventos para.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Você pode dissociar um manipulador de eventos de um evento executando a [instrução RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Consulte também

- [Procedimentos](index.md)
- [Subprocedimentos](sub-procedures.md)
- [Instrução Sub](../../../language-reference/statements/sub-statement.md)
- [Operador AddressOf](../../../language-reference/operators/addressof-operator.md)
- [Como: Criar um procedimento](how-to-create-a-procedure.md)
- [Como: Chamar um procedimento que não retorna um valor](how-to-call-a-procedure-that-does-not-return-a-value.md)

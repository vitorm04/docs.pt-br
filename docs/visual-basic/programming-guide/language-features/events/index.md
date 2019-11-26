---
title: Eventos
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345114"
---
# <a name="events-visual-basic"></a>Eventos (Visual Basic)
While you might visualize a Visual Studio project as a series of procedures that execute in a sequence, in reality, most programs are event driven—meaning the flow of execution is determined by external occurrences called *events*.  
  
 Um evento é um sinal que informa a um aplicativo que algo importante ocorreu. Por exemplo, quando um usuário clica em um controle em um formulário, o formulário pode lançar um evento `Click` e chamar um procedimento que manipula o evento. Os eventos também permitem que tarefas separadas se comuniquem. Por exemplo, digamos que seu aplicativo executa uma tarefa de classificação separadamente do aplicativo principal. Se um usuário cancelar a classificação, seu aplicativo poderá enviar um evento de cancelamento instruindo o processo de classificação para parar.  
  
## <a name="event-terms-and-concepts"></a>Conceitos e termos de evento  
 This section describes the terms and concepts used with events in Visual Basic.  
  
### <a name="declaring-events"></a>Declarando eventos  
 Você declara eventos dentro de classes, estruturas, módulos e interfaces usando a palavra-chave `Event`, como no exemplo a seguir:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Acionando eventos  
 Um evento é como uma mensagem anunciando que algo importante ocorreu. O ato de transmitir a mensagem é chamado para *acionar* o evento. In Visual Basic, you raise events with the `RaiseEvent` statement, as in the following example:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Os eventos devem ser acionados dentro do escopo da classe, módulo ou estrutura na qual eles são declarados. Por exemplo, uma classe derivada não pode acionar eventos herdados de uma classe base.  
  
### <a name="event-senders"></a>Remetentes do evento  
 Qualquer objeto capaz de acionar um evento é um *remetente do evento*, também conhecido como uma *origem do evento*. Formulários, controles e objetos definidos pelo usuário são exemplos de remetentes de eventos.  
  
### <a name="event-handlers"></a>Manipuladores de Eventos  
 *Manipuladores de eventos* são procedimentos que são chamados quando ocorre um evento correspondente. Você pode usar qualquer sub-rotina válida com uma assinatura correspondente como um manipulador de eventos. Você não pode usar uma função como um manipulador de eventos, porque ela não retorna um valor para a origem do evento.  
  
 Visual Basic uses a standard naming convention for event handlers that combines the name of the event sender, an underscore, and the name of the event. Por exemplo, o evento `Click` de um botão chamado `button1` seria nomeado `Sub button1_Click`.  
  
> [!NOTE]
> É recomendável que você use esta convenção de nomenclatura ao definir manipuladores de eventos para seus próprios eventos, mas não é necessário. Você pode usar qualquer nome de sub-rotina válido.  
  
## <a name="associating-events-with-event-handlers"></a>Associar eventos a manipuladores de eventos  
 Antes de um manipulador de eventos se tornar útil, você deve primeiro associá-lo a um evento usando a instrução `Handles` ou `AddHandler`.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents e a cláusula Handles  
 A instrução `WithEvents` e a cláusula `Handles` fornecem uma maneira declarativa de especificar os manipuladores de eventos. Um evento gerado por um objeto declarado com a palavra-chave `WithEvents` pode ser tratado por qualquer procedimento com uma instrução `Handles` para esse evento, conforme mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 A instrução `WithEvents` e a cláusula `Handles` geralmente são a melhor opção para manipuladores de eventos, pois a sintaxe declarativa usada torna mais fácil a codificação, a leitura e a depuração para a manipulação de eventos. No entanto, esteja ciente das seguintes limitações no uso de variáveis `WithEvents`:  
  
- Não é possível usar uma variável `WithEvents` como uma variável de objeto. Ou seja, você não pode declará-la como `Object`— você deve especificar o nome da classe quando declarar a variável.  
  
- Because shared events are not tied to class instances, you cannot use `WithEvents` to declaratively handle shared events. Da mesma forma, você não pode usar `WithEvents` ou `Handles` para manipular eventos de um `Structure`. Em ambos os casos, você pode usar a instrução `AddHandler` para manipular esses eventos.  
  
- Não é possível criar matrizes de variáveis `WithEvents`.  
  
 As variáveis `WithEvents` permitem que um único manipulador de eventos manipule um ou mais tipos de evento, ou que um ou mais manipuladores de eventos manipulem o mesmo tipo de evento.  
  
 Embora a cláusula `Handles` seja a maneira padrão de associar um evento a um manipulador de eventos, ela é limitada a associar eventos a manipuladores de eventos em tempo de compilação.  
  
 In some cases, such as with events associated with forms or controls, Visual Basic automatically stubs out an empty event handler and associates it with an event. For example, when you double-click a command button on a form in design mode, Visual Basic creates an empty event handler and a `WithEvents` variable for the command button, as in the following code:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler e RemoveHandler  
 A instrução `AddHandler` é semelhante à cláusula `Handles`, pois ambas permitem que você especifique um manipulador de eventos. No entanto, `AddHandler`, usado com `RemoveHandler`, fornece maior flexibilidade do que a cláusula `Handles`, permitindo que você adicione, remova e altere dinamicamente o manipulador de eventos associado a um evento. Se quiser manipular eventos compartilhados ou eventos de uma estrutura, você deverá usar `AddHandler`.  
  
 `AddHandler` leva dois argumentos: o nome de um evento de um remetente do evento, como um controle, e uma expressão que avalia um delegado. Você não precisa especificar explicitamente a classe delegado ao usar `AddHandler`, pois a instrução `AddressOf` sempre retorna uma referência ao delegado. O exemplo a seguir associa um manipulador de eventos a um evento acionado por um objeto:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 `RemoveHandler`, que desconecta um evento de um manipulador de eventos, usa a mesma sintaxe que `AddHandler`. Por exemplo:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 No exemplo a seguir, um manipulador de eventos é associado a um evento e o evento é acionado. O manipulador de evento captura o evento e exibe uma mensagem.  
  
 Em seguida, o primeiro manipulador de eventos é removido e um manipulador de eventos diferente é associado ao evento. Quando o evento for acionado novamente, será exibida uma mensagem diferente.  
  
 Por fim, o segundo manipulador de eventos é removido e o evento é acionado pela terceira vez. Como não há um manipulador de eventos associado ao evento, nenhuma ação será tomada.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Manipulação de eventos herdados de uma classe base  
 *Classes derivadas* — classes que herdam características de uma classe base e que podem manipular eventos acionados por suas classes base usando a instrução `Handles MyBase`.  
  
### <a name="to-handle-events-from-a-base-class"></a>Como manipular eventos de uma classe base  
  
- Declare um manipulador de eventos na classe derivada adicionando uma instrução `Handles MyBase.` *eventname* à linha da declaração de seu procedimento do manipulador de eventos, no qual *eventname* é o nome do evento na classe base manipulada. Por exemplo:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>Seções relacionadas  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Instruções passo a passo: declarando e acionando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Fornece uma descrição passo a passo de como declarar e acionar eventos para uma classe.|  
|[Instruções passo a passo: tratando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Demonstra como escrever um procedimento de manipulador de eventos.|  
|[Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Demonstra como definir um evento personalizado que permite que seus manipuladores de eventos sejam chamados assincronicamente.|  
|[Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Demonstra como definir um evento personalizado que utiliza memória somente quando o evento é manipulado.|  
|[Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Lista problemas comuns que ocorrem com os manipuladores de eventos em componentes herdados.|  
|[Eventos](../../../../standard/events/index.md)|Apresenta uma visão geral do modelo de evento no .NET Framework.|  
|[Criando manipuladores de eventos no Windows Forms](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Descreve como trabalhar com eventos associados aos objetos do Windows Forms.|  
|[Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Fornece uma visão geral de delegados no Visual Basic.|

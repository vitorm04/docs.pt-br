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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: dc0174d50c7b5f5cda9d057bce39960b3e563f4e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="3b75b-102">Como chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b75b-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="3b75b-103">Um *evento* é uma ação ou ocorrência — como um mouse clique ou um limite de crédito excedido — que é reconhecida pelo componente algum programa, e para o qual você pode escrever código para responder.</span><span class="sxs-lookup"><span data-stu-id="3b75b-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="3b75b-104">Um *manipulador de eventos* é o código que você escreve para responder a um evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="3b75b-105">Um manipulador de eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-105">An event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="3b75b-106">No entanto, você não chamá-lo normalmente a mesma maneira que outras `Sub` procedimentos.</span><span class="sxs-lookup"><span data-stu-id="3b75b-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="3b75b-107">Em vez disso, você deve identificar o procedimento como um manipulador para o evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="3b75b-108">Você pode fazer isso com um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula e um [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variável, ou com um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b75b-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="3b75b-109">Usando um `Handles` cláusula é a maneira padrão para declarar um manipulador de eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b75b-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="3b75b-110">Essa é a maneira que os manipuladores de eventos são gravados pelos designers quando você programa no ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="3b75b-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="3b75b-111">O `AddHandler` instrução é adequada para elevar eventos dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3b75b-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="3b75b-112">Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente chama o procedimento de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3b75b-112">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="3b75b-113">Qualquer código que tenha acesso ao evento pode fazer com que ele ocorrer ao executar uma [instrução RaiseEvent](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b75b-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="3b75b-114">Você pode associar mais de um manipulador de eventos com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="3b75b-115">Em alguns casos você pode dissociar um manipulador de um evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="3b75b-116">Para obter mais informações, consulte [eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b75b-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="3b75b-117">Para chamar um manipulador de eventos usando identificadores e WithEvents</span><span class="sxs-lookup"><span data-stu-id="3b75b-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="3b75b-118">Verifique se o evento é declarado com um [declaração de evento](../../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b75b-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="3b75b-119">Declare uma variável de objeto no módulo ou classe de nível, usando o [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="3b75b-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="3b75b-120">O `As` cláusula para esta variável deve especificar a classe que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="3b75b-121">Na declaração do manipulador de eventos `Sub` procedimento, adicione uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula que especifica o `WithEvents` variável e o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="3b75b-122">Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama automaticamente o `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-122">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="3b75b-123">Seu código pode usar uma `RaiseEvent` instrução para fazer com que o evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="3b75b-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="3b75b-124">O exemplo a seguir define um evento e um `WithEvents` variável que faz referência à classe que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="3b75b-125">A manipulação de eventos `Sub` procedimento usa um `Handles` cláusula para especificar a classe e o evento manipula.</span><span class="sxs-lookup"><span data-stu-id="3b75b-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     <span data-ttu-id="3b75b-126">[!code-vb[VbVbcnProcedures n º&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3b75b-126">[!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span></span>  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="3b75b-127">Para chamar um manipulador de eventos usando AddHandler</span><span class="sxs-lookup"><span data-stu-id="3b75b-127">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="3b75b-128">Verifique se o evento é declarado com um `Event` instrução.</span><span class="sxs-lookup"><span data-stu-id="3b75b-128">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="3b75b-129">Executar uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) conectem dinamicamente a manipulação de eventos `Sub` procedimento com o evento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-129">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="3b75b-130">Quando o evento ocorre, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] chama automaticamente o `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3b75b-130">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="3b75b-131">Seu código pode usar uma `RaiseEvent` instrução para fazer com que o evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="3b75b-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="3b75b-132">O exemplo a seguir define uma `Sub` procedimento para manipular o <xref:System.Windows.Forms.Form.Closing>evento de um formulário.</xref:System.Windows.Forms.Form.Closing></span><span class="sxs-lookup"><span data-stu-id="3b75b-132">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="3b75b-133">Ele usa o [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) para associar o `catchClose` procedimento como um manipulador de eventos <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing></span><span class="sxs-lookup"><span data-stu-id="3b75b-133">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     <span data-ttu-id="3b75b-134">[!code-vb[VbVbcnProcedures n º&5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3b75b-134">[!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span></span>  
  
     <span data-ttu-id="3b75b-135">Você pode dissociar um manipulador de eventos de um evento executando o [Instrução RemoveHandler](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b75b-135">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b75b-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b75b-136">See Also</span></span>  
 <span data-ttu-id="3b75b-137">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="3b75b-137">[Procedures](./index.md) </span></span>  
<span data-ttu-id="3b75b-138"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="3b75b-138"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="3b75b-139"> [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3b75b-139"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="3b75b-140"> [Operador AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="3b75b-140"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="3b75b-141"> [Como: criar um procedimento](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3b75b-141"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="3b75b-142"> [Como chamar um procedimento que não retorne um valor](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="3b75b-142"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>

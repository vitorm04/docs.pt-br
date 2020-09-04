---
title: Como chamar um manipulador de eventos
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464955"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="97753-102">Como chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97753-102">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="97753-103">Um *evento* é uma ação ou ocorrência — como um clique do mouse ou um limite de crédito excedido — que é reconhecido por algum componente do programa e para o qual você pode escrever código para responder.</span><span class="sxs-lookup"><span data-stu-id="97753-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="97753-104">Um *manipulador de eventos* é o código que você escreve para responder a um evento.</span><span class="sxs-lookup"><span data-stu-id="97753-104">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="97753-105">Um manipulador de eventos no Visual Basic é um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="97753-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="97753-106">No entanto, você normalmente não o chama da mesma maneira que outros `Sub` procedimentos.</span><span class="sxs-lookup"><span data-stu-id="97753-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="97753-107">Em vez disso, você identifica o procedimento como um manipulador para o evento.</span><span class="sxs-lookup"><span data-stu-id="97753-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="97753-108">Isso pode ser feito com uma [`Handles`](../../../language-reference/statements/handles-clause.md) cláusula e uma [`WithEvents`](../../../language-reference/modifiers/withevents.md) variável, ou com uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97753-108">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="97753-109">O uso de uma `Handles` cláusula é a maneira padrão de declarar um manipulador de eventos em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="97753-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="97753-110">Essa é a maneira como os manipuladores de eventos são escritos pelos designers quando você programa no ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="97753-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="97753-111">A `AddHandler` instrução é adequada para gerar eventos dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="97753-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="97753-112">Quando o evento ocorre, Visual Basic chama automaticamente o procedimento do manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="97753-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="97753-113">Qualquer código que tenha acesso ao evento pode fazer com que ele ocorra executando uma [instrução RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97753-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="97753-114">Você pode associar mais de um manipulador de eventos com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="97753-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="97753-115">Em alguns casos, você pode dissociar um manipulador de um evento.</span><span class="sxs-lookup"><span data-stu-id="97753-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="97753-116">Para obter mais informações, consulte [Eventos](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="97753-116">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a><span data-ttu-id="97753-117">Chamar um manipulador de eventos usando :::no-loc text="Handles"::: e WithEvents</span><span class="sxs-lookup"><span data-stu-id="97753-117">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="97753-118">Verifique se o evento é declarado com uma [instrução de evento](../../../language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97753-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="97753-119">Declare uma variável de objeto no nível de módulo ou classe, usando a [`WithEvents`](../../../language-reference/modifiers/withevents.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="97753-119">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="97753-120">A `As` cláusula para essa variável deve especificar a classe que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="97753-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="97753-121">Na declaração do procedimento de manipulação de eventos `Sub` , adicione uma [`Handles`](../../../language-reference/statements/handles-clause.md) cláusula que especifica a `WithEvents` variável e o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="97753-121">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="97753-122">Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="97753-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="97753-123">Seu código pode usar uma `RaiseEvent` instrução para fazer o evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="97753-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="97753-124">O exemplo a seguir define um evento e uma `WithEvents` variável que se refere à classe que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="97753-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="97753-125">O procedimento de manipulação de eventos `Sub` usa uma `Handles` cláusula para especificar a classe e o evento que ele manipula.</span><span class="sxs-lookup"><span data-stu-id="97753-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="97753-126">Chamar um manipulador de eventos usando AddHandler</span><span class="sxs-lookup"><span data-stu-id="97753-126">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="97753-127">Verifique se o evento é declarado com uma `Event` instrução.</span><span class="sxs-lookup"><span data-stu-id="97753-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="97753-128">Execute uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) para conectar dinamicamente o procedimento de manipulação de eventos `Sub` com o evento.</span><span class="sxs-lookup"><span data-stu-id="97753-128">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="97753-129">Quando o evento ocorre, Visual Basic chama automaticamente o `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="97753-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="97753-130">Seu código pode usar uma `RaiseEvent` instrução para fazer o evento ocorrer.</span><span class="sxs-lookup"><span data-stu-id="97753-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="97753-131">O exemplo a seguir usa a [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) no construtor para associar o `OnFormClosing` procedimento como um manipulador de eventos para <xref:System.Windows.Forms.Form.FormClosing> .</span><span class="sxs-lookup"><span data-stu-id="97753-131">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="97753-132">Você pode dissociar um manipulador de eventos de um evento executando a [instrução RemoveHandler](../../../language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97753-132">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97753-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="97753-133">See also</span></span>

- [<span data-ttu-id="97753-134">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="97753-134">Procedures</span></span>](index.md)
- [<span data-ttu-id="97753-135">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="97753-135">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="97753-136">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="97753-136">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="97753-137">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="97753-137">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="97753-138">Como criar um procedimento</span><span class="sxs-lookup"><span data-stu-id="97753-138">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="97753-139">Como chamar um procedimento que não retorne um valor</span><span class="sxs-lookup"><span data-stu-id="97753-139">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)

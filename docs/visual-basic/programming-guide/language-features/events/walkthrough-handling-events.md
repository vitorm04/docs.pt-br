---
title: Manipulação de eventos (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1743e5f5d9dcdf83ab646407cd1fcdc77ff71cd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="8040f-102">Instruções passo a passo: tratando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8040f-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="8040f-103">Este é o segundo dos dois tópicos que demonstram como trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="8040f-104">O primeiro tópico, [passo a passo: declarativo e geração de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), mostra como declarar e gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="8040f-105">Esta seção usa o formulário e a classe a partir desse passo a passo que mostram como tratar eventos quando eles ocorrem.</span><span class="sxs-lookup"><span data-stu-id="8040f-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="8040f-106">O `Widget` usa o exemplo de classe tradicionais instruções de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="8040f-107">Visual Basic fornece outras técnicas para trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="8040f-108">Como um exercício, você pode modificar esse exemplo para usar o `AddHandler` e `Handles` instruções.</span><span class="sxs-lookup"><span data-stu-id="8040f-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="8040f-109">Para manipular o evento PercentDone da classe Widget</span><span class="sxs-lookup"><span data-stu-id="8040f-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="8040f-110">Coloque o seguinte código em `Form1`:</span><span class="sxs-lookup"><span data-stu-id="8040f-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="8040f-111">O `WithEvents` palavra-chave especifica que a variável `mWidget` é usada para manipular eventos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="8040f-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="8040f-112">Você pode especificar o tipo de objeto, fornecendo o nome da classe da qual o objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="8040f-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="8040f-113">A variável `mWidget` declarado em `Form1` porque `WithEvents` variáveis devem ser o nível de classe.</span><span class="sxs-lookup"><span data-stu-id="8040f-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="8040f-114">Isso é verdadeiro independentemente do tipo de classe que colocá-las no.</span><span class="sxs-lookup"><span data-stu-id="8040f-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="8040f-115">A variável `mblnCancel` é usado para cancelar o `LongTask` método.</span><span class="sxs-lookup"><span data-stu-id="8040f-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="8040f-116">Escrevendo código para manipular um evento</span><span class="sxs-lookup"><span data-stu-id="8040f-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="8040f-117">Assim que você declara uma variável usando `WithEvents`, o nome da variável é exibido na lista suspensa à esquerda da classe de **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="8040f-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="8040f-118">Quando você seleciona `mWidget`, o `Widget` eventos da classe aparecem na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="8040f-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="8040f-119">Selecionando um evento exibe o procedimento de evento correspondente, com o prefixo `mWidget` e um caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="8040f-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="8040f-120">Todos os procedimentos de evento associados com um `WithEvents` variável recebem o nome da variável como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="8040f-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="8040f-121">Para identificar um evento</span><span class="sxs-lookup"><span data-stu-id="8040f-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="8040f-122">Selecione `mWidget` da lista suspensa à esquerda no **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="8040f-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="8040f-123">Selecione o `PercentDone` evento na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="8040f-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="8040f-124">O **Editor de códigos** abre o `mWidget_PercentDone` procedimento de evento.</span><span class="sxs-lookup"><span data-stu-id="8040f-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8040f-125">O **Editor de códigos** é útil, mas não é necessária, para inserir novos manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="8040f-126">Neste passo a passo, é mais direto para copiar apenas os manipuladores de eventos diretamente em seu código.</span><span class="sxs-lookup"><span data-stu-id="8040f-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="8040f-127">Adicione o seguinte código ao manipulador de eventos do `mWidget_PercentDone`:</span><span class="sxs-lookup"><span data-stu-id="8040f-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="8040f-128">Sempre que o `PercentDone` é gerado, o procedimento de evento exibe a porcentagem concluída em um `Label` controle.</span><span class="sxs-lookup"><span data-stu-id="8040f-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="8040f-129">O `DoEvents` método permite que o rótulo redesenhar e também permite que o usuário clique o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="8040f-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="8040f-130">Adicione o seguinte código para o `Button2_Click` manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="8040f-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="8040f-131">Se o usuário clica o **Cancelar** botão ao `LongTask` está em execução, o `Button2_Click` evento é executado assim que o `DoEvents` instrução permite o processamento de evento ocorra.</span><span class="sxs-lookup"><span data-stu-id="8040f-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="8040f-132">A variável de nível de classe `mblnCancel` é definido como `True`e o `mWidget_PercentDone` evento, em seguida, testa e define o `ByRef Cancel` argumento `True`.</span><span class="sxs-lookup"><span data-stu-id="8040f-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="8040f-133">Conectar-se a uma variável WithEvents para um objeto</span><span class="sxs-lookup"><span data-stu-id="8040f-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="8040f-134">`Form1` agora está configurada para manipular um `Widget` eventos do objeto.</span><span class="sxs-lookup"><span data-stu-id="8040f-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="8040f-135">Tudo o que falta é localizar um `Widget` em algum lugar.</span><span class="sxs-lookup"><span data-stu-id="8040f-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="8040f-136">Quando você declara uma variável `WithEvents` em tempo de design, nenhum objeto está associado ele.</span><span class="sxs-lookup"><span data-stu-id="8040f-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="8040f-137">Um `WithEvents` variável é exatamente como qualquer outra variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="8040f-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="8040f-138">Você precisa criar um objeto e atribuir uma referência a ele com o `WithEvents` variável.</span><span class="sxs-lookup"><span data-stu-id="8040f-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="8040f-139">Para criar um objeto e atribuir uma referência a ele</span><span class="sxs-lookup"><span data-stu-id="8040f-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="8040f-140">Selecione **(Form1 Events)** da lista suspensa à esquerda no **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="8040f-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="8040f-141">Selecione o `Load` evento na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="8040f-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="8040f-142">O **Editor de códigos** abre o `Form1_Load` procedimento de evento.</span><span class="sxs-lookup"><span data-stu-id="8040f-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="8040f-143">Adicione o seguinte código para o `Form1_Load` procedimento de evento para criar o `Widget`:</span><span class="sxs-lookup"><span data-stu-id="8040f-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="8040f-144">Quando esse código é executado, o Visual Basic cria um `Widget` do objeto e conecta seus eventos para os procedimentos de evento associados `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="8040f-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="8040f-145">Partir desse ponto, sempre que o `Widget` gera seu `PercentDone` evento, o `mWidget_PercentDone` evento procedimento é executado.</span><span class="sxs-lookup"><span data-stu-id="8040f-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="8040f-146">Para chamar o método LongTask</span><span class="sxs-lookup"><span data-stu-id="8040f-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="8040f-147">Adicione o seguinte código ao manipulador de eventos do `Button1_Click`:</span><span class="sxs-lookup"><span data-stu-id="8040f-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="8040f-148">Antes do `LongTask` método é chamado, o rótulo que exibe o percentual de conclusão deve ser inicializado e o nível de classe `Boolean` sinalizador para cancelar o método deve ser definido como `False`.</span><span class="sxs-lookup"><span data-stu-id="8040f-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="8040f-149">`LongTask` é chamado com duração de uma tarefa de 12.2 segundos.</span><span class="sxs-lookup"><span data-stu-id="8040f-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="8040f-150">O `PercentDone` é gerado uma vez cada um terço de um segundo.</span><span class="sxs-lookup"><span data-stu-id="8040f-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="8040f-151">Cada vez que o evento é gerado, o `mWidget_PercentDone` evento procedimento é executado.</span><span class="sxs-lookup"><span data-stu-id="8040f-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="8040f-152">Quando `LongTask` é feita, `mblnCancel` é testado para ver se `LongTask` foi encerrado normalmente, ou se ele tiver parado porque `mblnCancel` foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="8040f-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="8040f-153">A porcentagem concluída é atualizada somente no caso anterior.</span><span class="sxs-lookup"><span data-stu-id="8040f-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="8040f-154">Para executar o programa</span><span class="sxs-lookup"><span data-stu-id="8040f-154">To run the program</span></span>  
  
1.  <span data-ttu-id="8040f-155">Pressione F5 para colocar o projeto no modo de execução.</span><span class="sxs-lookup"><span data-stu-id="8040f-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="8040f-156">Clique o **Iniciar tarefa** botão.</span><span class="sxs-lookup"><span data-stu-id="8040f-156">Click the **Start Task** button.</span></span> <span data-ttu-id="8040f-157">Cada vez que o `PercentDone` evento é gerado, o rótulo é atualizado com a porcentagem da tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="8040f-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="8040f-158">Clique o **Cancelar** botão para interromper a tarefa.</span><span class="sxs-lookup"><span data-stu-id="8040f-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="8040f-159">Observe que a aparência do **Cancelar** botão não é alterado imediatamente quando você clica nele.</span><span class="sxs-lookup"><span data-stu-id="8040f-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="8040f-160">O `Click` evento não pode ocorrer até que o `My.Application.DoEvents` instrução permite o processamento de eventos.</span><span class="sxs-lookup"><span data-stu-id="8040f-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8040f-161">O `My.Application.DoEvents` método não processa os eventos exatamente da mesma maneira como faz o formulário.</span><span class="sxs-lookup"><span data-stu-id="8040f-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="8040f-162">Por exemplo, este passo a passo, você deve clicar no **Cancelar** botão duas vezes.</span><span class="sxs-lookup"><span data-stu-id="8040f-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="8040f-163">Para permitir que o formulário para manipular os eventos diretamente, você pode usar multithreading.</span><span class="sxs-lookup"><span data-stu-id="8040f-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="8040f-164">Para obter mais informações, consulte [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="8040f-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="8040f-165">Você pode achar instrutivos para executar o programa com F11 e percorrer o código uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="8040f-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="8040f-166">Você pode ver claramente como entrada de execução `LongTask`e, em seguida, brevemente reinserido `Form1` cada vez que o `PercentDone` é gerado.</span><span class="sxs-lookup"><span data-stu-id="8040f-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="8040f-167">O que aconteceria se, durante a execução foi novamente no código de `Form1`, o `LongTask` método foi chamado novamente?</span><span class="sxs-lookup"><span data-stu-id="8040f-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="8040f-168">Na pior das hipóteses, um estouro de pilha pode ocorrer se `LongTask` foi chamado sempre que o evento foi gerado.</span><span class="sxs-lookup"><span data-stu-id="8040f-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="8040f-169">Você pode fazer com que a variável `mWidget` para manipular eventos para outro `Widget` objeto atribuindo uma referência para o novo `Widget` para `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="8040f-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="8040f-170">Na verdade, você pode tornar o código em `Button1_Click` isso toda vez que você clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="8040f-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="8040f-171">Para manipular eventos para um widget diferente</span><span class="sxs-lookup"><span data-stu-id="8040f-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="8040f-172">Adicione a seguinte linha de código para o `Button1_Click` procedimento, logo após a linha que lê `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="8040f-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="8040f-173">O código acima cria um novo `Widget` cada vez que o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="8040f-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="8040f-174">Assim que o `LongTask` método é concluído, a referência para o `Widget` é liberado e o `Widget` é destruído.</span><span class="sxs-lookup"><span data-stu-id="8040f-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="8040f-175">Um `WithEvents` variável pode conter apenas um objeto de referência ao mesmo tempo, portanto, se você atribuir outro `Widget` do objeto para `mWidget`, anterior `Widget` eventos do objeto não serão tratados.</span><span class="sxs-lookup"><span data-stu-id="8040f-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="8040f-176">Se `mWidget` é a única variável de objeto que contém uma referência para o antigo `Widget`, o objeto é destruído.</span><span class="sxs-lookup"><span data-stu-id="8040f-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="8040f-177">Se você desejar tratar eventos de vários `Widget` objetos, use o `AddHandler` instrução para processar eventos de cada objeto separadamente.</span><span class="sxs-lookup"><span data-stu-id="8040f-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8040f-178">Você pode declarar tantos `WithEvents` variáveis que você precisam, mas matrizes de `WithEvents` variáveis não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="8040f-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8040f-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8040f-179">See Also</span></span>  
 [<span data-ttu-id="8040f-180">Instruções passo a passo: declarando e acionando eventos</span><span class="sxs-lookup"><span data-stu-id="8040f-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="8040f-181">Eventos</span><span class="sxs-lookup"><span data-stu-id="8040f-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)

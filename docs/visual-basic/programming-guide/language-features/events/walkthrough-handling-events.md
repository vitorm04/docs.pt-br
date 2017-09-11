---
title: "Manipulação de eventos (Visual Basic) | Documentos do Microsoft"
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
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
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
ms.openlocfilehash: b4ad77b3b0236e762fc17b8aba9d34108c8d75b5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="01874-102">Instruções passo a passo: tratando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01874-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="01874-103">Este é o segundo dos dois tópicos que demonstram como trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="01874-104">O primeiro tópico, [passo a passo: declarativo e levantando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), mostra como declarar e gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="01874-105">Esta seção usa o formulário e a classe dessa explicação passo a passo que mostram como tratar eventos quando eles ocorrem.</span><span class="sxs-lookup"><span data-stu-id="01874-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="01874-106">O `Widget` usa o exemplo de classe tradicionais instruções de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-106">The `Widget` class example uses traditional event-handling statements.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="01874-107">fornece outras técnicas para trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-107"> provides other techniques for working with events.</span></span> <span data-ttu-id="01874-108">Como um exercício, você pode modificar este exemplo para usar o `AddHandler` e `Handles` instruções.</span><span class="sxs-lookup"><span data-stu-id="01874-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="01874-109">Para manipular o evento PercentDone da classe Widget</span><span class="sxs-lookup"><span data-stu-id="01874-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="01874-110">Coloque o seguinte código no `Form1`:</span><span class="sxs-lookup"><span data-stu-id="01874-110">Place the following code in `Form1`:</span></span>  
  
     <span data-ttu-id="01874-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span></span>  
  
     <span data-ttu-id="01874-112">O `WithEvents` palavra-chave especifica que a variável `mWidget` é usada para manipular eventos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="01874-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="01874-113">Você pode especificar o tipo de objeto, fornecendo o nome da classe da qual o objeto será criado.</span><span class="sxs-lookup"><span data-stu-id="01874-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="01874-114">A variável `mWidget` é declarada em `Form1` porque `WithEvents` variáveis devem estar no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="01874-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="01874-115">Isso é verdadeiro independentemente do tipo de classe em que é colocá-los.</span><span class="sxs-lookup"><span data-stu-id="01874-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="01874-116">A variável `mblnCancel` é usado para cancelar o `LongTask` método.</span><span class="sxs-lookup"><span data-stu-id="01874-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="01874-117">Escrever código para manipular um evento</span><span class="sxs-lookup"><span data-stu-id="01874-117">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="01874-118">Assim que você declara uma variável usando `WithEvents`, o nome da variável é exibido na lista suspensa à esquerda da classe **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="01874-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="01874-119">Quando você seleciona `mWidget`, o `Widget` eventos da classe aparecem na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="01874-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="01874-120">Selecionando um evento exibe o procedimento de evento correspondente, com o prefixo `mWidget` e um caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="01874-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="01874-121">Todos os procedimentos de evento associados com um `WithEvents` variável recebem o nome da variável como um prefixo.</span><span class="sxs-lookup"><span data-stu-id="01874-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="01874-122">Para identificar um evento</span><span class="sxs-lookup"><span data-stu-id="01874-122">To handle an event</span></span>  
  
1.  <span data-ttu-id="01874-123">Selecione `mWidget` da lista suspensa à esquerda no **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="01874-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="01874-124">Selecione o `PercentDone` evento na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="01874-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="01874-125">O **Editor de códigos** abre o `mWidget_PercentDone` procedimento de evento.</span><span class="sxs-lookup"><span data-stu-id="01874-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01874-126">O **Editor de códigos** é útil, mas não obrigatórios, para inserir novos manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="01874-127">Neste passo a passo, é mais direto para copiar apenas os manipuladores de eventos diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="01874-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="01874-128">Adicione o seguinte código ao manipulador de eventos do `mWidget_PercentDone`:</span><span class="sxs-lookup"><span data-stu-id="01874-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     <span data-ttu-id="01874-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span></span>  
  
     <span data-ttu-id="01874-130">Sempre que o `PercentDone` é gerado, o procedimento de evento exibe a porcentagem concluída em um `Label` controle.</span><span class="sxs-lookup"><span data-stu-id="01874-130">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="01874-131">O `DoEvents` método permite que o rótulo a ser redesenhado e também permite que o usuário clique o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="01874-131">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="01874-132">Adicione o seguinte código para o `Button2_Click` manipulador de eventos:</span><span class="sxs-lookup"><span data-stu-id="01874-132">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     <span data-ttu-id="01874-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span></span>  
  
 <span data-ttu-id="01874-134">Se o usuário clica o **Cancelar** botão enquanto `LongTask` está em execução, o `Button2_Click` evento é executado assim que o `DoEvents` instrução permite o processamento de evento ocorra.</span><span class="sxs-lookup"><span data-stu-id="01874-134">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="01874-135">A variável de nível de classe `mblnCancel` é definido como `True`e o `mWidget_PercentDone` eventos, em seguida, testa-o e define o `ByRef Cancel` argumento `True`.</span><span class="sxs-lookup"><span data-stu-id="01874-135">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="01874-136">Conectar-se a uma variável WithEvents para um objeto</span><span class="sxs-lookup"><span data-stu-id="01874-136">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="01874-137">`Form1`agora está configurado para manipular um `Widget` eventos do objeto.</span><span class="sxs-lookup"><span data-stu-id="01874-137">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="01874-138">Tudo o que falta é localizar um `Widget` em algum lugar.</span><span class="sxs-lookup"><span data-stu-id="01874-138">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="01874-139">Quando você declara uma variável `WithEvents` em tempo de design, nenhum objeto é associado a ele.</span><span class="sxs-lookup"><span data-stu-id="01874-139">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="01874-140">Um `WithEvents` variável é exatamente como qualquer outra variável de objeto.</span><span class="sxs-lookup"><span data-stu-id="01874-140">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="01874-141">Você precisa criar um objeto e atribuir uma referência a ele com o `WithEvents` variável.</span><span class="sxs-lookup"><span data-stu-id="01874-141">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="01874-142">Para criar um objeto e atribuir uma referência a ele</span><span class="sxs-lookup"><span data-stu-id="01874-142">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="01874-143">Selecione **(Form1 Events)** da lista suspensa à esquerda no **Editor de código**.</span><span class="sxs-lookup"><span data-stu-id="01874-143">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="01874-144">Selecione o `Load` evento na lista suspensa à direita.</span><span class="sxs-lookup"><span data-stu-id="01874-144">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="01874-145">O **Editor de códigos** abre o `Form1_Load` procedimento de evento.</span><span class="sxs-lookup"><span data-stu-id="01874-145">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="01874-146">Adicione o seguinte código para o `Form1_Load` procedimento de evento para criar o `Widget`:</span><span class="sxs-lookup"><span data-stu-id="01874-146">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     <span data-ttu-id="01874-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span></span>  
  
 <span data-ttu-id="01874-148">Quando esse código é executado, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria um `Widget` do objeto e conecta seus eventos para os procedimentos de evento associados `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="01874-148">When this code executes, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="01874-149">Partir desse ponto, sempre que o `Widget` gera seu `PercentDone` evento, o `mWidget_PercentDone` procedimento de evento é executado.</span><span class="sxs-lookup"><span data-stu-id="01874-149">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="01874-150">Para chamar o método LongTask</span><span class="sxs-lookup"><span data-stu-id="01874-150">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="01874-151">Adicione o seguinte código ao manipulador de eventos do `Button1_Click`:</span><span class="sxs-lookup"><span data-stu-id="01874-151">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     <span data-ttu-id="01874-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span></span>  
  
 <span data-ttu-id="01874-153">Antes do `LongTask` método é chamado, o rótulo que exibe o percentual de conclusão deve ser inicializado e o nível de classe `Boolean` sinalizador para cancelar o método deve ser definido como `False`.</span><span class="sxs-lookup"><span data-stu-id="01874-153">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="01874-154">`LongTask`é chamado com a duração de uma tarefa de 12.2 segundos.</span><span class="sxs-lookup"><span data-stu-id="01874-154">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="01874-155">O `PercentDone` é gerado uma vez cada um terço de um segundo.</span><span class="sxs-lookup"><span data-stu-id="01874-155">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="01874-156">Cada vez que o evento é gerado, o `mWidget_PercentDone` procedimento de evento é executado.</span><span class="sxs-lookup"><span data-stu-id="01874-156">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="01874-157">Quando `LongTask` é feita, `mblnCancel` é testado para ver se `LongTask` terminou normalmente, ou se ele parou, pois `mblnCancel` foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="01874-157">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="01874-158">A porcentagem concluída é atualizada somente no caso anterior.</span><span class="sxs-lookup"><span data-stu-id="01874-158">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="01874-159">Para executar o programa</span><span class="sxs-lookup"><span data-stu-id="01874-159">To run the program</span></span>  
  
1.  <span data-ttu-id="01874-160">Pressione F5 para colocar o projeto no modo de execução.</span><span class="sxs-lookup"><span data-stu-id="01874-160">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="01874-161">Clique o **Iniciar tarefa** botão.</span><span class="sxs-lookup"><span data-stu-id="01874-161">Click the **Start Task** button.</span></span> <span data-ttu-id="01874-162">Cada vez que o `PercentDone` é gerado, o rótulo é atualizado com a porcentagem da tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="01874-162">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="01874-163">Clique o **Cancelar** botão para interromper a tarefa.</span><span class="sxs-lookup"><span data-stu-id="01874-163">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="01874-164">Observe que a aparência do **Cancelar** botão não é alterado imediatamente quando você clica nele.</span><span class="sxs-lookup"><span data-stu-id="01874-164">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="01874-165">O `Click` evento não pode ocorrer até que o `My.Application.DoEvents` instrução permite o processamento de eventos.</span><span class="sxs-lookup"><span data-stu-id="01874-165">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01874-166">O `My.Application.DoEvents` método não processa os eventos exatamente da mesma maneira como faz o formulário.</span><span class="sxs-lookup"><span data-stu-id="01874-166">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="01874-167">Por exemplo, esta explicação passo a passo, você deve clicar o **Cancelar** botão duas vezes.</span><span class="sxs-lookup"><span data-stu-id="01874-167">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="01874-168">Para permitir que o formulário para manipular os eventos diretamente, você pode usar multithreading.</span><span class="sxs-lookup"><span data-stu-id="01874-168">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="01874-169">Para obter mais informações, consulte [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="01874-169">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="01874-170">Você pode encontrar instrutivo executá-lo com F11 e percorrer o código uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="01874-170">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="01874-171">Você pode ver claramente como entrada de execução `LongTask`e, em seguida, brevemente reinserido `Form1` cada vez que o `PercentDone` é gerado.</span><span class="sxs-lookup"><span data-stu-id="01874-171">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="01874-172">O que aconteceria se, enquanto a execução foi novamente no código de `Form1`, o `LongTask` método foi chamado novamente?</span><span class="sxs-lookup"><span data-stu-id="01874-172">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="01874-173">Na pior das hipóteses, um estouro de pilha pode ocorrer se `LongTask` foi chamado sempre que o evento foi gerado.</span><span class="sxs-lookup"><span data-stu-id="01874-173">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="01874-174">Você pode fazer com que a variável `mWidget` para manipular eventos para um outro `Widget` objeto atribuindo uma referência para o novo `Widget` para `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="01874-174">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="01874-175">Na verdade, você pode tornar o código em `Button1_Click` isso sempre que você clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="01874-175">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="01874-176">Para manipular eventos para um widget diferente</span><span class="sxs-lookup"><span data-stu-id="01874-176">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="01874-177">Adicione a seguinte linha de código para o `Button1_Click` procedimento, logo após a linha que lê `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="01874-177">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     <span data-ttu-id="01874-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="01874-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span></span>  
  
 <span data-ttu-id="01874-179">O código acima cria um novo `Widget` toda vez que o botão é clicado.</span><span class="sxs-lookup"><span data-stu-id="01874-179">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="01874-180">Assim que o `LongTask` método é concluído, a referência para o `Widget` é liberado e o `Widget` é destruído.</span><span class="sxs-lookup"><span data-stu-id="01874-180">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="01874-181">A `WithEvents` variável pode conter referência somente um objeto por vez, dessa forma, se você atribuir outro `Widget` objeto `mWidget`, anterior `Widget` eventos do objeto não serão tratados.</span><span class="sxs-lookup"><span data-stu-id="01874-181">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="01874-182">Se `mWidget` é a única variável de objeto que contém uma referência para o antigo `Widget`, o objeto é destruído.</span><span class="sxs-lookup"><span data-stu-id="01874-182">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="01874-183">Se você quiser manipular eventos de vários `Widget` objetos, use o `AddHandler` instrução para processar eventos de cada objeto separadamente.</span><span class="sxs-lookup"><span data-stu-id="01874-183">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01874-184">Você pode declarar tantos `WithEvents` variáveis que você precisam, mas matrizes de `WithEvents` variáveis não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="01874-184">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01874-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01874-185">See Also</span></span>  
 <span data-ttu-id="01874-186">[Passo a passo: Declarando e disparando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span><span class="sxs-lookup"><span data-stu-id="01874-186">[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span></span>  
<span data-ttu-id="01874-187"> [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="01874-187"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>

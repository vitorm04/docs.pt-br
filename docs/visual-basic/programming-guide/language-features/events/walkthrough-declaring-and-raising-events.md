---
title: Declarando e gerando eventos (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf75cfba5102be5d837af385e2d3578f78a03c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="4de4f-102">Instruções passo a passo: declarando e acionando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4de4f-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="4de4f-103">Este passo a passo demonstra como declarar e disparar eventos de uma classe denominada `Widget`.</span><span class="sxs-lookup"><span data-stu-id="4de4f-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="4de4f-104">Depois de concluir as etapas, talvez você queira ler o tópico [passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4de4f-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="4de4f-105">A classe de Widget</span><span class="sxs-lookup"><span data-stu-id="4de4f-105">The Widget Class</span></span>  
 <span data-ttu-id="4de4f-106">Suponha que você tem um `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="4de4f-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="4de4f-107">O `Widget` classe tem um método que pode levar muito tempo para executar, e você deseja que o aplicativo seja capaz de colocar em backup algum tipo de indicador de conclusão.</span><span class="sxs-lookup"><span data-stu-id="4de4f-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="4de4f-108">Obviamente, você pode fazer o `Widget` objeto mostrar uma caixa de diálogo de porcentagem concluída, mas, em seguida, você estaria preso a caixa de diálogo em cada projeto que você usou o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="4de4f-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="4de4f-109">Um bom princípio de design do objeto é permitir que o aplicativo que usa um identificador de objeto da interface do usuário, a menos que seja a finalidade do objeto gerenciar uma caixa de diálogo ou formulário.</span><span class="sxs-lookup"><span data-stu-id="4de4f-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="4de4f-110">A finalidade de `Widget` é executar outras tarefas, portanto, é melhor adicionar um `PercentDone` evento e deixar que o procedimento que chama `Widget`do métodos manipular atualizações de status de evento e a exibição.</span><span class="sxs-lookup"><span data-stu-id="4de4f-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="4de4f-111">O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="4de4f-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="4de4f-112">Para criar o exemplo de código neste tópico</span><span class="sxs-lookup"><span data-stu-id="4de4f-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="4de4f-113">Abra uma nova [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] aplicativo do Windows do projeto e criar um formulário denominado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4de4f-113">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="4de4f-114">Adicione dois botões e um rótulo para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="4de4f-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="4de4f-115">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4de4f-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="4de4f-116">Objeto</span><span class="sxs-lookup"><span data-stu-id="4de4f-116">Object</span></span>|<span data-ttu-id="4de4f-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="4de4f-117">Property</span></span>|<span data-ttu-id="4de4f-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="4de4f-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="4de4f-119">Iniciar tarefa</span><span class="sxs-lookup"><span data-stu-id="4de4f-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="4de4f-120">Cancelar</span><span class="sxs-lookup"><span data-stu-id="4de4f-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="4de4f-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="4de4f-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="4de4f-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="4de4f-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="4de4f-123">Sobre o **projeto** menu, escolha **Adicionar classe de** para adicionar uma classe denominada `Widget.vb` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4de4f-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="4de4f-124">Para declarar um evento para a classe Widget</span><span class="sxs-lookup"><span data-stu-id="4de4f-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="4de4f-125">Use o `Event` palavra-chave para declarar um evento no `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="4de4f-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="4de4f-126">Observe que um evento pode ter `ByVal` e `ByRef` argumentos, como `Widget`do `PercentDone` evento demonstra:</span><span class="sxs-lookup"><span data-stu-id="4de4f-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 <span data-ttu-id="4de4f-127">Quando o objeto chamado recebe um `PercentDone` evento, o `Percent` argumento contém a porcentagem da tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="4de4f-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="4de4f-128">O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="4de4f-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4de4f-129">Você pode declarar argumentos de evento exatamente como você faria argumentos de procedimentos, com as seguintes exceções: eventos não podem ter `Optional` ou `ParamArray` argumentos e eventos não têm valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="4de4f-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="4de4f-130">O `PercentDone` é gerado pelo `LongTask` método o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="4de4f-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="4de4f-131">`LongTask`leva dois argumentos: o período de tempo que o método estaria para trabalho e o intervalo de tempo mínimo antes de fazer `LongTask` pare de gerar o `PercentDone` evento.</span><span class="sxs-lookup"><span data-stu-id="4de4f-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="4de4f-132">Para gerar o evento PercentDone</span><span class="sxs-lookup"><span data-stu-id="4de4f-132">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="4de4f-133">Para simplificar o acesso para o `Timer` propriedade usada por essa classe, adicione uma `Imports` à parte superior da seção de declarações do seu módulo de classe, acima o `Class Widget` instrução.</span><span class="sxs-lookup"><span data-stu-id="4de4f-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  <span data-ttu-id="4de4f-134">Adicione o seguinte código à classe `Widget`:</span><span class="sxs-lookup"><span data-stu-id="4de4f-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 <span data-ttu-id="4de4f-135">Quando o aplicativo chama o `LongTask` método, o `Widget` classe gera o `PercentDone` evento cada `MinimumInterval` segundos.</span><span class="sxs-lookup"><span data-stu-id="4de4f-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="4de4f-136">Quando um evento retorna, `LongTask` verifica se o `Cancel` argumento foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="4de4f-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="4de4f-137">Algumas isenções são necessárias aqui.</span><span class="sxs-lookup"><span data-stu-id="4de4f-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="4de4f-138">Para simplificar, o `LongTask` procedimento supõe que você sabe com antecedência quanto tempo levará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="4de4f-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="4de4f-139">Isso quase nunca é o caso.</span><span class="sxs-lookup"><span data-stu-id="4de4f-139">This is almost never the case.</span></span> <span data-ttu-id="4de4f-140">Dividir tarefas em partes do mesmo tamanho pode ser difícil, e geralmente o que mais importa para os usuários é simplesmente a quantidade de tempo decorrido antes de obter uma indicação de que algo está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="4de4f-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="4de4f-141">Você pode ter observado outra falha neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4de4f-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="4de4f-142">O `Timer` propriedade retorna o número de segundos que passaram desde a meia-noite; portanto, o aplicativo travou se ele for iniciado antes de meia-noite.</span><span class="sxs-lookup"><span data-stu-id="4de4f-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="4de4f-143">Uma abordagem mais cuidadosa para medição de tempo seria limite condições levadas em consideração ou evitar completamente, usando as propriedades, como `Now`.</span><span class="sxs-lookup"><span data-stu-id="4de4f-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="4de4f-144">Agora que o `Widget` classe pode gerar eventos, você pode mover para a próximo passo a passo.</span><span class="sxs-lookup"><span data-stu-id="4de4f-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="4de4f-145">[Passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de eventos com o `PercentDone` evento.</span><span class="sxs-lookup"><span data-stu-id="4de4f-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4de4f-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4de4f-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [<span data-ttu-id="4de4f-147">Instruções passo a passo: tratando eventos</span><span class="sxs-lookup"><span data-stu-id="4de4f-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [<span data-ttu-id="4de4f-148">Eventos</span><span class="sxs-lookup"><span data-stu-id="4de4f-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)

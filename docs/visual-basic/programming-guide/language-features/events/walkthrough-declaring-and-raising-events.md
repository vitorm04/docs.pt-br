---
title: Declarando e acionando eventos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320685"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="f6716-102">Passo a passo: Declarando e acionando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6716-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="f6716-103">Este passo a passo demonstra como declarar e acionar eventos para uma classe chamada `Widget`.</span><span class="sxs-lookup"><span data-stu-id="f6716-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="f6716-104">Depois de concluir as etapas, você talvez queira ler o tópico [passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f6716-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="f6716-105">A classe de Widget</span><span class="sxs-lookup"><span data-stu-id="f6716-105">The Widget Class</span></span>  
 <span data-ttu-id="f6716-106">Suponha para o momento em que você tem um `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="f6716-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="f6716-107">Seu `Widget` classe tem um método que pode levar muito tempo para executar, e você deseja que o aplicativo seja capaz de juntar-se de algum tipo de indicador de conclusão.</span><span class="sxs-lookup"><span data-stu-id="f6716-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="f6716-108">É claro, você poderia fazer o `Widget` objeto mostrar uma caixa de diálogo de porcentagem de conclusão, mas, em seguida, você estaria preso com essa caixa de diálogo em cada projeto que você usou o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="f6716-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="f6716-109">Um princípio de design do objeto é permitir que o aplicativo que usa um identificador de objeto da interface do usuário — a menos que a finalidade do objeto é gerenciar uma caixa de diálogo ou formulário.</span><span class="sxs-lookup"><span data-stu-id="f6716-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="f6716-110">A finalidade `Widget` é executar outras tarefas, portanto, é melhor adicionar uma `PercentDone` evento e deixar que o procedimento que chama `Widget`do métodos lidam com atualizações de status de evento e a exibição.</span><span class="sxs-lookup"><span data-stu-id="f6716-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="f6716-111">O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="f6716-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="f6716-112">Para compilar o exemplo de código para este tópico</span><span class="sxs-lookup"><span data-stu-id="f6716-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="f6716-113">Abra um novo projeto de aplicativo do Windows Visual Basic e crie um formulário chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f6716-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="f6716-114">Adicione dois botões e um rótulo para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="f6716-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="f6716-115">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f6716-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="f6716-116">Objeto</span><span class="sxs-lookup"><span data-stu-id="f6716-116">Object</span></span>|<span data-ttu-id="f6716-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="f6716-117">Property</span></span>|<span data-ttu-id="f6716-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="f6716-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="f6716-119">Iniciar tarefa</span><span class="sxs-lookup"><span data-stu-id="f6716-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="f6716-120">Cancelar</span><span class="sxs-lookup"><span data-stu-id="f6716-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="f6716-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="f6716-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="f6716-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="f6716-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="f6716-123">Sobre o **projeto** menu, escolha **Adicionar classe** para adicionar uma classe chamada `Widget.vb` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="f6716-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="f6716-124">Para declarar um evento para a classe de Widget</span><span class="sxs-lookup"><span data-stu-id="f6716-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="f6716-125">Use o `Event` palavra-chave para declarar um evento no `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="f6716-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="f6716-126">Observe que um evento pode ter `ByVal` e `ByRef` argumentos, como `Widget`do `PercentDone` evento demonstra:</span><span class="sxs-lookup"><span data-stu-id="f6716-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="f6716-127">Quando o objeto de chamada recebe um `PercentDone` evento, o `Percent` argumento contém a porcentagem da tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f6716-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="f6716-128">O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="f6716-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6716-129">Você pode declarar argumentos de evento, assim como faria argumentos dos procedimentos, com as seguintes exceções: Eventos não podem ter `Optional` ou `ParamArray` argumentos e eventos não têm valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="f6716-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="f6716-130">O `PercentDone` é gerado pela `LongTask` método o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="f6716-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="f6716-131">`LongTask` leva dois argumentos: o período de tempo, o método aparenta estar fazendo o trabalho e o intervalo de tempo mínimo antes `LongTask` pausas para gerar o `PercentDone` eventos.</span><span class="sxs-lookup"><span data-stu-id="f6716-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="f6716-132">Para gerar o evento PercentDone</span><span class="sxs-lookup"><span data-stu-id="f6716-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="f6716-133">Para simplificar o acesso para o `Timer` propriedade usada por essa classe, adicione uma `Imports` instrução na parte superior da seção de declarações do seu módulo de classe, acima o `Class Widget` instrução.</span><span class="sxs-lookup"><span data-stu-id="f6716-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="f6716-134">Adicione o seguinte código à classe `Widget`:</span><span class="sxs-lookup"><span data-stu-id="f6716-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="f6716-135">Quando seu aplicativo chama o `LongTask` método, o `Widget` classe gera o `PercentDone` evento cada `MinimumInterval` segundos.</span><span class="sxs-lookup"><span data-stu-id="f6716-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="f6716-136">Quando o evento é retornado, `LongTask` verifica se o `Cancel` argumento foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="f6716-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="f6716-137">Alguns avisos de isenção de responsabilidade aqui são necessários.</span><span class="sxs-lookup"><span data-stu-id="f6716-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="f6716-138">Para simplificar, o `LongTask` procedimento pressupõe que você sabe de antemão quanto tempo levará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="f6716-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="f6716-139">Isso quase nunca é o caso.</span><span class="sxs-lookup"><span data-stu-id="f6716-139">This is almost never the case.</span></span> <span data-ttu-id="f6716-140">Dividir tarefas em partes do mesmo tamanho pode ser difícil, e muitas vezes o que é mais importante para os usuários é simplesmente a quantidade de tempo decorrido antes que eles recebem uma indicação de que algo está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="f6716-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="f6716-141">Você pode ter observado outra falha neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f6716-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="f6716-142">O `Timer` propriedade retorna o número de segundos decorridos desde a meia-noite; portanto, o aplicativo travar se ele for iniciado antes de meia-noite.</span><span class="sxs-lookup"><span data-stu-id="f6716-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="f6716-143">Uma abordagem mais cuidadosa para medição de tempo levariam condições de limite como isso em consideração, ou evitá-los completamente, usando propriedades como `Now`.</span><span class="sxs-lookup"><span data-stu-id="f6716-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="f6716-144">Agora que o `Widget` classe pode gerar eventos, você pode mover para a próximo passo a passo.</span><span class="sxs-lookup"><span data-stu-id="f6716-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="f6716-145">[Passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de eventos com o `PercentDone` eventos.</span><span class="sxs-lookup"><span data-stu-id="f6716-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6716-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6716-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="f6716-147">Passo a passo: Manipulação de eventos</span><span class="sxs-lookup"><span data-stu-id="f6716-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="f6716-148">Eventos</span><span class="sxs-lookup"><span data-stu-id="f6716-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)

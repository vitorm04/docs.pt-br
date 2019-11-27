---
title: declarar e gerar eventos
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345097"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="e195a-102">Instruções passo a passo: declarando e acionando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e195a-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="e195a-103">Este tutorial demonstra como declarar e gerar eventos para uma classe chamada `Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="e195a-104">Depois de concluir as etapas, talvez você queira ler o tópico complementar, [Walkthrough: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e195a-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="e195a-105">A classe Widget</span><span class="sxs-lookup"><span data-stu-id="e195a-105">The Widget Class</span></span>  
 <span data-ttu-id="e195a-106">Suponha que, por enquanto, você tenha uma classe de `Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="e195a-107">Sua classe de `Widget` tem um método que pode levar muito tempo para ser executado e você deseja que seu aplicativo seja capaz de colocar algum tipo de indicador de conclusão.</span><span class="sxs-lookup"><span data-stu-id="e195a-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="e195a-108">É claro que você pode fazer com que o objeto `Widget` mostre uma caixa de diálogo de porcentagem concluída, mas, em seguida, você estaria preso a essa caixa de diálogo em todos os projetos nos quais usou a classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="e195a-109">Um bom princípio do design de objeto é permitir que o aplicativo que usa um objeto manipule a interface do usuário — a menos que a finalidade do objeto seja gerenciar um formulário ou caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="e195a-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="e195a-110">A finalidade do `Widget` é executar outras tarefas, portanto, é melhor adicionar um evento de `PercentDone` e permitir que o procedimento que chama os métodos de `Widget`manipule esse evento e exiba as atualizações de status.</span><span class="sxs-lookup"><span data-stu-id="e195a-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="e195a-111">O evento `PercentDone` também pode fornecer um mecanismo para cancelar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="e195a-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="e195a-112">Para criar o exemplo de código para este tópico</span><span class="sxs-lookup"><span data-stu-id="e195a-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="e195a-113">Abra um novo projeto de aplicativo do Windows Visual Basic e crie um formulário chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="e195a-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="e195a-114">Adicione dois botões e um rótulo a `Form1`.</span><span class="sxs-lookup"><span data-stu-id="e195a-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="e195a-115">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e195a-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="e195a-116">Object</span><span class="sxs-lookup"><span data-stu-id="e195a-116">Object</span></span>|<span data-ttu-id="e195a-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e195a-117">Property</span></span>|<span data-ttu-id="e195a-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="e195a-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="e195a-119">Tarefa de início</span><span class="sxs-lookup"><span data-stu-id="e195a-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="e195a-120">Cancel</span><span class="sxs-lookup"><span data-stu-id="e195a-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="e195a-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="e195a-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="e195a-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="e195a-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="e195a-123">No menu **projeto** , escolha **Adicionar classe** para adicionar uma classe chamada `Widget.vb` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="e195a-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="e195a-124">Para declarar um evento para a classe Widget</span><span class="sxs-lookup"><span data-stu-id="e195a-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="e195a-125">Use a palavra-chave `Event` para declarar um evento na classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="e195a-126">Observe que um evento pode ter argumentos `ByVal` e `ByRef`, como o evento de `PercentDone` de `Widget`demonstra:</span><span class="sxs-lookup"><span data-stu-id="e195a-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="e195a-127">Quando o objeto de chamada recebe um evento `PercentDone`, o argumento `Percent` contém a porcentagem da tarefa concluída.</span><span class="sxs-lookup"><span data-stu-id="e195a-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="e195a-128">O argumento `Cancel` pode ser definido como `True` para cancelar o método que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="e195a-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e195a-129">Você pode declarar argumentos de evento da mesma forma como faz argumentos de procedimentos, com as seguintes exceções: os eventos não podem ter argumentos `Optional` ou `ParamArray`, e os eventos não têm valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="e195a-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="e195a-130">O evento `PercentDone` é gerado pelo método `LongTask` da classe `Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="e195a-131">`LongTask` usa dois argumentos: o período de tempo que o método pretende a fazer funcionar e o intervalo de tempo mínimo antes de `LongTask` pausa para gerar o evento de `PercentDone`.</span><span class="sxs-lookup"><span data-stu-id="e195a-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="e195a-132">Para gerar o evento PercentDone</span><span class="sxs-lookup"><span data-stu-id="e195a-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="e195a-133">Para simplificar o acesso à propriedade `Timer` usada por essa classe, adicione uma instrução `Imports` à parte superior da seção de declarações do seu módulo de classe, acima da instrução `Class Widget`.</span><span class="sxs-lookup"><span data-stu-id="e195a-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="e195a-134">Adicione o seguinte código à classe `Widget`:</span><span class="sxs-lookup"><span data-stu-id="e195a-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="e195a-135">Quando o aplicativo chama o método `LongTask`, a classe `Widget` gera o evento `PercentDone` a cada `MinimumInterval` segundos.</span><span class="sxs-lookup"><span data-stu-id="e195a-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="e195a-136">Quando o evento retorna, `LongTask` verifica se o argumento `Cancel` foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="e195a-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="e195a-137">Alguns isenções de responsabilidade são necessários aqui.</span><span class="sxs-lookup"><span data-stu-id="e195a-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="e195a-138">Para simplificar, o procedimento `LongTask` pressupõe que você saiba com antecedência quanto tempo a tarefa levará.</span><span class="sxs-lookup"><span data-stu-id="e195a-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="e195a-139">Esse é quase nunca o caso.</span><span class="sxs-lookup"><span data-stu-id="e195a-139">This is almost never the case.</span></span> <span data-ttu-id="e195a-140">Dividir tarefas em partes de tamanho par pode ser difícil e, muitas vezes, o que mais importa para os usuários é simplesmente a quantidade de tempo que o passa antes de receber uma indicação de que algo está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="e195a-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="e195a-141">Você pode ter extratado outra falha neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="e195a-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="e195a-142">A propriedade `Timer` retorna o número de segundos que passaram desde a meia-noite; Portanto, o aplicativo ficará preso se ele for iniciado logo antes da meia-noite.</span><span class="sxs-lookup"><span data-stu-id="e195a-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="e195a-143">Uma abordagem mais cuidadosa para medir o tempo teria condições de limite como essa em consideração ou evitá-las completamente, usando propriedades como `Now`.</span><span class="sxs-lookup"><span data-stu-id="e195a-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="e195a-144">Agora que a classe `Widget` pode gerar eventos, você pode ir para o próximo passo a passos.</span><span class="sxs-lookup"><span data-stu-id="e195a-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="e195a-145">[Walkthrough: manipular eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de eventos ao evento `PercentDone`.</span><span class="sxs-lookup"><span data-stu-id="e195a-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e195a-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e195a-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="e195a-147">Instruções passo a passo: tratando eventos</span><span class="sxs-lookup"><span data-stu-id="e195a-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="e195a-148">Eventos</span><span class="sxs-lookup"><span data-stu-id="e195a-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)

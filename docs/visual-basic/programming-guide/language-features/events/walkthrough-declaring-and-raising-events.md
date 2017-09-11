---
title: Declarando e acionando eventos (Visual Basic) | Documentos do Microsoft
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
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
ms.openlocfilehash: eca112aca39bd998697d379a1705845e8f607367
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="28f19-102">Instruções passo a passo: declarando e acionando eventos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28f19-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="28f19-103">Este passo a passo demonstra como declarar e gerar eventos para uma classe denominada `Widget`.</span><span class="sxs-lookup"><span data-stu-id="28f19-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="28f19-104">Depois de concluir as etapas, você talvez queira ler o tópico [passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), que mostra como usar eventos de `Widget` objetos para fornecer informações de status em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28f19-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="28f19-105">A classe Widget</span><span class="sxs-lookup"><span data-stu-id="28f19-105">The Widget Class</span></span>  
 <span data-ttu-id="28f19-106">Suponha que você tem um `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="28f19-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="28f19-107">O `Widget` classe tem um método que pode levar muito tempo para executar, e você deseja que o aplicativo seja capaz de colocar em backup algum tipo de indicador de conclusão.</span><span class="sxs-lookup"><span data-stu-id="28f19-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="28f19-108">Obviamente, você pode fazer o `Widget` objeto mostrar uma caixa de diálogo de porcentagem de conclusão, mas, em seguida, você estaria preso a caixa de diálogo em cada projeto que você usou o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="28f19-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="28f19-109">Um princípio de design do objeto é permitir que o aplicativo que usa um identificador de objeto da interface do usuário — a menos que seja o único propósito do objeto gerenciar uma caixa de diálogo ou formulário.</span><span class="sxs-lookup"><span data-stu-id="28f19-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="28f19-110">A finalidade do `Widget` é realizar outras tarefas, portanto, é melhor adicionar um `PercentDone` evento e deixar que o procedimento que chama `Widget`do métodos lidar com atualizações de status de evento e a exibição.</span><span class="sxs-lookup"><span data-stu-id="28f19-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="28f19-111">O `PercentDone` evento também pode fornecer um mecanismo para cancelar a tarefa.</span><span class="sxs-lookup"><span data-stu-id="28f19-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="28f19-112">Para compilar o exemplo de código para este tópico</span><span class="sxs-lookup"><span data-stu-id="28f19-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="28f19-113">Abra uma nova [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] aplicativo do Windows do projeto e criar um formulário chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="28f19-113">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="28f19-114">Adicione dois botões e um rótulo para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="28f19-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="28f19-115">Nomeie os objetos como mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="28f19-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="28f19-116">Objeto</span><span class="sxs-lookup"><span data-stu-id="28f19-116">Object</span></span>|<span data-ttu-id="28f19-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="28f19-117">Property</span></span>|<span data-ttu-id="28f19-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="28f19-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="28f19-119">Iniciar tarefa</span><span class="sxs-lookup"><span data-stu-id="28f19-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="28f19-120">Cancelar</span><span class="sxs-lookup"><span data-stu-id="28f19-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="28f19-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="28f19-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="28f19-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="28f19-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="28f19-123">Sobre o **projeto** menu, escolha **Add Class** para adicionar uma classe denominada `Widget.vb` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="28f19-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="28f19-124">Para declarar um evento para a classe Widget</span><span class="sxs-lookup"><span data-stu-id="28f19-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="28f19-125">Use o `Event` palavra-chave para declarar um evento na `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="28f19-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="28f19-126">Observe que um evento pode ter `ByVal` e `ByRef` argumentos, como `Widget`do `PercentDone` evento demonstra:</span><span class="sxs-lookup"><span data-stu-id="28f19-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     <span data-ttu-id="28f19-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="28f19-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span></span>  
  
 <span data-ttu-id="28f19-128">Quando o objeto de chamada recebe uma `PercentDone` evento, o `Percent` argumento contém a porcentagem da tarefa que foi concluída.</span><span class="sxs-lookup"><span data-stu-id="28f19-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="28f19-129">O `Cancel` argumento pode ser definido como `True` para cancelar o método que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="28f19-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28f19-130">Você pode declarar argumentos de evento, assim como você faz argumentos de procedimentos, com as seguintes exceções: eventos não podem ter `Optional` ou `ParamArray` argumentos e eventos não têm valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="28f19-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="28f19-131">O `PercentDone` é gerado pelo `LongTask` método o `Widget` classe.</span><span class="sxs-lookup"><span data-stu-id="28f19-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="28f19-132">`LongTask`leva dois argumentos: o período de tempo que o método estaria estar fazendo o trabalho e o intervalo de tempo mínimo antes de `LongTask` pare de gerar o `PercentDone` evento.</span><span class="sxs-lookup"><span data-stu-id="28f19-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="28f19-133">Para elevar o evento PercentDone</span><span class="sxs-lookup"><span data-stu-id="28f19-133">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="28f19-134">Para simplificar o acesso para o `Timer` propriedade usada por essa classe, adicione uma `Imports` instrução na parte superior da seção de declarações do seu módulo de classe, acima de `Class Widget` instrução.</span><span class="sxs-lookup"><span data-stu-id="28f19-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     <span data-ttu-id="28f19-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="28f19-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span></span>  
  
2.  <span data-ttu-id="28f19-136">Adicione o seguinte código à classe `Widget`:</span><span class="sxs-lookup"><span data-stu-id="28f19-136">Add the following code to the `Widget` class:</span></span>  
  
     <span data-ttu-id="28f19-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents n º&3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="28f19-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span></span>  
  
 <span data-ttu-id="28f19-138">Quando o aplicativo chama o `LongTask` método, o `Widget` classe gera o `PercentDone` evento cada `MinimumInterval` segundos.</span><span class="sxs-lookup"><span data-stu-id="28f19-138">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="28f19-139">Quando um evento retorna, `LongTask` verifica se o `Cancel` argumento foi definido como `True`.</span><span class="sxs-lookup"><span data-stu-id="28f19-139">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="28f19-140">Algumas isenções são necessárias aqui.</span><span class="sxs-lookup"><span data-stu-id="28f19-140">A few disclaimers are necessary here.</span></span> <span data-ttu-id="28f19-141">Para simplificar, o `LongTask` procedimento pressupõe que você saiba com antecedência quanto tempo levará a tarefa.</span><span class="sxs-lookup"><span data-stu-id="28f19-141">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="28f19-142">Isso é quase nunca o caso.</span><span class="sxs-lookup"><span data-stu-id="28f19-142">This is almost never the case.</span></span> <span data-ttu-id="28f19-143">Dividir tarefas em partes do mesmo tamanho pode ser difícil, e geralmente o que mais importa aos usuários é simplesmente a quantidade de tempo que passa antes de obter uma indicação de que algo está acontecendo.</span><span class="sxs-lookup"><span data-stu-id="28f19-143">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="28f19-144">Você pode ter observado outra falha neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="28f19-144">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="28f19-145">O `Timer` propriedade retorna o número de segundos decorridos desde a meia-noite; portanto, o aplicativo fica preso se ele for iniciado antes de meia-noite.</span><span class="sxs-lookup"><span data-stu-id="28f19-145">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="28f19-146">Uma abordagem mais cuidadosa para medição de tempo levariam condições de limite como isso em consideração, ou evitadas simultaneamente, utilizando propriedades tais como `Now`.</span><span class="sxs-lookup"><span data-stu-id="28f19-146">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="28f19-147">Agora que o `Widget` classe pode gerar eventos, você pode mover para a próximo passo a passo.</span><span class="sxs-lookup"><span data-stu-id="28f19-147">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="28f19-148">[Passo a passo: Manipulação de eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstra como usar `WithEvents` para associar um manipulador de evento com o `PercentDone` evento.</span><span class="sxs-lookup"><span data-stu-id="28f19-148">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f19-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28f19-149">See Also</span></span>  
 <span data-ttu-id="28f19-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span><span class="sxs-lookup"><span data-stu-id="28f19-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span></span>   
 <span data-ttu-id="28f19-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="28f19-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span></span>   
<span data-ttu-id="28f19-152"> [Passo a passo: Manipulando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span><span class="sxs-lookup"><span data-stu-id="28f19-152"> [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span></span>  
<span data-ttu-id="28f19-153"> [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="28f19-153"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>

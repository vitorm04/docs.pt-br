---
title: Instrução RaiseEvent (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ee52b4adf893ea0926c4016fcb6a89d0010ee6ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957774"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="b3ffe-102">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="b3ffe-102">RaiseEvent Statement</span></span>
<span data-ttu-id="b3ffe-103">Dispara um evento declarado no nível de módulo dentro de uma classe, formulário ou documento.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ffe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3ffe-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="b3ffe-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b3ffe-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="b3ffe-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-106">Required.</span></span> <span data-ttu-id="b3ffe-107">Nome do evento a ser disparado.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="b3ffe-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-108">Optional.</span></span> <span data-ttu-id="b3ffe-109">Lista delimitada por vírgula de variáveis, matrizes ou expressões.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="b3ffe-110">O `argumentlist` argumento deve ser colocado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="b3ffe-111">Se não houver argumentos, os parênteses deverão ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3ffe-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3ffe-112">Remarks</span></span>  
 <span data-ttu-id="b3ffe-113">O necessário `eventname` é o nome de um evento declarado dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="b3ffe-114">Ele segue Visual Basic convenções de nomenclatura de variáveis.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="b3ffe-115">Se o evento não tiver sido declarado dentro do módulo no qual ele é gerado, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="b3ffe-116">O fragmento de código a seguir ilustra uma declaração de evento e um procedimento no qual o evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="b3ffe-117">Você não pode `RaiseEvent` usar o para gerar eventos que não são declarados explicitamente no módulo.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="b3ffe-118">Por exemplo, todos os formulários herdam <xref:System.Windows.Forms.Control.Click> um <xref:System.Windows.Forms.Form?displayProperty=nameWithType>evento de, não podem ser `RaiseEvent` gerados usando em um formulário derivado.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="b3ffe-119">Se você declarar um `Click` evento no módulo de formulário, ele sombreia o próprio <xref:System.Windows.Forms.Control.Click> evento do formulário.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="b3ffe-120">Você ainda pode invocar o evento <xref:System.Windows.Forms.Control.Click> do formulário chamando o <xref:System.Windows.Forms.Control.OnClick%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="b3ffe-121">Por padrão, um evento definido em Visual Basic gera seus manipuladores de eventos na ordem em que as conexões são estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="b3ffe-122">Como os eventos podem `ByRef` ter parâmetros, um processo que se conecta tardiamente pode receber parâmetros que foram alterados por um manipulador de eventos anterior.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="b3ffe-123">Depois que os manipuladores de eventos são executados, o controle é retornado para a sub-rotina que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3ffe-124">Eventos não compartilhados não devem ser gerados dentro do construtor da classe na qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="b3ffe-125">Embora tais eventos não causem erros em tempo de execução, eles podem não ser detectados por manipuladores de eventos associados.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="b3ffe-126">Use o `Shared` modificador para criar um evento compartilhado se você precisar gerar um evento a partir de um construtor.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3ffe-127">Você pode alterar o comportamento padrão de eventos definindo um evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="b3ffe-128">Para eventos personalizados, a `RaiseEvent` instrução invoca o acessador `RaiseEvent` do evento.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="b3ffe-129">Para obter mais informações sobre eventos personalizados, consulte [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b3ffe-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3ffe-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3ffe-130">Example</span></span>  
 <span data-ttu-id="b3ffe-131">O exemplo a seguir usa eventos para contar os segundos de 10 a 0.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="b3ffe-132">O código ilustra vários dos métodos, propriedades e instruções relacionados ao evento, incluindo a `RaiseEvent` instrução.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="b3ffe-133">A classe que gera um evento é a origem do evento, e os métodos que processam o evento são os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="b3ffe-134">Uma origem de evento pode ter vários manipuladores para os eventos que ele gera.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="b3ffe-135">Quando a classe gera o evento, esse evento é gerado em todas as classes que escolheram manipular eventos para essa instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="b3ffe-136">O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto`TextBox1`().</span><span class="sxs-lookup"><span data-stu-id="b3ffe-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="b3ffe-137">Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 a 0 segundos.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="b3ffe-138">Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibirá "concluído".</span><span class="sxs-lookup"><span data-stu-id="b3ffe-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="b3ffe-139">O código para `Form1` especifica os Estados inicial e de terminal do formulário.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="b3ffe-140">Ele também contém o código executado quando eventos são gerados.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="b3ffe-141">Para usar este exemplo, abra um novo projeto de aplicativo do Windows, adicione um `Button1` botão chamado e uma caixa `TextBox1` de texto nomeada ao formulário principal `Form1`, denominada.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="b3ffe-142">Em seguida, clique com o botão direito do mouse no formulário e clique em **Exibir código** para abrir o editor de código.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="b3ffe-143">Adicione uma `WithEvents` variável à seção `Form1` de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b3ffe-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3ffe-144">Example</span></span>  
 <span data-ttu-id="b3ffe-145">Adicione o código a seguir ao código para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="b3ffe-146">Substitua quaisquer procedimentos duplicados que possam existir, `Form_Load`como ou. `Button_Click`</span><span class="sxs-lookup"><span data-stu-id="b3ffe-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="b3ffe-147">Pressione F5 para executar o exemplo anterior e clique no botão chamado **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="b3ffe-148">A primeira caixa de texto começa a contar os segundos.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="b3ffe-149">Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibirá "concluído".</span><span class="sxs-lookup"><span data-stu-id="b3ffe-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3ffe-150">O `My.Application.DoEvents` método não processa eventos exatamente da mesma forma que o formulário.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="b3ffe-151">Para permitir que o formulário manipule os eventos diretamente, você pode usar multithreading.</span><span class="sxs-lookup"><span data-stu-id="b3ffe-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="b3ffe-152">Para obter mais informações, consulte [Threading gerenciado](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3ffe-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ffe-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3ffe-153">See also</span></span>

- [<span data-ttu-id="b3ffe-154">Eventos</span><span class="sxs-lookup"><span data-stu-id="b3ffe-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="b3ffe-155">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="b3ffe-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="b3ffe-156">Instrução AddHandler</span><span class="sxs-lookup"><span data-stu-id="b3ffe-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="b3ffe-157">Instrução RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="b3ffe-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="b3ffe-158">Handles</span><span class="sxs-lookup"><span data-stu-id="b3ffe-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)

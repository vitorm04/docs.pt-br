---
title: "Instrução RaiseEvent | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
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
ms.openlocfilehash: 6a0cf1c5635335f22fddd57c7dd2baaeca6ddd23
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="raiseevent-statement"></a><span data-ttu-id="121c6-102">Instrução RaiseEvent</span><span class="sxs-lookup"><span data-stu-id="121c6-102">RaiseEvent Statement</span></span>
<span data-ttu-id="121c6-103">Gatilhos de um evento declarado no nível de módulo em uma classe, formulário ou documento.</span><span class="sxs-lookup"><span data-stu-id="121c6-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="121c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="121c6-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="121c6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="121c6-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="121c6-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="121c6-106">Required.</span></span> <span data-ttu-id="121c6-107">Nome do evento para disparar.</span><span class="sxs-lookup"><span data-stu-id="121c6-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="121c6-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="121c6-108">Optional.</span></span> <span data-ttu-id="121c6-109">Lista delimitada por vírgulas de variáveis, matrizes ou expressões.</span><span class="sxs-lookup"><span data-stu-id="121c6-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="121c6-110">O `argumentlist` argumento deve ser delimitado por parênteses.</span><span class="sxs-lookup"><span data-stu-id="121c6-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="121c6-111">Se não houver nenhum argumento, os parênteses devem ser omitidos.</span><span class="sxs-lookup"><span data-stu-id="121c6-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="121c6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="121c6-112">Remarks</span></span>  
 <span data-ttu-id="121c6-113">Necessário `eventname` é o nome de um evento declarado dentro do módulo.</span><span class="sxs-lookup"><span data-stu-id="121c6-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="121c6-114">Ele segue as convenções de nomenclatura de variável do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="121c6-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="121c6-115">Se o evento não foi declarado dentro do módulo no qual ele é disparado, ocorrerá um erro.</span><span class="sxs-lookup"><span data-stu-id="121c6-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="121c6-116">O fragmento de código a seguir ilustra uma declaração de evento e um procedimento no qual o evento é gerado.</span><span class="sxs-lookup"><span data-stu-id="121c6-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 <span data-ttu-id="121c6-117">[!code-vb[VbVbalrEvents&#37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="121c6-117">[!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="121c6-118">Você não pode usar `RaiseEvent` para gerar eventos que não são explicitamente declarados no módulo.</span><span class="sxs-lookup"><span data-stu-id="121c6-118">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="121c6-119">Por exemplo, todos os formulários herdam uma <xref:System.Windows.Forms.Control.Click>eventos de <xref:System.Windows.Forms.Form?displayProperty=fullName>, ele não pode ser gerado usando `RaiseEvent` em um formulário derivado.</xref:System.Windows.Forms.Form?displayProperty=fullName> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="121c6-119">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=fullName>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="121c6-120">Se você declarar uma `Click` eventos no módulo de formulário, ele shadows do formulário próprio <xref:System.Windows.Forms.Control.Click>evento.</xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="121c6-120">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="121c6-121">Você ainda pode invocar o formulário <xref:System.Windows.Forms.Control.Click>evento chamando o <xref:System.Windows.Forms.Control.OnClick%2A>método.</xref:System.Windows.Forms.Control.OnClick%2A> </xref:System.Windows.Forms.Control.Click></span><span class="sxs-lookup"><span data-stu-id="121c6-121">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="121c6-122">Por padrão, um evento definido no Visual Basic gera seus manipuladores de eventos na ordem em que as conexões são estabelecidas.</span><span class="sxs-lookup"><span data-stu-id="121c6-122">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="121c6-123">Como os eventos podem ter `ByRef` parâmetros, um processo que se conecta tardia pode receber parâmetros que foram alterados por um manipulador de eventos anterior.</span><span class="sxs-lookup"><span data-stu-id="121c6-123">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="121c6-124">Depois de executar os manipuladores de eventos, o controle é retornado para a sub-rotina que gerou o evento.</span><span class="sxs-lookup"><span data-stu-id="121c6-124">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="121c6-125">Eventos não compartilhados não devem ser gerados dentro do construtor da classe em que elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="121c6-125">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="121c6-126">Embora esses eventos não causam erros de tempo de execução, eles podem não ser detectadas por manipuladores de evento associado.</span><span class="sxs-lookup"><span data-stu-id="121c6-126">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="121c6-127">Use o `Shared` modificador para criar um evento compartilhado, se você precisar disparar um evento de um construtor.</span><span class="sxs-lookup"><span data-stu-id="121c6-127">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="121c6-128">Você pode alterar o comportamento padrão de eventos definindo um evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="121c6-128">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="121c6-129">Para eventos personalizados, o `RaiseEvent` instrução chama o evento `RaiseEvent` acessador.</span><span class="sxs-lookup"><span data-stu-id="121c6-129">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="121c6-130">Para obter mais informações sobre eventos personalizados, consulte [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="121c6-130">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="121c6-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="121c6-131">Example</span></span>  
 <span data-ttu-id="121c6-132">O exemplo a seguir usa os eventos a contagem regressiva de 10 segundos para 0.</span><span class="sxs-lookup"><span data-stu-id="121c6-132">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="121c6-133">O código ilustra vários métodos relacionados a eventos, propriedades e instruções, inclusive o `RaiseEvent` instrução.</span><span class="sxs-lookup"><span data-stu-id="121c6-133">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="121c6-134">A classe que gera um evento é a origem do evento e os métodos que processam o evento são os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="121c6-134">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="121c6-135">Uma fonte de evento pode ter vários manipuladores para eventos que ela gera.</span><span class="sxs-lookup"><span data-stu-id="121c6-135">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="121c6-136">Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="121c6-136">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="121c6-137">O exemplo também usa um formulário (`Form1`) com um botão (`Button1`) e uma caixa de texto (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="121c6-137">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="121c6-138">Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos.</span><span class="sxs-lookup"><span data-stu-id="121c6-138">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="121c6-139">Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".</span><span class="sxs-lookup"><span data-stu-id="121c6-139">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="121c6-140">O código para `Form1` Especifica os estados iniciais e de terminal do formulário.</span><span class="sxs-lookup"><span data-stu-id="121c6-140">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="121c6-141">Ele também contém o código executado quando os eventos são gerados.</span><span class="sxs-lookup"><span data-stu-id="121c6-141">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="121c6-142">Para usar esse exemplo, abra um novo projeto de aplicativo do Windows, adicione um botão chamado `Button1` e uma caixa de texto denominada `TextBox1` ao formulário principal, chamado `Form1`.</span><span class="sxs-lookup"><span data-stu-id="121c6-142">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="121c6-143">Em seguida, clique com botão direito do formulário e clique em **Exibir código** para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="121c6-143">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="121c6-144">Adicionar uma `WithEvents` à seção de declarações de variável de `Form1` classe.</span><span class="sxs-lookup"><span data-stu-id="121c6-144">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 <span data-ttu-id="121c6-145">[!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="121c6-145">[!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="121c6-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="121c6-146">Example</span></span>  
 <span data-ttu-id="121c6-147">Adicione o seguinte código ao código para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="121c6-147">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="121c6-148">Substituir qualquer procedimentos duplicados que podem existir, como `Form_Load`, ou `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="121c6-148">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 <span data-ttu-id="121c6-149">[!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="121c6-149">[!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="121c6-150">Pressione F5 para executar o exemplo anterior e clique no botão **iniciar**.</span><span class="sxs-lookup"><span data-stu-id="121c6-150">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="121c6-151">A primeira caixa de texto inicia a contagem regressiva de segundos.</span><span class="sxs-lookup"><span data-stu-id="121c6-151">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="121c6-152">Quando o tempo total (10 segundos) tiver decorrido, a primeira caixa de texto exibe "Concluído".</span><span class="sxs-lookup"><span data-stu-id="121c6-152">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="121c6-153">O `My.Application.DoEvents` método não processa os eventos exatamente da mesma maneira como faz o formulário.</span><span class="sxs-lookup"><span data-stu-id="121c6-153">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="121c6-154">Para permitir que o formulário para manipular os eventos diretamente, você pode usar multithreading.</span><span class="sxs-lookup"><span data-stu-id="121c6-154">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="121c6-155">Para obter mais informações, consulte [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="121c6-155">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="121c6-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="121c6-156">See Also</span></span>  
 <span data-ttu-id="121c6-157">[Eventos](../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="121c6-157">[Events](../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="121c6-158"> [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="121c6-158"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="121c6-159"> [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="121c6-159"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="121c6-160"> [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="121c6-160"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="121c6-161"> [Identificadores](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="121c6-161"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)</span></span>

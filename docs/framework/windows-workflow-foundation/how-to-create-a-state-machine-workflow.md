---
title: "Como criar um fluxo de trabalho de máquina de estado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 797cdc425c0f3088aa2b75c0285ca6bea2dd425b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="04ade-102">Como criar um fluxo de trabalho de máquina de estado</span><span class="sxs-lookup"><span data-stu-id="04ade-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="04ade-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="04ade-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="04ade-104">Este tópico percorre criando um fluxo de trabalho que usa as duas atividades internas, como o <xref:System.Activities.Statements.StateMachine> atividade e as atividades personalizadas do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="04ade-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="04ade-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="04ade-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ade-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="04ade-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="04ade-107">Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="04ade-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ade-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="04ade-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="04ade-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="04ade-110">Clique com botão direito **NumberGuessWorkflowActivities** na **Solution Explorer** e selecione **adicionar**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="04ade-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="04ade-111">No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="04ade-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="04ade-112">Selecione **atividade** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="04ade-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="04ade-113">Tipo `StateMachineNumberGuessWorkflow` para o **nome** caixa e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="04ade-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="04ade-114">Arraste um **StateMachine** atividade do **máquina de estado** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo em a superfície de design de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="04ade-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="04ade-116">Clique duas vezes em **StateMachineNumberGuessWorkflow.xaml** na **Solution Explorer** para exibir o fluxo de trabalho no designer, se ainda não estiver sendo exibida.</span><span class="sxs-lookup"><span data-stu-id="04ade-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="04ade-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="04ade-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="04ade-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="04ade-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="04ade-119">Tipo `MaxNumber` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="04ade-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="04ade-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="04ade-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="04ade-121">Tipo `Turns` para o **nome** caixa abaixo recém-adicionado `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="04ade-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="04ade-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="04ade-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="04ade-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="04ade-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="04ade-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="04ade-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="04ade-125">Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.StateMachine> atividade na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="04ade-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="04ade-126">Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="04ade-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="04ade-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="04ade-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="04ade-128">Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="04ade-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="04ade-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="04ade-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="04ade-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="04ade-131">Clique em **State1** para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="04ade-131">Click **State1** to select it.</span></span> <span data-ttu-id="04ade-132">No **janela propriedades**, altere o **DisplayName** para `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="04ade-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="04ade-133">Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="04ade-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2.  <span data-ttu-id="04ade-134">Clique duas vezes em renomeada recentemente **destino inicializar** estado no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="04ade-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3.  <span data-ttu-id="04ade-135">Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **entrada** seção do estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="04ade-136">Tipo `Target` no **para** caixa e a expressão a seguir para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="04ade-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="04ade-137">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="04ade-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4.  <span data-ttu-id="04ade-138">Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5.  <span data-ttu-id="04ade-139">Arraste um **estado** atividade do **máquina de estado** seção o **caixa de ferramentas** para o designer de fluxo de trabalho e passe o mouse sobre o **destino inicializar** estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="04ade-140">Observe que os quatro triângulos aparecerá ao redor de **destino inicializar** estado quando o novo estado é sobre ele.</span><span class="sxs-lookup"><span data-stu-id="04ade-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="04ade-141">Descarte o estado novo no triângulo que está imediatamente abaixo do **destino inicializar** estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="04ade-142">Isso coloca o novo estado para o fluxo de trabalho e cria uma transição do **destino inicializar** estado para o novo estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6.  <span data-ttu-id="04ade-143">Clique em **State1** para selecioná-lo, altere o **DisplayName** para `Enter Guess`e, em seguida, clique duas vezes o estado no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="04ade-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7.  <span data-ttu-id="04ade-144">Arraste um **WriteLine** atividade do **primitivos** seção o **caixa de ferramentas** e solte-a para o **entrada** seção do estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8.  <span data-ttu-id="04ade-145">Digite a seguinte expressão para o **texto** caixa de propriedade do **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="04ade-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="04ade-146">Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e solte o **saída** seção do estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="04ade-147">Tipo `Turns` para o **para** caixa e `Turns + 1` no **insira uma expressão de c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="04ade-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="04ade-148">Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="04ade-149">Arrastar um **FinalState** atividade do **máquina de estado** seção o **caixa de ferramentas**, passe o mouse sobre o **insira adivinhar** estado e solte-o para o triângulo que aparece à direita do **insira adivinhar** de estado para que seja criada uma transição entre **insira adivinhar** e **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="04ade-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="04ade-150">O nome padrão da transição é **T2**.</span><span class="sxs-lookup"><span data-stu-id="04ade-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="04ade-151">Clique na transição no designer de fluxo de trabalho para selecioná-lo e definir seu **DisplayName** para **adivinhar correto**.</span><span class="sxs-lookup"><span data-stu-id="04ade-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="04ade-152">Em seguida, clique em e selecione o **FinalState**e arraste-o para que haja espaço para o nome de transição completa a ser exibido sem sobreposição de qualquer um dos dois estados.</span><span class="sxs-lookup"><span data-stu-id="04ade-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="04ade-153">Isso facilitará a conclusão das etapas restantes no tutorial.</span><span class="sxs-lookup"><span data-stu-id="04ade-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="04ade-154">Clique duas vezes em renomeada recentemente **adivinhar correto** transição no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="04ade-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="04ade-155">Arraste um **ReadInt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **gatilho** seção da transição.</span><span class="sxs-lookup"><span data-stu-id="04ade-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="04ade-156">No **janela propriedades** para o **ReadInt** atividade, digite `"EnterGuess"` incluindo as aspas para o **BookmarkName** caixa de valor de propriedade e digite `Guess`para o **resultados** caixa de valor de propriedade</span><span class="sxs-lookup"><span data-stu-id="04ade-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="04ade-157">Digite a seguinte expressão para o **adivinhar correto** da transição **condição** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04ade-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="04ade-158">Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04ade-159">Uma transição ocorre quando o evento de gatilho é recebido e o <xref:System.Activities.Statements.Transition.Condition%2A>, se houver, é avaliado como `True`.</span><span class="sxs-lookup"><span data-stu-id="04ade-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="04ade-160">Para essa transição, se o usuário `Guess` corresponde gerado aleatoriamente `Target`, em seguida, o controle passará para o **FinalState** e conclui o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="04ade-161">Dependendo se a previsão está correta, o fluxo de trabalho deve fazer a transição para o **FinalState** ou de volta para o **insira estimativa** estado para tentar.</span><span class="sxs-lookup"><span data-stu-id="04ade-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="04ade-162">Ambas as transições de compartilham o mesmo gatilho de espera para a estimativa do usuário ser recebida por meio de **ReadInt** atividade.</span><span class="sxs-lookup"><span data-stu-id="04ade-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="04ade-163">Isso é chamado de uma transição compartilhada.</span><span class="sxs-lookup"><span data-stu-id="04ade-163">This is called a shared transition.</span></span> <span data-ttu-id="04ade-164">Para criar uma transição compartilhada, clique no círculo que indica o início do **adivinhar correto** transição e arraste-o para o estado desejado.</span><span class="sxs-lookup"><span data-stu-id="04ade-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="04ade-165">Nesse caso, a transição é uma transição interna, portanto, arraste o ponto inicial do **adivinhar correto** transição e solte-a novamente na parte inferior da **insira adivinhar** estado.</span><span class="sxs-lookup"><span data-stu-id="04ade-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="04ade-166">Depois de criar a transição, selecione-a no designer de fluxo de trabalho e defina seu **DisplayName** propriedade **adivinhar incorreto**.</span><span class="sxs-lookup"><span data-stu-id="04ade-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04ade-167">Transições compartilhadas também podem ser criadas de dentro do designer de transição clicando **adicionar compartilhado transição de gatilho** na parte inferior do designer de transição e, em seguida, selecionar o estado de destino desejado do  **Estados disponíveis para conexão** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="04ade-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="04ade-168">Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `false` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `false`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados.</span><span class="sxs-lookup"><span data-stu-id="04ade-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="04ade-169">Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas (temos ações específicas para se o palpite está correto ou incorreto).</span><span class="sxs-lookup"><span data-stu-id="04ade-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="04ade-170">Clique duas vezes o **adivinhar incorreto** transição no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="04ade-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="04ade-171">Observe que o **gatilho** já está definido para o mesmo **ReadInt** atividade que foi usada o **adivinhar correto** transição.</span><span class="sxs-lookup"><span data-stu-id="04ade-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="04ade-172">Digite a seguinte expressão para o **condição** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04ade-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="04ade-173">Arraste um **se** atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **ação** seção da transição.</span><span class="sxs-lookup"><span data-stu-id="04ade-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="04ade-174">Digite a seguinte expressão para o **se** da atividade **condição** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04ade-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="04ade-175">Arraste dois **WriteLine** atividades do **primitivos** seção o **caixa de ferramentas** e soltá-los para que um está no **, em seguida,** seção o **se** atividade e é no **Else** seção.</span><span class="sxs-lookup"><span data-stu-id="04ade-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="04ade-176">Clique o **WriteLine** atividade no **, em seguida,** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04ade-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="04ade-177">Clique o **WriteLine** atividade no **Else** seção para selecioná-lo e, em seguida, digite a expressão a seguir para o **texto** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04ade-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="04ade-178">Retornar ao geral exibição no designer de fluxo de trabalho de máquina de estado clicando **StateMachine** na navegação estrutural exibidas na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="04ade-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="04ade-179">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="04ade-179">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="04ade-180">![Fluxo de trabalho de máquina de estado concluído](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span><span class="sxs-lookup"><span data-stu-id="04ade-180">![Completed State Machine Workflow](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="04ade-181">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-181">To build the workflow</span></span>  
  
1.  <span data-ttu-id="04ade-182">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="04ade-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="04ade-183">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="04ade-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="04ade-184">Se você já tiver concluído a [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) etapa com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho de máquina de estado desta etapa, vá para o [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="04ade-184">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ade-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04ade-185">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="04ade-186">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="04ade-186">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="04ade-187">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-187">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="04ade-188">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="04ade-188">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="04ade-189">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="04ade-189">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="04ade-190">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="04ade-190">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)

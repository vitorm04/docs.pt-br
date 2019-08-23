---
title: 'Como: criar um fluxo de trabalho da máquina de estado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 3f1c1beda7519a113ea15c5fed84bcb017afae12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962356"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="f0817-102">Como: criar um fluxo de trabalho da máquina de estado</span><span class="sxs-lookup"><span data-stu-id="f0817-102">How to: Create a State Machine Workflow</span></span>
<span data-ttu-id="f0817-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="f0817-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="f0817-104">Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.StateMachine> atividade, e as atividades personalizadas da seção [como: Criar um tópico](how-to-create-an-activity.md) de atividade.</span><span class="sxs-lookup"><span data-stu-id="f0817-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="f0817-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="f0817-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0817-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="f0817-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="f0817-107">Para concluir este tópico, você deve primeiro concluir [como: Crie uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="f0817-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0817-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="f0817-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="f0817-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="f0817-110">Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="f0817-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="f0817-111">No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**.</span><span class="sxs-lookup"><span data-stu-id="f0817-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="f0817-112">Selecione **atividade** na lista **fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="f0817-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="f0817-113">Digite `StateMachineNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="f0817-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="f0817-114">Arraste uma atividade **StateMachine** da seção **máquina de estado** da caixa de **ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="f0817-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="f0817-116">Clique duas vezes em **StateMachineNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="f0817-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="f0817-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="f0817-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="f0817-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="f0817-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="f0817-119">Digite `MaxNumber` na caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa **tipo de argumento** e pressione ENTER para salvar o argumento...</span><span class="sxs-lookup"><span data-stu-id="f0817-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="f0817-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="f0817-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="f0817-121">Digite `Turns` na caixa de **nome** que `MaxNumber` está abaixo do argumento recém-adicionado, selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="f0817-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="f0817-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="f0817-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="f0817-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="f0817-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="f0817-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="f0817-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="f0817-125">Se nenhuma caixa **criar variável** for exibida, clique na <xref:System.Activities.Statements.StateMachine> atividade na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="f0817-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="f0817-126">Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="f0817-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="f0817-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="f0817-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="f0817-128">Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="f0817-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="f0817-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="f0817-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="f0817-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="f0817-131">Clique em **State1** para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="f0817-131">Click **State1** to select it.</span></span> <span data-ttu-id="f0817-132">Na **janela Propriedades**, altere o **DisplayName** para `Initialize Target`.</span><span class="sxs-lookup"><span data-stu-id="f0817-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="f0817-133">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="f0817-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="f0817-134">Clique duas vezes no estado de destino de **inicialização** renomeado recentemente no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="f0817-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="f0817-135">Arraste uma atividade **atribuir** da seção **primitivas** da caixa de **ferramentas** e solte-a na seção **entrada** do estado.</span><span class="sxs-lookup"><span data-stu-id="f0817-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="f0817-136">Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="f0817-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="f0817-137">Se a janela **caixa de ferramentas** não for exibida, selecione caixa de **ferramentas** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="f0817-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="f0817-138">Retorne à exibição de máquina de estado geral no designer de fluxo de trabalho clicando em **StateMachine** na exibição de navegação estrutural na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="f0817-139">Arraste uma atividade de **estado** da seção **máquina de estado** da **caixa de ferramentas** para o designer de fluxo de trabalho e passe o mouse sobre o estado de destino de **inicialização** .</span><span class="sxs-lookup"><span data-stu-id="f0817-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="f0817-140">Observe que quatro triângulos aparecerão em torno do estado de **inicialização de destino** quando o novo estado estiver sobre ele.</span><span class="sxs-lookup"><span data-stu-id="f0817-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="f0817-141">Descarte o novo estado no triângulo imediatamente abaixo do estado de **inicialização de destino** .</span><span class="sxs-lookup"><span data-stu-id="f0817-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="f0817-142">Isso coloca o novo estado no fluxo de trabalho e cria uma transição do estado de **destino de inicialização** para o novo estado.</span><span class="sxs-lookup"><span data-stu-id="f0817-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="f0817-143">Clique em **State1** para selecioná-lo, altere o `Enter Guess` **DisplayName** para e clique duas vezes no estado no designer de fluxo de trabalho para expandi-lo.</span><span class="sxs-lookup"><span data-stu-id="f0817-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="f0817-144">Arraste uma atividade **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-a na seção **entrada** do estado.</span><span class="sxs-lookup"><span data-stu-id="f0817-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="f0817-145">Digite a expressão a seguir na caixa de propriedade **texto** de **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="f0817-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="f0817-146">Arraste uma atividade **assign** da seção **primitivas** da caixa de **ferramentas** e solte na seção **sair** do estado.</span><span class="sxs-lookup"><span data-stu-id="f0817-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="f0817-147">Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="f0817-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="f0817-148">Retorne à exibição de máquina de estado geral no designer de fluxo de trabalho clicando em **StateMachine** na exibição de navegação estrutural na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="f0817-149">Arraste uma atividade FinalState da seção **máquina de estado** da **caixa de ferramentas**, passe o mouse sobre o estado de **adivinhação Enter** e solte-o no triângulo que aparece à direita do estado **Enter estimar** para que uma transição seja criado entre **Enter estimativa** e **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="f0817-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="f0817-150">O nome padrão da transição é **T2**.</span><span class="sxs-lookup"><span data-stu-id="f0817-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="f0817-151">Clique na transição no designer de fluxo de trabalho para selecioná-la e defina seu **DisplayName** como **palpite correto**.</span><span class="sxs-lookup"><span data-stu-id="f0817-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="f0817-152">Em seguida, clique eselecione o FinalState e arraste-o para a direita para que haja espaço para que o nome de transição completo seja exibido sem sobreposição de qualquer um dos dois Estados.</span><span class="sxs-lookup"><span data-stu-id="f0817-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="f0817-153">Isso facilitará a conclusão das etapas restantes no tutorial.</span><span class="sxs-lookup"><span data-stu-id="f0817-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="f0817-154">Clique duas vezes na transição **correta** de adivinhação renomeada no designer de fluxo de trabalho para expandi-la.</span><span class="sxs-lookup"><span data-stu-id="f0817-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="f0817-155">Arraste uma atividade **ReadInt** da seção **NumberGuessWorkflowActivities** da caixa de **ferramentas** e solte-a na seção **gatilho** da transição.</span><span class="sxs-lookup"><span data-stu-id="f0817-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="f0817-156">Na **janela Propriedades** da atividade **ReadInt** , digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** e digite `Guess` na caixa valor da propriedade de **resultado**</span><span class="sxs-lookup"><span data-stu-id="f0817-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="f0817-157">Digite a expressão a seguir na caixa de valor da propriedade **Condition** da transição **correta** .</span><span class="sxs-lookup"><span data-stu-id="f0817-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="f0817-158">Retorne à exibição de máquina de estado geral no designer de fluxo de trabalho clicando em **StateMachine** na exibição de navegação estrutural na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0817-159">Uma transição ocorre quando o evento de gatilho é recebido e o <xref:System.Activities.Statements.Transition.Condition%2A>, se houver, é avaliado como `True`.</span><span class="sxs-lookup"><span data-stu-id="f0817-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="f0817-160">Para essa transição, se o usuário corresponder `Guess` ao gerado `Target`aleatoriamente, o controle passará para o FinalState e o fluxo de trabalho será concluído.</span><span class="sxs-lookup"><span data-stu-id="f0817-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="f0817-161">Dependendo se a estimativa está correta, o fluxo de trabalho deve fazer a transição para o FinalState ou de volta para o estado de **adivinhação Enter** para outra tentativa.</span><span class="sxs-lookup"><span data-stu-id="f0817-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="f0817-162">Ambas as transições compartilham o mesmo gatilho de aguardando que a adivinhação do usuário seja recebida por meio da atividade **ReadInt** .</span><span class="sxs-lookup"><span data-stu-id="f0817-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="f0817-163">Isso é chamado de uma transição compartilhada.</span><span class="sxs-lookup"><span data-stu-id="f0817-163">This is called a shared transition.</span></span> <span data-ttu-id="f0817-164">Para criar uma transição compartilhada, clique no círculo que indica o início da transição de **adivinhação correta** e arraste-a para o estado desejado.</span><span class="sxs-lookup"><span data-stu-id="f0817-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="f0817-165">Nesse caso, a transição é uma transição automática, portanto, arraste o ponto inicial da transição de **adivinhação correta** e solte-a de volta na parte inferior do estado de **adivinhação Enter** .</span><span class="sxs-lookup"><span data-stu-id="f0817-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="f0817-166">Depois de criar a transição, selecione-a no designer de fluxo de trabalho e defina sua propriedade **DisplayName** como **adivinhar incorreta**.</span><span class="sxs-lookup"><span data-stu-id="f0817-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0817-167">As transições compartilhadas também podem ser criadas de dentro do designer de transição clicando em **Adicionar transição de gatilho compartilhado** na parte inferior do designer de transição e, em seguida, selecionando o estado de destino desejado nos **Estados disponíveis para se conectar** menu suspenso.</span><span class="sxs-lookup"><span data-stu-id="f0817-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f0817-168">Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como `false` (ou todas as condições de uma transição do gatilho compartilhada for avaliada como `false`), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados.</span><span class="sxs-lookup"><span data-stu-id="f0817-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="f0817-169">Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas (temos ações específicas para se o palpite está correto ou incorreto).</span><span class="sxs-lookup"><span data-stu-id="f0817-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="f0817-170">Clique duas vezes em **adivinhar** transição incorreta no designer de fluxo de trabalho para expandi-la.</span><span class="sxs-lookup"><span data-stu-id="f0817-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="f0817-171">Observe que o **gatilho** já está definido como a mesma atividade **ReadInt** que foi usada pela transição de **adivinhação correta** .</span><span class="sxs-lookup"><span data-stu-id="f0817-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="f0817-172">Digite a expressão a seguir na caixa valor da propriedade de **condição** .</span><span class="sxs-lookup"><span data-stu-id="f0817-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="f0817-173">Arraste uma atividade **If** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a na seção **ação** da transição.</span><span class="sxs-lookup"><span data-stu-id="f0817-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="f0817-174">Digite a expressão a seguir na caixa de valor da propriedade **condição** **If** da atividade.</span><span class="sxs-lookup"><span data-stu-id="f0817-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
24. <span data-ttu-id="f0817-175">Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que uma esteja na seção **em seguida** da atividade **se** e outra esteja na seção **else** .</span><span class="sxs-lookup"><span data-stu-id="f0817-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="f0817-176">Clique na atividade **WriteLine** na seção **em seguida** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="f0817-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="f0817-177">Clique na atividade **WriteLine** na seção **else** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="f0817-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="f0817-178">Retorne à exibição de máquina de estado geral no designer de fluxo de trabalho clicando em **StateMachine** na exibição de navegação estrutural na parte superior do designer de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="f0817-179">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="f0817-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Ilustração que mostra o fluxo de trabalho da máquina de estado concluído.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="f0817-181">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="f0817-182">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="f0817-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="f0817-183">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [, como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="f0817-184">Se você já tiver concluído o [como: Execute uma etapa](how-to-run-a-workflow.md) de fluxo de trabalho com um estilo diferente de fluxo de trabalho e queira executá-lo usando o fluxo de trabalho de máquina de estado nesta etapa, pule para a seção [ [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="f0817-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0817-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0817-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="f0817-186">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="f0817-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="f0817-187">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="f0817-188">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="f0817-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="f0817-189">Como: Criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="f0817-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="f0817-190">Como: Executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="f0817-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

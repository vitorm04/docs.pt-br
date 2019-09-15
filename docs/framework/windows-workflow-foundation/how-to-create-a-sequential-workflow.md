---
title: 'Como: criar um fluxo de trabalho sequencial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: 61e3f01b1259536ff15d71526e91aef42069722e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989698"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="72162-102">Como: criar um fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="72162-102">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="72162-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="72162-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="72162-104">Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.Sequence> atividade, e as atividades personalizadas da seção [como: Criar um tópico](how-to-create-an-activity.md) de atividade.</span><span class="sxs-lookup"><span data-stu-id="72162-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="72162-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="72162-105">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="72162-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="72162-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="72162-107">Para concluir este tópico, você deve primeiro concluir [como: Crie uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="72162-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="72162-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="72162-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="72162-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-109">To create the workflow</span></span>

1. <span data-ttu-id="72162-110">Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="72162-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="72162-111">No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**.</span><span class="sxs-lookup"><span data-stu-id="72162-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="72162-112">Selecione **atividade** na lista **fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="72162-112">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="72162-113">Digite `SequentialNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="72162-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="72162-114">Arraste uma atividade de **sequência** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="72162-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="72162-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-115">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="72162-116">Clique duas vezes em **SequentialNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="72162-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="72162-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="72162-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="72162-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="72162-118">Click **Create Argument**.</span></span>

4. <span data-ttu-id="72162-119">Digite `MaxNumber` na caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa **tipo de argumento** e pressione ENTER para salvar o argumento...</span><span class="sxs-lookup"><span data-stu-id="72162-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="72162-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="72162-120">Click **Create Argument**.</span></span>

6. <span data-ttu-id="72162-121">Digite `Turns` na caixa de **nome** que `MaxNumber` está abaixo do argumento recém-adicionado, selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="72162-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="72162-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="72162-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="72162-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="72162-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="72162-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="72162-124">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="72162-125">Se nenhuma caixa **criar variável** for exibida, clique na atividade **sequência** na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="72162-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="72162-126">Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="72162-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="72162-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="72162-127">Click **Create Variable**.</span></span>

12. <span data-ttu-id="72162-128">Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="72162-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="72162-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="72162-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="72162-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-130">To add the workflow activities</span></span>

1. <span data-ttu-id="72162-131">Arraste uma atividade **assign** da seção **primitivas** da caixa de **ferramentas** e solte-a na atividade **sequência** .</span><span class="sxs-lookup"><span data-stu-id="72162-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="72162-132">Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="72162-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="72162-133">Se a janela **caixa de ferramentas** não for exibida, selecione caixa de **ferramentas** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="72162-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="72162-134">Arraste uma atividade **DoWhile** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no fluxo de trabalho para que ela esteja abaixo da atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="72162-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="72162-135">Digite a expressão a seguir na caixa de valor da propriedade de **condição** **DoWhile** da atividade.</span><span class="sxs-lookup"><span data-stu-id="72162-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="72162-136">Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="72162-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="72162-137">Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente.</span><span class="sxs-lookup"><span data-stu-id="72162-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="72162-138">Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.</span><span class="sxs-lookup"><span data-stu-id="72162-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="72162-139">Arraste uma atividade de **prompt** da seção **NumberGuessWorkflowActivities** da **caixa de ferramentas** e solte-a na atividade **DoWhile** da etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="72162-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="72162-140">Na **janela Propriedades**, digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** da atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="72162-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="72162-141">Digite `Guess` na caixa valor da propriedade de **resultado** e digite a expressão a seguir na caixa de propriedade **texto** .</span><span class="sxs-lookup"><span data-stu-id="72162-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="72162-142">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="72162-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="72162-143">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e solte-a na atividade **DoWhile** para que ela siga a atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="72162-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="72162-144">Quando você remove a atividade **atribuir** , observe como o designer de fluxo de trabalho adiciona automaticamente uma atividade de **sequência** para conter a atividade de **prompt** e a atividade **assign** recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="72162-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="72162-145">Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="72162-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="72162-146">Arraste uma atividade **If** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a na atividade **sequência** para que ela siga a atividade **atribuir** recém adicionada.</span><span class="sxs-lookup"><span data-stu-id="72162-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="72162-147">Digite a expressão a seguir na caixa de valor da propriedade **condição** **If** da atividade.</span><span class="sxs-lookup"><span data-stu-id="72162-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="72162-148">Arraste outra atividade **If** da seção **fluxo de controle** da caixa de **ferramentas** e solte-a na seção **em seguida** da primeira atividade **If** .</span><span class="sxs-lookup"><span data-stu-id="72162-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="72162-149">Digite a expressão a seguir na caixa de valor da propriedade **condição** **da atividade do recém-adicionado.**</span><span class="sxs-lookup"><span data-stu-id="72162-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="72162-150">Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que uma delas esteja na seção **em seguida** da atividade **se** adicionada recentemente, e outra esteja na seção **else** .</span><span class="sxs-lookup"><span data-stu-id="72162-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="72162-151">Clique na atividade **WriteLine** na seção **em seguida** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="72162-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="72162-152">Clique na atividade **WriteLine** na seção **else** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="72162-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="72162-153">O exemplo a seguir ilustra o fluxo de trabalho concluído:</span><span class="sxs-lookup"><span data-stu-id="72162-153">The following example illustrates the completed workflow:</span></span>

     ![Captura de tela que mostra o fluxo de trabalho Sequencial concluído.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="72162-155">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-155">To build the workflow</span></span>

1. <span data-ttu-id="72162-156">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="72162-156">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="72162-157">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [, como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="72162-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="72162-158">Se você já tiver concluído o [como: Execute uma etapa](how-to-run-a-workflow.md) de fluxo de trabalho com um estilo diferente de fluxo de trabalho e queira executá-lo usando o fluxo de trabalho Sequencial nesta etapa, pule para a seção [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="72162-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72162-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72162-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="72162-160">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="72162-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="72162-161">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="72162-162">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="72162-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="72162-163">Como: Criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="72162-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="72162-164">Como: Executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="72162-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

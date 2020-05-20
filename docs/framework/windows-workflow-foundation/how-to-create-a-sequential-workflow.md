---
title: Como criar um fluxo de trabalho sequencial
description: Este artigo cria um fluxo de trabalho que usa atividades internas, como a atividade de sequência e atividades personalizadas.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: f80ac471fdcc425504b11b5fb17effa888aa9590
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419688"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="8eb52-103">Como criar um fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="8eb52-103">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="8eb52-104">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8eb52-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="8eb52-105">Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.Sequence> atividade, e as atividades personalizadas do tópico [como criar uma atividade](how-to-create-an-activity.md) anterior.</span><span class="sxs-lookup"><span data-stu-id="8eb52-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="8eb52-106">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="8eb52-106">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="8eb52-107">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="8eb52-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8eb52-108">Para concluir este tópico, você deve primeiro concluir [como: criar uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="8eb52-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8eb52-109">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8eb52-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="8eb52-110">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-110">To create the workflow</span></span>

1. <span data-ttu-id="8eb52-111">Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="8eb52-112">No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="8eb52-113">Selecione **Atividade** na lista **Fluxo de Trabalho**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-113">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="8eb52-114">Digite `SequentialNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-114">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="8eb52-115">Arraste uma atividade de **sequência** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8eb52-115">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="8eb52-116">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-116">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="8eb52-117">Clique duas vezes em **SequentialNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="8eb52-117">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="8eb52-118">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="8eb52-119">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-119">Click **Create Argument**.</span></span>

4. <span data-ttu-id="8eb52-120">Digite na `MaxNumber` caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e pressione ENTER para salvar o argumento...</span><span class="sxs-lookup"><span data-stu-id="8eb52-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="8eb52-121">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-121">Click **Create Argument**.</span></span>

6. <span data-ttu-id="8eb52-122">Digite `Turns` na caixa de **nome** que está abaixo do argumento recém-adicionado `MaxNumber` , selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="8eb52-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="8eb52-123">Clique em **Argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **Argumentos**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="8eb52-124">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="8eb52-125">Clique em **Criar Variável**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-125">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="8eb52-126">Se nenhuma caixa **criar variável** for exibida, clique na atividade **sequência** na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="8eb52-126">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="8eb52-127">Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="8eb52-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="8eb52-128">Clique em **Criar Variável**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-128">Click **Create Variable**.</span></span>

12. <span data-ttu-id="8eb52-129">Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="8eb52-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="8eb52-130">Clique em **Variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **Variáveis**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="8eb52-131">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-131">To add the workflow activities</span></span>

1. <span data-ttu-id="8eb52-132">Arraste uma atividade **assign** da seção **primitivas** da caixa de **ferramentas** e solte-a na atividade **sequência** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="8eb52-133">Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma expressão C#** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-133">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="8eb52-134">Se a janela da **Caixa de Ferramentas** não abrir, selecione **Caixa de Ferramentas** no menu **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="8eb52-134">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="8eb52-135">Arraste uma atividade **DoWhile** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no fluxo de trabalho para que ela esteja abaixo da atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-135">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="8eb52-136">Digite a expressão a seguir na caixa de valor da propriedade de **condição** **DoWhile** da atividade.</span><span class="sxs-lookup"><span data-stu-id="8eb52-136">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="8eb52-137">Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="8eb52-137">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="8eb52-138">Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente.</span><span class="sxs-lookup"><span data-stu-id="8eb52-138">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="8eb52-139">Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.</span><span class="sxs-lookup"><span data-stu-id="8eb52-139">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="8eb52-140">Arraste uma atividade de **prompt** da seção **NumberGuessWorkflowActivities** da **caixa de ferramentas** e solte-a na atividade **DoWhile** da etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="8eb52-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="8eb52-141">Na **janela Propriedades**, digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** da atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-141">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="8eb52-142">Digite na `Guess` caixa valor da propriedade de **resultado** e digite a expressão a seguir na caixa de propriedade **texto** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-142">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="8eb52-143">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-143">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="8eb52-144">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e solte-a na atividade **DoWhile** para que ela siga a atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-144">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8eb52-145">Quando você remove a atividade **atribuir** , observe como o designer de fluxo de trabalho adiciona automaticamente uma atividade de **sequência** para conter a atividade de **prompt** e a atividade **assign** recém-adicionada.</span><span class="sxs-lookup"><span data-stu-id="8eb52-145">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="8eb52-146">Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma expressão C#** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-146">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="8eb52-147">Arraste uma atividade **If** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a na atividade **sequência** para que ela siga a atividade **atribuir** recém adicionada.</span><span class="sxs-lookup"><span data-stu-id="8eb52-147">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="8eb52-148">Digite a expressão a seguir na caixa de valor da propriedade **condição** **If** da atividade.</span><span class="sxs-lookup"><span data-stu-id="8eb52-148">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="8eb52-149">Arraste outra atividade **If** da seção **fluxo de controle** da caixa de **ferramentas** e solte-a na seção **em seguida** da primeira atividade **If** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-149">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="8eb52-150">Digite a expressão a seguir na caixa de valor da propriedade **condição** **da atividade do recém-adicionado.**</span><span class="sxs-lookup"><span data-stu-id="8eb52-150">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="8eb52-151">Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que uma delas esteja na seção **em seguida** da atividade **se** adicionada recentemente, e outra esteja na seção **else** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-151">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="8eb52-152">Clique na atividade **WriteLine** na seção **em seguida** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-152">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="8eb52-153">Clique na atividade **WriteLine** na seção **else** para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** .</span><span class="sxs-lookup"><span data-stu-id="8eb52-153">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="8eb52-154">O exemplo a seguir ilustra o fluxo de trabalho concluído:</span><span class="sxs-lookup"><span data-stu-id="8eb52-154">The following example illustrates the completed workflow:</span></span>

     ![Captura de tela que mostra o fluxo de trabalho Sequencial concluído.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="8eb52-156">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-156">To build the workflow</span></span>

1. <span data-ttu-id="8eb52-157">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="8eb52-157">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="8eb52-158">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [como: executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8eb52-158">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="8eb52-159">Se você já tiver concluído a etapa [como executar um fluxo de trabalho](how-to-run-a-workflow.md) com um estilo diferente de fluxo de trabalho e desejar executá-lo usando o fluxo de trabalho Sequencial nesta etapa, pule para a seção [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [como: executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8eb52-159">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8eb52-160">Veja também</span><span class="sxs-lookup"><span data-stu-id="8eb52-160">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="8eb52-161">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8eb52-161">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="8eb52-162">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-162">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="8eb52-163">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="8eb52-163">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="8eb52-164">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="8eb52-164">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="8eb52-165">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8eb52-165">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

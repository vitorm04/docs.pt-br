---
title: 'Como: criar um fluxo de trabalho sequencial'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: c8a16dc0269fbd768a73e99f15f53e38c207a8d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326834"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="b2547-102">Como: criar um fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="b2547-102">How to: Create a Sequential Workflow</span></span>
<span data-ttu-id="b2547-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b2547-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="b2547-104">Este tópico orienta a criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.Sequence> atividade e atividades personalizadas do anterior [como: Criar uma atividade](how-to-create-an-activity.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="b2547-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="b2547-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="b2547-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2547-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2547-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b2547-107">Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="b2547-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2547-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b2547-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-workflow"></a><span data-ttu-id="b2547-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="b2547-110">Clique com botão direito **NumberGuessWorkflowActivities** na **Gerenciador de soluções** e selecione **Add**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="b2547-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="b2547-111">No **Installed**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="b2547-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="b2547-112">Selecione **atividade** da **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="b2547-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="b2547-113">Tipo de `SequentialNumberGuessWorkflow` para o **nome** caixa e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="b2547-113">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="b2547-114">Arraste uma **sequência** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulos no superfície de design de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b2547-114">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="b2547-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="b2547-116">Clique duas vezes em **Sequentialnumberguessworkflow** na **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, caso ainda não esteja sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="b2547-116">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="b2547-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="b2547-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="b2547-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="b2547-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="b2547-119">Tipo `MaxNumber` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="b2547-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="b2547-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="b2547-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="b2547-121">Tipo `Turns` para o **nome** caixa abaixo recém-adicionada `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b2547-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="b2547-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="b2547-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="b2547-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="b2547-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="b2547-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="b2547-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b2547-125">Se nenhum **criar variável** caixa é exibida, clique no **sequência** atividade na superfície do designer de fluxo de trabalho para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="b2547-125">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="b2547-126">Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="b2547-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="b2547-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="b2547-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="b2547-128">Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="b2547-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="b2547-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="b2547-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="b2547-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="b2547-131">Arraste uma **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="b2547-132">Tipo `Target` para o **para** caixa e a seguinte expressão na **insira uma expressão c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="b2547-132">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="b2547-133">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="b2547-133">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="b2547-134">Arraste uma **DoWhile** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no fluxo de trabalho para que fique abaixo o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-134">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>  
  
3. <span data-ttu-id="b2547-135">Digite a seguinte expressão para o **DoWhile** da atividade **condição** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-135">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
     <span data-ttu-id="b2547-136">Uma atividade <xref:System.Activities.Statements.DoWhile> executa suas atividades filho e avalia seu <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2547-136">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="b2547-137">Se o <xref:System.Activities.Statements.DoWhile.Condition%2A> é avaliado como `True`, as atividades no <xref:System.Activities.Statements.DoWhile> são executadas novamente.</span><span class="sxs-lookup"><span data-stu-id="b2547-137">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="b2547-138">Neste exemplo, o palpite do usuário será avaliado e o <xref:System.Activities.Statements.DoWhile> continuará até que a previsão esteja correta.</span><span class="sxs-lookup"><span data-stu-id="b2547-138">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>  
  
4. <span data-ttu-id="b2547-139">Arraste uma **Prompt** a atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="b2547-139">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>  
  
5. <span data-ttu-id="b2547-140">No **janela de propriedades**, tipo `"EnterGuess"` incluindo as aspas na **BookmarkName** caixa de valor de propriedade para o **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-140">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="b2547-141">Tipo de `Guess` para o **resultado** caixa do valor de propriedade e digite a seguinte expressão na **texto** caixa da propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-141">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="b2547-142">Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="b2547-142">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
6. <span data-ttu-id="b2547-143">Arraste um **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **DoWhile** atividade para que ela siga a **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-143">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2547-144">Quando você solta o **atribuir** atividade, observe como o designer de fluxo de trabalho adiciona automaticamente uma **sequência** atividade para conter o **Prompt** recém-adicionada e atividade **Atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-144">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>  
  
7. <span data-ttu-id="b2547-145">Tipo de `Turns` no **para** caixa e `Turns + 1` no **insira uma expressão c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="b2547-145">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
8. <span data-ttu-id="b2547-146">Arraste uma **se** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a adicionados recentemente **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-146">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>  
  
9. <span data-ttu-id="b2547-147">Digite a seguinte expressão para o **se** da atividade **condição** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-147">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
10. <span data-ttu-id="b2547-148">Arraste outro **se** atividade da **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **, em seguida,** seção dos primeiros **Se** atividade.</span><span class="sxs-lookup"><span data-stu-id="b2547-148">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>  
  
11. <span data-ttu-id="b2547-149">Digite a seguinte expressão na recém-adicionada **se** da atividade **condição** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-149">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
12. <span data-ttu-id="b2547-150">Arraste dois **WriteLine** atividades da **primitivos** seção do **caixa de ferramentas** e soltá-los de modo que uma esteja no **, em seguida,** seção recém-adicionada **se** atividade e outra esteja na **Else** seção.</span><span class="sxs-lookup"><span data-stu-id="b2547-150">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>  
  
13. <span data-ttu-id="b2547-151">Clique o **WriteLine** atividade na **, em seguida,** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-151">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
14. <span data-ttu-id="b2547-152">Clique o **WriteLine** atividade na **Else** seção para selecioná-lo e, em seguida, digite a seguinte expressão na **texto** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b2547-152">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
     <span data-ttu-id="b2547-153">O exemplo a seguir ilustra o fluxo de trabalho concluído:</span><span class="sxs-lookup"><span data-stu-id="b2547-153">The following example illustrates the completed workflow:</span></span>  
  
     ![Captura de tela que mostra o fluxo de trabalho sequencial concluído.](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)  
  
## <a name="to-build-the-workflow"></a><span data-ttu-id="b2547-155">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-155">To build the workflow</span></span>  
  
1. <span data-ttu-id="b2547-156">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="b2547-156">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="b2547-157">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b2547-157">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="b2547-158">Se você já tiver concluído o [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) passo a passo com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho sequencial dessa etapa, pule para a [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b2547-158">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2547-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2547-159">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="b2547-160">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="b2547-160">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="b2547-161">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-161">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="b2547-162">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="b2547-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="b2547-163">Como: Criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="b2547-163">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="b2547-164">Como: Executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b2547-164">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

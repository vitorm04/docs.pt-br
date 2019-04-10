---
title: 'Como: criar um fluxo de trabalho de fluxograma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 15cf94d5ea191435723f754f35e43d65632142e2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311195"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="a950b-102">Como: criar um fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="a950b-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="a950b-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a950b-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="a950b-104">Este tópico orienta a criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.Flowchart> atividade e atividades personalizadas do anterior [como: Criar uma atividade](how-to-create-an-activity.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="a950b-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="a950b-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="a950b-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a950b-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="a950b-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="a950b-107">Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="a950b-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a950b-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="a950b-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="a950b-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="a950b-110">Clique com botão direito **NumberGuessWorkflowActivities** na **Gerenciador de soluções** e selecione **Add**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="a950b-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="a950b-111">No **Installed**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="a950b-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="a950b-112">Selecione **atividade** da **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="a950b-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="a950b-113">Tipo de `FlowchartNumberGuessWorkflow` para o **nome** caixa e clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="a950b-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="a950b-114">Arraste uma **fluxograma** a atividade do **fluxograma** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulos no superfície de design de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a950b-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="a950b-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="a950b-116">Clique duas vezes em **Flowchartnumberguessworkflow** na **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, caso ainda não esteja sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="a950b-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="a950b-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="a950b-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="a950b-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="a950b-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="a950b-119">Tipo `MaxNumber` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="a950b-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="a950b-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="a950b-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="a950b-121">Tipo `Turns` para o **nome** caixa abaixo recém-adicionada `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="a950b-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="a950b-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="a950b-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="a950b-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="a950b-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="a950b-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="a950b-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="a950b-125">Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="a950b-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="a950b-126">Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="a950b-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="a950b-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="a950b-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="a950b-128">Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="a950b-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="a950b-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="a950b-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="a950b-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="a950b-131">Arraste um **atribuir** a atividade do **primitivos** seção o **caixa de ferramentas** e passe o mouse sobre o **iniciar** nó, que é na parte superior do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="a950b-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="a950b-132">Quando o **atribuir** atividade está sobre o **iniciar** nó, três triângulos aparecerão em torno do **iniciar** nó.</span><span class="sxs-lookup"><span data-stu-id="a950b-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="a950b-133">Descartar os **atribuir** atividade no triângulo que está diretamente abaixo de **iniciar** nó.</span><span class="sxs-lookup"><span data-stu-id="a950b-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="a950b-134">Isso vinculará os dois itens juntos e designa a **atribuir** atividade como a primeira atividade no fluxograma.</span><span class="sxs-lookup"><span data-stu-id="a950b-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a950b-135">As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem.</span><span class="sxs-lookup"><span data-stu-id="a950b-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="a950b-136">Para fazer isso, passe o mouse sobre o **inicie** nó, clique em um dos retângulos que aparecem quando o mouse está sobre o **iniciar** nó e arraste a conectar-se da linha até a atividade desejada e solte-o em um dos os retângulos que aparecem.</span><span class="sxs-lookup"><span data-stu-id="a950b-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="a950b-137">Você também pode designar uma atividade como a atividade de início clicando duas vezes o it e escolhendo **definido como nó de início**.</span><span class="sxs-lookup"><span data-stu-id="a950b-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="a950b-138">Tipo `Target` para o **para** caixa e a seguinte expressão na **insira uma expressão c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="a950b-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="a950b-139">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="a950b-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="a950b-140">Arrastar um **Prompt** a atividade do **NumberGuessWorkflowActivities** seção do **caixa de ferramentas**, solte-o abaixo de **atribuir** atividade do anterior etapa e conecte-se a **Prompt** atividade para o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="a950b-141">Há três modos de conectar as duas atividades.</span><span class="sxs-lookup"><span data-stu-id="a950b-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="a950b-142">A primeira maneira é para conectá-los conforme você descartar a **Prompt** atividade do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a950b-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="a950b-143">Como você está arrastando o **Prompt** atividade ao fluxo de trabalho, focalize-lo a **atribuir** atividade e solte-o em um dos quatro triângulos que aparecem quando o **Prompt** atividade está sobre o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="a950b-144">A segunda maneira é descartar o **Prompt** atividade no fluxo de trabalho no local desejado.</span><span class="sxs-lookup"><span data-stu-id="a950b-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="a950b-145">Em seguida, passe o mouse sobre o **atribua** atividade e arraste um dos retângulos que aparece para o **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="a950b-146">Arraste o mouse para que a linha de conexão das **atribuir** atividade se conecta a um dos retângulos das **Prompt** atividade e, em seguida, solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="a950b-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="a950b-147">A terceira maneira é muito semelhante ao primeiro, exceto que em vez de arrastar o **Prompt** atividade da **caixa de ferramentas**, arraste-o de seu local na superfície de design de fluxo de trabalho, passe o mouse sobre o  **Atribuir** atividade e solte-o em um dos triângulos que aparece.</span><span class="sxs-lookup"><span data-stu-id="a950b-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="a950b-148">No **janela de propriedades** para o **Prompt** atividade, digite `"EnterGuess"` incluindo as aspas no **BookmarkName** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a950b-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="a950b-149">Tipo de `Guess` para o **resultado** caixa do valor de propriedade e digite a seguinte expressão na **texto** caixa da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a950b-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="a950b-150">Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="a950b-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="a950b-151">Arraste um **atribuir** atividade da **primitivos** seção o **caixa de ferramentas** e conectá-lo usando um dos métodos descritos na etapa anterior para que fique abaixo de  **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="a950b-152">Tipo de `Turns` no **para** caixa e `Turns + 1` no **insira uma expressão c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="a950b-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="a950b-153">Arraste um **FlowDecision** da **fluxograma** seção o **caixa de ferramentas** e conectá-la abaixo o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="a950b-154">No **janela de propriedades**, digite a seguinte expressão na **condição** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a950b-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="a950b-155">Arraste outro **FlowDecision** atividades desde o **caixa de ferramentas** e solte-o abaixo da primeira.</span><span class="sxs-lookup"><span data-stu-id="a950b-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="a950b-156">Conecte as duas atividades arrastando do retângulo que é rotulado **falsos** na parte superior **FlowDecision** atividade para o retângulo na parte superior da segunda **FlowDecision**atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="a950b-157">Se você não vir o **verdadeira** e **falso** rótulos no **FlowDecision**, passe o mouse sobre o **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="a950b-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="a950b-158">Clique na segunda **FlowDecision** atividade para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="a950b-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="a950b-159">No **janela de propriedades**, digite a seguinte expressão na **condição** caixa do valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a950b-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="a950b-160">Arraste duas **WriteLine** atividades da **primitivos** seção o **caixa de ferramentas** e soltá-los para que fiquem lado a lado abaixo das duas **FlowDecision**  atividades.</span><span class="sxs-lookup"><span data-stu-id="a950b-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="a950b-161">Conectar-se a **verdadeira** ação da parte inferior **FlowDecision** atividade mais à esquerda **WriteLine** atividade e o **False** ação para o mais à direita **WriteLine** atividade.</span><span class="sxs-lookup"><span data-stu-id="a950b-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="a950b-162">Clique em mais à esquerda **WriteLine** atividade para selecioná-la e digite a seguinte expressão na **texto** caixa do valor de propriedade **janela propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a950b-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="a950b-163">Conectar-se a **WriteLine** para o lado esquerdo das **Prompt** atividade que está acima dela.</span><span class="sxs-lookup"><span data-stu-id="a950b-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="a950b-164">Clique em mais à direita **WriteLine** atividade para selecioná-la e digite a seguinte expressão na **texto** caixa do valor de propriedade **janela propriedades**.</span><span class="sxs-lookup"><span data-stu-id="a950b-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="a950b-165">Conectar-se a **WriteLine** atividade para o lado direito das **Prompt** atividade acima dele.</span><span class="sxs-lookup"><span data-stu-id="a950b-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="a950b-166">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="a950b-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="a950b-167">![Concluído o Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="a950b-167">![Completed Windows Workflow Foundation](./media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="a950b-168">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="a950b-169">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="a950b-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="a950b-170">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a950b-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="a950b-171">Se você já tiver concluído o [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md) passo a passo com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho de fluxograma dessa etapa, pule para a [para compilar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) seção [como: Executar um fluxo de trabalho](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a950b-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a950b-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a950b-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="a950b-173">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="a950b-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="a950b-174">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="a950b-175">Guia de introdução ao tutorial</span><span class="sxs-lookup"><span data-stu-id="a950b-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="a950b-176">Como: criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="a950b-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="a950b-177">Como: executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="a950b-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

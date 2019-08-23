---
title: 'Como: criar um fluxo de trabalho de fluxograma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: 6d67629503d5acfeff7e14e1889a047444a8d399
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962384"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="bf9b9-102">Como: criar um fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="bf9b9-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="bf9b9-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="bf9b9-104">Este tópico percorre a criação de um fluxo de trabalho que usa atividades internas, como a <xref:System.Activities.Statements.Flowchart> atividade, e as atividades personalizadas da seção [como: Criar um tópico](how-to-create-an-activity.md) de atividade.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="bf9b9-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf9b9-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="bf9b9-107">Para concluir este tópico, você deve primeiro concluir [como: Crie uma atividade](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="bf9b9-107">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf9b9-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="bf9b9-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="bf9b9-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="bf9b9-110">Clique com o botão direito do mouse em **NumberGuessWorkflowActivities** em **Gerenciador de soluções** e selecione **Adicionar**, **novo item**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="bf9b9-111">No nó **itens comuns** **instalados**, selecione fluxo de **trabalho**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="bf9b9-112">Selecione **atividade** na lista **fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="bf9b9-113">Digite `FlowchartNumberGuessWorkflow` na caixa **nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="bf9b9-114">Arraste uma atividade de **fluxograma** da seção **fluxograma** da **caixa de ferramentas** e solte-a no rótulo **soltar atividade aqui** na superfície de design do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="bf9b9-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="bf9b9-116">Clique duas vezes em **FlowchartNumberGuessWorkflow. XAML** em **Gerenciador de soluções** para exibir o fluxo de trabalho no designer, se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="bf9b9-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="bf9b9-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="bf9b9-119">Digite `MaxNumber` na caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **Int32** na lista suspensa **tipo de argumento** e pressione ENTER para salvar o argumento...</span><span class="sxs-lookup"><span data-stu-id="bf9b9-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="bf9b9-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="bf9b9-121">Digite `Turns` na caixa de **nome** que `MaxNumber` está abaixo do argumento recém-adicionado, selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e, em seguida, pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="bf9b9-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **argumentos** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="bf9b9-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="bf9b9-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bf9b9-125">Se nenhuma caixa **criar variável** for exibida, clique na <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="bf9b9-126">Digite `Guess` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="bf9b9-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="bf9b9-128">Digite `Target` na caixa **nome** , selecione **Int32** na lista suspensa **tipo de variável** e pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="bf9b9-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o painel **variáveis** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="bf9b9-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="bf9b9-131">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e focalize-a sobre o nó **inicial** , que está na parte superior do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="bf9b9-132">Quando a atividade **assign** estiver sobre o nó **inicial** , três triângulos aparecerão em torno do nó **inicial** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="bf9b9-133">Descarte a atividade **atribuir** no triângulo que está diretamente abaixo do nó de **início** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="bf9b9-134">Isso vinculará os dois itens em conjunto e designará a atividade **atribuir** como a primeira atividade no fluxograma.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf9b9-135">As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="bf9b9-136">Para fazer isso, passe o mouse sobre o nó **inicial** , clique em um dos retângulos que aparecem quando o mouse está sobre o nó **inicial** e arraste a linha de conexão para baixo até a atividade desejada e solte-a em um dos retângulos que aparecem.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="bf9b9-137">Você também pode designar uma atividade como a atividade inicial clicando com o botão direito do mouse nela e escolhendo **definir como nó inicial**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="bf9b9-138">Digite `Target` na caixa **para** e a expressão a seguir na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="bf9b9-139">Se a janela **caixa de ferramentas** não for exibida, selecione caixa de **ferramentas** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="bf9b9-140">Arraste uma atividade de **prompt** da seção **NumberGuessWorkflowActivities** da **caixa de ferramentas**, solte-a abaixo da atividade **atribuir** da etapa anterior e conecte a atividade de **prompt** à atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="bf9b9-141">Há três modos de conectar as duas atividades.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="bf9b9-142">A primeira maneira é conectá-los à medida que você remove a atividade **prompt** no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="bf9b9-143">Conforme você está arrastando a atividade de **prompt** para o fluxo de trabalho, passe o mouse sobre a atividade **atribuir** e solte-a em um dos quatro triângulos que aparecem quando a atividade de **prompt** está sobre a atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="bf9b9-144">A segunda maneira é descartar a atividade de **prompt** no fluxo de trabalho no local desejado.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="bf9b9-145">Em seguida, passe o mouse sobre a atividade **atribuir** e arraste um dos retângulos que aparece até a atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="bf9b9-146">Arraste o mouse para que a linha de conexão da atividade **atribuir** se conecte a um dos retângulos da atividade de **prompt** e, em seguida, solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="bf9b9-147">A terceira maneira é muito semelhante à primeira maneira, exceto que, em vez de arrastar a atividade **prompt** da **caixa de ferramentas**, você a arrasta de seu local na superfície de design do fluxo de trabalho, passa o mouse sobre a atividade **atribuir** e a solta em uma das triângulos que aparece.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="bf9b9-148">Na **janela Propriedades** da atividade **prompt** , digite `"EnterGuess"` incluindo as aspas na caixa valor da propriedade **BookmarkName** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="bf9b9-149">Digite `Guess` na caixa valor da propriedade de **resultado** e digite a expressão a seguir na caixa de propriedade **texto** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="bf9b9-150">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="bf9b9-151">Arraste uma atividade **atribuir** da seção **primitivos** da caixa de **ferramentas** e conecte-a usando um dos métodos descritos na etapa anterior para que ela esteja abaixo da atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="bf9b9-152">Digite `Turns` na caixa **para** e `Turns + 1` na caixa **Inserir uma C# expressão** ou **Inserir uma expressão VB** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="bf9b9-153">Arraste um **FlowDecision** da seção **fluxograma** da caixa de **ferramentas** e conecte-o abaixo da atividade **atribuir** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="bf9b9-154">Na **janela Propriedades**, digite a expressão a seguir na caixa valor da propriedade de **condição** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="bf9b9-155">Arraste outra atividade **FlowDecision** da **caixa de ferramentas** e solte-a abaixo da primeira.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="bf9b9-156">Conecte as duas atividades arrastando do retângulo rotulado como **falso** na atividade **FlowDecision** superior para o retângulo na parte superior da segunda atividade **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bf9b9-157">Se você não vir os rótulos **verdadeiro** e **falso** no **FlowDecision**, passe o mouse sobre o **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="bf9b9-158">Clique na segunda atividade **FlowDecision** para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="bf9b9-159">Na **janela Propriedades**, digite a expressão a seguir na caixa valor da propriedade de **condição** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="bf9b9-160">Arraste duas atividades **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-as para que elas fiquem lado a lado abaixo das duas atividades **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="bf9b9-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="bf9b9-161">Conecte a ação **verdadeira** da atividade **FlowDecision** inferior à atividade **WriteLine** mais à esquerda e a ação **false** para a atividade **WriteLine** mais à direita.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="bf9b9-162">Clique na atividade **WriteLine** mais à esquerda para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** na **janela Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="bf9b9-163">Conecte o **WriteLine** ao lado esquerdo da atividade de **prompt** que está acima dele.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="bf9b9-164">Clique na atividade **WriteLine** mais à direita para selecioná-la e digite a expressão a seguir na caixa valor da propriedade de **texto** na **janela Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="bf9b9-165">Conecte a atividade **WriteLine** ao lado direito da atividade de **prompt** acima dela.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="bf9b9-166">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Diagrama que mostra um fluxograma de Windows Workflow Foundation concluído.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="bf9b9-168">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="bf9b9-169">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="bf9b9-170">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico [, como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="bf9b9-171">Se você já tiver concluído o [como: Execute uma etapa](how-to-run-a-workflow.md) de fluxo de trabalho com um estilo diferente de fluxo de trabalho e deseje executá-lo usando o fluxo de trabalho de fluxograma nesta etapa, pule para a seção [para criar e executar o aplicativo](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) de [como: Executar um fluxo](how-to-run-a-workflow.md)de trabalho.</span><span class="sxs-lookup"><span data-stu-id="bf9b9-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9b9-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf9b9-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="bf9b9-173">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="bf9b9-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="bf9b9-174">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="bf9b9-175">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="bf9b9-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="bf9b9-176">Como: Criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="bf9b9-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="bf9b9-177">Como: Executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="bf9b9-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)

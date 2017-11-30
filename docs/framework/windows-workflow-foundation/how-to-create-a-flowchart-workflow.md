---
title: Como criar um fluxo de trabalho de fluxograma
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
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 570e51c3b9c8ee227a9c5688fc7caa1b4a0d9c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="889af-102">Como criar um fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="889af-102">How to: Create a Flowchart Workflow</span></span>
<span data-ttu-id="889af-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="889af-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="889af-104">Este tópico percorre criando um fluxo de trabalho que usa as duas atividades internas, como o <xref:System.Activities.Statements.Flowchart> atividade e as atividades personalizadas do anterior [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="889af-104">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="889af-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="889af-105">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="889af-106">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="889af-106">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="889af-107">Para concluir este tópico, você deve completar [como: criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="889af-107">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="889af-108">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="889af-108">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="889af-109">Para criar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-109">To create the workflow</span></span>  
  
1.  <span data-ttu-id="889af-110">Clique com botão direito **NumberGuessWorkflowActivities** na **Solution Explorer** e selecione **adicionar**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="889af-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2.  <span data-ttu-id="889af-111">No **instalado**, **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="889af-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="889af-112">Selecione **atividade** do **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="889af-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3.  <span data-ttu-id="889af-113">Tipo `FlowchartNumberGuessWorkflow` para o **nome** caixa e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="889af-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4.  <span data-ttu-id="889af-114">Arraste um **fluxograma** atividade do **fluxograma** seção o **caixa de ferramentas** e solte-a para o **descartar atividade aqui** rótulo no superfície de design de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="889af-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="889af-115">Para criar as variáveis e os argumentos do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-115">To create the workflow variables and arguments</span></span>  
  
1.  <span data-ttu-id="889af-116">Clique duas vezes em **FlowchartNumberGuessWorkflow.xaml** na **Solution Explorer** para exibir o fluxo de trabalho no designer, se ainda não estiver sendo exibida.</span><span class="sxs-lookup"><span data-stu-id="889af-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2.  <span data-ttu-id="889af-117">Clique em **argumentos** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="889af-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3.  <span data-ttu-id="889af-118">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="889af-118">Click **Create Argument**.</span></span>  
  
4.  <span data-ttu-id="889af-119">Tipo `MaxNumber` no **nome** caixa, selecione **na** do **direção** lista suspensa, selecione **Int32** da **Tipo de argumento** lista suspensa e, em seguida, pressione ENTER para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="889af-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5.  <span data-ttu-id="889af-120">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="889af-120">Click **Create Argument**.</span></span>  
  
6.  <span data-ttu-id="889af-121">Tipo `Turns` para o **nome** caixa abaixo recém-adicionado `MaxNumber` argumento, selecione **Out** do **direção** lista suspensa, selecione  **Int32** do **tipo de argumento** lista suspensa e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="889af-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7.  <span data-ttu-id="889af-122">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="889af-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8.  <span data-ttu-id="889af-123">Clique em **variáveis** no lado inferior esquerdo do designer de fluxo de trabalho para exibir o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="889af-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="889af-124">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="889af-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="889af-125">Se nenhum **criar variável** caixa é exibida, clique no <xref:System.Activities.Statements.Flowchart> atividade na superfície do designer de fluxo de trabalho para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="889af-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="889af-126">Tipo `Guess` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="889af-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="889af-127">Clique em **criar variável**.</span><span class="sxs-lookup"><span data-stu-id="889af-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="889af-128">Tipo `Target` para o **nome** caixa, selecione **Int32** do **tipo de variável** lista suspensa e, em seguida, pressione ENTER para salvar a variável.</span><span class="sxs-lookup"><span data-stu-id="889af-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="889af-129">Clique em **variáveis** no lado inferior esquerdo do designer de atividade para fechar o **variáveis** painel.</span><span class="sxs-lookup"><span data-stu-id="889af-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="889af-130">Para adicionar as atividades de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-130">To add the workflow activities</span></span>  
  
1.  <span data-ttu-id="889af-131">Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e passe o mouse sobre o **iniciar** nó, que está no topo do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="889af-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="889af-132">Quando o **atribuir** atividade está sobre o **iniciar** nó, três triângulos aparecerá ao redor o **iniciar** nó.</span><span class="sxs-lookup"><span data-stu-id="889af-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="889af-133">Descartar o **atribuir** atividade no triângulo que está diretamente abaixo do **iniciar** nó.</span><span class="sxs-lookup"><span data-stu-id="889af-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="889af-134">Isso vinculará os dois itens juntos e designa o **atribuir** atividade como a primeira atividade do fluxograma.</span><span class="sxs-lookup"><span data-stu-id="889af-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="889af-135">As atividades também podem ser indicadas como a atividade de início no fluxo de trabalho manualmente vinculando-as ao nó de origem.</span><span class="sxs-lookup"><span data-stu-id="889af-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="889af-136">Para fazer isso, passe o mouse sobre o **iniciar** nó, clique em um dos retângulos que aparecem quando o mouse estiver sobre o **iniciar** nó e arraste a conexão de linha para baixo até a atividade desejada e solte-o em um dos os retângulos que aparecem.</span><span class="sxs-lookup"><span data-stu-id="889af-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="889af-137">Você também pode designar e atividade como a atividade inicial clicando duas vezes o it e escolhendo **definido como nó iniciar**.</span><span class="sxs-lookup"><span data-stu-id="889af-137">You can also designate and activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2.  <span data-ttu-id="889af-138">Tipo `Target` no **para** caixa e a expressão a seguir para o **insira uma expressão de c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="889af-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="889af-139">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="889af-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="889af-140">Arrastar um **Prompt** atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas**, solte-o abaixo de **atribuir** atividade do anterior etapa e conecte-se a **Prompt** atividade para o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="889af-141">Há três modos de conectar as duas atividades.</span><span class="sxs-lookup"><span data-stu-id="889af-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="889af-142">O primeiro modo é para conectá-los como você descartar o **Prompt** atividade no fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="889af-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="889af-143">Como você está arrastando o **Prompt** atividade ao fluxo de trabalho, o focalize o **atribuir** atividade e solte-a para um dos quatro triângulos que aparecem quando o **Prompt** atividade está sobre o **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="889af-144">A segunda maneira é remover o **Prompt** atividade no fluxo de trabalho no local desejado.</span><span class="sxs-lookup"><span data-stu-id="889af-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="889af-145">Em seguida, passe o mouse sobre o **atribuir** atividade e arraste um dos retângulos que aparece para o **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="889af-146">Arraste o mouse para que a conexão de linha do **atribuir** atividade se conecta a um dos retângulos do **Prompt** atividade e, em seguida, solte o botão do mouse.</span><span class="sxs-lookup"><span data-stu-id="889af-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="889af-147">A terceira maneira é muito semelhante à forma como primeiro, exceto que, em vez de arrastar o **Prompt** atividade a partir de **caixa de ferramentas**, arraste-o de seu local na superfície de design de fluxo de trabalho, passe o mouse sobre o  **Atribuir** atividade e soltá-lo em uma de triângulos que aparece.</span><span class="sxs-lookup"><span data-stu-id="889af-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4.  <span data-ttu-id="889af-148">No **janela propriedades** para o **Prompt** atividade, digite `"EnterGuess"` incluindo as aspas no **BookmarkName** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="889af-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="889af-149">Tipo `Guess` no **resultados** propriedade valor caixa e digite a seguinte expressão para o **texto** caixa da propriedade.</span><span class="sxs-lookup"><span data-stu-id="889af-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="889af-150">Se o **janela propriedades** não é exibida, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="889af-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="889af-151">Arraste um **atribuir** atividade do **primitivos** seção o **caixa de ferramentas** e conectá-lo usando um dos métodos descritos na etapa anterior para que ele fique abaixo do  **Prompt** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6.  <span data-ttu-id="889af-152">Tipo `Turns` para o **para** caixa e `Turns + 1` no **insira uma expressão de c#** ou **insira uma expressão VB** caixa.</span><span class="sxs-lookup"><span data-stu-id="889af-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7.  <span data-ttu-id="889af-153">Arraste um **FlowDecision** do **fluxograma** seção do **caixa de ferramentas** e conecte-o abaixo de **atribuir** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="889af-154">No **janela propriedades**, digite a seguinte expressão para o **condição** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="889af-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8.  <span data-ttu-id="889af-155">Arraste outro **FlowDecision** atividade a partir de **caixa de ferramentas** e solte-o abaixo do primeiro.</span><span class="sxs-lookup"><span data-stu-id="889af-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="889af-156">Conecte as duas atividades, arrastando do retângulo que é rotulado **False** na parte superior **FlowDecision** atividade para o retângulo na parte superior da segunda **FlowDecision**atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="889af-157">Se você não vir o **True** e **False** rótulos no **FlowDecision**, passe o mouse sobre o **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="889af-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="889af-158">Clique no segundo **FlowDecision** atividade para selecioná-la.</span><span class="sxs-lookup"><span data-stu-id="889af-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="889af-159">No **janela propriedades**, digite a seguinte expressão para o **condição** caixa de valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="889af-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```
    Guess < Target  
    ```  
  
10. <span data-ttu-id="889af-160">Arraste dois **WriteLine** atividades do **primitivos** seção o **caixa de ferramentas** e soltá-los para que fiquem lado a lado abaixo os dois **FlowDecision**  atividades.</span><span class="sxs-lookup"><span data-stu-id="889af-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="889af-161">Conecte-se a **True** ação da parte inferior **FlowDecision** atividade para a esquerda **WriteLine** atividade e o **False** ação para o mais à direita **WriteLine** atividade.</span><span class="sxs-lookup"><span data-stu-id="889af-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="889af-162">Clique em mais à esquerda **WriteLine** atividade para selecioná-lo e digite a expressão a seguir para o **texto** caixa valor da propriedade o **janela propriedades**.</span><span class="sxs-lookup"><span data-stu-id="889af-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="889af-163">Conecte-se a **WriteLine** para o lado esquerdo do **Prompt** atividade acima dele.</span><span class="sxs-lookup"><span data-stu-id="889af-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="889af-164">Clique em mais à direita **WriteLine** atividade para selecioná-lo e digite a seguinte expressão no **texto** caixa valor da propriedade de **janela propriedades**.</span><span class="sxs-lookup"><span data-stu-id="889af-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="889af-165">Conecte-se a **WriteLine** à direita da atividade a **Prompt** atividade acima dele.</span><span class="sxs-lookup"><span data-stu-id="889af-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="889af-166">O exemplo a seguir ilustra o fluxo de trabalho concluído.</span><span class="sxs-lookup"><span data-stu-id="889af-166">The following example illustrates the completed workflow.</span></span>  
  
     <span data-ttu-id="889af-167">![Concluído o Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span><span class="sxs-lookup"><span data-stu-id="889af-167">![Completed Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/media/gettingstartedtutorialcompletedflowchart.PNG "GettingStartedTutorialCompletedFlowchart")</span></span>  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="889af-168">Para compilar o fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-168">To build the workflow</span></span>  
  
1.  <span data-ttu-id="889af-169">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="889af-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="889af-170">Para obter instruções sobre como executar o fluxo de trabalho, consulte o próximo tópico, [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="889af-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span> <span data-ttu-id="889af-171">Se você já tiver concluído a [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) etapa com um estilo diferente de fluxo de trabalho e quiser executá-lo usando o fluxo de trabalho do fluxograma desta etapa, vá para o [para compilar e executar o aplicativo](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication)seção [como: executar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="889af-171">If you have already completed the [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="889af-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="889af-172">See Also</span></span>  
 <xref:System.Activities.Statements.Flowchart>  
 <xref:System.Activities.Statements.FlowDecision>  
 [<span data-ttu-id="889af-173">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="889af-173">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="889af-174">Criando fluxos de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-174">Designing Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/designing-workflows.md)  
 [<span data-ttu-id="889af-175">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="889af-175">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="889af-176">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="889af-176">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 [<span data-ttu-id="889af-177">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="889af-177">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)

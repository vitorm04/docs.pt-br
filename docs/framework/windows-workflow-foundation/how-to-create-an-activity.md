---
title: Como criar uma atividade
description: 'Este artigo mostra como criar duas atividades no Workflow Foundation: uma que usa o código para implementar sua lógica e outra definida usando outras atividades.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: dae099d102b0c85d09a1ef8bcce56e8a9096bd20
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419584"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="40063-103">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="40063-103">How to: Create an Activity</span></span>

<span data-ttu-id="40063-104">As atividades são a unidade principal de comportamento no [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40063-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="40063-105">A lógica de execução de uma atividade pode ser implementada em código gerenciado ou pode ser implementada usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="40063-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="40063-106">Este tópico demonstra como criar duas atividades.</span><span class="sxs-lookup"><span data-stu-id="40063-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="40063-107">A primeira atividade é uma atividade simples que usa o código para implementar a sua lógica de execução.</span><span class="sxs-lookup"><span data-stu-id="40063-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="40063-108">A implementação da segunda atividade é definida usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="40063-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="40063-109">Essas atividades são usadas nas seguintes etapas no tutorial.</span><span class="sxs-lookup"><span data-stu-id="40063-109">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="40063-110">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) – introdução tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="40063-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="40063-111">Criar o projeto de biblioteca de atividades</span><span class="sxs-lookup"><span data-stu-id="40063-111">Create the activity library project</span></span>

1. <span data-ttu-id="40063-112">Abra o Visual Studio e escolha **novo**  >  **projeto** no menu **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="40063-112">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="40063-113">Na caixa de diálogo **novo projeto** , na categoria **instalado** , selecione **Visual C#**  >  **fluxo de trabalho** do Visual C# (ou **Visual Basic**  >  **fluxo de trabalho**).</span><span class="sxs-lookup"><span data-stu-id="40063-113">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="40063-114">Se você não vir a categoria de modelo de **fluxo de trabalho** , talvez seja necessário instalar o componente **Windows Workflow Foundation** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40063-114">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="40063-115">Escolha o link **abrir instalador do Visual Studio** no lado esquerdo da caixa de diálogo **novo projeto** .</span><span class="sxs-lookup"><span data-stu-id="40063-115">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="40063-116">Em Instalador do Visual Studio, selecione a guia **componentes individuais** . Em seguida, na categoria **atividades de desenvolvimento** , selecione o componente **Windows Workflow Foundation** .</span><span class="sxs-lookup"><span data-stu-id="40063-116">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="40063-117">Escolha **Modificar** para instalar o componente.</span><span class="sxs-lookup"><span data-stu-id="40063-117">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="40063-118">Selecione o modelo de projeto de **biblioteca de atividades** .</span><span class="sxs-lookup"><span data-stu-id="40063-118">Select the **Activity Library** project template.</span></span> <span data-ttu-id="40063-119">Digite `NumberGuessWorkflowActivities` na caixa **Nome** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="40063-119">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="40063-120">Clique com o botão direito do mouse em **Activity1.xaml** no **Gerenciador de Soluções** e selecione **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="40063-120">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="40063-121">Clique em **OK** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="40063-121">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="40063-122">Criar a atividade ReadInt</span><span class="sxs-lookup"><span data-stu-id="40063-122">Create the ReadInt activity</span></span>

1. <span data-ttu-id="40063-123">Escolha **Adicionar novo item** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="40063-123">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="40063-124">No nó **Installed**  >  **itens comuns** instalados, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="40063-124">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="40063-125">Selecione **atividade de código** na lista **fluxo de trabalho** .</span><span class="sxs-lookup"><span data-stu-id="40063-125">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="40063-126">Digite `ReadInt` na caixa **Nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="40063-126">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="40063-127">Substitua a definição existente de `ReadInt` pela seguinte definição.</span><span class="sxs-lookup"><span data-stu-id="40063-127">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="40063-128">A atividade `ReadInt` é derivada de <xref:System.Activities.NativeActivity%601> em vez de <xref:System.Activities.CodeActivity>, que é o padrão para o modelo de atividade de código.</span><span class="sxs-lookup"><span data-stu-id="40063-128">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="40063-129"><xref:System.Activities.CodeActivity%601> poderá ser usado se a atividade fornecer um único resultado, que é exposto através do argumento <xref:System.Activities.Activity%601.Result%2A>, mas <xref:System.Activities.CodeActivity%601> não oferece suporte ao uso de indicadores, portanto <xref:System.Activities.NativeActivity%601> será usado.</span><span class="sxs-lookup"><span data-stu-id="40063-129"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="40063-130">Criar a atividade de prompt</span><span class="sxs-lookup"><span data-stu-id="40063-130">Create the Prompt activity</span></span>

1. <span data-ttu-id="40063-131">Pressione **Ctrl** + **Shift** + **B** para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="40063-131">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="40063-132">Compilar o projeto permite que a atividade `ReadInt` neste projeto seja usada para criar a atividade personalizada dessa etapa.</span><span class="sxs-lookup"><span data-stu-id="40063-132">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="40063-133">Escolha **Adicionar novo item** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="40063-133">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="40063-134">No nó **Installed**  >  **itens comuns** instalados, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="40063-134">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="40063-135">Selecione **Atividade** na lista **Fluxo de Trabalho**.</span><span class="sxs-lookup"><span data-stu-id="40063-135">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="40063-136">Digite `Prompt` na caixa **Nome** e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="40063-136">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="40063-137">Clique duas vezes em **prompt. XAML** em **Gerenciador de soluções** para exibi-lo no designer se ele ainda não estiver sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="40063-137">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="40063-138">Clique em **Argumentos** no lado inferior esquerdo do designer de atividade para exibir o painel **Argumentos**.</span><span class="sxs-lookup"><span data-stu-id="40063-138">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="40063-139">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="40063-139">Click **Create Argument**.</span></span>

8. <span data-ttu-id="40063-140">Digite na `BookmarkName` caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **cadeia de caracteres** na lista suspensa tipo de **argumento** e pressione **Enter** para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="40063-140">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="40063-141">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="40063-141">Click **Create Argument**.</span></span>

10. <span data-ttu-id="40063-142">Digite `Result` na caixa de **nome** que está abaixo do argumento recém-adicionado `BookmarkName` , selecione **fora** na lista suspensa **direção** , selecione **Int32** na lista suspensa tipo de **argumento** e pressione **Enter**para.</span><span class="sxs-lookup"><span data-stu-id="40063-142">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="40063-143">Clique em **Criar Argumento**.</span><span class="sxs-lookup"><span data-stu-id="40063-143">Click **Create Argument**.</span></span>

12. <span data-ttu-id="40063-144">Digite na `Text` caixa **nome** , selecione **em na** lista suspensa **direção** , selecione **cadeia de caracteres** na lista suspensa tipo de **argumento** e pressione **Enter** para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="40063-144">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="40063-145">Esses três argumentos são associados aos argumentos correspondentes das atividades <xref:System.Activities.Statements.WriteLine> e `ReadInt` que são adicionadas à atividade `Prompt` nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="40063-145">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="40063-146">Clique em **Argumentos** no lado inferior esquerdo do designer de atividade para fechar o painel **Argumentos**.</span><span class="sxs-lookup"><span data-stu-id="40063-146">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="40063-147">Arraste uma atividade de **sequência** da seção **fluxo de controle** da **caixa de ferramentas** e solte-a no rótulo **descartar atividade aqui** do designer de atividade de **prompt** .</span><span class="sxs-lookup"><span data-stu-id="40063-147">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="40063-148">Se a janela da **Caixa de Ferramentas** não abrir, selecione **Caixa de Ferramentas** no menu **Exibir**.</span><span class="sxs-lookup"><span data-stu-id="40063-148">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="40063-149">Arraste uma atividade **WriteLine** da seção **primitivas** da caixa de **ferramentas** e solte-a no rótulo **descartar atividade aqui** da atividade de **sequência** .</span><span class="sxs-lookup"><span data-stu-id="40063-149">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="40063-150">Vincule o argumento **Text** da atividade **WriteLine** ao argumento Text da atividade **prompt** digitando na caixa de **texto** `Text` **Inserir uma expressão C#** ou **Inserir uma expressão VB** na janela **Propriedades** e, em seguida, pressione a tecla **Tab** duas vezes.</span><span class="sxs-lookup"><span data-stu-id="40063-150">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="40063-151">Isso fecha a janela dos membros da lista do IntelliSense e salva o valor da propriedade removendo a seleção da propriedade.</span><span class="sxs-lookup"><span data-stu-id="40063-151">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="40063-152">Essa propriedade também pode ser definida digitando na `Text` caixa **Inserir uma expressão C#** ou **Inserir uma expressão VB** na própria atividade.</span><span class="sxs-lookup"><span data-stu-id="40063-152">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="40063-153">Se a **janela Propriedades** não for exibida, selecione **janela Propriedades** no menu **Exibir** .</span><span class="sxs-lookup"><span data-stu-id="40063-153">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="40063-154">Arraste uma atividade **ReadInt** da seção **NumberGuessWorkflowActivities** da caixa de **ferramentas** e solte-a na atividade **Sequence** para que ela siga a atividade **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="40063-154">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="40063-155">Associe o argumento **BookmarkName** da atividade **ReadInt** ao argumento **BookmarkName** da atividade **prompt** , digitando `BookmarkName` na caixa **Inserir uma expressão VB** à direita do argumento **BookmarkName** na **janela Propriedades**e pressione a tecla **Tab** duas vezes para fechar a janela membros da lista do IntelliSense e salvar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="40063-155">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="40063-156">Vincule o argumento **Result** da atividade **ReadInt** ao argumento **Result** da atividade **prompt** , digitando `Result` na caixa **Inserir uma expressão VB** à direita do argumento **resultado** na **janela Propriedades**e pressione a tecla **Tab** duas vezes...</span><span class="sxs-lookup"><span data-stu-id="40063-156">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="40063-157">Pressione **Ctrl** + **Shift** + **B** para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="40063-157">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="40063-158">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="40063-158">Next steps</span></span>

<span data-ttu-id="40063-159">Para obter instruções sobre como criar um fluxo de trabalho usando essas atividades, consulte a próxima etapa do tutorial [como: criar um fluxo de trabalho](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="40063-159">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40063-160">Veja também</span><span class="sxs-lookup"><span data-stu-id="40063-160">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="40063-161">Criando e implementando atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="40063-161">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="40063-162">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="40063-162">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="40063-163">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="40063-163">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="40063-164">Usando o ExpressionTextBox em um designer personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="40063-164">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)

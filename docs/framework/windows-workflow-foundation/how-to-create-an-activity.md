---
title: Como criar uma atividade
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 8aa6900b26bbe9f77fe0802a7929febe5af61269
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539598"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="8d2db-102">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="8d2db-102">How to: Create an Activity</span></span>

<span data-ttu-id="8d2db-103">As atividades são a unidade principal de comportamento no [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d2db-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="8d2db-104">A lógica de execução de uma atividade pode ser implementada em código gerenciado ou pode ser implementada usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="8d2db-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="8d2db-105">Este tópico demonstra como criar duas atividades.</span><span class="sxs-lookup"><span data-stu-id="8d2db-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="8d2db-106">A primeira atividade é uma atividade simples que usa o código para implementar a sua lógica de execução.</span><span class="sxs-lookup"><span data-stu-id="8d2db-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="8d2db-107">A implementação da segunda atividade é definida usando outras atividades.</span><span class="sxs-lookup"><span data-stu-id="8d2db-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="8d2db-108">Essas atividades são usadas nas seguintes etapas no tutorial.</span><span class="sxs-lookup"><span data-stu-id="8d2db-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="8d2db-109">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8d2db-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="8d2db-110">Criar o projeto de biblioteca de atividade</span><span class="sxs-lookup"><span data-stu-id="8d2db-110">Create the activity library project</span></span>

1.  <span data-ttu-id="8d2db-111">Abra o Visual Studio e escolha **New** > **projeto** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="8d2db-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2.  <span data-ttu-id="8d2db-112">No **novo projeto** caixa de diálogo, sob o **instalado** categoria, selecione **Visual c#** > **fluxo de trabalho** (ou **Visual Basic** > **fluxo de trabalho**).</span><span class="sxs-lookup"><span data-stu-id="8d2db-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="8d2db-113">Se você não vir as **fluxo de trabalho** categoria do modelo, você talvez precise instalar o **Windows Workflow Foundation** componente do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d2db-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="8d2db-114">Escolha o **abrir instalador do Visual Studio** link no lado esquerdo das **novo projeto** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="8d2db-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="8d2db-115">No instalador do Visual Studio, selecione o **componentes individuais** guia. Em seguida, na **atividades de desenvolvimento** categoria, selecione o **Windows Workflow Foundation** componente.</span><span class="sxs-lookup"><span data-stu-id="8d2db-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="8d2db-116">Escolher **modificar** para instalar o componente.</span><span class="sxs-lookup"><span data-stu-id="8d2db-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="8d2db-117">Selecione o **biblioteca de atividades** modelo de projeto.</span><span class="sxs-lookup"><span data-stu-id="8d2db-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="8d2db-118">Tipo de `NumberGuessWorkflowActivities` no **nome** caixa e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4.  <span data-ttu-id="8d2db-119">Clique com botão direito **Activity1.xaml** na **Gerenciador de soluções** e escolha **excluir**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="8d2db-120">Clique em **Okey** para confirmar.</span><span class="sxs-lookup"><span data-stu-id="8d2db-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="8d2db-121">Criar a atividade de ReadInt</span><span class="sxs-lookup"><span data-stu-id="8d2db-121">Create the ReadInt activity</span></span>

1.  <span data-ttu-id="8d2db-122">Escolher **Adicionar Novo Item** da **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="8d2db-122">Choose **Add New Item** from the **Project** menu.</span></span>

2.  <span data-ttu-id="8d2db-123">No **Installed** > **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="8d2db-124">Selecione **atividade de código** da **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="8d2db-124">Select **Code Activity** from the **Workflow** list.</span></span>

3.  <span data-ttu-id="8d2db-125">Tipo de `ReadInt` para o **nome** caixa e, em seguida, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4.  <span data-ttu-id="8d2db-126">Substitua a definição existente de `ReadInt` pela seguinte definição.</span><span class="sxs-lookup"><span data-stu-id="8d2db-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="8d2db-127">A atividade `ReadInt` é derivada de <xref:System.Activities.NativeActivity%601> em vez de <xref:System.Activities.CodeActivity>, que é o padrão para o modelo de atividade de código.</span><span class="sxs-lookup"><span data-stu-id="8d2db-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="8d2db-128"><xref:System.Activities.CodeActivity%601> poderá ser usado se a atividade fornecer um único resultado, que é exposto através do argumento <xref:System.Activities.Activity%601.Result%2A>, mas <xref:System.Activities.CodeActivity%601> não oferece suporte ao uso de indicadores, portanto <xref:System.Activities.NativeActivity%601> será usado.</span><span class="sxs-lookup"><span data-stu-id="8d2db-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="8d2db-129">Criar a atividade de Prompt</span><span class="sxs-lookup"><span data-stu-id="8d2db-129">Create the Prompt activity</span></span>

1.  <span data-ttu-id="8d2db-130">Pressione **Ctrl**+**Shift**+**B** para compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="8d2db-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="8d2db-131">Compilar o projeto permite que a atividade `ReadInt` neste projeto seja usada para criar a atividade personalizada dessa etapa.</span><span class="sxs-lookup"><span data-stu-id="8d2db-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2.  <span data-ttu-id="8d2db-132">Escolher **Adicionar Novo Item** da **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="8d2db-132">Choose **Add New Item** from the **Project** menu.</span></span>

3.  <span data-ttu-id="8d2db-133">No **Installed** > **itens comuns** nó, selecione **fluxo de trabalho**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="8d2db-134">Selecione **atividade** da **fluxo de trabalho** lista.</span><span class="sxs-lookup"><span data-stu-id="8d2db-134">Select **Activity** from the **Workflow** list.</span></span>

4.  <span data-ttu-id="8d2db-135">Tipo de `Prompt` para o **nome** caixa e, em seguida, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5.  <span data-ttu-id="8d2db-136">Clique duas vezes em **prompt** na **Gerenciador de soluções** para exibi-lo no designer caso ainda não esteja sendo exibido.</span><span class="sxs-lookup"><span data-stu-id="8d2db-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6.  <span data-ttu-id="8d2db-137">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para exibir o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="8d2db-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7.  <span data-ttu-id="8d2db-138">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-138">Click **Create Argument**.</span></span>

8.  <span data-ttu-id="8d2db-139">Tipo `BookmarkName` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e pressione **Enter** para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="8d2db-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="8d2db-140">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="8d2db-141">Tipo `Result` para o **nome** caixa que está embaixo recém-adicionada `BookmarkName` argumento, selecione **Out** do **direção** lista suspensa, selecione **Int32** da **tipo de argumento** lista suspensa e pressione **Enter**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="8d2db-142">Clique em **criar argumento**.</span><span class="sxs-lookup"><span data-stu-id="8d2db-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="8d2db-143">Tipo `Text` para o **nome** caixa, selecione **no** do **direção** lista suspensa, selecione **cadeia de caracteres** da **Tipo de argumento** lista suspensa e pressione **Enter** para salvar o argumento.</span><span class="sxs-lookup"><span data-stu-id="8d2db-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="8d2db-144">Esses três argumentos são associados aos argumentos correspondentes das atividades <xref:System.Activities.Statements.WriteLine> e `ReadInt` que são adicionadas à atividade `Prompt` nas seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="8d2db-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="8d2db-145">Clique em **argumentos** no lado inferior esquerdo do designer de atividade para fechar o **argumentos** painel.</span><span class="sxs-lookup"><span data-stu-id="8d2db-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="8d2db-146">Arraste um **sequência** a atividade do **fluxo de controle** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulo da **Prompt** designer de atividade.</span><span class="sxs-lookup"><span data-stu-id="8d2db-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="8d2db-147">Se o **caixa de ferramentas** janela não for exibida, selecione **caixa de ferramentas** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="8d2db-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="8d2db-148">Arraste um **WriteLine** a atividade do **primitivos** seção o **caixa de ferramentas** e solte-o no **soltar atividade aqui** rótulo da **Sequência** atividade.</span><span class="sxs-lookup"><span data-stu-id="8d2db-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="8d2db-149">Associar o **texto** argumento do **WriteLine** atividade para o **texto** argumento do **Prompt** atividade digitando `Text` para o **insira uma expressão c#** ou **insira uma expressão VB** caixa **propriedades** janela e, em seguida, pressione o **guia** chave de duas vezes.</span><span class="sxs-lookup"><span data-stu-id="8d2db-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="8d2db-150">Isso fecha a janela dos membros da lista do IntelliSense e salva o valor da propriedade removendo a seleção da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d2db-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="8d2db-151">Essa propriedade também pode ser definida digitando `Text` para o **inserir uma expressão c#** ou **insira uma expressão VB** caixa na própria atividade.</span><span class="sxs-lookup"><span data-stu-id="8d2db-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="8d2db-152">Se o **janela de propriedades** não for exibido, selecione **janela propriedades** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="8d2db-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="8d2db-153">Arraste uma **ReadInt** a atividade do **NumberGuessWorkflowActivities** seção o **caixa de ferramentas** e solte-o no **sequência** atividade para que ela siga a **WriteLine** atividade.</span><span class="sxs-lookup"><span data-stu-id="8d2db-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="8d2db-154">Associar o **BookmarkName** argumento do **ReadInt** atividade para o **BookmarkName** argumento do **Prompt** atividade digitando `BookmarkName` no **inserir uma expressão de VB** caixa à direita do **BookmarkName** argumento no **janela propriedades**e, em seguida, pressione a **Guia** duas vezes para fechar a janela de membros da lista do IntelliSense e salvar a propriedade de chave.</span><span class="sxs-lookup"><span data-stu-id="8d2db-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="8d2db-155">Associar o **resultado** argumento do **ReadInt** atividade para o **resultados** argumento do **Prompt** atividade digitando `Result` na **insira uma expressão VB** caixa à direita do **resultado** argumento no **janela propriedades**e, em seguida, pressione o **guia** duas vezes de chave.</span><span class="sxs-lookup"><span data-stu-id="8d2db-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="8d2db-156">Pressione **Ctrl**+**Shift**+**B** para compilar a solução.</span><span class="sxs-lookup"><span data-stu-id="8d2db-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8d2db-157">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8d2db-157">Next steps</span></span>

<span data-ttu-id="8d2db-158">Para obter instruções sobre como criar um fluxo de trabalho por meio dessas atividades, consulte a próxima etapa no tutorial, [como: criar um fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8d2db-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d2db-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d2db-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="8d2db-160">Criando e implementando atividades personalizadas</span><span class="sxs-lookup"><span data-stu-id="8d2db-160">Designing and Implementing Custom Activities</span></span>](../../../docs/framework/windows-workflow-foundation/designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="8d2db-161">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="8d2db-161">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)
- [<span data-ttu-id="8d2db-162">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d2db-162">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)
- [<span data-ttu-id="8d2db-163">Usando o ExpressionTextBox em um designer personalizado de atividades</span><span class="sxs-lookup"><span data-stu-id="8d2db-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
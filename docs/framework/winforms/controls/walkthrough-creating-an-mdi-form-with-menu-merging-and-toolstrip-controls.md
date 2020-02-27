---
title: 'Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628781"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="4b5da-102">Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b5da-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="4b5da-103">O namespace <xref:System.Windows.Forms?displayProperty=nameWithType> dá suporte a aplicativos de interface de vários documentos (MDI) e o controle de <xref:System.Windows.Forms.MenuStrip> dá suporte à mesclagem de menus.</span><span class="sxs-lookup"><span data-stu-id="4b5da-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="4b5da-104">Os formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="4b5da-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="4b5da-105">Este tutorial demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="4b5da-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="4b5da-106">O formulário também dá suporte à mesclagem com menus filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="4b5da-107">As seguintes tarefas são ilustradas nesta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="4b5da-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="4b5da-108">Criando um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4b5da-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="4b5da-109">Criando o menu principal do formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-109">Creating the main menu for your form.</span></span> <span data-ttu-id="4b5da-110">O nome real do menu variará.</span><span class="sxs-lookup"><span data-stu-id="4b5da-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="4b5da-111">Adicionar o controle de <xref:System.Windows.Forms.ToolStripPanel> à **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="4b5da-112">Criando um formulário filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-112">Creating a child form.</span></span>

- <span data-ttu-id="4b5da-113">Organizando os controles de <xref:System.Windows.Forms.ToolStripPanel> por ordem z.</span><span class="sxs-lookup"><span data-stu-id="4b5da-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="4b5da-114">Quando terminar, você terá um formulário MDI que dá suporte à mesclagem de menus e aos controles de <xref:System.Windows.Forms.ToolStrip> móvel.</span><span class="sxs-lookup"><span data-stu-id="4b5da-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="4b5da-115">Para copiar o código neste tópico como uma única lista, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4b5da-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b5da-116">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="4b5da-116">Prerequisites</span></span>

<span data-ttu-id="4b5da-117">Você precisará do Visual Studio para concluir este passo a passos.</span><span class="sxs-lookup"><span data-stu-id="4b5da-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="4b5da-118">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="4b5da-118">Create the project</span></span>

1. <span data-ttu-id="4b5da-119">No Visual Studio, crie um projeto de aplicativo do Windows chamado **MDIForm** (**File** > **New** > **Project** >  **C# Visual** ou **Visual Basic** > **Classic desktop** > **aplicativo Windows Forms**).</span><span class="sxs-lookup"><span data-stu-id="4b5da-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="4b5da-120">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="4b5da-121">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="4b5da-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="4b5da-122">Criar o menu principal</span><span class="sxs-lookup"><span data-stu-id="4b5da-122">Create the main menu</span></span>

<span data-ttu-id="4b5da-123">O formulário MDI pai contém o menu principal.</span><span class="sxs-lookup"><span data-stu-id="4b5da-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="4b5da-124">O menu principal tem um item de menu chamado **Janela**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="4b5da-125">Com o item de menu **Janela**, você pode criar formulários filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="4b5da-126">Os itens de menu de formulários filho são mesclados no menu principal.</span><span class="sxs-lookup"><span data-stu-id="4b5da-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="4b5da-127">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="4b5da-128">Adicione um <xref:System.Windows.Forms.ToolStripMenuItem> ao controle de <xref:System.Windows.Forms.MenuStrip> e nomeie-o como **janela**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="4b5da-129">Selecione o controle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="4b5da-130">Na janela Propriedades, defina o valor da propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> como `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="4b5da-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="4b5da-131">Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="4b5da-132">Na janela Propriedades, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="4b5da-133">Clique duas vezes no evento <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="4b5da-134">O Designer de Formulários do Windows gera um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="4b5da-135">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="4b5da-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="4b5da-136">Adicionar o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="4b5da-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="4b5da-137">Quando você usa controles de <xref:System.Windows.Forms.MenuStrip> com um formulário MDI, você deve ter o controle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="4b5da-138">Você deve adicionar o controle de <xref:System.Windows.Forms.ToolStripPanel> à **caixa de ferramentas** para criar seu formulário MDI no designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="4b5da-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="4b5da-139">Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.</span><span class="sxs-lookup"><span data-stu-id="4b5da-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="4b5da-140">Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="4b5da-141">Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="4b5da-142">Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="4b5da-143">O controle <xref:System.Windows.Forms.ToolStripPanel> aparece na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="4b5da-144">Criar um formulário filho</span><span class="sxs-lookup"><span data-stu-id="4b5da-144">Create a child form</span></span>

<span data-ttu-id="4b5da-145">Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio controle de <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="4b5da-146">Os itens de menu para esse formulário são mesclados com as do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="4b5da-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="4b5da-147">Adicione um novo formulário chamado `ChildForm` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4b5da-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="4b5da-148">Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b5da-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="4b5da-149">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="4b5da-150">Clique no glifo ações do designer do controle de <xref:System.Windows.Forms.MenuStrip> (![seta preta pequena](./media/designer-actions-glyph.gif)) e, em seguida, selecione **Editar itens**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-150">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="4b5da-151">Na caixa de diálogo **Editor de coleção de itens** , adicione um novo <xref:System.Windows.Forms.ToolStripMenuItem> chamado **ChildMenuItem** ao menu filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="4b5da-152">Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b5da-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="4b5da-153">Testar o formulário</span><span class="sxs-lookup"><span data-stu-id="4b5da-153">Test the form</span></span>

1. <span data-ttu-id="4b5da-154">Pressione **F5** para compilar e executar o formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="4b5da-155">Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="4b5da-156">Um novo formulário filho é criado na área de cliente do MDI do formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="4b5da-157">O menu do formulário filho será mesclado com o menu principal.</span><span class="sxs-lookup"><span data-stu-id="4b5da-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="4b5da-158">Feche o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="4b5da-158">Close the child form.</span></span>

     <span data-ttu-id="4b5da-159">O menu do formulário filho será removido do menu principal.</span><span class="sxs-lookup"><span data-stu-id="4b5da-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="4b5da-160">Clique em **Novo** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="4b5da-160">Click **New** several times.</span></span>

     <span data-ttu-id="4b5da-161">Os formulários filho são listados automaticamente no item de menu **janela** porque a propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> do controle de <xref:System.Windows.Forms.MenuStrip> é atribuída.</span><span class="sxs-lookup"><span data-stu-id="4b5da-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="4b5da-162">Adicionar suporte a ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b5da-162">Add ToolStrip support</span></span>

<span data-ttu-id="4b5da-163">Neste procedimento, você adicionará quatro controles <xref:System.Windows.Forms.ToolStrip> ao formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="4b5da-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="4b5da-164">Cada controle de <xref:System.Windows.Forms.ToolStrip> é adicionado dentro de um controle de <xref:System.Windows.Forms.ToolStripPanel>, que é encaixado na borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="4b5da-165">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.ToolStripPanel> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="4b5da-166">Com o controle de <xref:System.Windows.Forms.ToolStripPanel> selecionado, clique duas vezes no controle de <xref:System.Windows.Forms.ToolStrip> na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="4b5da-167">Um controle de <xref:System.Windows.Forms.ToolStrip> é criado no controle de <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="4b5da-168">Selecione o controle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="4b5da-169">No janela Propriedades, altere o valor da propriedade <xref:System.Windows.Forms.Control.Dock%2A> do controle para <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="4b5da-170">O controle de <xref:System.Windows.Forms.ToolStripPanel> se encaixa no lado esquerdo do formulário, abaixo do menu principal.</span><span class="sxs-lookup"><span data-stu-id="4b5da-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="4b5da-171">A área do cliente MDI é redimensionada para se ajustar ao controle de <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="4b5da-172">Repita as etapas de 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="4b5da-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="4b5da-173">Encaixe o novo controle de <xref:System.Windows.Forms.ToolStripPanel> na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="4b5da-174">O controle de <xref:System.Windows.Forms.ToolStripPanel> é encaixado sob o menu principal, mas à direita do primeiro controle <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="4b5da-175">Esta etapa ilustra a importância da ordem z no posicionamento correto de <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="4b5da-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="4b5da-176">Repita as etapas de 1 a 4 para mais dois controles de <xref:System.Windows.Forms.ToolStripPanel>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="4b5da-177">Encaixe os novos controles de <xref:System.Windows.Forms.ToolStripPanel> à direita e à parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="4b5da-178">Organizar os controles ToolStripPanel por ordem Z</span><span class="sxs-lookup"><span data-stu-id="4b5da-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="4b5da-179">A posição de um controle de <xref:System.Windows.Forms.ToolStripPanel> encaixado em seu formulário MDI é determinada pela posição do controle na ordem z.</span><span class="sxs-lookup"><span data-stu-id="4b5da-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="4b5da-180">Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.</span><span class="sxs-lookup"><span data-stu-id="4b5da-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="4b5da-181">No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="4b5da-182">A organização dos controles de <xref:System.Windows.Forms.ToolStripPanel> do procedimento anterior não é padrão.</span><span class="sxs-lookup"><span data-stu-id="4b5da-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="4b5da-183">Isso ocorre porque a ordem z não está correta.</span><span class="sxs-lookup"><span data-stu-id="4b5da-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="4b5da-184">Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.</span><span class="sxs-lookup"><span data-stu-id="4b5da-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="4b5da-185">Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="4b5da-186">Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.</span><span class="sxs-lookup"><span data-stu-id="4b5da-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="4b5da-187">O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.</span><span class="sxs-lookup"><span data-stu-id="4b5da-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="4b5da-188">Selecione **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="4b5da-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="4b5da-189">Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.</span><span class="sxs-lookup"><span data-stu-id="4b5da-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="4b5da-190">O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.</span><span class="sxs-lookup"><span data-stu-id="4b5da-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="4b5da-191">Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z.</span><span class="sxs-lookup"><span data-stu-id="4b5da-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="4b5da-192">Observe o efeito da ordem z no posicionamento de controles encaixados.</span><span class="sxs-lookup"><span data-stu-id="4b5da-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="4b5da-193">Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.</span><span class="sxs-lookup"><span data-stu-id="4b5da-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="4b5da-194">Ponto de verificação-testar seu formulário</span><span class="sxs-lookup"><span data-stu-id="4b5da-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="4b5da-195">Pressione **F5** para compilar e executar o formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="4b5da-196">Clique na alça de um controle de <xref:System.Windows.Forms.ToolStrip> e arraste o controle para posições diferentes no formulário.</span><span class="sxs-lookup"><span data-stu-id="4b5da-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="4b5da-197">Você pode arrastar um controle de <xref:System.Windows.Forms.ToolStrip> de um controle de <xref:System.Windows.Forms.ToolStripPanel> para outro.</span><span class="sxs-lookup"><span data-stu-id="4b5da-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b5da-198">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4b5da-198">Next steps</span></span>

<span data-ttu-id="4b5da-199">Neste tutorial, você criou um formulário pai MDI com controles <xref:System.Windows.Forms.ToolStrip> e mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="4b5da-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="4b5da-200">Você pode usar a família de controles de <xref:System.Windows.Forms.ToolStrip> para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="4b5da-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="4b5da-201">Crie menus de atalho para seus controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="4b5da-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="4b5da-202">Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4b5da-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="4b5da-203">Foi criado um formulário com um menu padrão preenchido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4b5da-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="4b5da-204">Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="4b5da-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="4b5da-205">Dê ao seu <xref:System.Windows.Forms.ToolStrip> controles uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="4b5da-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="4b5da-206">Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="4b5da-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b5da-207">Confira também</span><span class="sxs-lookup"><span data-stu-id="4b5da-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="4b5da-208">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="4b5da-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="4b5da-209">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="4b5da-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="4b5da-210">Como inserir um MenuStrip um menu suspenso do MDI</span><span class="sxs-lookup"><span data-stu-id="4b5da-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="4b5da-211">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="4b5da-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

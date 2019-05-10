---
title: 'Passo a passo: Criar um formulário MDI com mesclagem de menu e controles ToolStrip'
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
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211553"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="dc5ec-102">Passo a passo: Criar um formulário MDI com mesclagem de menu e controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ec-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>

<span data-ttu-id="dc5ec-103">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte a vários aplicativos MDI (interface MDI) de documento e o <xref:System.Windows.Forms.MenuStrip> controle dá suporte à mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="dc5ec-104">Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="dc5ec-105">Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="dc5ec-106">O formulário também dá suporte à mesclagem com menus filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="dc5ec-107">As seguintes tarefas são ilustradas nesta explicação passo a passo:</span><span class="sxs-lookup"><span data-stu-id="dc5ec-107">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="dc5ec-108">Criando um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-108">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="dc5ec-109">Criando o menu principal do formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-109">Creating the main menu for your form.</span></span> <span data-ttu-id="dc5ec-110">O nome real do menu variará.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-110">The actual name of the menu will vary.</span></span>

- <span data-ttu-id="dc5ec-111">Adicionando o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>

- <span data-ttu-id="dc5ec-112">Criando um formulário filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-112">Creating a child form.</span></span>

- <span data-ttu-id="dc5ec-113">Organizando <xref:System.Windows.Forms.ToolStripPanel> controles pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>

<span data-ttu-id="dc5ec-114">Quando tiver terminado, você terá um formulário MDI que dá suporte à mesclagem de menu e movidos <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>

<span data-ttu-id="dc5ec-115">Para copiar o código deste tópico como uma única listagem, confira [Como: Criar um formulário MDI com mesclagem de Menu e controles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc5ec-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dc5ec-116">Prerequisites</span></span>

<span data-ttu-id="dc5ec-117">Será necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-117">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="dc5ec-118">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="dc5ec-118">Create the project</span></span>

1. <span data-ttu-id="dc5ec-119">No Visual Studio, crie um projeto de aplicativo do Windows chamado **MdiForm** (**arquivo** > **novo** > **projeto**  >  **Visual C#**  ou **Visual Basic** > **área de trabalho clássica**  >   **Aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-119">In Visual Studio, create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="dc5ec-120">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-120">In the Windows Forms Designer, select the form.</span></span>

3. <span data-ttu-id="dc5ec-121">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-121">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>

## <a name="create-the-main-menu"></a><span data-ttu-id="dc5ec-122">Criar o menu principal</span><span class="sxs-lookup"><span data-stu-id="dc5ec-122">Create the main menu</span></span>

<span data-ttu-id="dc5ec-123">O formulário MDI pai contém o menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-123">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="dc5ec-124">O menu principal tem um item de menu chamado **Janela**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-124">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="dc5ec-125">Com o item de menu **Janela**, você pode criar formulários filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-125">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="dc5ec-126">Os itens de menu de formulários filho são mesclados no menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-126">Menu items from child forms are merged into the main menu.</span></span>

1. <span data-ttu-id="dc5ec-127">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>

2. <span data-ttu-id="dc5ec-128">Adicionar um <xref:System.Windows.Forms.ToolStripMenuItem> para o <xref:System.Windows.Forms.MenuStrip> controlar e nomeie-o **janela**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-128">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>

3. <span data-ttu-id="dc5ec-129">Selecione o <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-129">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

4. <span data-ttu-id="dc5ec-130">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade para `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-130">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>

5. <span data-ttu-id="dc5ec-131">Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-131">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>

6. <span data-ttu-id="dc5ec-132">Na janela Propriedades, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-132">In the Properties window, click **Events**.</span></span>

7. <span data-ttu-id="dc5ec-133">Clique duas vezes o <xref:System.Windows.Forms.ToolStripItem.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-133">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

     <span data-ttu-id="dc5ec-134">O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-134">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>

8. <span data-ttu-id="dc5ec-135">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-135">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="dc5ec-136">Adicionar o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="dc5ec-136">Add the ToolStripPanel control to the Toolbox</span></span>

<span data-ttu-id="dc5ec-137">Quando você usa <xref:System.Windows.Forms.MenuStrip> controles com um formulário MDI que você deve ter o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-137">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="dc5ec-138">Você deve adicionar o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas** para criar o formulário MDI no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-138">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="dc5ec-139">Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-139">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>

2. <span data-ttu-id="dc5ec-140">Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-140">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>

3. <span data-ttu-id="dc5ec-141">Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-141">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>

4. <span data-ttu-id="dc5ec-142">Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-142">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>

     <span data-ttu-id="dc5ec-143">O <xref:System.Windows.Forms.ToolStripPanel> controle aparece na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-143">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>

## <a name="create-a-child-form"></a><span data-ttu-id="dc5ec-144">Criar um formulário filho</span><span class="sxs-lookup"><span data-stu-id="dc5ec-144">Create a child form</span></span>

<span data-ttu-id="dc5ec-145">Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-145">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="dc5ec-146">Os itens de menu para esse formulário são mesclados com as do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-146">The menu items for this form are merged with those of the parent form.</span></span>

1. <span data-ttu-id="dc5ec-147">Adicione um novo formulário chamado `ChildForm` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-147">Add a new form named `ChildForm` to the project.</span></span>

     <span data-ttu-id="dc5ec-148">Para obter mais informações, confira [Como: Adicionar o Windows Forms a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-148">For more information, see [How to: Add Windows Forms to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).</span></span>

2. <span data-ttu-id="dc5ec-149">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-149">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>

3. <span data-ttu-id="dc5ec-150">Clique o <xref:System.Windows.Forms.MenuStrip> glifo de smart tag do controle (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e, em seguida, selecione **editar itens**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-150">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>

4. <span data-ttu-id="dc5ec-151">No **Editor de coleção de itens** diálogo caixa, adicione uma nova <xref:System.Windows.Forms.ToolStripMenuItem> denominada **ChildMenuItem** ao menu filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-151">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>

     <span data-ttu-id="dc5ec-152">Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-152">For more information, see [ToolStrip Items Collection Editor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).</span></span>

## <a name="test-the-form"></a><span data-ttu-id="dc5ec-153">Testar o formulário</span><span class="sxs-lookup"><span data-stu-id="dc5ec-153">Test the form</span></span>

1. <span data-ttu-id="dc5ec-154">Pressione **F5** para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-154">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="dc5ec-155">Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-155">Click the **Window** menu item to open the menu, and then click **New**.</span></span>

     <span data-ttu-id="dc5ec-156">Um novo formulário filho é criado na área de cliente do MDI do formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-156">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="dc5ec-157">O menu do formulário filho será mesclado com o menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-157">The child form's menu is merged with the main menu.</span></span>

3. <span data-ttu-id="dc5ec-158">Feche o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-158">Close the child form.</span></span>

     <span data-ttu-id="dc5ec-159">O menu do formulário filho será removido do menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-159">The child form's menu is removed from the main menu.</span></span>

4. <span data-ttu-id="dc5ec-160">Clique em **Novo** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-160">Click **New** several times.</span></span>

     <span data-ttu-id="dc5ec-161">Os formulários filho são automaticamente listados sob o **janela** porque o item de menu a <xref:System.Windows.Forms.MenuStrip> do controle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> atribuído da propriedade.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-161">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>

## <a name="add-toolstrip-support"></a><span data-ttu-id="dc5ec-162">Adicionar suporte de ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ec-162">Add ToolStrip support</span></span>

<span data-ttu-id="dc5ec-163">Neste procedimento, você adicionará quatro <xref:System.Windows.Forms.ToolStrip> controles ao formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-163">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="dc5ec-164">Cada <xref:System.Windows.Forms.ToolStrip> controle é adicionado em uma <xref:System.Windows.Forms.ToolStripPanel> controle, que está encaixada na borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-164">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>

1. <span data-ttu-id="dc5ec-165">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStripPanel> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-165">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>

2. <span data-ttu-id="dc5ec-166">Com o <xref:System.Windows.Forms.ToolStripPanel> controle selecionado, clique duas vezes o <xref:System.Windows.Forms.ToolStrip> no controlar as **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-166">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>

     <span data-ttu-id="dc5ec-167">Um <xref:System.Windows.Forms.ToolStrip> controle é criado no <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-167">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

3. <span data-ttu-id="dc5ec-168">Selecione o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-168">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

4. <span data-ttu-id="dc5ec-169">Na janela Propriedades, altere o valor do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-169">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>

     <span data-ttu-id="dc5ec-170">O <xref:System.Windows.Forms.ToolStripPanel> controlar encaixa do lado esquerdo do formulário, abaixo do menu principal.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-170">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="dc5ec-171">A área de cliente do MDI é redimensionada para ajustar o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-171">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>

5. <span data-ttu-id="dc5ec-172">Repita as etapas de 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-172">Repeat steps 1 through 4.</span></span>

     <span data-ttu-id="dc5ec-173">Encaixe o novo <xref:System.Windows.Forms.ToolStripPanel> controle na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-173">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>

     <span data-ttu-id="dc5ec-174">O <xref:System.Windows.Forms.ToolStripPanel> controle está encaixado abaixo do menu principal, mas à direita do primeiro <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-174">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="dc5ec-175">Esta etapa ilustra a importância da ordem z no posicionamento correto dos <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-175">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

6. <span data-ttu-id="dc5ec-176">Repita as etapas 1 a 4 para mais duas <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-176">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>

     <span data-ttu-id="dc5ec-177">Encaixe o novo <xref:System.Windows.Forms.ToolStripPanel> controles à direita e inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-177">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>

## <a name="arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="dc5ec-178">Organizar controles ToolStripPanel pela ordem Z</span><span class="sxs-lookup"><span data-stu-id="dc5ec-178">Arrange ToolStripPanel controls by Z-order</span></span>

<span data-ttu-id="dc5ec-179">A posição de um encaixado <xref:System.Windows.Forms.ToolStripPanel> controle no formulário MDI é determinada pela posição do controle na ordem z.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-179">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="dc5ec-180">Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-180">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>

1. <span data-ttu-id="dc5ec-181">No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-181">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>

     <span data-ttu-id="dc5ec-182">A organização dos seus <xref:System.Windows.Forms.ToolStripPanel> controles do procedimento anterior não é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-182">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="dc5ec-183">Isso ocorre porque a ordem z não está correta.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-183">This is because the z-order is not correct.</span></span> <span data-ttu-id="dc5ec-184">Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-184">Use the Document Outline window to change the z-order of the controls.</span></span>

2. <span data-ttu-id="dc5ec-185">Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-185">In the Document Outline window, select **ToolStripPanel4**.</span></span>

3. <span data-ttu-id="dc5ec-186">Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-186">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>

     <span data-ttu-id="dc5ec-187">O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-187">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>

4. <span data-ttu-id="dc5ec-188">Selecione **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-188">Select **ToolStripPanel2**.</span></span>

5. <span data-ttu-id="dc5ec-189">Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-189">Click the down-arrow button one time to position the control third in the list.</span></span>

     <span data-ttu-id="dc5ec-190">O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-190">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>

6. <span data-ttu-id="dc5ec-191">Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-191">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="dc5ec-192">Observe o efeito da ordem z no posicionamento de controles encaixados.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-192">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="dc5ec-193">Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-193">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>

## <a name="checkpoint---test-your-form"></a><span data-ttu-id="dc5ec-194">Ponto de verificação – testar o formulário</span><span class="sxs-lookup"><span data-stu-id="dc5ec-194">Checkpoint - test your form</span></span>

1. <span data-ttu-id="dc5ec-195">Pressione **F5** para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-195">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="dc5ec-196">Clique na alça de um <xref:System.Windows.Forms.ToolStrip> controlar e arraste o controle para diferentes posições no formulário.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-196">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>

     <span data-ttu-id="dc5ec-197">Você pode arrastar uma <xref:System.Windows.Forms.ToolStrip> controle de um <xref:System.Windows.Forms.ToolStripPanel> controle para outro.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-197">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc5ec-198">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="dc5ec-198">Next steps</span></span>

<span data-ttu-id="dc5ec-199">Neste passo a passo, você criou um formulário MDI pai com <xref:System.Windows.Forms.ToolStrip> controles e mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-199">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="dc5ec-200">Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="dc5ec-200">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="dc5ec-201">Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-201">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="dc5ec-202">Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-202">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="dc5ec-203">Foi criado um formulário com um menu padrão preenchido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-203">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="dc5ec-204">Para obter mais informações, confira [Passo a passo: Fornecendo itens de Menu padrão para um formulário](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-204">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="dc5ec-205">Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="dc5ec-205">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="dc5ec-206">Para obter mais informações, confira [Como: Definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="dc5ec-206">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc5ec-207">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc5ec-207">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="dc5ec-208">Como: Criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="dc5ec-208">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="dc5ec-209">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="dc5ec-209">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="dc5ec-210">Como: Inserir um MenuStrip um Menu suspenso do MDI</span><span class="sxs-lookup"><span data-stu-id="dc5ec-210">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [<span data-ttu-id="dc5ec-211">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ec-211">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

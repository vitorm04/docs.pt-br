---
title: 'Instruções passo a passo: fornecendo itens de menu padrão para um formulário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628768"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="6ec7a-102">Instruções passo a passo: fornecendo itens de menu padrão para um formulário</span><span class="sxs-lookup"><span data-stu-id="6ec7a-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="6ec7a-103">Você pode fornecer um menu padrão para seus formulários com o controle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="6ec7a-104">Este tutorial demonstra como usar um controle de <xref:System.Windows.Forms.MenuStrip> para criar um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="6ec7a-105">O formulário também responde quando um usuário seleciona um item de menu.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="6ec7a-106">As seguintes tarefas são ilustradas nesta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="6ec7a-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="6ec7a-107">Criando um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="6ec7a-108">Criando um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-108">Creating a standard menu.</span></span>

- <span data-ttu-id="6ec7a-109">Criar um controle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="6ec7a-110">Manipulação da seleção de item de menu.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-110">Handling menu item selection.</span></span>

<span data-ttu-id="6ec7a-111">Quando terminar, você terá um formulário com um menu padrão que exibe as seleções do item de menu em um controle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="6ec7a-112">Para copiar o código deste tópico como uma única lista, consulte [Como fornecer itens de menu padrão para um formulário](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="6ec7a-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ec7a-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6ec7a-113">Prerequisites</span></span>

<span data-ttu-id="6ec7a-114">Você precisará do Visual Studio para concluir este passo a passos.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="6ec7a-115">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="6ec7a-115">Create the project</span></span>

1. <span data-ttu-id="6ec7a-116">No Visual Studio, crie um projeto de aplicativo do Windows chamado **StandardMenuForm** (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > Windows Forms **aplicativo**).</span><span class="sxs-lookup"><span data-stu-id="6ec7a-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="6ec7a-117">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="6ec7a-118">Criar um menu padrão</span><span class="sxs-lookup"><span data-stu-id="6ec7a-118">Create a standard menu</span></span>

<span data-ttu-id="6ec7a-119">O Designer de Formulários do Windows pode preencher automaticamente um controle de <xref:System.Windows.Forms.MenuStrip> com itens de menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="6ec7a-120">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="6ec7a-121">Clique no glifo ações do designer do controle de <xref:System.Windows.Forms.MenuStrip> (![seta preta pequena](./media/designer-actions-glyph.gif)) e selecione **Inserir itens padrão**.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-121">Click the <xref:System.Windows.Forms.MenuStrip> control's designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="6ec7a-122">O controle de <xref:System.Windows.Forms.MenuStrip> é preenchido com os itens de menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="6ec7a-123">Clique no item de menu **Arquivo** para ver seus itens de menu padrão e ícones correspondentes.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="6ec7a-124">Criar um controle StatusStrip</span><span class="sxs-lookup"><span data-stu-id="6ec7a-124">Create a StatusStrip control</span></span>

<span data-ttu-id="6ec7a-125">Use o controle <xref:System.Windows.Forms.StatusStrip> para exibir o status de seus aplicativos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="6ec7a-126">No exemplo atual, os itens de menu selecionados pelo usuário são exibidos em um controle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="6ec7a-127">Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.StatusStrip> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="6ec7a-128">O controle de <xref:System.Windows.Forms.StatusStrip> se encaixa automaticamente na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="6ec7a-129">Clique no botão suspenso do controle de <xref:System.Windows.Forms.StatusStrip> e selecione **StatusLabel** para adicionar um controle de <xref:System.Windows.Forms.ToolStripStatusLabel> ao controle de <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="6ec7a-130">Processar seleção de item</span><span class="sxs-lookup"><span data-stu-id="6ec7a-130">Handle item selection</span></span>

<span data-ttu-id="6ec7a-131">Manipule o evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> para responder quando o usuário seleciona um item de menu.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="6ec7a-132">Clique no item de menu **Arquivo** que você criou na seção Criando um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="6ec7a-133">Na janela **Propriedades**, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="6ec7a-134">Clique duas vezes no evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="6ec7a-135">O Designer de Formulários do Windows gera um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="6ec7a-136">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="6ec7a-137">Inserir a definição de método de utilitário `UpdateStatus` ao formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="6ec7a-138">Ponto de verificação-testar seu formulário</span><span class="sxs-lookup"><span data-stu-id="6ec7a-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="6ec7a-139">Pressione **F5** para compilar e executar o formulário.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="6ec7a-140">Clique no item de menu **Arquivo** para abrir o menu.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="6ec7a-141">No menu **Arquivo**, clique em um dos itens para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="6ec7a-142">O controle de <xref:System.Windows.Forms.StatusStrip> exibe o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6ec7a-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6ec7a-143">Next steps</span></span>

<span data-ttu-id="6ec7a-144">Neste passo a passo, você criou um formulário com um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="6ec7a-145">Você pode usar a família de controles de <xref:System.Windows.Forms.ToolStrip> para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="6ec7a-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="6ec7a-146">Crie menus de atalho para seus controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="6ec7a-147">Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6ec7a-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="6ec7a-148">Crie um formulário MDI (interface de vários documentos) com controles de <xref:System.Windows.Forms.ToolStrip> de encaixe.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="6ec7a-149">Para obter mais informações, consulte [Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6ec7a-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="6ec7a-150">Dê ao seu <xref:System.Windows.Forms.ToolStrip> controles uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="6ec7a-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="6ec7a-151">Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="6ec7a-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ec7a-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ec7a-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="6ec7a-153">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="6ec7a-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)

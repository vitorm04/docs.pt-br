---
title: 'Passo a passo: Fornecer itens de menu padrão para um formulário'
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
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211511"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a><span data-ttu-id="db550-102">Passo a passo: Fornecer itens de menu padrão para um formulário</span><span class="sxs-lookup"><span data-stu-id="db550-102">Walkthrough: Providing Standard Menu Items to a Form</span></span>

<span data-ttu-id="db550-103">Você pode fornecer um menu padrão para os formulários com o <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="db550-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="db550-104">Este passo a passo demonstra como usar um <xref:System.Windows.Forms.MenuStrip> controle para criar um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-104">This walkthrough demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a standard menu.</span></span> <span data-ttu-id="db550-105">O formulário também responde quando um usuário seleciona um item de menu.</span><span class="sxs-lookup"><span data-stu-id="db550-105">The form also responds when a user selects a menu item.</span></span> <span data-ttu-id="db550-106">As seguintes tarefas são ilustradas nesta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="db550-106">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="db550-107">Criando um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="db550-107">Creating a Windows Forms project.</span></span>

- <span data-ttu-id="db550-108">Criando um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-108">Creating a standard menu.</span></span>

- <span data-ttu-id="db550-109">Criando um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="db550-109">Creating a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

- <span data-ttu-id="db550-110">Manipulação da seleção de item de menu.</span><span class="sxs-lookup"><span data-stu-id="db550-110">Handling menu item selection.</span></span>

<span data-ttu-id="db550-111">Quando tiver terminado, você terá um formulário com um menu padrão que exibe as seleções de item de menu em um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="db550-111">When you are finished, you will have a form with a standard menu that displays menu item selections in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

<span data-ttu-id="db550-112">Para copiar o código deste tópico como uma única listagem, confira [Como: Fornecer itens de Menu padrão para um formulário](how-to-provide-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="db550-112">To copy the code in this topic as a single listing, see [How to: Provide Standard Menu Items to a Form](how-to-provide-standard-menu-items-to-a-form.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db550-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="db550-113">Prerequisites</span></span>

<span data-ttu-id="db550-114">Será necessário o Visual Studio para concluir este passo a passo.</span><span class="sxs-lookup"><span data-stu-id="db550-114">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="db550-115">Criar o projeto</span><span class="sxs-lookup"><span data-stu-id="db550-115">Create the project</span></span>

1. <span data-ttu-id="db550-116">No Visual Studio, crie um projeto de aplicativo do Windows chamado **StandardMenuForm** (**arquivo** > **novo** > **projeto**   >  **Visual C#**  ou **Visual Basic** > **área de trabalho clássica**  >  **Aplicativo de formulários do Windows**).</span><span class="sxs-lookup"><span data-stu-id="db550-116">In Visual Studio, create a Windows application project called **StandardMenuForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="db550-117">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-117">In the Windows Forms Designer, select the form.</span></span>

## <a name="create-a-standard-menu"></a><span data-ttu-id="db550-118">Criar um menu padrão</span><span class="sxs-lookup"><span data-stu-id="db550-118">Create a standard menu</span></span>

<span data-ttu-id="db550-119">O Designer de formulários do Windows pode preencher automaticamente um <xref:System.Windows.Forms.MenuStrip> controle com itens de menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-119">The Windows Forms Designer can automatically populate a <xref:System.Windows.Forms.MenuStrip> control with standard menu items.</span></span>

1. <span data-ttu-id="db550-120">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-120">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto your form.</span></span>

2. <span data-ttu-id="db550-121">Clique o <xref:System.Windows.Forms.MenuStrip> glifo de smart tag do controle (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **inserir itens padrão**.</span><span class="sxs-lookup"><span data-stu-id="db550-121">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) and select **Insert Standard Items**.</span></span>

     <span data-ttu-id="db550-122">O <xref:System.Windows.Forms.MenuStrip> controle é preenchido com os itens de menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-122">The <xref:System.Windows.Forms.MenuStrip> control is populated with the standard menu items.</span></span>

3. <span data-ttu-id="db550-123">Clique no item de menu **Arquivo** para ver seus itens de menu padrão e ícones correspondentes.</span><span class="sxs-lookup"><span data-stu-id="db550-123">Click the **File** menu item to see its default menu items and corresponding icons.</span></span>

## <a name="create-a-statusstrip-control"></a><span data-ttu-id="db550-124">Criar um controle StatusStrip</span><span class="sxs-lookup"><span data-stu-id="db550-124">Create a StatusStrip control</span></span>

<span data-ttu-id="db550-125">Use o <xref:System.Windows.Forms.StatusStrip> controle para exibir o status de seus aplicativos dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="db550-125">Use the <xref:System.Windows.Forms.StatusStrip> control to display status for your Windows Forms applications.</span></span> <span data-ttu-id="db550-126">No exemplo atual, os itens de menu selecionados pelo usuário são exibidos em um <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="db550-126">In the current example, menu items selected by the user are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>

1. <span data-ttu-id="db550-127">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.StatusStrip> controle para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-127">From the **Toolbox**, drag a <xref:System.Windows.Forms.StatusStrip> control onto your form.</span></span>

     <span data-ttu-id="db550-128">O <xref:System.Windows.Forms.StatusStrip> controle se encaixa automaticamente na parte inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-128">The <xref:System.Windows.Forms.StatusStrip> control automatically docks to the bottom of the form.</span></span>

2. <span data-ttu-id="db550-129">Clique o <xref:System.Windows.Forms.StatusStrip> do controle botão de lista suspensa e selecione **StatusLabel** para adicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> o controle para o <xref:System.Windows.Forms.StatusStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="db550-129">Click the <xref:System.Windows.Forms.StatusStrip> control's drop-down button and select **StatusLabel** to add a <xref:System.Windows.Forms.ToolStripStatusLabel> control to the <xref:System.Windows.Forms.StatusStrip> control.</span></span>

## <a name="handle-item-selection"></a><span data-ttu-id="db550-130">Lidar com a seleção de item</span><span class="sxs-lookup"><span data-stu-id="db550-130">Handle item selection</span></span>

<span data-ttu-id="db550-131">Manipular o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos para responder quando o usuário seleciona um item de menu.</span><span class="sxs-lookup"><span data-stu-id="db550-131">Handle the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event to respond when the user selects a menu item.</span></span>

1. <span data-ttu-id="db550-132">Clique no item de menu **Arquivo** que você criou na seção Criando um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-132">Click the **File** menu item that you created in the Creating a Standard Menu section.</span></span>

2. <span data-ttu-id="db550-133">Na janela **Propriedades**, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="db550-133">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="db550-134">Clique duas vezes o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos.</span><span class="sxs-lookup"><span data-stu-id="db550-134">Double-click the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

     <span data-ttu-id="db550-135">O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos.</span><span class="sxs-lookup"><span data-stu-id="db550-135">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> event.</span></span>

4. <span data-ttu-id="db550-136">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="db550-136">Insert the following code into the event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. <span data-ttu-id="db550-137">Inserir a definição de método de utilitário `UpdateStatus` ao formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-137">Insert the `UpdateStatus` utility method definition into the form.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a><span data-ttu-id="db550-138">Ponto de verificação – testar o formulário</span><span class="sxs-lookup"><span data-stu-id="db550-138">Checkpoint -test your form</span></span>

1. <span data-ttu-id="db550-139">Pressione **F5** para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="db550-139">Press **F5** to compile and run your form.</span></span>

2. <span data-ttu-id="db550-140">Clique no item de menu **Arquivo** para abrir o menu.</span><span class="sxs-lookup"><span data-stu-id="db550-140">Click the **File** menu item to open the menu.</span></span>

3. <span data-ttu-id="db550-141">No menu **Arquivo**, clique em um dos itens para selecioná-lo.</span><span class="sxs-lookup"><span data-stu-id="db550-141">On the **File** menu, click one of the items to select it.</span></span>

     <span data-ttu-id="db550-142">O <xref:System.Windows.Forms.StatusStrip> controle exibe o item selecionado.</span><span class="sxs-lookup"><span data-stu-id="db550-142">The <xref:System.Windows.Forms.StatusStrip> control displays the selected item.</span></span>

## <a name="next-steps"></a><span data-ttu-id="db550-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="db550-143">Next steps</span></span>

<span data-ttu-id="db550-144">Neste passo a passo, você criou um formulário com um menu padrão.</span><span class="sxs-lookup"><span data-stu-id="db550-144">In this walkthrough, you have created a form with a standard menu.</span></span> <span data-ttu-id="db550-145">Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="db550-145">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="db550-146">Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="db550-146">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="db550-147">Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="db550-147">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="db550-148">Criar um formulário de MDI (interface MDI) de vários documentos com encaixe <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="db550-148">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="db550-149">Para obter mais informações, confira [Passo a passo: Criando um formulário MDI com mesclagem de Menu e controles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="db550-149">For more information, see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

- <span data-ttu-id="db550-150">Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="db550-150">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="db550-151">Para obter mais informações, confira [Como: Definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="db550-151">For more information, see [How to: Set the ToolStrip Renderer for an Application](how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db550-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db550-152">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="db550-153">Controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="db550-153">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)

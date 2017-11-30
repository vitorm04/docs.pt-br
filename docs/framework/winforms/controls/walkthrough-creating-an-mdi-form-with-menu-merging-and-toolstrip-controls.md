---
title: "Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bca5439f247951496d82c03b57ec1fa0e21a8271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="5522c-102">Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5522c-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="5522c-103">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte para vários aplicativos de interface (MDI) do documento e o <xref:System.Windows.Forms.MenuStrip> controle oferece suporte a mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="5522c-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="5522c-104">Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="5522c-105">Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="5522c-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="5522c-106">O formulário também dá suporte à mesclagem com menus filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="5522c-107">As seguintes tarefas são ilustradas nesta explicação passo a passo:</span><span class="sxs-lookup"><span data-stu-id="5522c-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="5522c-108">Criando um projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5522c-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="5522c-109">Criando o menu principal do formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-109">Creating the main menu for your form.</span></span> <span data-ttu-id="5522c-110">O nome real do menu variará.</span><span class="sxs-lookup"><span data-stu-id="5522c-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="5522c-111">Adicionando o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5522c-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="5522c-112">Criando um formulário filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="5522c-113">Organizando <xref:System.Windows.Forms.ToolStripPanel> controles por ordem z.</span><span class="sxs-lookup"><span data-stu-id="5522c-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="5522c-114">Quando você terminar, você terá um formulário MDI que dá suporte à mesclagem de menu e movable <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="5522c-115">Para copiar o código neste tópico como uma única lista, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5522c-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5522c-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="5522c-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5522c-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5522c-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5522c-118">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5522c-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5522c-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5522c-119">Prerequisites</span></span>  
 <span data-ttu-id="5522c-120">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="5522c-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="5522c-121">Permissões suficientes para poder criar e executar projetos de Aplicativo do Windows Forms no computador no qual [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] está instalado.</span><span class="sxs-lookup"><span data-stu-id="5522c-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="5522c-122">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="5522c-122">Creating the Project</span></span>  
 <span data-ttu-id="5522c-123">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="5522c-124">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="5522c-124">To create the project</span></span>  
  
1.  <span data-ttu-id="5522c-125">Criar um projeto de aplicativos do Windows chamado **MdiForm**.</span><span class="sxs-lookup"><span data-stu-id="5522c-125">Create a Windows Application project called **MdiForm**.</span></span>  
  
     <span data-ttu-id="5522c-126">Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="5522c-126">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="5522c-127">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-127">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="5522c-128">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="5522c-128">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="5522c-129">Criando o menu principal</span><span class="sxs-lookup"><span data-stu-id="5522c-129">Creating the Main Menu</span></span>  
 <span data-ttu-id="5522c-130">O formulário MDI pai contém o menu principal.</span><span class="sxs-lookup"><span data-stu-id="5522c-130">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="5522c-131">O menu principal tem um item de menu chamado **Janela**.</span><span class="sxs-lookup"><span data-stu-id="5522c-131">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="5522c-132">Com o item de menu **Janela**, você pode criar formulários filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-132">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="5522c-133">Os itens de menu de formulários filho são mesclados no menu principal.</span><span class="sxs-lookup"><span data-stu-id="5522c-133">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="5522c-134">Como criar o menu principal</span><span class="sxs-lookup"><span data-stu-id="5522c-134">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="5522c-135">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-135">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="5522c-136">Adicionar um <xref:System.Windows.Forms.ToolStripMenuItem> para o <xref:System.Windows.Forms.MenuStrip> controlar e nomeie-o **janela**.</span><span class="sxs-lookup"><span data-stu-id="5522c-136">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="5522c-137">Selecione o <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-137">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="5522c-138">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="5522c-138">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="5522c-139">Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.</span><span class="sxs-lookup"><span data-stu-id="5522c-139">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="5522c-140">Na janela Propriedades, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="5522c-140">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="5522c-141">Clique duas vezes o <xref:System.Windows.Forms.ToolStripItem.Click> evento.</span><span class="sxs-lookup"><span data-stu-id="5522c-141">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="5522c-142">O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento.</span><span class="sxs-lookup"><span data-stu-id="5522c-142">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="5522c-143">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5522c-143">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="5522c-144">Adicionando o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="5522c-144">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="5522c-145">Quando você usa <xref:System.Windows.Forms.MenuStrip> controles com um formulário MDI deve ter o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-145">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5522c-146">Você deve adicionar o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas** para criar o formulário MDI no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5522c-146">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="5522c-147">Como adicionar o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="5522c-147">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="5522c-148">Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.</span><span class="sxs-lookup"><span data-stu-id="5522c-148">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="5522c-149">Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.</span><span class="sxs-lookup"><span data-stu-id="5522c-149">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="5522c-150">Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="5522c-150">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="5522c-151">Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5522c-151">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5522c-152">O <xref:System.Windows.Forms.ToolStripPanel> controle aparece no **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5522c-152">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="5522c-153">Criando um formulário filho</span><span class="sxs-lookup"><span data-stu-id="5522c-153">Creating a Child Form</span></span>  
 <span data-ttu-id="5522c-154">Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-154">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="5522c-155">Os itens de menu para esse formulário são mesclados com as do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="5522c-155">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="5522c-156">Como definir um formulário filho</span><span class="sxs-lookup"><span data-stu-id="5522c-156">To define a child form</span></span>  
  
1.  <span data-ttu-id="5522c-157">Adicione um novo formulário chamado `ChildForm` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5522c-157">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="5522c-158">Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="5522c-158">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="5522c-159">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-159">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="5522c-160">Clique o <xref:System.Windows.Forms.MenuStrip> glifo de marca inteligente do controle (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e, em seguida, selecione **editar itens**.</span><span class="sxs-lookup"><span data-stu-id="5522c-160">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="5522c-161">No **Editor de coleção de itens** caixa de diálogo caixa, adicione uma nova <xref:System.Windows.Forms.ToolStripMenuItem> chamado **ChildMenuItem** ao menu filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-161">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="5522c-162">Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="5522c-162">For more information, see [ToolStrip Items Collection Editor](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="5522c-163">Testando o formulário</span><span class="sxs-lookup"><span data-stu-id="5522c-163">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="5522c-164">Como testar o formulário</span><span class="sxs-lookup"><span data-stu-id="5522c-164">To test your form</span></span>  
  
1.  <span data-ttu-id="5522c-165">Pressione F5 para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-165">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="5522c-166">Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="5522c-166">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="5522c-167">Um novo formulário filho é criado na área de cliente do MDI do formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-167">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="5522c-168">O menu do formulário filho será mesclado com o menu principal.</span><span class="sxs-lookup"><span data-stu-id="5522c-168">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="5522c-169">Feche o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="5522c-169">Close the child form.</span></span>  
  
     <span data-ttu-id="5522c-170">O menu do formulário filho será removido do menu principal.</span><span class="sxs-lookup"><span data-stu-id="5522c-170">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="5522c-171">Clique em **Novo** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="5522c-171">Click **New** several times.</span></span>  
  
     <span data-ttu-id="5522c-172">Os formulários filho automaticamente são listados na l**janela** porque o item de menu a <xref:System.Windows.Forms.MenuStrip> do controle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade é atribuída.</span><span class="sxs-lookup"><span data-stu-id="5522c-172">The child forms are automatically listed under the W**indow** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="5522c-173">Adicionando suporte ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5522c-173">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="5522c-174">Neste procedimento, você adicionará quatro <xref:System.Windows.Forms.ToolStrip> controles ao formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="5522c-174">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="5522c-175">Cada <xref:System.Windows.Forms.ToolStrip> controle é adicionado dentro de um <xref:System.Windows.Forms.ToolStripPanel> controle, que é encaixado na borda da forma.</span><span class="sxs-lookup"><span data-stu-id="5522c-175">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="5522c-176">Como adicionar controles ToolStrip ao formulário pai do MDI</span><span class="sxs-lookup"><span data-stu-id="5522c-176">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="5522c-177">Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStripPanel> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-177">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="5522c-178">Com o <xref:System.Windows.Forms.ToolStripPanel> controle selecionado, clique duas vezes o <xref:System.Windows.Forms.ToolStrip> controlar o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5522c-178">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="5522c-179">Um <xref:System.Windows.Forms.ToolStrip> controle é criado no <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-179">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="5522c-180">Selecione o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-180">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="5522c-181">Na janela Propriedades, altere o valor do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="5522c-181">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="5522c-182">O <xref:System.Windows.Forms.ToolStripPanel> controlar módulos de ancoragem para o lado esquerdo do formulário, sob o menu principal.</span><span class="sxs-lookup"><span data-stu-id="5522c-182">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="5522c-183">A área do cliente MDI é redimensionada para ajustar o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-183">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="5522c-184">Repita as etapas de 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="5522c-184">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="5522c-185">Encaixar o novo <xref:System.Windows.Forms.ToolStripPanel> controle para a parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-185">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="5522c-186">O <xref:System.Windows.Forms.ToolStripPanel> controle está encaixado sob o menu principal, mas à direita do primeiro <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="5522c-186">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="5522c-187">Esta etapa ilustra a importância de ordem z no posicionamento corretamente <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-187">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="5522c-188">Repita as etapas 1 a 4 para duas mais <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-188">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="5522c-189">Encaixar o novo <xref:System.Windows.Forms.ToolStripPanel> controles à direita e inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-189">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="5522c-190">Organizando controles ToolStripPanel pela ordem Z</span><span class="sxs-lookup"><span data-stu-id="5522c-190">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="5522c-191">A posição de um encaixada <xref:System.Windows.Forms.ToolStripPanel> controle do formulário MDI é determinada pela posição do controle na ordem z.</span><span class="sxs-lookup"><span data-stu-id="5522c-191">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="5522c-192">Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.</span><span class="sxs-lookup"><span data-stu-id="5522c-192">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="5522c-193">Como organizar controles ToolStripPanel pela ordem Z</span><span class="sxs-lookup"><span data-stu-id="5522c-193">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="5522c-194">No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.</span><span class="sxs-lookup"><span data-stu-id="5522c-194">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="5522c-195">A organização dos seus <xref:System.Windows.Forms.ToolStripPanel> controles do procedimento anterior é o padrão.</span><span class="sxs-lookup"><span data-stu-id="5522c-195">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="5522c-196">Isso ocorre porque a ordem z não está correta.</span><span class="sxs-lookup"><span data-stu-id="5522c-196">This is because the z-order is not correct.</span></span> <span data-ttu-id="5522c-197">Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-197">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="5522c-198">Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="5522c-198">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="5522c-199">Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.</span><span class="sxs-lookup"><span data-stu-id="5522c-199">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="5522c-200">O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-200">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="5522c-201">Selecione **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="5522c-201">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="5522c-202">Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.</span><span class="sxs-lookup"><span data-stu-id="5522c-202">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="5522c-203">O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-203">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="5522c-204">Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z.</span><span class="sxs-lookup"><span data-stu-id="5522c-204">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="5522c-205">Observe o efeito da ordem z no posicionamento de controles encaixados.</span><span class="sxs-lookup"><span data-stu-id="5522c-205">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="5522c-206">Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.</span><span class="sxs-lookup"><span data-stu-id="5522c-206">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="5522c-207">Ponto de verificação</span><span class="sxs-lookup"><span data-stu-id="5522c-207">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="5522c-208">Testar o formulário</span><span class="sxs-lookup"><span data-stu-id="5522c-208">To test your form</span></span>  
  
1.  <span data-ttu-id="5522c-209">Pressione F5 para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-209">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="5522c-210">Clique a alça de um <xref:System.Windows.Forms.ToolStrip> controlar e arraste o controle para posições diferentes no formulário.</span><span class="sxs-lookup"><span data-stu-id="5522c-210">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="5522c-211">Você pode arrastar um <xref:System.Windows.Forms.ToolStrip> controle de um <xref:System.Windows.Forms.ToolStripPanel> controle para outro.</span><span class="sxs-lookup"><span data-stu-id="5522c-211">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5522c-212">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5522c-212">Next Steps</span></span>  
 <span data-ttu-id="5522c-213">Neste passo a passo, você criou um formulário de pai MDI com <xref:System.Windows.Forms.ToolStrip> mesclagem de menu e controles.</span><span class="sxs-lookup"><span data-stu-id="5522c-213">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="5522c-214">Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="5522c-214">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="5522c-215">Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="5522c-215">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="5522c-216">Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5522c-216">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="5522c-217">Foi criado um formulário com um menu padrão preenchido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5522c-217">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="5522c-218">Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="5522c-218">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="5522c-219">Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="5522c-219">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="5522c-220">Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="5522c-220">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5522c-221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5522c-221">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="5522c-222">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="5522c-222">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="5522c-223">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="5522c-223">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="5522c-224">Como inserir um MenuStrip um menu suspenso do MDI</span><span class="sxs-lookup"><span data-stu-id="5522c-224">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="5522c-225">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5522c-225">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

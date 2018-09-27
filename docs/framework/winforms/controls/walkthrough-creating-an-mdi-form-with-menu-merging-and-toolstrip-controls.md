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
ms.openlocfilehash: 6236190340833e3f8810387e51ad53e1cb10d37b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47232866"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="c25b4-102">Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c25b4-102">Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="c25b4-103">O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte a vários aplicativos MDI (interface MDI) de documento e o <xref:System.Windows.Forms.MenuStrip> controle dá suporte à mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="c25b4-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="c25b4-104">Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="c25b4-105">Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI.</span><span class="sxs-lookup"><span data-stu-id="c25b4-105">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="c25b4-106">O formulário também dá suporte à mesclagem com menus filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-106">The form also supports menu merging with child menus.</span></span> <span data-ttu-id="c25b4-107">As seguintes tarefas são ilustradas nesta explicação passo a passo:</span><span class="sxs-lookup"><span data-stu-id="c25b4-107">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="c25b4-108">Criando um projeto do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c25b4-108">Creating a Windows Forms project.</span></span>  
  
-   <span data-ttu-id="c25b4-109">Criando o menu principal do formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-109">Creating the main menu for your form.</span></span> <span data-ttu-id="c25b4-110">O nome real do menu variará.</span><span class="sxs-lookup"><span data-stu-id="c25b4-110">The actual name of the menu will vary.</span></span>  
  
-   <span data-ttu-id="c25b4-111">Adicionando o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-111">Adding the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox**.</span></span>  
  
-   <span data-ttu-id="c25b4-112">Criando um formulário filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-112">Creating a child form.</span></span>  
  
-   <span data-ttu-id="c25b4-113">Organizando <xref:System.Windows.Forms.ToolStripPanel> controles pela ordem z.</span><span class="sxs-lookup"><span data-stu-id="c25b4-113">Arranging <xref:System.Windows.Forms.ToolStripPanel> controls by z-order.</span></span>  
  
 <span data-ttu-id="c25b4-114">Quando tiver terminado, você terá um formulário MDI que dá suporte à mesclagem de menu e movidos <xref:System.Windows.Forms.ToolStrip> controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-114">When you are finished, you will have an MDI form that supports menu merging and movable <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="c25b4-115">Para copiar o código neste tópico como uma única lista, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c25b4-115">To copy the code in this topic as a single listing, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c25b4-116">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="c25b4-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c25b4-117">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c25b4-118">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c25b4-118">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c25b4-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c25b4-119">Prerequisites</span></span>  
 <span data-ttu-id="c25b4-120">Para concluir este passo a passo, você precisará de:</span><span class="sxs-lookup"><span data-stu-id="c25b4-120">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="c25b4-121">Permissões suficientes para poder criar e executar projetos de aplicativos dos Windows Forms no computador no qual Visual Studio está instalado.</span><span class="sxs-lookup"><span data-stu-id="c25b4-121">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="c25b4-122">Criando o Projeto</span><span class="sxs-lookup"><span data-stu-id="c25b4-122">Creating the Project</span></span>  
 <span data-ttu-id="c25b4-123">A primeira etapa é criar o projeto e configurar o formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-123">The first step is to create the project and set up the form.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="c25b4-124">Para criar o projeto</span><span class="sxs-lookup"><span data-stu-id="c25b4-124">To create the project</span></span>  
  
1.  <span data-ttu-id="c25b4-125">Crie um projeto de aplicativo do Windows chamado **MdiForm** (**arquivo** > **novo** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **doaplicativodeformuláriosdoWindows**).</span><span class="sxs-lookup"><span data-stu-id="c25b4-125">Create a Windows Application project called **MdiForm** (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="c25b4-126">No Designer de Formulários do Windows, selecione o formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-126">In the Windows Forms Designer, select the form.</span></span>  
  
3.  <span data-ttu-id="c25b4-127">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> para `true`.</span><span class="sxs-lookup"><span data-stu-id="c25b4-127">In the Properties window, set the value of the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> to `true`.</span></span>  
  
## <a name="creating-the-main-menu"></a><span data-ttu-id="c25b4-128">Criando o menu principal</span><span class="sxs-lookup"><span data-stu-id="c25b4-128">Creating the Main Menu</span></span>  
 <span data-ttu-id="c25b4-129">O formulário MDI pai contém o menu principal.</span><span class="sxs-lookup"><span data-stu-id="c25b4-129">The parent MDI form contains the main menu.</span></span> <span data-ttu-id="c25b4-130">O menu principal tem um item de menu chamado **Janela**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-130">The main menu has one menu item named **Window**.</span></span> <span data-ttu-id="c25b4-131">Com o item de menu **Janela**, você pode criar formulários filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-131">With the **Window** menu item, you can create child forms.</span></span> <span data-ttu-id="c25b4-132">Os itens de menu de formulários filho são mesclados no menu principal.</span><span class="sxs-lookup"><span data-stu-id="c25b4-132">Menu items from child forms are merged into the main menu.</span></span>  
  
#### <a name="to-create-the-main-menu"></a><span data-ttu-id="c25b4-133">Como criar o menu principal</span><span class="sxs-lookup"><span data-stu-id="c25b4-133">To create the Main menu</span></span>  
  
1.  <span data-ttu-id="c25b4-134">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the form.</span></span>  
  
2.  <span data-ttu-id="c25b4-135">Adicionar um <xref:System.Windows.Forms.ToolStripMenuItem> para o <xref:System.Windows.Forms.MenuStrip> controlar e nomeie-o **janela**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-135">Add a <xref:System.Windows.Forms.ToolStripMenuItem> to the <xref:System.Windows.Forms.MenuStrip> control and name it **Window**.</span></span>  
  
3.  <span data-ttu-id="c25b4-136">Selecione o <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-136">Select the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
4.  <span data-ttu-id="c25b4-137">Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade para `ToolStripMenuItem1`.</span><span class="sxs-lookup"><span data-stu-id="c25b4-137">In the Properties window, set the value of the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to `ToolStripMenuItem1`.</span></span>  
  
5.  <span data-ttu-id="c25b4-138">Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-138">Add a subitem to the **Window** menu item, and then name the subitem **New**.</span></span>  
  
6.  <span data-ttu-id="c25b4-139">Na janela Propriedades, clique em **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-139">In the Properties window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="c25b4-140">Clique duas vezes o <xref:System.Windows.Forms.ToolStripItem.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="c25b4-140">Double-click the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
     <span data-ttu-id="c25b4-141">O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> eventos.</span><span class="sxs-lookup"><span data-stu-id="c25b4-141">The Windows Forms Designer generates an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event.</span></span>  
  
8.  <span data-ttu-id="c25b4-142">Insira o seguinte código ao manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c25b4-142">Insert the following code into the event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="c25b4-143">Adicionando o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="c25b4-143">Adding the ToolStripPanel Control to the Toolbox</span></span>  
 <span data-ttu-id="c25b4-144">Quando você usa <xref:System.Windows.Forms.MenuStrip> controles com um formulário MDI que você deve ter o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-144">When you use <xref:System.Windows.Forms.MenuStrip> controls with an MDI form you must have the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="c25b4-145">Você deve adicionar o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas** para criar o formulário MDI no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="c25b4-145">You must add the <xref:System.Windows.Forms.ToolStripPanel> control to the **Toolbox** to build your MDI form in the Windows Forms Designer.</span></span>  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a><span data-ttu-id="c25b4-146">Como adicionar o controle ToolStripPanel à caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="c25b4-146">To add the ToolStripPanel control to the Toolbox</span></span>  
  
1.  <span data-ttu-id="c25b4-147">Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c25b4-147">Open the **Toolbox**, and then click the **All Windows Forms** tab to show the available Windows Forms controls.</span></span>  
  
2.  <span data-ttu-id="c25b4-148">Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-148">Right-click to open the shortcut menu, and select **Choose Items**.</span></span>  
  
3.  <span data-ttu-id="c25b4-149">Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-149">In the **Choose Toolbox Items** dialog box, scroll down the **Name** column until you find **ToolStripPanel**.</span></span>  
  
4.  <span data-ttu-id="c25b4-150">Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-150">Select the check box by **ToolStripPanel**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c25b4-151">O <xref:System.Windows.Forms.ToolStripPanel> controle aparece na **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-151">The <xref:System.Windows.Forms.ToolStripPanel> control appears in the **Toolbox**.</span></span>  
  
## <a name="creating-a-child-form"></a><span data-ttu-id="c25b4-152">Criando um formulário filho</span><span class="sxs-lookup"><span data-stu-id="c25b4-152">Creating a Child Form</span></span>  
 <span data-ttu-id="c25b4-153">Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio <xref:System.Windows.Forms.MenuStrip> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-153">In this procedure, you will define a separate child form class that has its own <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="c25b4-154">Os itens de menu para esse formulário são mesclados com as do formulário pai.</span><span class="sxs-lookup"><span data-stu-id="c25b4-154">The menu items for this form are merged with those of the parent form.</span></span>  
  
#### <a name="to-define-a-child-form"></a><span data-ttu-id="c25b4-155">Como definir um formulário filho</span><span class="sxs-lookup"><span data-stu-id="c25b4-155">To define a child form</span></span>  
  
1.  <span data-ttu-id="c25b4-156">Adicione um novo formulário chamado `ChildForm` ao projeto.</span><span class="sxs-lookup"><span data-stu-id="c25b4-156">Add a new form named `ChildForm` to the project.</span></span>  
  
     <span data-ttu-id="c25b4-157">Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span><span class="sxs-lookup"><span data-stu-id="c25b4-157">For more information, see [How to: Add Windows Forms to a Project](https://msdn.microsoft.com/library/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
2.  <span data-ttu-id="c25b4-158">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-158">From the **Toolbox**, drag a <xref:System.Windows.Forms.MenuStrip> control onto the child form.</span></span>  
  
3.  <span data-ttu-id="c25b4-159">Clique o <xref:System.Windows.Forms.MenuStrip> glifo de smart tag do controle (![glifo de Smart Tag](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e, em seguida, selecione **editar itens**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-159">Click the <xref:System.Windows.Forms.MenuStrip> control's smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), and then select **Edit Items**.</span></span>  
  
4.  <span data-ttu-id="c25b4-160">No **Editor de coleção de itens** diálogo caixa, adicione uma nova <xref:System.Windows.Forms.ToolStripMenuItem> denominada **ChildMenuItem** ao menu filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-160">In the **Items Collection Editor** dialog box, add a new <xref:System.Windows.Forms.ToolStripMenuItem> named **ChildMenuItem** to the child menu.</span></span>  
  
     <span data-ttu-id="c25b4-161">Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span><span class="sxs-lookup"><span data-stu-id="c25b4-161">For more information, see [ToolStrip Items Collection Editor](https://msdn.microsoft.com/library/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).</span></span>  
  
## <a name="testing-the-form"></a><span data-ttu-id="c25b4-162">Testando o formulário</span><span class="sxs-lookup"><span data-stu-id="c25b4-162">Testing the Form</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="c25b4-163">Como testar o formulário</span><span class="sxs-lookup"><span data-stu-id="c25b4-163">To test your form</span></span>  
  
1.  <span data-ttu-id="c25b4-164">Pressione F5 para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-164">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="c25b4-165">Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-165">Click the **Window** menu item to open the menu, and then click **New**.</span></span>  
  
     <span data-ttu-id="c25b4-166">Um novo formulário filho é criado na área de cliente do MDI do formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-166">A new child form is created in the form's MDI client area.</span></span> <span data-ttu-id="c25b4-167">O menu do formulário filho será mesclado com o menu principal.</span><span class="sxs-lookup"><span data-stu-id="c25b4-167">The child form's menu is merged with the main menu.</span></span>  
  
3.  <span data-ttu-id="c25b4-168">Feche o formulário filho.</span><span class="sxs-lookup"><span data-stu-id="c25b4-168">Close the child form.</span></span>  
  
     <span data-ttu-id="c25b4-169">O menu do formulário filho será removido do menu principal.</span><span class="sxs-lookup"><span data-stu-id="c25b4-169">The child form's menu is removed from the main menu.</span></span>  
  
4.  <span data-ttu-id="c25b4-170">Clique em **Novo** várias vezes.</span><span class="sxs-lookup"><span data-stu-id="c25b4-170">Click **New** several times.</span></span>  
  
     <span data-ttu-id="c25b4-171">Os formulários filho são automaticamente listados sob o **janela** porque o item de menu a <xref:System.Windows.Forms.MenuStrip> do controle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> atribuído da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c25b4-171">The child forms are automatically listed under the **Window** menu item because the <xref:System.Windows.Forms.MenuStrip> control's <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property is assigned.</span></span>  
  
## <a name="adding-toolstrip-support"></a><span data-ttu-id="c25b4-172">Adicionando suporte ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c25b4-172">Adding ToolStrip Support</span></span>  
 <span data-ttu-id="c25b4-173">Neste procedimento, você adicionará quatro <xref:System.Windows.Forms.ToolStrip> controles ao formulário pai MDI.</span><span class="sxs-lookup"><span data-stu-id="c25b4-173">In this procedure, you will add four <xref:System.Windows.Forms.ToolStrip> controls to the MDI parent form.</span></span> <span data-ttu-id="c25b4-174">Cada <xref:System.Windows.Forms.ToolStrip> controle é adicionado em uma <xref:System.Windows.Forms.ToolStripPanel> controle, que está encaixada na borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-174">Each <xref:System.Windows.Forms.ToolStrip> control is added inside a <xref:System.Windows.Forms.ToolStripPanel> control, which is docked to the edge of the form.</span></span>  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a><span data-ttu-id="c25b4-175">Como adicionar controles ToolStrip ao formulário pai do MDI</span><span class="sxs-lookup"><span data-stu-id="c25b4-175">To add ToolStrip controls to the MDI parent form</span></span>  
  
1.  <span data-ttu-id="c25b4-176">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStripPanel> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-176">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStripPanel> control onto the form.</span></span>  
  
2.  <span data-ttu-id="c25b4-177">Com o <xref:System.Windows.Forms.ToolStripPanel> controle selecionado, clique duas vezes o <xref:System.Windows.Forms.ToolStrip> no controlar as **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-177">With the <xref:System.Windows.Forms.ToolStripPanel> control selected, double-click the <xref:System.Windows.Forms.ToolStrip> control in the **Toolbox**.</span></span>  
  
     <span data-ttu-id="c25b4-178">Um <xref:System.Windows.Forms.ToolStrip> controle é criado no <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-178">A <xref:System.Windows.Forms.ToolStrip> control is created in the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
3.  <span data-ttu-id="c25b4-179">Selecione o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-179">Select the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
4.  <span data-ttu-id="c25b4-180">Na janela Propriedades, altere o valor do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="c25b4-180">In the Properties window, change the value of the control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span>  
  
     <span data-ttu-id="c25b4-181">O <xref:System.Windows.Forms.ToolStripPanel> controlar encaixa do lado esquerdo do formulário, abaixo do menu principal.</span><span class="sxs-lookup"><span data-stu-id="c25b4-181">The <xref:System.Windows.Forms.ToolStripPanel> control docks to the left side of the form, underneath the main menu.</span></span> <span data-ttu-id="c25b4-182">A área de cliente do MDI é redimensionada para ajustar o <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-182">The MDI client area resizes to fit the <xref:System.Windows.Forms.ToolStripPanel> control.</span></span>  
  
5.  <span data-ttu-id="c25b4-183">Repita as etapas de 1 a 4.</span><span class="sxs-lookup"><span data-stu-id="c25b4-183">Repeat steps 1 through 4.</span></span>  
  
     <span data-ttu-id="c25b4-184">Encaixe o novo <xref:System.Windows.Forms.ToolStripPanel> controle na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-184">Dock the new <xref:System.Windows.Forms.ToolStripPanel> control to the top of the form.</span></span>  
  
     <span data-ttu-id="c25b4-185">O <xref:System.Windows.Forms.ToolStripPanel> controle está encaixado abaixo do menu principal, mas à direita do primeiro <xref:System.Windows.Forms.ToolStripPanel> controle.</span><span class="sxs-lookup"><span data-stu-id="c25b4-185">The <xref:System.Windows.Forms.ToolStripPanel> control is docked underneath the main menu, but to the right of the first <xref:System.Windows.Forms.ToolStripPanel> control.</span></span> <span data-ttu-id="c25b4-186">Esta etapa ilustra a importância da ordem z no posicionamento correto dos <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-186">This step illustrates the importance of z-order in correctly positioning <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
6.  <span data-ttu-id="c25b4-187">Repita as etapas 1 a 4 para mais duas <xref:System.Windows.Forms.ToolStripPanel> controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-187">Repeat steps 1 through 4 for two more <xref:System.Windows.Forms.ToolStripPanel> controls.</span></span>  
  
     <span data-ttu-id="c25b4-188">Encaixe o novo <xref:System.Windows.Forms.ToolStripPanel> controles à direita e inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-188">Dock the new <xref:System.Windows.Forms.ToolStripPanel> controls to the right and bottom of the form.</span></span>  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="c25b4-189">Organizando controles ToolStripPanel pela ordem Z</span><span class="sxs-lookup"><span data-stu-id="c25b4-189">Arranging ToolStripPanel Controls by Z-order</span></span>  
 <span data-ttu-id="c25b4-190">A posição de um encaixado <xref:System.Windows.Forms.ToolStripPanel> controle no formulário MDI é determinada pela posição do controle na ordem z.</span><span class="sxs-lookup"><span data-stu-id="c25b4-190">The position of a docked <xref:System.Windows.Forms.ToolStripPanel> control on your MDI form is determined by the control's position in the z-order.</span></span> <span data-ttu-id="c25b4-191">Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.</span><span class="sxs-lookup"><span data-stu-id="c25b4-191">You can easily arrange the z-order of your controls in the Document Outline window.</span></span>  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a><span data-ttu-id="c25b4-192">Como organizar controles ToolStripPanel pela ordem Z</span><span class="sxs-lookup"><span data-stu-id="c25b4-192">To arrange ToolStripPanel controls by Z-order</span></span>  
  
1.  <span data-ttu-id="c25b4-193">No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-193">In the **View** menu, click **Other Windows**, and then click **Document Outline**.</span></span>  
  
     <span data-ttu-id="c25b4-194">A organização dos seus <xref:System.Windows.Forms.ToolStripPanel> controles do procedimento anterior não é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c25b4-194">The arrangement of your <xref:System.Windows.Forms.ToolStripPanel> controls from the previous procedure is nonstandard.</span></span> <span data-ttu-id="c25b4-195">Isso ocorre porque a ordem z não está correta.</span><span class="sxs-lookup"><span data-stu-id="c25b4-195">This is because the z-order is not correct.</span></span> <span data-ttu-id="c25b4-196">Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-196">Use the Document Outline window to change the z-order of the controls.</span></span>  
  
2.  <span data-ttu-id="c25b4-197">Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-197">In the Document Outline window, select **ToolStripPanel4**.</span></span>  
  
3.  <span data-ttu-id="c25b4-198">Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.</span><span class="sxs-lookup"><span data-stu-id="c25b4-198">Click the down-arrow button repeatedly, until **ToolStripPanel4** is at the bottom of the list.</span></span>  
  
     <span data-ttu-id="c25b4-199">O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-199">The **ToolStripPanel4** control is docked to the bottom of the form, underneath the other controls.</span></span>  
  
4.  <span data-ttu-id="c25b4-200">Selecione **ToolStripPanel2**.</span><span class="sxs-lookup"><span data-stu-id="c25b4-200">Select **ToolStripPanel2**.</span></span>  
  
5.  <span data-ttu-id="c25b4-201">Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.</span><span class="sxs-lookup"><span data-stu-id="c25b4-201">Click the down-arrow button one time to position the control third in the list.</span></span>  
  
     <span data-ttu-id="c25b4-202">O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.</span><span class="sxs-lookup"><span data-stu-id="c25b4-202">The **ToolStripPanel2** control is docked to the top of the form, underneath the main menu and above the other controls.</span></span>  
  
6.  <span data-ttu-id="c25b4-203">Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z.</span><span class="sxs-lookup"><span data-stu-id="c25b4-203">Select various controls in the **Document Outline** window and move them to different positions in the z-order.</span></span> <span data-ttu-id="c25b4-204">Observe o efeito da ordem z no posicionamento de controles encaixados.</span><span class="sxs-lookup"><span data-stu-id="c25b4-204">Note the effect of the z-order on the placement of docked controls.</span></span> <span data-ttu-id="c25b4-205">Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.</span><span class="sxs-lookup"><span data-stu-id="c25b4-205">Use CTRL-Z or **Undo** on the **Edit** menu to undo your changes.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="c25b4-206">Ponto de verificação</span><span class="sxs-lookup"><span data-stu-id="c25b4-206">Checkpoint</span></span>  
  
#### <a name="to-test-your-form"></a><span data-ttu-id="c25b4-207">Testar o formulário</span><span class="sxs-lookup"><span data-stu-id="c25b4-207">To test your form</span></span>  
  
1.  <span data-ttu-id="c25b4-208">Pressione F5 para compilar e executar seu formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-208">Press F5 to compile and run your form.</span></span>  
  
2.  <span data-ttu-id="c25b4-209">Clique na alça de um <xref:System.Windows.Forms.ToolStrip> controlar e arraste o controle para diferentes posições no formulário.</span><span class="sxs-lookup"><span data-stu-id="c25b4-209">Click the grip of a <xref:System.Windows.Forms.ToolStrip> control and drag the control to different positions on the form.</span></span>  
  
     <span data-ttu-id="c25b4-210">Você pode arrastar uma <xref:System.Windows.Forms.ToolStrip> controle de um <xref:System.Windows.Forms.ToolStripPanel> controle para outro.</span><span class="sxs-lookup"><span data-stu-id="c25b4-210">You can drag a <xref:System.Windows.Forms.ToolStrip> control from one <xref:System.Windows.Forms.ToolStripPanel> control to another.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c25b4-211">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c25b4-211">Next Steps</span></span>  
 <span data-ttu-id="c25b4-212">Neste passo a passo, você criou um formulário MDI pai com <xref:System.Windows.Forms.ToolStrip> controles e mesclagem de menu.</span><span class="sxs-lookup"><span data-stu-id="c25b4-212">In this walkthrough, you have created an MDI parent form with <xref:System.Windows.Forms.ToolStrip> controls and menu merging.</span></span> <span data-ttu-id="c25b4-213">Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:</span><span class="sxs-lookup"><span data-stu-id="c25b4-213">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="c25b4-214">Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="c25b4-214">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="c25b4-215">Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c25b4-215">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="c25b4-216">Foi criado um formulário com um menu padrão preenchido automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c25b4-216">Created a form with an automatically populated standard menu.</span></span> <span data-ttu-id="c25b4-217">Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="c25b4-217">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="c25b4-218">Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional.</span><span class="sxs-lookup"><span data-stu-id="c25b4-218">Give your <xref:System.Windows.Forms.ToolStrip> controls a professional appearance.</span></span> <span data-ttu-id="c25b4-219">Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="c25b4-219">For more information, see [How to: Set the ToolStrip Renderer for an Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25b4-220">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c25b4-220">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="c25b4-221">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="c25b4-221">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="c25b4-222">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="c25b4-222">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [<span data-ttu-id="c25b4-223">Como inserir um MenuStrip um menu suspenso do MDI</span><span class="sxs-lookup"><span data-stu-id="c25b4-223">How to: Insert a MenuStrip into an MDI Drop-Down Menu</span></span>](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [<span data-ttu-id="c25b4-224">Controle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c25b4-224">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

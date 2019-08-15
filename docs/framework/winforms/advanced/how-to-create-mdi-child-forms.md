---
title: 'Como: criar formulários filho MDI'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040106"
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="d0624-102">Como: Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="d0624-102">How to: Create MDI child forms</span></span>

<span data-ttu-id="d0624-103">Os formulários filho MDI são um elemento essencial de [aplicativos de interface de vários documentos (MDI)](multiple-document-interface-mdi-applications.md), pois esses formulários são o centro da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="d0624-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) applications](multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>

<span data-ttu-id="d0624-104">No procedimento a seguir, você usará o Visual Studio para criar um formulário filho MDI que exibe <xref:System.Windows.Forms.RichTextBox> um controle, semelhante à maioria dos aplicativos de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="d0624-104">In the following procedure, you'll use Visual Studio to create an MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="d0624-105">Ao substituir o <xref:System.Windows.Forms> controle por outros controles, como o <xref:System.Windows.Forms.DataGridView> controle ou uma mistura de controles, você pode criar janelas filho MDI (e, por extensão, aplicativos MDI) com diversas possibilidades.</span><span class="sxs-lookup"><span data-stu-id="d0624-105">By substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls, you can create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>

## <a name="create-mdi-child-forms"></a><span data-ttu-id="d0624-106">Criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="d0624-106">Create MDI child forms</span></span>

1. <span data-ttu-id="d0624-107">Crie um novo projeto de aplicativo Windows Forms no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0624-107">Create a new Windows Forms application project in Visual Studio.</span></span> <span data-ttu-id="d0624-108">Na janela **Propriedades** do formulário, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> defina sua propriedade como `true` e sua `WindowsState` Propriedade como `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="d0624-108">In the **Properties** window for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true` and its `WindowsState` property to `Maximized`.</span></span>

   <span data-ttu-id="d0624-109">Isso designa o formulário como um recipiente MDI para janelas filho.</span><span class="sxs-lookup"><span data-stu-id="d0624-109">This designates the form as an MDI container for child windows.</span></span>

2. <span data-ttu-id="d0624-110">No, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário. `Toolbox`</span><span class="sxs-lookup"><span data-stu-id="d0624-110">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="d0624-111">Defina sua propriedade `Text` para o **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="d0624-111">Set its `Text` property to **File**.</span></span>

3. <span data-ttu-id="d0624-112">Clique nas reticências (...) ao lado da propriedade Items e clique em **Adicionar** para adicionar dois itens de menu da ferramenta filho.</span><span class="sxs-lookup"><span data-stu-id="d0624-112">Click the ellipsis (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="d0624-113">Defina a propriedade `Text` para esses itens como **Novo** e **Janela**.</span><span class="sxs-lookup"><span data-stu-id="d0624-113">Set the `Text` property for these items to **New** and **Window**.</span></span>

4. <span data-ttu-id="d0624-114">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d0624-114">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

5. <span data-ttu-id="d0624-115">Na caixa de diálogo **Adicionar novo item** , selecione **Windows Form** (no Visual Basic ou no Visual C#) ou **Windows Forms aplicativo (.net)** (no Visual C++) no painel **modelos** .</span><span class="sxs-lookup"><span data-stu-id="d0624-115">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in Visual C++) from the **Templates** pane.</span></span> <span data-ttu-id="d0624-116">Na caixa **Nome**, dê o nome **Form2** ao formulário.</span><span class="sxs-lookup"><span data-stu-id="d0624-116">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="d0624-117">Selecione **abrir** para adicionar o formulário ao projeto.</span><span class="sxs-lookup"><span data-stu-id="d0624-117">Select **Open** to add the form to the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0624-118">O formulário MDI filho criado nesta etapa é um formulário padrão do Windows.</span><span class="sxs-lookup"><span data-stu-id="d0624-118">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="d0624-119">Assim, ele tem uma <xref:System.Windows.Forms.Form.Opacity%2A> Propriedade, que permite controlar a transparência do formulário.</span><span class="sxs-lookup"><span data-stu-id="d0624-119">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="d0624-120">No entanto <xref:System.Windows.Forms.Form.Opacity%2A> , a propriedade foi projetada para janelas de nível superior.</span><span class="sxs-lookup"><span data-stu-id="d0624-120">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="d0624-121">Não use-a com formulários filho MDI, pois podem ocorrer problemas de pintura.</span><span class="sxs-lookup"><span data-stu-id="d0624-121">Do not use it with MDI child forms, as painting problems can occur.</span></span>

     <span data-ttu-id="d0624-122">Este formulário será o modelo para seus formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="d0624-122">This form will be the template for your MDI child forms.</span></span>

     <span data-ttu-id="d0624-123">O **Designer de Formulários do Windows** é aberto, exibindo **Form2**.</span><span class="sxs-lookup"><span data-stu-id="d0624-123">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>

6. <span data-ttu-id="d0624-124">Na **Caixa de Ferramentas**, arraste um controle **RichTextBox** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d0624-124">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>

7. <span data-ttu-id="d0624-125">Na janela **Propriedades**, defina a propriedade `Anchor` como **Superior, Esquerda** e a propriedade `Dock` como **Preenchimento**.</span><span class="sxs-lookup"><span data-stu-id="d0624-125">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>

   <span data-ttu-id="d0624-126">Isso faz com <xref:System.Windows.Forms.RichTextBox> que o controle preencha completamente a área do formulário filho MDI, mesmo quando o formulário é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="d0624-126">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>

8. <span data-ttu-id="d0624-127">Clique duas vezes no **novo** item de menu para <xref:System.Windows.Forms.Control.Click> criar um manipulador de eventos para ele.</span><span class="sxs-lookup"><span data-stu-id="d0624-127">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>

9. <span data-ttu-id="d0624-128">Insira um código semelhante ao seguinte para criar um novo formulário filho MDI quando o usuário clicar no item de menu **Novo**.</span><span class="sxs-lookup"><span data-stu-id="d0624-128">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>

   > [!NOTE]
   > <span data-ttu-id="d0624-129">No exemplo a seguir, o manipulador de eventos manipula <xref:System.Windows.Forms.Control.Click> o evento `MenuItem2`para.</span><span class="sxs-lookup"><span data-stu-id="d0624-129">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="d0624-130">Lembre-se de que, dependendo das especificidades da arquitetura de seu aplicativo, seu item de menu **Novo** não poderá ser `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="d0624-130">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   <span data-ttu-id="d0624-131">No C++, adicione a seguinte `#include` diretiva na parte superior de Form1. h:</span><span class="sxs-lookup"><span data-stu-id="d0624-131">In C++, add the following `#include` directive at the top of Form1.h:</span></span>

   ```cpp
   #include "Form2.h"
   ```

10. <span data-ttu-id="d0624-132">Na lista suspensa na parte superior da janela **Propriedades** , selecione a faixa de menu que corresponde à faixa de menu **arquivo** e defina a <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade para a janela. <xref:System.Windows.Forms.ToolStripMenuItem></span><span class="sxs-lookup"><span data-stu-id="d0624-132">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

    <span data-ttu-id="d0624-133">Isso permite que o menu **janela** mantenha uma lista de janelas filho MDI abertas com uma marca de seleção ao lado da janela filho ativa.</span><span class="sxs-lookup"><span data-stu-id="d0624-133">This enables the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>

11. <span data-ttu-id="d0624-134">Pressione **F5** para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0624-134">Press **F5** to run the application.</span></span> <span data-ttu-id="d0624-135">Ao selecionar **Novo** do menu **Arquivo**, você pode criar novos formulários filho MDI, que são mantidos no item de menu **Janela**.</span><span class="sxs-lookup"><span data-stu-id="d0624-135">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d0624-136">Quando um formulário filho MDI tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, uma estrutura de menu de itens de menu) e é aberto em um formulário pai MDI que tem <xref:System.Windows.Forms.MainMenu> um componente (com, normalmente, uma estrutura de menu de itens de menu), os itens de menu serão mesclados automaticamente Se você tiver definido a <xref:System.Windows.Forms.MenuItem.MergeType%2A> Propriedade (e, opcionalmente, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> a propriedade).</span><span class="sxs-lookup"><span data-stu-id="d0624-136">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="d0624-137">Defina a <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade de ambos <xref:System.Windows.Forms.MainMenu> os componentes e todos os itens de menu do formulário filho como <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="d0624-137">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="d0624-138">Além disso, defina <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> a propriedade para que os itens de menu de ambos os menus apareçam na ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="d0624-138">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="d0624-139">Além disso, tenha em mente que quando você fecha um formulário pai MDI, cada um dos formulários filho MDI gera <xref:System.Windows.Forms.Form.Closing> um evento antes <xref:System.Windows.Forms.Form.Closing> que o evento para o pai MDI seja gerado.</span><span class="sxs-lookup"><span data-stu-id="d0624-139">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="d0624-140"><xref:System.Windows.Forms.Form.Closing> Cancelar o evento de um filho MDI não impedirá que o evento <xref:System.Windows.Forms.Form.Closing> do pai MDI seja gerado; no entanto, o <xref:System.ComponentModel.CancelEventArgs> argumento para o <xref:System.Windows.Forms.Form.Closing> evento do pai MDI agora será `true`definido como.</span><span class="sxs-lookup"><span data-stu-id="d0624-140">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="d0624-141">Você pode forçar o fechamento do pai MDI e todos os formulários filho MDI ao definir <xref:System.ComponentModel.CancelEventArgs> o argumento `false`como.</span><span class="sxs-lookup"><span data-stu-id="d0624-141">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0624-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0624-142">See also</span></span>

- [<span data-ttu-id="d0624-143">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="d0624-143">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="d0624-144">Como: Criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="d0624-144">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="d0624-145">Como: Determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="d0624-145">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="d0624-146">Como: Enviar dados para o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="d0624-146">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="d0624-147">Como: Organizar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="d0624-147">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)

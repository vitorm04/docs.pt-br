---
title: Como criar formulários filho MDI
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: d4351e88de896f366ae2c4050f0e1c32aa0188a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-mdi-child-forms"></a><span data-ttu-id="51bf3-102">Como criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="51bf3-102">How to: Create MDI Child Forms</span></span>
<span data-ttu-id="51bf3-103">Os formulários filho MDI são um elemento essencial dos [Aplicativos de Interface MDI](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), pois esses formulários são o centro da interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="51bf3-103">MDI child forms are an essential element of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), as these forms are the center of user interaction.</span></span>  
  
 <span data-ttu-id="51bf3-104">No procedimento a seguir, você criará um formulário MDI filho que exibe um <xref:System.Windows.Forms.RichTextBox> controle, semelhante a aplicativos de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="51bf3-104">In the following procedure, you will create MDI child form that displays a <xref:System.Windows.Forms.RichTextBox> control, similar to most word-processing applications.</span></span> <span data-ttu-id="51bf3-105">Substituindo o <xref:System.Windows.Forms> controle com outros controles, como o <xref:System.Windows.Forms.DataGridView> controle ou uma mistura de controles permite que você crie janelas filho MDI (e, por extensão, aplicativos MDI) com diversas possibilidades.</span><span class="sxs-lookup"><span data-stu-id="51bf3-105">Substituting the <xref:System.Windows.Forms> control with other controls, such as the <xref:System.Windows.Forms.DataGridView> control, or a mixture of controls enables you to create MDI child windows (and, by extension, MDI applications) with diverse possibilities.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51bf3-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="51bf3-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="51bf3-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="51bf3-108">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="51bf3-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-mdi-child-forms"></a><span data-ttu-id="51bf3-109">Para criar formulários filho MDI</span><span class="sxs-lookup"><span data-stu-id="51bf3-109">To create MDI child forms</span></span>  
  
1.  <span data-ttu-id="51bf3-110">Criar um novo projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="51bf3-110">Create a new Windows Forms project.</span></span> <span data-ttu-id="51bf3-111">Em **janelas propriedades** para o formulário, defina seu <xref:System.Windows.Forms.Form.IsMdiContainer%2A> propriedade `true`e sua `WindowsState` propriedade `Maximized`.</span><span class="sxs-lookup"><span data-stu-id="51bf3-111">In **the Properties Windows** for the form, set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`, and its `WindowsState` property to `Maximized`.</span></span>  
  
     <span data-ttu-id="51bf3-112">Isso designa o formulário como um recipiente MDI para janelas filho.</span><span class="sxs-lookup"><span data-stu-id="51bf3-112">This designates the form as an MDI container for child windows.</span></span>  
  
2.  <span data-ttu-id="51bf3-113">Do `Toolbox`, arraste um <xref:System.Windows.Forms.MenuStrip> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="51bf3-113">From the `Toolbox`, drag a <xref:System.Windows.Forms.MenuStrip> control to the form.</span></span> <span data-ttu-id="51bf3-114">Defina sua propriedade `Text` para o **Arquivo**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-114">Set its `Text` property to **File**.</span></span>  
  
3.  <span data-ttu-id="51bf3-115">Clique nas reticências (...) ao lado da propriedade **Itens** e clique em **Adicionar** para adicionar dois itens de menu filho da faixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="51bf3-115">Click the ellipses (…) next to the **Items** property, and click **Add** to add two child tool strip menu items.</span></span> <span data-ttu-id="51bf3-116">Defina a propriedade `Text` para esses itens como **Novo** e **Janela**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-116">Set the `Text` property for these items to **New** and **Window**.</span></span>  
  
4.  <span data-ttu-id="51bf3-117">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto, aponte para **Adicionar** e selecione **Adicionar novo item**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-117">In **Solution Explorer**, right-click the project, point to **Add**, and then select **Add New Item**.</span></span>  
  
5.  <span data-ttu-id="51bf3-118">No **Adicionar Novo Item** caixa de diálogo, selecione **Windows Form** (no Visual Basic ou no Visual c#) ou **aplicativos de formulários do Windows (.NET)** (em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) da  **Modelos de** painel.</span><span class="sxs-lookup"><span data-stu-id="51bf3-118">In the **Add New Item** dialog box, select **Windows Form** (in Visual Basic or in Visual C#) or **Windows Forms Application (.NET)** (in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) from the **Templates** pane.</span></span> <span data-ttu-id="51bf3-119">Na caixa **Nome**, dê o nome **Form2** ao formulário.</span><span class="sxs-lookup"><span data-stu-id="51bf3-119">In the **Name** box, name the form **Form2**.</span></span> <span data-ttu-id="51bf3-120">Clique no botão **Abrir** para adicionar o formulário ao projeto.</span><span class="sxs-lookup"><span data-stu-id="51bf3-120">Click the **Open** button to add the form to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51bf3-121">O formulário MDI filho criado nesta etapa é um formulário padrão do Windows.</span><span class="sxs-lookup"><span data-stu-id="51bf3-121">The MDI child form you created in this step is a standard Windows Form.</span></span> <span data-ttu-id="51bf3-122">Como tal, ele tem um <xref:System.Windows.Forms.Form.Opacity%2A> propriedade, que permite que você controle a transparência do formulário.</span><span class="sxs-lookup"><span data-stu-id="51bf3-122">As such, it has an <xref:System.Windows.Forms.Form.Opacity%2A> property, which enables you to control the transparency of the form.</span></span> <span data-ttu-id="51bf3-123">No entanto, o <xref:System.Windows.Forms.Form.Opacity%2A> propriedade foi projetada para janelas de nível superior.</span><span class="sxs-lookup"><span data-stu-id="51bf3-123">However, the <xref:System.Windows.Forms.Form.Opacity%2A> property was designed for top-level windows.</span></span> <span data-ttu-id="51bf3-124">Não use-a com formulários filho MDI, pois podem ocorrer problemas de pintura.</span><span class="sxs-lookup"><span data-stu-id="51bf3-124">Do not use it with MDI child forms, as painting problems can occur.</span></span>  
  
     <span data-ttu-id="51bf3-125">Este formulário será o modelo para seus formulários filho MDI.</span><span class="sxs-lookup"><span data-stu-id="51bf3-125">This form will be the template for your MDI child forms.</span></span>  
  
     <span data-ttu-id="51bf3-126">O **Designer de Formulários do Windows** é aberto, exibindo **Form2**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-126">The **Windows Forms Designer** opens, displaying **Form2**.</span></span>  
  
6.  <span data-ttu-id="51bf3-127">Na **Caixa de Ferramentas**, arraste um controle **RichTextBox** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="51bf3-127">From the **Toolbox**, drag a **RichTextBox** control to the form.</span></span>  
  
7.  <span data-ttu-id="51bf3-128">Na janela **Propriedades**, defina a propriedade `Anchor` como **Superior, Esquerda** e a propriedade `Dock` como **Preenchimento**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-128">In the **Properties** window, set the `Anchor` property to **Top, Left** and the `Dock` property to **Fill**.</span></span>  
  
     <span data-ttu-id="51bf3-129">Isso faz com que o <xref:System.Windows.Forms.RichTextBox> controle para preencher completamente a área do formulário filho MDI, mesmo quando o formulário é redimensionado.</span><span class="sxs-lookup"><span data-stu-id="51bf3-129">This causes the <xref:System.Windows.Forms.RichTextBox> control to completely fill the area of the MDI child form, even when the form is resized.</span></span>  
  
8.  <span data-ttu-id="51bf3-130">Clique duas vezes o **novo** item de menu para criar um <xref:System.Windows.Forms.Control.Click> manipulador de eventos para ele.</span><span class="sxs-lookup"><span data-stu-id="51bf3-130">Double click the **New** menu item to create a <xref:System.Windows.Forms.Control.Click> event handler for it.</span></span>  
  
9. <span data-ttu-id="51bf3-131">Insira um código semelhante ao seguinte para criar um novo formulário filho MDI quando o usuário clicar no item de menu **Novo**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-131">Insert code similar to the following to create a new MDI child form when the user clicks the **New** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51bf3-132">No exemplo a seguir, o manipulador de eventos controla o <xref:System.Windows.Forms.Control.Click> evento `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="51bf3-132">In the following example, the event handler handles the <xref:System.Windows.Forms.Control.Click> event for `MenuItem2`.</span></span> <span data-ttu-id="51bf3-133">Lembre-se de que, dependendo das especificidades da arquitetura de seu aplicativo, seu item de menu **Novo** não poderá ser `MenuItem2`.</span><span class="sxs-lookup"><span data-stu-id="51bf3-133">Be aware that, depending on the specifics of your application architecture, your **New** menu item may not be `MenuItem2`.</span></span>  
  
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
  
     <span data-ttu-id="51bf3-134">Em [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], adicione a seguinte diretiva `#include` na parte superior do Form1.h:</span><span class="sxs-lookup"><span data-stu-id="51bf3-134">In [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], add the following `#include` directive at the top of Form1.h:</span></span>  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. <span data-ttu-id="51bf3-135">Na lista suspensa na parte superior do **propriedades** janela, selecione a faixa de menu que corresponde ao **arquivo** faixa de menu e defina o <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade na janela <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="51bf3-135">In the drop-down list at the top of the **Properties** window, select the menu strip that corresponds to the **File** menu strip and set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property to the Window <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
     <span data-ttu-id="51bf3-136">Isso permitirá que o menu **Janela** mantenha uma lista de janelas filho MDI abertas com uma marca de seleção próxima à janela filho ativa.</span><span class="sxs-lookup"><span data-stu-id="51bf3-136">This will enable the **Window** menu to maintain a list of open MDI child windows with a check mark next to the active child window.</span></span>  
  
11. <span data-ttu-id="51bf3-137">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="51bf3-137">Press F5 to run the application.</span></span> <span data-ttu-id="51bf3-138">Ao selecionar **Novo** do menu **Arquivo**, você pode criar novos formulários filho MDI, que são mantidos no item de menu **Janela**.</span><span class="sxs-lookup"><span data-stu-id="51bf3-138">By selecting **New** from the **File** menu, you can create new MDI child forms, which are kept track of in the **Window** menu item.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51bf3-139">Quando um formulário MDI filho tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, com uma estrutura de itens de menu) e ele é aberto em um formulário pai MDI que tem um <xref:System.Windows.Forms.MainMenu> componente (com, geralmente, com uma estrutura de itens de menu), o menu itens mesclará automaticamente Se você tiver configurado o <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade (e, opcionalmente, o <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> propriedade).</span><span class="sxs-lookup"><span data-stu-id="51bf3-139">When an MDI child form has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items) and it is opened within an MDI parent form that has a <xref:System.Windows.Forms.MainMenu> component (with, usually, a menu structure of menu items), the menu items will merge automatically if you have set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property (and optionally, the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property).</span></span> <span data-ttu-id="51bf3-140">Definir o <xref:System.Windows.Forms.MenuItem.MergeType%2A> propriedade do <xref:System.Windows.Forms.MainMenu> componentes e todos os itens de menu do formulário filho para <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span><span class="sxs-lookup"><span data-stu-id="51bf3-140">Set the <xref:System.Windows.Forms.MenuItem.MergeType%2A> property of both <xref:System.Windows.Forms.MainMenu> components and all of the menu items of the child form to <xref:System.Windows.Forms.MenuMerge.MergeItems>.</span></span> <span data-ttu-id="51bf3-141">Além disso, defina o <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> propriedade para que os itens de menu de ambos os menus apareçam na ordem desejada.</span><span class="sxs-lookup"><span data-stu-id="51bf3-141">Additionally, set the <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> property so that the menu items from both menus appear in the desired order.</span></span> <span data-ttu-id="51bf3-142">Além disso, tenha em mente que, quando você fecha um formulário pai MDI, cada um dos filhos MDI formulários gera um <xref:System.Windows.Forms.Form.Closing> evento antes do <xref:System.Windows.Forms.Form.Closing> é gerado para o pai MDI.</span><span class="sxs-lookup"><span data-stu-id="51bf3-142">Moreover, keep in mind that when you close an MDI parent form, each of the MDI child forms raises a <xref:System.Windows.Forms.Form.Closing> event before the <xref:System.Windows.Forms.Form.Closing> event for the MDI parent is raised.</span></span> <span data-ttu-id="51bf3-143">Cancelando um filho MDI <xref:System.Windows.Forms.Form.Closing> evento não impedirá que o pai MDI <xref:System.Windows.Forms.Form.Closing> evento seja gerado; no entanto, o <xref:System.ComponentModel.CancelEventArgs> argumento para o pai MDI <xref:System.Windows.Forms.Form.Closing> evento agora será definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="51bf3-143">Canceling an MDI child's <xref:System.Windows.Forms.Form.Closing> event will not prevent the MDI parent's <xref:System.Windows.Forms.Form.Closing> event from being raised; however, the <xref:System.ComponentModel.CancelEventArgs> argument for the MDI parent's <xref:System.Windows.Forms.Form.Closing> event will now be set to `true`.</span></span> <span data-ttu-id="51bf3-144">Você pode forçar o pai MDI e todos os filhos MDI a definindo o <xref:System.ComponentModel.CancelEventArgs> argumento `false`.</span><span class="sxs-lookup"><span data-stu-id="51bf3-144">You can force the MDI parent and all MDI child forms to close by setting the <xref:System.ComponentModel.CancelEventArgs> argument to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51bf3-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51bf3-145">See Also</span></span>  
 [<span data-ttu-id="51bf3-146">Aplicativos da interface MDI (Interface de Vários Documentos)</span><span class="sxs-lookup"><span data-stu-id="51bf3-146">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [<span data-ttu-id="51bf3-147">Como criar formulários pai MDI</span><span class="sxs-lookup"><span data-stu-id="51bf3-147">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [<span data-ttu-id="51bf3-148">Como determinar o filho MDI ativo</span><span class="sxs-lookup"><span data-stu-id="51bf3-148">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [<span data-ttu-id="51bf3-149">Como Enviar Dados para o Filho MDI Ativo</span><span class="sxs-lookup"><span data-stu-id="51bf3-149">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [<span data-ttu-id="51bf3-150">Como Organizar Formulários Filho MDI</span><span class="sxs-lookup"><span data-stu-id="51bf3-150">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)

---
title: Adicionar botões carregar, salvar e cancelar ao controle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 0305df5e7566f9441ce09fa3346a8b2dc67c8943
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627962"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="f5304-102">Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5304-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="f5304-103">O controle de <xref:System.Windows.Forms.BindingNavigator> é um controle de <xref:System.Windows.Forms.ToolStrip> de finalidade especial que se destina a navegar e manipular controles no formulário que estão associados a dados.</span><span class="sxs-lookup"><span data-stu-id="f5304-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="f5304-104">Como é um controle <xref:System.Windows.Forms.ToolStrip>, o componente <xref:System.Windows.Forms.BindingNavigator> pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.</span><span class="sxs-lookup"><span data-stu-id="f5304-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="f5304-105">No procedimento a seguir, um controle de <xref:System.Windows.Forms.TextBox> está associado a dados e o controle de <xref:System.Windows.Forms.ToolStrip> que é adicionado ao formulário é modificado para incluir os botões carregar, salvar e cancelar.</span><span class="sxs-lookup"><span data-stu-id="f5304-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="f5304-106">Adicionar os botões carregar, salvar e cancelar ao componente BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f5304-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="f5304-107">No Visual Studio, adicione um controle de <xref:System.Windows.Forms.TextBox> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="f5304-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="f5304-108">Associá-lo a um <xref:System.Windows.Forms.BindingSource>, que está associado a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="f5304-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="f5304-109">Para este exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f5304-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="f5304-110">Após a geração do conjunto de tabelas e do adaptador de tabela, arraste um controle de <xref:System.Windows.Forms.BindingNavigator> para o formulário.</span><span class="sxs-lookup"><span data-stu-id="f5304-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="f5304-111">Defina a propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> do controle de <xref:System.Windows.Forms.BindingNavigator> como a <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.</span><span class="sxs-lookup"><span data-stu-id="f5304-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="f5304-112">Selecione o controle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f5304-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="f5304-113">Clique no glifo ações do designer (![seta preta pequena](./media/designer-actions-glyph.gif)) para que a caixa de diálogo **tarefas do BindingNavigator** seja exibida e selecione **Editar itens**.</span><span class="sxs-lookup"><span data-stu-id="f5304-113">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="f5304-114">O **Editor de Coleção de Itens** aparece.</span><span class="sxs-lookup"><span data-stu-id="f5304-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="f5304-115">No **Editor de Coleção de Itens**, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5304-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="f5304-116">Adicione um <xref:System.Windows.Forms.ToolStripSeparator> e três itens de <xref:System.Windows.Forms.ToolStripButton> selecionando o tipo apropriado de <xref:System.Windows.Forms.ToolStripItem> e clicando no botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="f5304-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="f5304-117">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Name%2A> dos botões como **loadButton**, **SaveButton**e **CancelButton**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f5304-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="f5304-118">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.Text%2A> dos botões para **carregar**, **salvar**e **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="f5304-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="f5304-119">Defina a propriedade <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> para cada um dos botões em **texto**.</span><span class="sxs-lookup"><span data-stu-id="f5304-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="f5304-120">Como alternativa, você pode definir essa propriedade como **Image** ou **ImageAndText**e definir a imagem a ser exibida na propriedade <xref:System.Windows.Forms.ToolStripItem.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="f5304-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="f5304-121">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f5304-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="f5304-122">Os botões são adicionados à <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5304-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="f5304-123">Clique com o botão direito do mouse do formulário e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="f5304-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="f5304-124">No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela.</span><span class="sxs-lookup"><span data-stu-id="f5304-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="f5304-125">Esse código foi gerado quando você configura a vinculação de dados na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="f5304-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="f5304-126">O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="f5304-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="f5304-127">Isso provavelmente estará no evento de <xref:System.Windows.Forms.Form.Load> do formulário.</span><span class="sxs-lookup"><span data-stu-id="f5304-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="f5304-128">Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> da **carga** <xref:System.Windows.Forms.ToolStripButton> criada anteriormente e mova esse código de carregamento de dados para ele.</span><span class="sxs-lookup"><span data-stu-id="f5304-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="f5304-129">Agora, seu código deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="f5304-129">Your code should now look similar to the following:</span></span>

    ```vb
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click
        TableAdapterName.Fill(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void LoadButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Fill(DataSetName.TableName);
    }
    ```

11. <span data-ttu-id="f5304-130">Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> do<xref:System.Windows.Forms.ToolStripButton> **salvar** que você criou anteriormente e escreva o código para atualizar os dados dentro da tabela à qual o controle está vinculado.</span><span class="sxs-lookup"><span data-stu-id="f5304-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

    ```vb
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click
        TableAdapterName.Update(DataSetName.TableName)
    End Sub
    ```

    ```csharp
    private void SaveButton_Click(System.Object sender,
        System.EventArgs e)
    {
        TableAdapterName.Update(DataSetName.TableName);
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f5304-131">Em alguns casos, o componente de <xref:System.Windows.Forms.BindingNavigator> já tem um botão **salvar** , mas nenhum código foi gerado pelo designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="f5304-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="f5304-132">Nesse caso, você pode posicionar o código anterior no manipulador de eventos <xref:System.Windows.Forms.ToolStripItem.Click> para esse botão, em vez de criar um botão totalmente novo na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5304-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="f5304-133">No entanto, o botão é desabilitado por padrão, portanto, você deve definir a propriedade <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> do botão como `true` para que o botão funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="f5304-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="f5304-134">Crie um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click> do **Cancelamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para cancelar as alterações no registro de dados exibido.</span><span class="sxs-lookup"><span data-stu-id="f5304-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

    ```vb
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click
        BindingSourceName.CancelEdit()
    End Sub
    ```

    ```csharp
    private void CancelButton_Click(System.Object sender, System.EventArgs e)
    {
        BindingSourceName.CancelEdit();
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="f5304-135">O método de <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> tem como escopo a linha de dados.</span><span class="sxs-lookup"><span data-stu-id="f5304-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="f5304-136">Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.</span><span class="sxs-lookup"><span data-stu-id="f5304-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5304-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5304-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="f5304-138">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="f5304-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="f5304-139">Visão geral do componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="f5304-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

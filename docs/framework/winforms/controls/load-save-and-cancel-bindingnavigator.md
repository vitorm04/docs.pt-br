---
title: Adicionar botões carregar, salvar e cancelar ao controle BindingNavigator
description: Saiba como adicionar botões carregar, salvar e cancelar ao controle Windows Forms BindingNavigator.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173413"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="1648e-103">Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1648e-103">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="1648e-104">O <xref:System.Windows.Forms.BindingNavigator> controle é um controle de finalidade especial <xref:System.Windows.Forms.ToolStrip> que destina-se a navegar e manipular controles no formulário que estão associados a dados.</span><span class="sxs-lookup"><span data-stu-id="1648e-104">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="1648e-105">Como é um <xref:System.Windows.Forms.ToolStrip> controle, o <xref:System.Windows.Forms.BindingNavigator> componente pode ser facilmente modificado para incluir comandos adicionais ou alternativos para o usuário.</span><span class="sxs-lookup"><span data-stu-id="1648e-105">Because it's a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="1648e-106">No procedimento a seguir, um <xref:System.Windows.Forms.TextBox> controle é associado a dados e o <xref:System.Windows.Forms.ToolStrip> controle que é adicionado ao formulário é modificado para incluir os botões carregar, salvar e cancelar.</span><span class="sxs-lookup"><span data-stu-id="1648e-106">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="1648e-107">Adicionar os botões carregar, salvar e cancelar ao componente BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="1648e-107">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="1648e-108">No Visual Studio, adicione um <xref:System.Windows.Forms.TextBox> controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="1648e-108">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="1648e-109">Associe-o a um <xref:System.Windows.Forms.BindingSource> , que está associado a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1648e-109">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="1648e-110">Para este exemplo, o <xref:System.Windows.Forms.BindingSource> está associado a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="1648e-110">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="1648e-111">Após a geração do conjunto de tabelas e do adaptador de tabela, arraste um <xref:System.Windows.Forms.BindingNavigator> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="1648e-111">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="1648e-112">Defina a <xref:System.Windows.Forms.BindingNavigator> Propriedade do controle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> como o <xref:System.Windows.Forms.BindingSource> no formulário que está associado aos controles.</span><span class="sxs-lookup"><span data-stu-id="1648e-112">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="1648e-113">Selecione o controle <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="1648e-113">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="1648e-114">Clique no glifo ações do designer ( ![ seta preta pequena ](./media/designer-actions-glyph.gif) ) para que a caixa de diálogo **tarefas do BindingNavigator** seja exibida e selecione **Editar itens**.</span><span class="sxs-lookup"><span data-stu-id="1648e-114">Click the designer actions glyph (![Small black arrow](./media/designer-actions-glyph.gif)) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="1648e-115">O **Editor de Coleção de Itens** aparece.</span><span class="sxs-lookup"><span data-stu-id="1648e-115">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="1648e-116">No **Editor de Coleção de Itens**, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1648e-116">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="1648e-117">Adicione um <xref:System.Windows.Forms.ToolStripSeparator> e três <xref:System.Windows.Forms.ToolStripButton> itens selecionando o tipo apropriado <xref:System.Windows.Forms.ToolStripItem> e clicando no botão **Adicionar** .</span><span class="sxs-lookup"><span data-stu-id="1648e-117">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="1648e-118">Defina a <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriedade dos botões como **loadButton**, **SaveButton**e **CancelButton**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="1648e-118">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="1648e-119">Defina a <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriedade dos botões para **carregar**, **salvar**e **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="1648e-119">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="1648e-120">Defina a <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriedade para cada um dos botões em **texto**.</span><span class="sxs-lookup"><span data-stu-id="1648e-120">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="1648e-121">Como alternativa, você pode definir essa propriedade como **Image** ou **ImageAndText**e definir a imagem a ser exibida na <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1648e-121">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="1648e-122">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1648e-122">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="1648e-123">Os botões são adicionados ao <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="1648e-123">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="1648e-124">Clique com o botão direito do mouse no formulário e escolha **Exibir Código**.</span><span class="sxs-lookup"><span data-stu-id="1648e-124">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="1648e-125">No Editor de Códigos, localize a linha de código que carrega dados no adaptador de tabela.</span><span class="sxs-lookup"><span data-stu-id="1648e-125">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="1648e-126">Esse código foi gerado quando você configura a vinculação de dados na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="1648e-126">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="1648e-127">O código deve ser semelhante ao seguinte: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="1648e-127">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="1648e-128">Provavelmente estará no evento do formulário <xref:System.Windows.Forms.Form.Load> .</span><span class="sxs-lookup"><span data-stu-id="1648e-128">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="1648e-129">Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento da **carga** <xref:System.Windows.Forms.ToolStripButton> que você criou anteriormente e mova esse código de carregamento de dados para ele.</span><span class="sxs-lookup"><span data-stu-id="1648e-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="1648e-130">Agora, seu código deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="1648e-130">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="1648e-131">Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento do **salvamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para atualizar os dados dentro da tabela à qual o controle está vinculado.</span><span class="sxs-lookup"><span data-stu-id="1648e-131">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="1648e-132">Em alguns casos, o <xref:System.Windows.Forms.BindingNavigator> componente já tem um botão **salvar** , mas nenhum código foi gerado pelo designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="1648e-132">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="1648e-133">Nesse caso, você pode posicionar o código anterior no <xref:System.Windows.Forms.ToolStripItem.Click> manipulador de eventos para esse botão, em vez de criar um botão totalmente novo no <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="1648e-133">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="1648e-134">No entanto, o botão é desabilitado por padrão, portanto, você deve definir a <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> Propriedade do botão como `true` para que o botão funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="1648e-134">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="1648e-135">Crie um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento do **cancelamento** <xref:System.Windows.Forms.ToolStripButton> criado anteriormente e escreva o código para cancelar as alterações no registro de dados exibido.</span><span class="sxs-lookup"><span data-stu-id="1648e-135">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="1648e-136">O <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> método tem como escopo a linha de dados.</span><span class="sxs-lookup"><span data-stu-id="1648e-136">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="1648e-137">Salve as alterações feitas ao exibir um registro individual antes de navegar até o próximo registro.</span><span class="sxs-lookup"><span data-stu-id="1648e-137">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="1648e-138">Veja também</span><span class="sxs-lookup"><span data-stu-id="1648e-138">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="1648e-139">Controle BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="1648e-139">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="1648e-140">Visão geral do componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="1648e-140">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)

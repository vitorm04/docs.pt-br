---
title: 'Passo a passo: Criar uma interface no estilo do Explorer com os controles ListView e TreeView usando o Designer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: d80f8e3bc729689b274af520bc37fda8417b0407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658579"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="ec162-102">Passo a passo: Criar uma interface no estilo do Explorer com os controles ListView e TreeView usando o Designer</span><span class="sxs-lookup"><span data-stu-id="ec162-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="ec162-103">Um dos benefícios do Visual Studio é a capacidade de criar aplicativos dos Windows Forms com aparência profissional em pouco tempo.</span><span class="sxs-lookup"><span data-stu-id="ec162-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="ec162-104">Um cenário comum é a criação de uma interface do usuário com <xref:System.Windows.Forms.ListView> controles <xref:System.Windows.Forms.TreeView> e que se assemelham ao recurso do Windows Explorer de sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="ec162-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="ec162-105">O Windows Explorer exibe uma estrutura hierárquica de arquivos e pastas no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="ec162-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="ec162-106">Para criar o formulário contendo controles ListView e TreeView</span><span class="sxs-lookup"><span data-stu-id="ec162-106">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="ec162-107">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="ec162-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="ec162-108">Na caixa de diálogo **Novo Projeto**, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ec162-108">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="ec162-109">Em categorias, escolha **Visual Basic** ou **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="ec162-109">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="ec162-110">Na lista de modelos, escolha **Aplicativo dos Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="ec162-110">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="ec162-111">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec162-111">Click **OK**.</span></span> <span data-ttu-id="ec162-112">Um novo projeto dos Windows Forms é criado.</span><span class="sxs-lookup"><span data-stu-id="ec162-112">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="ec162-113">Adicione um <xref:System.Windows.Forms.SplitContainer> controle ao formulário e defina sua <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ec162-113">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="ec162-114">Adicione um <xref:System.Windows.Forms.ImageList> nome `imageList1` ao formulário e use o janela Propriedades para adicionar duas imagens: uma imagem de pasta e uma imagem de documento, nessa ordem.</span><span class="sxs-lookup"><span data-stu-id="ec162-114">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="ec162-115">Adicione um <xref:System.Windows.Forms.TreeView> controle chamado `treeview1` ao formulário e posicione-o no lado esquerdo do <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="ec162-115">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="ec162-116">Na janela Propriedades para `treeView1`, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ec162-116">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="ec162-117">Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ec162-117">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="ec162-118">Defina a propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> como `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="ec162-118">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="ec162-119">Adicione um <xref:System.Windows.Forms.ListView> controle chamado `listView1` ao formulário e posicione-o no lado direito do <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="ec162-119">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="ec162-120">Na janela Propriedades para `listview1`, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ec162-120">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="ec162-121">Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="ec162-121">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="ec162-122">Defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> como <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="ec162-122">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="ec162-123">Abra o editor de coleção ColumnHeader clicando nas reticências (![o botão de reticências (...) na janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) na <xref:System.Windows.Forms.ListView.Columns%2A> propriedade **.**</span><span class="sxs-lookup"><span data-stu-id="ec162-123">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="ec162-124">Adicione três colunas e defina sua <xref:System.Windows.Forms.ColumnHeader.Text%2A> Propriedade como `Name`, `Type`e `Last Modified`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ec162-124">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="ec162-125">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ec162-125">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="ec162-126">Defina a propriedade <xref:System.Windows.Forms.ListView.SmallImageList%2A> como `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="ec162-126">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="ec162-127">Implemente o código para popular <xref:System.Windows.Forms.TreeView> o com nós e subnós.</span><span class="sxs-lookup"><span data-stu-id="ec162-127">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="ec162-128">Adicione este código à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="ec162-128">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="ec162-129">Uma vez que o código anterior usa o namespace System.IO, adicione as instruções using ou import adequadas na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="ec162-129">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="ec162-130">Chame o método de configuração da etapa anterior no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> no método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="ec162-130">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="ec162-131">Adicione este código ao construtor de formulário.</span><span class="sxs-lookup"><span data-stu-id="ec162-131">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="ec162-132">Manipule o <xref:System.Windows.Forms.TreeView.NodeMouseClick> evento para `treeview1`e implemente o código para preencher `listview1` com o conteúdo de um nó quando um nó é clicado.</span><span class="sxs-lookup"><span data-stu-id="ec162-132">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="ec162-133">Adicione este código à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="ec162-133">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="ec162-134">Se você estiver usando C#o, verifique se você tem <xref:System.Windows.Forms.TreeView.NodeMouseClick> o evento associado ao seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="ec162-134">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="ec162-135">Adicione este código ao construtor de formulário.</span><span class="sxs-lookup"><span data-stu-id="ec162-135">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="ec162-136">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec162-136">Testing the Application</span></span>

<span data-ttu-id="ec162-137">Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.</span><span class="sxs-lookup"><span data-stu-id="ec162-137">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="ec162-138">Para testar o formulário</span><span class="sxs-lookup"><span data-stu-id="ec162-138">To test the form</span></span>

- <span data-ttu-id="ec162-139">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec162-139">Press F5 to run the application.</span></span>

     <span data-ttu-id="ec162-140">Você verá um formulário dividido que contém um <xref:System.Windows.Forms.TreeView> controle que exibe o diretório do projeto no lado esquerdo e um <xref:System.Windows.Forms.ListView> controle no lado direito com três colunas.</span><span class="sxs-lookup"><span data-stu-id="ec162-140">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="ec162-141">Você pode percorrer o <xref:System.Windows.Forms.TreeView> selecionando nós de diretório e o <xref:System.Windows.Forms.ListView> é preenchido com o conteúdo do diretório selecionado.</span><span class="sxs-lookup"><span data-stu-id="ec162-141">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec162-142">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ec162-142">Next Steps</span></span>

<span data-ttu-id="ec162-143">Esse aplicativo fornece um exemplo de uma maneira que você pode usar <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ListView> controlar juntos.</span><span class="sxs-lookup"><span data-stu-id="ec162-143">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="ec162-144">Para obter mais informações sobre esses controles, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="ec162-144">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="ec162-145">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ec162-145">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="ec162-146">Como: Adicionar recursos de pesquisa a um controle ListView</span><span class="sxs-lookup"><span data-stu-id="ec162-146">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="ec162-147">Como: Anexar um menu de atalho a um nó TreeView</span><span class="sxs-lookup"><span data-stu-id="ec162-147">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="ec162-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec162-148">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="ec162-149">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="ec162-149">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="ec162-150">Como: Adicionar e remover nós com o Windows Forms controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ec162-150">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="ec162-151">Como: Adicionar e remover itens com o controle Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="ec162-151">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="ec162-152">Como: Adicionar colunas ao controle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec162-152">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)

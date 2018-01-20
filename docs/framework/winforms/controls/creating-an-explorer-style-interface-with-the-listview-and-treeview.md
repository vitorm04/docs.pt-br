---
title: "Instruções passo a passo: criando uma interface no estilo do Explorer com os controles ListView e TreeView usando o designer"
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
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d8d7991f706f8098e4ac475ae057771de200197
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="d766e-102">Instruções passo a passo: criando uma interface no estilo do Explorer com os controles ListView e TreeView usando o designer</span><span class="sxs-lookup"><span data-stu-id="d766e-102">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>
<span data-ttu-id="d766e-103">Um dos benefícios do Visual Studio é a capacidade de criar aplicativos dos Windows Forms com aparência profissional em pouco tempo.</span><span class="sxs-lookup"><span data-stu-id="d766e-103">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="d766e-104">Um cenário comum é criar uma interface do usuário (UI) com <xref:System.Windows.Forms.ListView> e <xref:System.Windows.Forms.TreeView> controles que se parece com o recurso do Windows Explorer dos sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="d766e-104">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="d766e-105">O Windows Explorer exibe uma estrutura hierárquica de arquivos e pastas no computador do usuário.</span><span class="sxs-lookup"><span data-stu-id="d766e-105">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d766e-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="d766e-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d766e-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d766e-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d766e-108">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d766e-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="d766e-109">Para criar o formulário contendo controles ListView e TreeView</span><span class="sxs-lookup"><span data-stu-id="d766e-109">To create the form containing a ListView and TreeView control</span></span>  
  
1.  <span data-ttu-id="d766e-110">No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d766e-110">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d766e-111">Na caixa de diálogo **Novo Projeto**, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d766e-111">In the **New Project** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="d766e-112">Em categorias, escolha **Visual Basic** ou **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="d766e-112">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>  
  
    2.  <span data-ttu-id="d766e-113">Na lista de modelos, escolha **Aplicativo dos Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="d766e-113">In the list of templates, choose **Windows Forms Application**.</span></span>  
  
3.  <span data-ttu-id="d766e-114">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d766e-114">Click **OK**.</span></span> <span data-ttu-id="d766e-115">Um novo projeto dos Windows Forms é criado.</span><span class="sxs-lookup"><span data-stu-id="d766e-115">A new Windows Forms project is created.</span></span>  
  
4.  <span data-ttu-id="d766e-116">Adicionar um <xref:System.Windows.Forms.SplitContainer> controle para o formulário e defina seu <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="d766e-116">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
5.  <span data-ttu-id="d766e-117">Adicionar uma <xref:System.Windows.Forms.ImageList> chamado `imageList1` para o formulário e use a janela Propriedades para adicionar duas imagens: uma imagem de pasta e uma imagem de documento, nessa ordem.</span><span class="sxs-lookup"><span data-stu-id="d766e-117">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>  
  
6.  <span data-ttu-id="d766e-118">Adicionar um <xref:System.Windows.Forms.TreeView> controle chamado `treeview1` para o formulário e posicione-o no lado esquerdo do <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="d766e-118">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="d766e-119">Na janela Propriedades para `treeView1`, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d766e-119">In the Properties window for `treeView1` do the following:</span></span>  
  
    1.  <span data-ttu-id="d766e-120">Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="d766e-120">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="d766e-121">Defina a propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> como `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="d766e-121">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>  
  
7.  <span data-ttu-id="d766e-122">Adicionar um <xref:System.Windows.Forms.ListView> controle chamado `listView1` para o formulário e posicione-o à direita do <xref:System.Windows.Forms.SplitContainer> controle.</span><span class="sxs-lookup"><span data-stu-id="d766e-122">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="d766e-123">Na janela Propriedades para `listview1`, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d766e-123">In the Properties window for `listview1` do the following:</span></span>  
  
    1.  <span data-ttu-id="d766e-124">Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="d766e-124">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    2.  <span data-ttu-id="d766e-125">Defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> como <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="d766e-125">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
    3.  <span data-ttu-id="d766e-126">Abra o Editor de coleção ColumnHeader clicando nas reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) no <xref:System.Windows.Forms.ListView.Columns%2A> propriedade**.**</span><span class="sxs-lookup"><span data-stu-id="d766e-126">Open the ColumnHeader Collection Editor by clicking the ellipses (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the <xref:System.Windows.Forms.ListView.Columns%2A> property**.**</span></span> <span data-ttu-id="d766e-127">Adicione três colunas e defina seus <xref:System.Windows.Forms.ColumnHeader.Text%2A> propriedade `Name`, `Type`, e `Last Modified`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d766e-127">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="d766e-128">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d766e-128">Click **OK** to close the dialog box.</span></span>  
  
    4.  <span data-ttu-id="d766e-129">Defina a propriedade <xref:System.Windows.Forms.ListView.SmallImageList%2A> como `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="d766e-129">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>  
  
8.  <span data-ttu-id="d766e-130">Implementar o código para preencher o <xref:System.Windows.Forms.TreeView> conosco e subnós.</span><span class="sxs-lookup"><span data-stu-id="d766e-130">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="d766e-131">Adicione este código à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d766e-131">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. <span data-ttu-id="d766e-132">Uma vez que o código anterior usa o namespace System.IO, adicione as instruções using ou import adequadas na parte superior do formulário.</span><span class="sxs-lookup"><span data-stu-id="d766e-132">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="d766e-133">Chame o método de instalação da etapa anterior no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="d766e-133">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="d766e-134">Adicione este código ao construtor de formulário.</span><span class="sxs-lookup"><span data-stu-id="d766e-134">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. <span data-ttu-id="d766e-135">Manipular o <xref:System.Windows.Forms.TreeView.NodeMouseClick> evento `treeview1` **,** e implementar o código para preencher `listview1` com conteúdo de um nó quando um nó é clicado.</span><span class="sxs-lookup"><span data-stu-id="d766e-135">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="d766e-136">Adicione este código à classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d766e-136">Add this code to the `Form1` class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     <span data-ttu-id="d766e-137">Se você estiver usando c#, verifique se você tem o <xref:System.Windows.Forms.TreeView.NodeMouseClick> evento associado com seu método de manipulação de eventos.</span><span class="sxs-lookup"><span data-stu-id="d766e-137">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="d766e-138">Adicione este código ao construtor de formulário.</span><span class="sxs-lookup"><span data-stu-id="d766e-138">Add this code to the form constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="d766e-139">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="d766e-139">Testing the Application</span></span>  
 <span data-ttu-id="d766e-140">Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.</span><span class="sxs-lookup"><span data-stu-id="d766e-140">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="d766e-141">Para testar o formulário</span><span class="sxs-lookup"><span data-stu-id="d766e-141">To test the form</span></span>  
  
-   <span data-ttu-id="d766e-142">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d766e-142">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="d766e-143">Você verá um formulário de divisão que contém um <xref:System.Windows.Forms.TreeView> controle que exibe o diretório do projeto no lado esquerdo, e um <xref:System.Windows.Forms.ListView> controle à direita com três colunas.</span><span class="sxs-lookup"><span data-stu-id="d766e-143">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="d766e-144">Você pode percorrer o <xref:System.Windows.Forms.TreeView> selecionando nós do diretório e o <xref:System.Windows.Forms.ListView> é preenchido com o conteúdo da pasta selecionada.</span><span class="sxs-lookup"><span data-stu-id="d766e-144">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d766e-145">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d766e-145">Next Steps</span></span>  
 <span data-ttu-id="d766e-146">Esse aplicativo fornece um exemplo de uma maneira que você pode usar <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ListView> controla juntos.</span><span class="sxs-lookup"><span data-stu-id="d766e-146">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="d766e-147">Para obter mais informações sobre esses controles, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="d766e-147">For more information on these controls, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d766e-148">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d766e-148">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [<span data-ttu-id="d766e-149">Como Adicionar Recursos de Pesquisa a um Controle ListView</span><span class="sxs-lookup"><span data-stu-id="d766e-149">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [<span data-ttu-id="d766e-150">Como anexar um menu de atalho a um nó TreeView</span><span class="sxs-lookup"><span data-stu-id="d766e-150">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a><span data-ttu-id="d766e-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d766e-151">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [<span data-ttu-id="d766e-152">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="d766e-152">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="d766e-153">Como adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d766e-153">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="d766e-154">Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d766e-154">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="d766e-155">Como adicionar colunas ao controle ListView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d766e-155">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)

---
title: 'Como: Definir ícones para o controle TreeView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: c7c801242c7d5958cce9826a5f60d13a0b257add
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348049"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="ad3b6-102">Como: Definir ícones para o controle TreeView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad3b6-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="ad3b6-103">Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle pode exibir ícones ao lado de cada nó.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="ad3b6-104">Os ícones são posicionados imediatamente à esquerda do texto do nó.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="ad3b6-105">Para exibir esses ícones, você deve associar o modo de exibição de árvore com um <xref:System.Windows.Forms.ImageList> controle.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="ad3b6-106">Para obter mais informações sobre listas de imagens, consulte [componente ImageList](imagelist-component-windows-forms.md) e [como: Adicionar ou remover imagens com o Windows Forms componente ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="ad3b6-106">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad3b6-107">Um bug na versão 1.1 do Microsoft .NET Framework impede que imagens que aparecem em <xref:System.Windows.Forms.TreeView> nós quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ad3b6-108">Solução alternativa para esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> em seu `Main` método imediatamente depois de chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="ad3b6-109">Esse bug foi corrigido no .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-109">This bug is fixed in .NET Framework 2.0.</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="ad3b6-110">Para exibir imagens em um modo de exibição de árvore</span><span class="sxs-lookup"><span data-stu-id="ad3b6-110">To display images in a tree view</span></span>  
  
1. <span data-ttu-id="ad3b6-111">Defina as <xref:System.Windows.Forms.TreeView> do controle <xref:System.Windows.Forms.TreeView.ImageList%2A> propriedade à existente <xref:System.Windows.Forms.ImageList> controle você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="ad3b6-112">Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. <span data-ttu-id="ad3b6-113">Definir o nó <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="ad3b6-114">O <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriedade determina a imagem exibida para os estados normal e expandido do nó e o <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedade determina a imagem exibida para o estado do nó selecionado.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="ad3b6-115">Essas propriedades podem ser definidas no código ou no Editor TreeNode.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="ad3b6-116">Para abrir o Editor TreeNode, clique no botão de reticências ( ![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado de <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="ad3b6-116">To open the TreeNode Editor, click the ellipsis button ( ![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ad3b6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad3b6-117">See also</span></span>

- [<span data-ttu-id="ad3b6-118">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ad3b6-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="ad3b6-119">Como: Adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad3b6-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="ad3b6-120">Como: Iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad3b6-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="ad3b6-121">Como: Determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="ad3b6-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="ad3b6-122">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ad3b6-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

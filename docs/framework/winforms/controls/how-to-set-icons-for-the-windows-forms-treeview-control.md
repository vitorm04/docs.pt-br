---
title: Como definir ícones para o controle TreeView dos Windows Forms
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
ms.openlocfilehash: b732aa510be22f3cbdc5197574f1e2a825c35df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536479"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a><span data-ttu-id="f15e2-102">Como definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f15e2-102">How to: Set Icons for the Windows Forms TreeView Control</span></span>
<span data-ttu-id="f15e2-103">Windows Forms <xref:System.Windows.Forms.TreeView> controle pode exibir ícones ao lado de cada nó.</span><span class="sxs-lookup"><span data-stu-id="f15e2-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control can display icons next to each node.</span></span> <span data-ttu-id="f15e2-104">Os ícones são posicionados imediatamente à esquerda do texto do nó.</span><span class="sxs-lookup"><span data-stu-id="f15e2-104">The icons are positioned to the immediate left of the node text.</span></span> <span data-ttu-id="f15e2-105">Para exibir esses ícones, você deve associar o modo de exibição de árvore com um <xref:System.Windows.Forms.ImageList> controle.</span><span class="sxs-lookup"><span data-stu-id="f15e2-105">To display these icons, you must associate the tree view with an <xref:System.Windows.Forms.ImageList> control.</span></span> <span data-ttu-id="f15e2-106">Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="f15e2-106">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f15e2-107">Um bug no Microsoft .NET Framework versão 1.1 impede que imagens que aparecem em <xref:System.Windows.Forms.TreeView> nós quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f15e2-107">A bug in Microsoft .NET Framework version 1.1 prevents images from appearing on <xref:System.Windows.Forms.TreeView> nodes when your application calls <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f15e2-108">Solução alternativa para esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> no seu `Main` método imediatamente depois de chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span><span class="sxs-lookup"><span data-stu-id="f15e2-108">To work around this bug, call <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> in your `Main` method immediately after calling <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.</span></span> <span data-ttu-id="f15e2-109">Esse bug foi corrigido no [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f15e2-109">This bug is fixed in [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
### <a name="to-display-images-in-a-tree-view"></a><span data-ttu-id="f15e2-110">Para exibir imagens em um modo de exibição de árvore</span><span class="sxs-lookup"><span data-stu-id="f15e2-110">To display images in a tree view</span></span>  
  
1.  <span data-ttu-id="f15e2-111">Definir o <xref:System.Windows.Forms.TreeView> do controle <xref:System.Windows.Forms.TreeView.ImageList%2A> propriedade existente <xref:System.Windows.Forms.ImageList> controle que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="f15e2-111">Set the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.ImageList%2A> property to the existing <xref:System.Windows.Forms.ImageList> control you wish to use.</span></span>  
  
     <span data-ttu-id="f15e2-112">Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.</span><span class="sxs-lookup"><span data-stu-id="f15e2-112">These properties can be set in the designer with the Properties window, or in code.</span></span>  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  <span data-ttu-id="f15e2-113">Definir o nó <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="f15e2-113">Set the node's <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> and <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> properties.</span></span> <span data-ttu-id="f15e2-114">O <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriedade determina a imagem exibida para estados normal e expandido do nó e o <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedade determina a imagem exibida para o estado do nó selecionado.</span><span class="sxs-lookup"><span data-stu-id="f15e2-114">The <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> property determines the image displayed for the node's normal and expanded states, and the <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> property determines the image displayed for the node's selected state.</span></span>  
  
     <span data-ttu-id="f15e2-115">Essas propriedades podem ser definidas no código ou no Editor TreeNode.</span><span class="sxs-lookup"><span data-stu-id="f15e2-115">These properties can be set in code, or within the TreeNode Editor.</span></span> <span data-ttu-id="f15e2-116">Para abrir o Editor de TreeNode, clique no botão de reticências ( ![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade na janela Propriedades.</span><span class="sxs-lookup"><span data-stu-id="f15e2-116">To open the TreeNode Editor, click the ellipsis button ( ![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property on the Properties window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f15e2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f15e2-117">See Also</span></span>  
 [<span data-ttu-id="f15e2-118">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="f15e2-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="f15e2-119">Como adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f15e2-119">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="f15e2-120">Como iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f15e2-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="f15e2-121">Como determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="f15e2-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="f15e2-122">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f15e2-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

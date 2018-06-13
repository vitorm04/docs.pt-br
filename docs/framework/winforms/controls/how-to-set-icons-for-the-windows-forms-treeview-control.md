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
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Como definir ícones para o controle TreeView dos Windows Forms
Windows Forms <xref:System.Windows.Forms.TreeView> controle pode exibir ícones ao lado de cada nó. Os ícones são posicionados imediatamente à esquerda do texto do nó. Para exibir esses ícones, você deve associar o modo de exibição de árvore com um <xref:System.Windows.Forms.ImageList> controle. Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Um bug no Microsoft .NET Framework versão 1.1 impede que imagens que aparecem em <xref:System.Windows.Forms.TreeView> nós quando o aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Solução alternativa para esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> no seu `Main` método imediatamente depois de chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Esse bug foi corrigido no [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### <a name="to-display-images-in-a-tree-view"></a>Para exibir imagens em um modo de exibição de árvore  
  
1.  Definir o <xref:System.Windows.Forms.TreeView> do controle <xref:System.Windows.Forms.TreeView.ImageList%2A> propriedade existente <xref:System.Windows.Forms.ImageList> controle que você deseja usar.  
  
     Essas propriedades podem ser definidas no designer com a janela Propriedades ou no código.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  Definir o nó <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedades. O <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriedade determina a imagem exibida para estados normal e expandido do nó e o <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> propriedade determina a imagem exibida para o estado do nó selecionado.  
  
     Essas propriedades podem ser definidas no código ou no Editor TreeNode. Para abrir o Editor de TreeNode, clique no botão de reticências ( ![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ao lado de <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade na janela Propriedades.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Como adicionar e remover nós com o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Como iterar em todos os nós de um controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Como determinar qual nó TreeView foi clicado](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

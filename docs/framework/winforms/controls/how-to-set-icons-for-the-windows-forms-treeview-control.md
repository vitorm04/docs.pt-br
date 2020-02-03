---
title: Definir ícones para controle TreeView
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
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737269"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Como definir ícones para o controle TreeView dos Windows Forms
O controle de <xref:System.Windows.Forms.TreeView> de Windows Forms pode exibir ícones ao lado de cada nó. Os ícones são posicionados imediatamente à esquerda do texto do nó. Para exibir esses ícones, você deve associar o modo de exibição de árvore a um controle de <xref:System.Windows.Forms.ImageList>. Para obter mais informações sobre listas de imagens, consulte [Componente ImageList](imagelist-component-windows-forms.md) e [Como adicionar ou remover imagens com o componente ImageList dos Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
> Um bug no Microsoft .NET Framework versão 1,1 impede que as imagens apareçam em nós <xref:System.Windows.Forms.TreeView> quando seu aplicativo chama <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Para contornar esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> no método `Main` imediatamente após chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Esse bug é corrigido no .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Para exibir imagens em um modo de exibição de árvore  
  
1. Defina a propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> do controle de <xref:System.Windows.Forms.TreeView> como o controle de <xref:System.Windows.Forms.ImageList> existente que você deseja usar.  
  
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
  
2. Defina as propriedades de <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> do nó. A propriedade <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> determina a imagem exibida para os Estados normal e expandido do nó, e a propriedade <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> determina a imagem exibida para o estado selecionado do nó.  
  
     Essas propriedades podem ser definidas no código ou no Editor TreeNode. Para abrir o editor de TreeNode, clique no botão de reticências (![botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) ao lado da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> na janela Propriedades.  
  
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

- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como adicionar e remover nós com o controle TreeView dos Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Como iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

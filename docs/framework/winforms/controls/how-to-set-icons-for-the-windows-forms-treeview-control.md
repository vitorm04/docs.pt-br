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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909803"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Como: Definir ícones para o controle TreeView do Windows Forms
O controle <xref:System.Windows.Forms.TreeView> Windows Forms pode exibir ícones ao lado de cada nó. Os ícones são posicionados imediatamente à esquerda do texto do nó. Para exibir esses ícones, você deve associar o modo de exibição de <xref:System.Windows.Forms.ImageList> árvore a um controle. Para obter mais informações sobre listas de imagens, consulte [componente ImageList](imagelist-component-windows-forms.md) e [como: Adicionar ou remover imagens com o componente](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)Windows Forms ImageList.  
  
> [!NOTE]
> Um bug no Microsoft .NET Framework versão 1,1 impede que as imagens apareçam nos <xref:System.Windows.Forms.TreeView> nós quando seu aplicativo chama. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> Para contornar esse bug, chame <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> em seu `Main` método imediatamente após a <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>chamada. Esse bug é corrigido no .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Para exibir imagens em um modo de exibição de árvore  
  
1. Defina a <xref:System.Windows.Forms.TreeView> Propriedade do <xref:System.Windows.Forms.TreeView.ImageList%2A> controle para o controle <xref:System.Windows.Forms.ImageList> existente que você deseja usar.  
  
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
  
2. Defina as propriedades e <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> do nó. A <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> propriedade determina a imagem exibida para os Estados normal e expandido do nó, e <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> a propriedade determina a imagem exibida para o estado selecionado do nó.  
  
     Essas propriedades podem ser definidas no código ou no Editor TreeNode. Para abrir o editor de TreeNode, clique no botão de ![reticências (o botão de reticências (...) na janela Propriedades](./media/visual-studio-ellipsis-button.png)do Visual Studio. <xref:System.Windows.Forms.TreeView.Nodes%2A> ) ao lado da propriedade na janela Propriedades.  
  
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
- [Como: Adicionar e remover nós com o Windows Forms controle TreeView](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Como: Iterar em todos os nós de um Windows Forms controle TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como: Determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

---
title: 'Como: Adicionar e remover nós com o controle TreeView dos Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 30dbe55711d92ea1fdbbbfd147a65b27d0dc9a50
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711495"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Como: Adicionar e remover nós com o controle TreeView dos Windows Forms
Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle armazena os nós de nível superior no seu <xref:System.Windows.Forms.TreeView.Nodes%2A> coleção. Cada <xref:System.Windows.Forms.TreeNode> também tem seu próprio <xref:System.Windows.Forms.TreeNode.Nodes%2A> coleção para armazenar seus nós filho. Ambas as propriedades de coleção são do tipo <xref:System.Windows.Forms.TreeNodeCollection>, que fornece a membros de coleção padrão que permitem adicionar, remover e reordenar os nós em um único nível da hierarquia de nós.  
  
### <a name="to-add-nodes-programmatically"></a>Para adicionar nós de forma programática  
  
1.  Use o <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> método de exibição de árvore <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade.  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a>Para remover nós de forma programática  
  
1.  Use o <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> método de exibição de árvore <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade para remover um único nó, ou o <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> método para limpar todos os nós.  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [Como: Definir ícones para o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como: Iterar em todos os nós de um controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como: Determinar qual nó TreeView foi clicado](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

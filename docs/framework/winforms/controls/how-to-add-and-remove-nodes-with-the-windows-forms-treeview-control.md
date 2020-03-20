---
title: Adicionar e remover ádereis com controle treeview
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
ms.openlocfilehash: f1e74e6d2f827167c32a6955b3010b59cb2f85b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142206"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Como adicionar e remover nós com o controle TreeView dos Windows Forms
O controle <xref:System.Windows.Forms.TreeView> do Windows Forms armazena os <xref:System.Windows.Forms.TreeView.Nodes%2A> nós de alto nível em sua coleção. Cada <xref:System.Windows.Forms.TreeNode> um também <xref:System.Windows.Forms.TreeNode.Nodes%2A> tem sua própria coleção para armazenar seus nódulos infantis. Ambas as propriedades <xref:System.Windows.Forms.TreeNodeCollection>de coleta são do tipo , que fornece membros de coleta padrão que permitem adicionar, remover e reorganizar os nós em um único nível da hierarquia do nó.  
  
### <a name="to-add-nodes-programmatically"></a>Para adicionar nódulos programáticamente  
  
1. Use <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> o método da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da vista da árvore.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Para remover os nódulos programáticamente  
  
1. Use <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> o método da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da vista da árvore para <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> remover um único nó ou o método para limpar todos os nós.  
  
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
  
## <a name="see-also"></a>Confira também

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

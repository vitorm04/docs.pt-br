---
title: Adicionar e remover nós com controle TreeView
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
ms.openlocfilehash: 02b3a7286798c6f2a6426e09c8fc6c18b74a6bf0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731964"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>Como adicionar e remover nós com o controle TreeView dos Windows Forms
O controle de <xref:System.Windows.Forms.TreeView> de Windows Forms armazena os nós de nível superior em sua coleção de <xref:System.Windows.Forms.TreeView.Nodes%2A>. Cada <xref:System.Windows.Forms.TreeNode> também tem sua própria coleção de <xref:System.Windows.Forms.TreeNode.Nodes%2A> para armazenar seus nós filho. Ambas as propriedades de coleção são do tipo <xref:System.Windows.Forms.TreeNodeCollection>, que fornece membros de coleção padrão que permitem que você adicione, remova e reorganize os nós em um único nível da hierarquia de nós.  
  
### <a name="to-add-nodes-programmatically"></a>Para adicionar nós programaticamente  
  
1. Use o método <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da exibição de árvore.  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>Para remover nós programaticamente  
  
1. Use o método <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da exibição de árvore para remover um único nó ou o método <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> para limpar todos os nós.  
  
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

- [Controle TreeView](treeview-control-windows-forms.md)
- [Visão geral do controle TreeView](treeview-control-overview-windows-forms.md)
- [Como definir ícones para o controle TreeView dos Windows Forms](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Como iterar em todos os nós de um controle TreeView dos Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Como determinar qual nó TreeView foi clicado](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

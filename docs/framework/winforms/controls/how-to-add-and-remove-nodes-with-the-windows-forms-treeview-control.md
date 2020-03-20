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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="e5ebf-102">Como adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5ebf-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="e5ebf-103">O controle <xref:System.Windows.Forms.TreeView> do Windows Forms armazena os <xref:System.Windows.Forms.TreeView.Nodes%2A> nós de alto nível em sua coleção.</span><span class="sxs-lookup"><span data-stu-id="e5ebf-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="e5ebf-104">Cada <xref:System.Windows.Forms.TreeNode> um também <xref:System.Windows.Forms.TreeNode.Nodes%2A> tem sua própria coleção para armazenar seus nódulos infantis.</span><span class="sxs-lookup"><span data-stu-id="e5ebf-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="e5ebf-105">Ambas as propriedades <xref:System.Windows.Forms.TreeNodeCollection>de coleta são do tipo , que fornece membros de coleta padrão que permitem adicionar, remover e reorganizar os nós em um único nível da hierarquia do nó.</span><span class="sxs-lookup"><span data-stu-id="e5ebf-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="e5ebf-106">Para adicionar nódulos programáticamente</span><span class="sxs-lookup"><span data-stu-id="e5ebf-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="e5ebf-107">Use <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> o método da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da vista da árvore.</span><span class="sxs-lookup"><span data-stu-id="e5ebf-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="e5ebf-108">Para remover os nódulos programáticamente</span><span class="sxs-lookup"><span data-stu-id="e5ebf-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="e5ebf-109">Use <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> o método da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da vista da árvore para <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> remover um único nó ou o método para limpar todos os nós.</span><span class="sxs-lookup"><span data-stu-id="e5ebf-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5ebf-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="e5ebf-110">See also</span></span>

- [<span data-ttu-id="e5ebf-111">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="e5ebf-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="e5ebf-112">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="e5ebf-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="e5ebf-113">Como definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5ebf-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="e5ebf-114">Como iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5ebf-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="e5ebf-115">Como determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="e5ebf-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="e5ebf-116">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e5ebf-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

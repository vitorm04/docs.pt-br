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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="2dfe5-102">Como adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2dfe5-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="2dfe5-103">O controle de <xref:System.Windows.Forms.TreeView> de Windows Forms armazena os nós de nível superior em sua coleção de <xref:System.Windows.Forms.TreeView.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="2dfe5-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="2dfe5-104">Cada <xref:System.Windows.Forms.TreeNode> também tem sua própria coleção de <xref:System.Windows.Forms.TreeNode.Nodes%2A> para armazenar seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="2dfe5-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="2dfe5-105">Ambas as propriedades de coleção são do tipo <xref:System.Windows.Forms.TreeNodeCollection>, que fornece membros de coleção padrão que permitem que você adicione, remova e reorganize os nós em um único nível da hierarquia de nós.</span><span class="sxs-lookup"><span data-stu-id="2dfe5-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="2dfe5-106">Para adicionar nós programaticamente</span><span class="sxs-lookup"><span data-stu-id="2dfe5-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="2dfe5-107">Use o método <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da exibição de árvore.</span><span class="sxs-lookup"><span data-stu-id="2dfe5-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="2dfe5-108">Para remover nós programaticamente</span><span class="sxs-lookup"><span data-stu-id="2dfe5-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="2dfe5-109">Use o método <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> da propriedade <xref:System.Windows.Forms.TreeView.Nodes%2A> da exibição de árvore para remover um único nó ou o método <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> para limpar todos os nós.</span><span class="sxs-lookup"><span data-stu-id="2dfe5-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2dfe5-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="2dfe5-110">See also</span></span>

- [<span data-ttu-id="2dfe5-111">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="2dfe5-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="2dfe5-112">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="2dfe5-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="2dfe5-113">Como definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2dfe5-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="2dfe5-114">Como iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2dfe5-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="2dfe5-115">Como determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="2dfe5-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="2dfe5-116">Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2dfe5-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

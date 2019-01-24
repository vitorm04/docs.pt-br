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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="bba87-102">Como: Adicionar e remover nós com o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba87-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="bba87-103">Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle armazena os nós de nível superior no seu <xref:System.Windows.Forms.TreeView.Nodes%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="bba87-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="bba87-104">Cada <xref:System.Windows.Forms.TreeNode> também tem seu próprio <xref:System.Windows.Forms.TreeNode.Nodes%2A> coleção para armazenar seus nós filho.</span><span class="sxs-lookup"><span data-stu-id="bba87-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="bba87-105">Ambas as propriedades de coleção são do tipo <xref:System.Windows.Forms.TreeNodeCollection>, que fornece a membros de coleção padrão que permitem adicionar, remover e reordenar os nós em um único nível da hierarquia de nós.</span><span class="sxs-lookup"><span data-stu-id="bba87-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="bba87-106">Para adicionar nós de forma programática</span><span class="sxs-lookup"><span data-stu-id="bba87-106">To add nodes programmatically</span></span>  
  
1.  <span data-ttu-id="bba87-107">Use o <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> método de exibição de árvore <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bba87-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
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
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="bba87-108">Para remover nós de forma programática</span><span class="sxs-lookup"><span data-stu-id="bba87-108">To remove nodes programmatically</span></span>  
  
1.  <span data-ttu-id="bba87-109">Use o <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> método de exibição de árvore <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade para remover um único nó, ou o <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> método para limpar todos os nós.</span><span class="sxs-lookup"><span data-stu-id="bba87-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bba87-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bba87-110">See also</span></span>
- [<span data-ttu-id="bba87-111">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="bba87-111">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
- [<span data-ttu-id="bba87-112">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="bba87-112">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="bba87-113">Como: Definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba87-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="bba87-114">Como: Iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bba87-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="bba87-115">Como: Determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="bba87-115">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="bba87-116">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="bba87-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)

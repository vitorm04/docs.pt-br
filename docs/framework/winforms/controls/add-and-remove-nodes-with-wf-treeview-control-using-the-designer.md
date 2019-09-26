---
title: 'Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040074"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="ef606-102">Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="ef606-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="ef606-103">Como o controle <xref:System.Windows.Forms.TreeView> de Windows Forms exibe nós de maneira hierárquica, ao adicionar um nó, você deve prestar atenção ao que é seu nó pai.</span><span class="sxs-lookup"><span data-stu-id="ef606-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="ef606-104">O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.TreeView> formulário que contém um controle.</span><span class="sxs-lookup"><span data-stu-id="ef606-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="ef606-105">Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ef606-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="ef606-106">Para adicionar ou remover nós no designer</span><span class="sxs-lookup"><span data-stu-id="ef606-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="ef606-107">Selecione o controle <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="ef606-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="ef606-108">Na janela **Propriedades** , clique nas **reticências** (![o botão de reticências (...) no janela Propriedades do Visual Studio](./media/visual-studio-ellipsis-button.png).) botão ao lado <xref:System.Windows.Forms.TreeView.Nodes%2A> da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ef606-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="ef606-109">O **Editor TreeNode** é exibido.</span><span class="sxs-lookup"><span data-stu-id="ef606-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="ef606-110">Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**.</span><span class="sxs-lookup"><span data-stu-id="ef606-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="ef606-111">Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.</span><span class="sxs-lookup"><span data-stu-id="ef606-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="ef606-112">Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="ef606-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef606-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef606-113">See also</span></span>

- [<span data-ttu-id="ef606-114">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ef606-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="ef606-115">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ef606-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="ef606-116">Como: Definir ícones para o Windows Forms controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ef606-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="ef606-117">Como: Iterar em todos os nós de um Windows Forms controle TreeView</span><span class="sxs-lookup"><span data-stu-id="ef606-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="ef606-118">Como: Determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="ef606-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="ef606-119">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ef606-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

---
title: 'Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 71ada3235343aa7e014e12ebf5b367ec744b00d3
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959666"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="3c7ae-102">Como: Adicionar e remover nós com o componente TreeView do Windows Forms usando o designer</span><span class="sxs-lookup"><span data-stu-id="3c7ae-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="3c7ae-103">Porque o Windows Forms <xref:System.Windows.Forms.TreeView> controle exibe nós de forma hierárquica, ao adicionar um nó que você deve prestar atenção a qual é seu nó pai.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="3c7ae-104">O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="3c7ae-105">Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3c7ae-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3c7ae-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3c7ae-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3c7ae-108">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3c7ae-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="3c7ae-109">Para adicionar ou remover nós no designer</span><span class="sxs-lookup"><span data-stu-id="3c7ae-109">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="3c7ae-110">Selecione o <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="3c7ae-111">No **propriedades** janela, clique no **reticências** (![botão do botão de reticências (...) na janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) lado a <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade .</span><span class="sxs-lookup"><span data-stu-id="3c7ae-111">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="3c7ae-112">O **Editor TreeNode** é exibido.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-112">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="3c7ae-113">Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="3c7ae-114">Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="3c7ae-115">Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="3c7ae-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c7ae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c7ae-116">See also</span></span>

- [<span data-ttu-id="3c7ae-117">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="3c7ae-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="3c7ae-118">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="3c7ae-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="3c7ae-119">Como: Definir ícones para o controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c7ae-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="3c7ae-120">Como: Iterar em todos os nós de um controle TreeView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c7ae-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="3c7ae-121">Como: Determinar qual nó TreeView foi clicado</span><span class="sxs-lookup"><span data-stu-id="3c7ae-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="3c7ae-122">Como: Adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3c7ae-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

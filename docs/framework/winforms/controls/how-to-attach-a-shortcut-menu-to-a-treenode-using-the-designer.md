---
title: 'Como: Anexar um menu de atalho a um TreeNode usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040454"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="62d24-102">Como: Anexar um menu de atalho a um TreeNode usando o designer</span><span class="sxs-lookup"><span data-stu-id="62d24-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="62d24-103">O controle <xref:System.Windows.Forms.TreeView> Windows Forms exibe uma hierarquia de nós, semelhante aos arquivos e pastas exibidos no painel esquerdo do recurso Windows Explorer em sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="62d24-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="62d24-104">Ao definir a <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> Propriedade, você pode fornecer operações sensíveis ao contexto ao usuário ao clicar com o botão direito do <xref:System.Windows.Forms.TreeView> mouse no controle.</span><span class="sxs-lookup"><span data-stu-id="62d24-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="62d24-105">Ao associar um <xref:System.Windows.Forms.ContextMenuStrip> componente a itens individuais <xref:System.Windows.Forms.TreeNode> , você pode adicionar um nível personalizado de funcionalidade de menu de atalho para <xref:System.Windows.Forms.TreeView> seus controles.</span><span class="sxs-lookup"><span data-stu-id="62d24-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="62d24-106">Para associar um menu de atalho a um TreeNode em tempo de design</span><span class="sxs-lookup"><span data-stu-id="62d24-106">To associate a shortcut menu with a TreeNode at design time</span></span>

1. <span data-ttu-id="62d24-107">Adicione um <xref:System.Windows.Forms.TreeView> controle ao seu formulário e, em seguida, adicione nós <xref:System.Windows.Forms.TreeView> ao conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="62d24-107">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="62d24-108">Para obter mais informações, confira [Como: Adicione e remova nós com o Windows Forms controle](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)TreeView.</span><span class="sxs-lookup"><span data-stu-id="62d24-108">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>

2. <span data-ttu-id="62d24-109">Adicione um <xref:System.Windows.Forms.ContextMenuStrip> componente ao formulário e, em seguida, adicione itens de menu ao menu de atalho que representam operações em nível de nó que você deseja disponibilizar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="62d24-109">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="62d24-110">Para obter mais informações, confira [Como: Adicione itens de menu a um](how-to-add-menu-items-to-a-contextmenustrip.md)ContextMenuStrip.</span><span class="sxs-lookup"><span data-stu-id="62d24-110">For more information, see [How to: Add Menu Items to a ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>

3. <span data-ttu-id="62d24-111">Reabra a caixa de diálogo **TreeNodeEditor** para <xref:System.Windows.Forms.TreeView> o controle, selecione o nó a ser editado e <xref:System.Windows.Forms.ContextMenuStrip> defina sua propriedade para o menu de atalho que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="62d24-111">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>

4. <span data-ttu-id="62d24-112">Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="62d24-112">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>

     <span data-ttu-id="62d24-113">Além disso, você desejará escrever código para manipular <xref:System.Windows.Forms.ToolStripItem.Click> os eventos para esses itens de menu.</span><span class="sxs-lookup"><span data-stu-id="62d24-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>

## <a name="see-also"></a><span data-ttu-id="62d24-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62d24-114">See also</span></span>

- [<span data-ttu-id="62d24-115">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="62d24-115">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="62d24-116">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="62d24-116">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="62d24-117">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="62d24-117">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)

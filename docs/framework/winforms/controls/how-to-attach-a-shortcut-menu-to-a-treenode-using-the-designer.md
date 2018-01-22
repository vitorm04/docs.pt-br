---
title: Como anexar um menu de atalho a um TreeNode usando o designer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ab73f6e4dc6a4e348853183046db564e748360b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="fffac-102">Como anexar um menu de atalho a um TreeNode usando o designer</span><span class="sxs-lookup"><span data-stu-id="fffac-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="fffac-103">Windows Forms <xref:System.Windows.Forms.TreeView> controle exibe uma hierarquia de nós, semelhantes aos arquivos e pastas exibidas no painel esquerdo do recurso Windows Explorer em sistemas operacionais Windows.</span><span class="sxs-lookup"><span data-stu-id="fffac-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="fffac-104">Definindo o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade, você pode fornecer operações sensíveis ao contexto para o usuário quando eles com o botão direito do <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="fffac-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="fffac-105">Associando um <xref:System.Windows.Forms.ContextMenuStrip> componente com individuais <xref:System.Windows.Forms.TreeNode> itens, você pode adicionar um nível personalizado de funcionalidade do menu de atalho para o <xref:System.Windows.Forms.TreeView> controles.</span><span class="sxs-lookup"><span data-stu-id="fffac-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fffac-106">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="fffac-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fffac-107">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="fffac-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fffac-108">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fffac-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="fffac-109">Para associar um menu de atalho a um TreeNode em tempo de design</span><span class="sxs-lookup"><span data-stu-id="fffac-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="fffac-110">Adicionar um <xref:System.Windows.Forms.TreeView> o controle para o formulário e, em seguida, adicionar nós a <xref:System.Windows.Forms.TreeView> conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="fffac-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="fffac-111">Para obter mais informações, veja [Como adicionar e remover nós com o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fffac-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="fffac-112">Adicionar uma <xref:System.Windows.Forms.ContextMenuStrip> ao formulário, o componente e, em seguida, adicionar itens de menu ao menu de atalho que representam as operações de nível de nó que você deseja disponibilizar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fffac-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="fffac-113">Para obter mais informações, veja [Como adicionar itens de menu a um ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="fffac-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="fffac-114">Reabra o **TreeNodeEditor** caixa de diálogo para o <xref:System.Windows.Forms.TreeView> de controle, selecione o nó para editar e definir seu <xref:System.Windows.Forms.ContextMenuStrip> propriedade para o menu de atalho que você adicionou.</span><span class="sxs-lookup"><span data-stu-id="fffac-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="fffac-115">Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="fffac-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="fffac-116">Além disso, você deve escrever código para manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para esses itens de menu.</span><span class="sxs-lookup"><span data-stu-id="fffac-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffac-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fffac-117">See Also</span></span>  
 [<span data-ttu-id="fffac-118">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="fffac-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="fffac-119">Visão geral do controle TreeView</span><span class="sxs-lookup"><span data-stu-id="fffac-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="fffac-120">Controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="fffac-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)

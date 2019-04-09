---
title: 'Como: Anexar um menu ShortCut a um nó TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: ba29e86f62c8d56b0d300d1841a70f434087dd84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100009"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a><span data-ttu-id="2d21d-102">Como: Anexar um menu ShortCut a um nó TreeView</span><span class="sxs-lookup"><span data-stu-id="2d21d-102">How to: Attach a ShortCut Menu to a TreeView Node</span></span>
<span data-ttu-id="2d21d-103">Os formulários do Windows <xref:System.Windows.Forms.TreeView> controle exibe uma hierarquia de nós, semelhantes aos arquivos e pastas exibidas no painel esquerdo do Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="2d21d-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of Windows Explorer.</span></span> <span data-ttu-id="2d21d-104">Definindo o <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriedade, você pode fornecer operações sensíveis ao contexto para o usuário quando eles com o botão direito do <xref:System.Windows.Forms.TreeView> controle.</span><span class="sxs-lookup"><span data-stu-id="2d21d-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="2d21d-105">Associando um <xref:System.Windows.Forms.ContextMenuStrip> componente com indivíduo <xref:System.Windows.Forms.TreeNode> itens, você pode adicionar um nível personalizado de funcionalidade do menu de atalho para seu <xref:System.Windows.Forms.TreeView> controles.</span><span class="sxs-lookup"><span data-stu-id="2d21d-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a><span data-ttu-id="2d21d-106">Para associar um menu de atalho a um TreeNode programaticamente</span><span class="sxs-lookup"><span data-stu-id="2d21d-106">To associate a shortcut menu with a TreeNode programmatically</span></span>  
  
1.  <span data-ttu-id="2d21d-107">Criar uma instância de um <xref:System.Windows.Forms.TreeView> controlar com as configurações de propriedade adequado, crie uma raiz <xref:System.Windows.Forms.TreeNode>e, em seguida, adicione subnós.</span><span class="sxs-lookup"><span data-stu-id="2d21d-107">Instantiate a <xref:System.Windows.Forms.TreeView> control with the appropriate property settings, create a root <xref:System.Windows.Forms.TreeNode>, and then add subnodes.</span></span>  
  
2.  <span data-ttu-id="2d21d-108">Criar uma instância de um <xref:System.Windows.Forms.ContextMenuStrip> componente e, em seguida, adicione um <xref:System.Windows.Forms.ToolStripMenuItem> para cada operação que você deseja disponibilizar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2d21d-108">Instantiate a <xref:System.Windows.Forms.ContextMenuStrip> component, and then add a <xref:System.Windows.Forms.ToolStripMenuItem> for each operation you want to make available at run time.</span></span>  
  
3.  <span data-ttu-id="2d21d-109">Defina as <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> propriedade do apropriado <xref:System.Windows.Forms.TreeNode> ao menu de atalho que você cria.</span><span class="sxs-lookup"><span data-stu-id="2d21d-109">Set the <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> property of the appropriate <xref:System.Windows.Forms.TreeNode> to the shortcut menu you create.</span></span>  
  
4.  <span data-ttu-id="2d21d-110">Quando essa propriedade for definida, o menu de atalho será exibido quando você clicar no nó com o botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="2d21d-110">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
 <span data-ttu-id="2d21d-111">O exemplo de código a seguir cria um basic <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ContextMenuStrip> associados à raiz <xref:System.Windows.Forms.TreeNode> da <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="2d21d-111">The following code example creates a basic <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ContextMenuStrip> associated with the root <xref:System.Windows.Forms.TreeNode> of the <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="2d21d-112">Você precisará personalizar as opções de menu para que se ajustem a <xref:System.Windows.Forms.TreeView> você está desenvolvendo.</span><span class="sxs-lookup"><span data-stu-id="2d21d-112">You will need to customize the menu choices to those that fit the <xref:System.Windows.Forms.TreeView> you are developing.</span></span> <span data-ttu-id="2d21d-113">Além disso, você vai querer escrever código para manipular o <xref:System.Windows.Forms.ToolStripItem.Click> eventos para esses itens de menu.</span><span class="sxs-lookup"><span data-stu-id="2d21d-113">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2d21d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d21d-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="2d21d-115">Controle TreeView</span><span class="sxs-lookup"><span data-stu-id="2d21d-115">TreeView Control</span></span>](treeview-control-windows-forms.md)

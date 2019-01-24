---
title: 'Como: Ocultar ToolStripMenuItems usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 966ee5a7e038b80eb21b77c5ad5c0b57efa21951
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517221"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="43781-102">Como: Ocultar ToolStripMenuItems usando o Designer</span><span class="sxs-lookup"><span data-stu-id="43781-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="43781-103">Ocultar itens de menu é uma maneira de controlar a interface do usuário (IU) do seu aplicativo e restringir comandos do usuário.</span><span class="sxs-lookup"><span data-stu-id="43781-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="43781-104">Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="43781-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="43781-105">Isso apresenta menos distrações para o usuário.</span><span class="sxs-lookup"><span data-stu-id="43781-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="43781-106">Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="43781-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="43781-107">Para obter mais informações sobre como desabilitar itens de menu, consulte [como: Desabilitar ToolStripMenuItems usando o Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="43781-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43781-108">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="43781-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="43781-109">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="43781-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="43781-110">Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="43781-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="43781-111">Ocultar um menu de nível superior e seus itens de submenu</span><span class="sxs-lookup"><span data-stu-id="43781-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="43781-112">Selecione o item de menu de nível superior e defina suas <xref:System.Windows.Forms.ToolStripItem.Visible%2A> ou <xref:System.Windows.Forms.ToolStripItem.Available%2A> propriedade `false`.</span><span class="sxs-lookup"><span data-stu-id="43781-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="43781-113">Quando você oculta o item de menu de nível superior, todos os itens de menu dentro desse menu também são ocultos.</span><span class="sxs-lookup"><span data-stu-id="43781-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="43781-114">Se você clicar em outro lugar além do <xref:System.Windows.Forms.MenuStrip> depois de definir <xref:System.Windows.Forms.ToolStripItem.Visible%2A> para `false`, o item de menu inteiro de nível superior e seus itens de submenu desaparecerão do formulário, mostrando assim o efeito do tempo de execução da ação.</span><span class="sxs-lookup"><span data-stu-id="43781-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="43781-115">Para exibir o item de menu de nível superior oculto em tempo de design, clique no <xref:System.Windows.Forms.MenuStrip> no **bandeja de componentes**, na **Document Outline**, ou na parte superior da grade de propriedade.</span><span class="sxs-lookup"><span data-stu-id="43781-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43781-116">Você raramente ocultará um menu inteiro, exceto por menus filho MDI (interface de vários documentos) em um cenário de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="43781-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="43781-117">Ocultar um item de submenu</span><span class="sxs-lookup"><span data-stu-id="43781-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="43781-118">Selecione o item de submenu e defina suas <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade para `false`.</span><span class="sxs-lookup"><span data-stu-id="43781-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="43781-119">Quando você oculta um item de submenu, ele permanece visível no formulário no tempo de design para que você pode selecioná-lo facilmente para continuar trabalhando nele.</span><span class="sxs-lookup"><span data-stu-id="43781-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="43781-120">Ele será ocultado efetivamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="43781-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43781-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43781-121">See also</span></span>
- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="43781-122">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="43781-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="43781-123">Como: Desabilitar ToolStripMenuItems usando o Designer</span><span class="sxs-lookup"><span data-stu-id="43781-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)

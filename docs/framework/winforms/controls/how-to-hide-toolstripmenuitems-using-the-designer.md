---
title: 'Como: Ocultar ToolStripMenuItems usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039754"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="64676-102">Como: Ocultar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="64676-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="64676-103">Ocultar itens de menu é uma maneira de controlar a interface do usuário (IU) do seu aplicativo e restringir comandos do usuário.</span><span class="sxs-lookup"><span data-stu-id="64676-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="64676-104">Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis.</span><span class="sxs-lookup"><span data-stu-id="64676-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="64676-105">Isso apresenta menos distrações para o usuário.</span><span class="sxs-lookup"><span data-stu-id="64676-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="64676-106">Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.</span><span class="sxs-lookup"><span data-stu-id="64676-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="64676-107">Para obter mais informações sobre como desabilitar itens de menu [, consulte Como: Desabilite ToolStripMenuItems usando o](how-to-disable-toolstripmenuitems-using-the-designer.md)designer.</span><span class="sxs-lookup"><span data-stu-id="64676-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="64676-108">Ocultar um menu de nível superior e seus itens de submenu</span><span class="sxs-lookup"><span data-stu-id="64676-108">To hide a top-level menu and its submenu items</span></span>

1. <span data-ttu-id="64676-109">Selecione o item de menu de nível superior e defina <xref:System.Windows.Forms.ToolStripItem.Visible%2A> sua <xref:System.Windows.Forms.ToolStripItem.Available%2A> propriedade ou `false`como.</span><span class="sxs-lookup"><span data-stu-id="64676-109">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>

     <span data-ttu-id="64676-110">Quando você oculta o item de menu de nível superior, todos os itens de menu dentro desse menu também são ocultos.</span><span class="sxs-lookup"><span data-stu-id="64676-110">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="64676-111">Se você clicar em algum lugar diferente de <xref:System.Windows.Forms.MenuStrip> na `false`configuração <xref:System.Windows.Forms.ToolStripItem.Visible%2A> após, o item de menu de nível superior inteiro e seus itens de submenu desaparecerão do formulário, mostrando assim o efeito de tempo de execução de sua ação.</span><span class="sxs-lookup"><span data-stu-id="64676-111">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="64676-112">Para exibir o item de menu de nível superior oculto em tempo de design, clique <xref:System.Windows.Forms.MenuStrip> no na **bandeja de componentes**, em **estrutura de tópicos do documento**ou na parte superior da grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="64676-112">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>

> [!NOTE]
>  <span data-ttu-id="64676-113">Você raramente ocultará um menu inteiro, exceto por menus filho MDI (interface de vários documentos) em um cenário de mesclagem.</span><span class="sxs-lookup"><span data-stu-id="64676-113">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>

## <a name="to-hide-a-submenu-item"></a><span data-ttu-id="64676-114">Ocultar um item de submenu</span><span class="sxs-lookup"><span data-stu-id="64676-114">To hide a submenu item</span></span>

1. <span data-ttu-id="64676-115">Selecione o item de submenu e defina <xref:System.Windows.Forms.ToolStripItem.Visible%2A> sua propriedade `false`como.</span><span class="sxs-lookup"><span data-stu-id="64676-115">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>

     <span data-ttu-id="64676-116">Quando você oculta um item de submenu, ele permanece visível no formulário no tempo de design para que você pode selecioná-lo facilmente para continuar trabalhando nele.</span><span class="sxs-lookup"><span data-stu-id="64676-116">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="64676-117">Ele será ocultado efetivamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="64676-117">It will actually be hidden at run time.</span></span>

## <a name="see-also"></a><span data-ttu-id="64676-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64676-118">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="64676-119">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="64676-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="64676-120">Como: Desabilitar ToolStripMenuItems usando o designer</span><span class="sxs-lookup"><span data-stu-id="64676-120">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)

---
title: Visão geral do componente MainMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168474"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="b9d68-102">Visão geral do componente MainMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b9d68-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b9d68-103">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="b9d68-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="b9d68-104">Os formulários do Windows <xref:System.Windows.Forms.MainMenu> componente exibe um menu no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b9d68-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="b9d68-105">Todos os submenus do menu principal e itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="b9d68-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="b9d68-106">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="b9d68-106">Key Properties</span></span>  
 <span data-ttu-id="b9d68-107">Um item de menu pode ser designado como o item padrão definindo a <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> propriedade para `true`.</span><span class="sxs-lookup"><span data-stu-id="b9d68-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="b9d68-108">O item padrão aparece em negrito quando o menu é clicado.</span><span class="sxs-lookup"><span data-stu-id="b9d68-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="b9d68-109">O item de menu <xref:System.Windows.Forms.MenuItem.Checked%2A> propriedade está `true` ou `false`e indica se o item de menu é selecionado.</span><span class="sxs-lookup"><span data-stu-id="b9d68-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="b9d68-110">O item de menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> propriedade personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `true`, um botão de opção é exibida ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> está definido como `false`, uma marca de seleção aparece ao lado do item.</span><span class="sxs-lookup"><span data-stu-id="b9d68-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d68-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9d68-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="b9d68-112">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="b9d68-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)

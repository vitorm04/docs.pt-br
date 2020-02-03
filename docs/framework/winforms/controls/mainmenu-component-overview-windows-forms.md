---
title: Visão geral do componente MainMenu
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745121"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="61ea6-102">Visão geral do componente MainMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="61ea6-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="61ea6-103">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="61ea6-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="61ea6-104">O componente Windows Forms <xref:System.Windows.Forms.MainMenu> exibe um menu em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="61ea6-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="61ea6-105">Todos os submenus do menu principal e itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="61ea6-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="61ea6-106">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="61ea6-106">Key Properties</span></span>  
 <span data-ttu-id="61ea6-107">Um item de menu pode ser designado como o item padrão definindo a propriedade <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="61ea6-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="61ea6-108">O item padrão é exibido em negrito quando o menu é clicado.</span><span class="sxs-lookup"><span data-stu-id="61ea6-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="61ea6-109">A propriedade <xref:System.Windows.Forms.MenuItem.Checked%2A> do item de menu é `true` ou `false`e indica se o item de menu está selecionado.</span><span class="sxs-lookup"><span data-stu-id="61ea6-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="61ea6-110">A propriedade <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> do item de menu personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> for definido como `true`, um botão de opção aparecerá ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> for definido como `false`, uma marca de seleção aparecerá ao lado do item.</span><span class="sxs-lookup"><span data-stu-id="61ea6-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ea6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61ea6-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="61ea6-112">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="61ea6-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)

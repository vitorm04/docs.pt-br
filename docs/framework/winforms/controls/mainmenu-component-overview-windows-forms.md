---
title: "Visão geral do componente MainMenu (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f5cfe3a97bbbd4d5ba2d3ba089736599b6a2190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="9b44c-102">Visão geral do componente MainMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9b44c-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="9b44c-103">Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> controles de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para uso futuro e compatibilidade com versões anteriores, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="9b44c-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="9b44c-104">Windows Forms <xref:System.Windows.Forms.MainMenu> componente exibe um menu no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9b44c-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="9b44c-105">Todos os submenus do menu principal e os itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.</span><span class="sxs-lookup"><span data-stu-id="9b44c-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="9b44c-106">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="9b44c-106">Key Properties</span></span>  
 <span data-ttu-id="9b44c-107">Um item de menu pode ser designado como o item padrão definindo o <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="9b44c-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="9b44c-108">O item padrão aparece em negrito quando o menu é clicado.</span><span class="sxs-lookup"><span data-stu-id="9b44c-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="9b44c-109">O item de menu <xref:System.Windows.Forms.MenuItem.Checked%2A> propriedade está `true` ou `false`e indica se o item de menu é selecionado.</span><span class="sxs-lookup"><span data-stu-id="9b44c-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="9b44c-110">O item de menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> propriedade personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `true`, um botão de opção é exibida ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `false`, uma marca de seleção aparece ao lado do item.</span><span class="sxs-lookup"><span data-stu-id="9b44c-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b44c-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b44c-111">See Also</span></span>  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="9b44c-112">Visão geral do controle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="9b44c-112">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)

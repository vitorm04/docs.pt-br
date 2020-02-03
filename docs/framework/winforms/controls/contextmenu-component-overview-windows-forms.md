---
title: Visão geral do componente ContextMenu
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746190"
---
# <a name="contextmenu-component-overview-windows-forms"></a>Visão geral do componente ContextMenu (Windows Forms)
> [!IMPORTANT]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.  
  
 Com o componente Windows Forms <xref:System.Windows.Forms.ContextMenu>, você pode fornecer aos usuários um menu de atalho facilmente acessível dos comandos usados com frequência que estão associados ao objeto selecionado. Os itens em um menu de atalho frequentemente são um subconjunto dos itens de menus principais que aparecem em outro lugar no aplicativo. Um usuário geralmente pode acessar um menu de atalho clicando com o botão direito do mouse. nos Windows Forms, menus de atalho são associados a controles.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Você pode associar um menu de atalho a um controle definindo a propriedade <xref:System.Windows.Forms.Control.ContextMenu%2A> do controle como o componente <xref:System.Windows.Forms.ContextMenu>. Um único menu de atalho pode ser associado a vários controles, mas cada controle pode ter apenas um menu de atalho.  
  
 A propriedade de chave do componente <xref:System.Windows.Forms.ContextMenu> é a propriedade <xref:System.Windows.Forms.Menu.MenuItems%2A>. Você pode adicionar itens de menu criando programaticamente <xref:System.Windows.Forms.MenuItem> objetos e adicionando-os à <xref:System.Windows.Forms.Menu.MenuItemCollection> do menu de atalho. Como os itens em um menu de atalho geralmente são retirados de outros menus, você provavelmente adicionará itens ao menu de atalho copiando-os.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>

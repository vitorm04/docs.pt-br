---
title: Visão geral do componente ContextMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975137"
---
# <a name="contextmenu-component-overview-windows-forms"></a>Visão geral do componente ContextMenu (Windows Forms)
> [!IMPORTANT]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 Com os formulários do Windows <xref:System.Windows.Forms.ContextMenu> componente, você pode fornecer aos usuários um menu de atalho facilmente acessível dos comandos usados com frequência que estão associados com o objeto selecionado. Os itens em um menu de atalho frequentemente são um subconjunto dos itens de menus principais que aparecem em outro lugar no aplicativo. Um usuário geralmente pode acessar um menu de atalho clicando com o botão direito do mouse. nos Windows Forms, menus de atalho são associados a controles.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Você pode associar um menu de atalho com um controle definindo o controle <xref:System.Windows.Forms.Control.ContextMenu%2A> propriedade para o <xref:System.Windows.Forms.ContextMenu> componente. Um único menu de atalho pode ser associado a vários controles, mas cada controle pode ter apenas um menu de atalho.  
  
 A propriedade de chave do <xref:System.Windows.Forms.ContextMenu> componente é o <xref:System.Windows.Forms.Menu.MenuItems%2A> propriedade. Você pode adicionar itens de menu criando programaticamente <xref:System.Windows.Forms.MenuItem> objetos e adicioná-los para o <xref:System.Windows.Forms.Menu.MenuItemCollection> no menu de atalho. Como os itens em um menu de atalho geralmente são retirados de outros menus, você provavelmente adicionará itens ao menu de atalho copiando-os.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>

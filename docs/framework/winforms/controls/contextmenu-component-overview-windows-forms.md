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
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962179"
---
# <a name="contextmenu-component-overview-windows-forms"></a>Visão geral do componente ContextMenu (Windows Forms)
> [!IMPORTANT]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.MainMenu> substituam e adicionem funcionalidade aos controles e de versões anteriores, e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher. <xref:System.Windows.Forms.ContextMenuStrip>  
  
 Com o componente <xref:System.Windows.Forms.ContextMenu> Windows Forms, você pode fornecer aos usuários um menu de atalho facilmente acessível dos comandos usados com frequência que estão associados ao objeto selecionado. Os itens em um menu de atalho frequentemente são um subconjunto dos itens de menus principais que aparecem em outro lugar no aplicativo. Um usuário geralmente pode acessar um menu de atalho clicando com o botão direito do mouse. nos Windows Forms, menus de atalho são associados a controles.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Você pode associar um menu de atalho a um controle definindo a propriedade do <xref:System.Windows.Forms.Control.ContextMenu%2A> controle para o <xref:System.Windows.Forms.ContextMenu> componente. Um único menu de atalho pode ser associado a vários controles, mas cada controle pode ter apenas um menu de atalho.  
  
 A propriedade de chave do <xref:System.Windows.Forms.ContextMenu> componente é a <xref:System.Windows.Forms.Menu.MenuItems%2A> propriedade. Você pode adicionar itens <xref:System.Windows.Forms.MenuItem> <xref:System.Windows.Forms.Menu.MenuItemCollection> de menu criando objetos programaticamente e adicionando-os à do menu de atalho. Como os itens em um menu de atalho geralmente são retirados de outros menus, você provavelmente adicionará itens ao menu de atalho copiando-os.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>

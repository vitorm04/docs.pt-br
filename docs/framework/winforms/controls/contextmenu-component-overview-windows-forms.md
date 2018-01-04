---
title: "Visão geral do componente ContextMenu (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b0db67e8da97f380c3bb2eb9aab951628c4b6487
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a>Visão geral do componente ContextMenu (Windows Forms)
> [!IMPORTANT]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> controles de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para uso futuro e compatibilidade com versões anteriores, se você escolher.  
  
 Com o Windows Forms <xref:System.Windows.Forms.ContextMenu> componente, você pode fornecer aos usuários um menu de atalho facilmente acessível de comandos usados com frequência que estão associados com o objeto selecionado. Os itens em um menu de atalho frequentemente são um subconjunto dos itens de menus principais que aparecem em outro lugar no aplicativo. Um usuário geralmente pode acessar um menu de atalho clicando com o botão direito do mouse. nos Windows Forms, menus de atalho são associados a controles.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Você pode associar um menu de atalho com um controle, definindo o controle <xref:System.Windows.Forms.Control.ContextMenu%2A> propriedade para o <xref:System.Windows.Forms.ContextMenu> componente. Um único menu de atalho pode ser associado a vários controles, mas cada controle pode ter apenas um menu de atalho.  
  
 A propriedade de chave de <xref:System.Windows.Forms.ContextMenu> componente é a <xref:System.Windows.Forms.Menu.MenuItems%2A> propriedade. Você pode adicionar itens de menu programaticamente criando <xref:System.Windows.Forms.MenuItem> objetos e adicioná-los para o <xref:System.Windows.Forms.Menu.MenuItemCollection> do menu de atalho. Como os itens em um menu de atalho geralmente são retirados de outros menus, você provavelmente adicionará itens ao menu de atalho copiando-os.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>

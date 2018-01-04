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
ms.workload: dotnet
ms.openlocfilehash: c8681635f2f97e74893704513f57313106168e52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a>Visão geral do componente MainMenu (Windows Forms)
> [!IMPORTANT]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> controles de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para uso futuro e compatibilidade com versões anteriores, se você escolher.  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> componente exibe um menu no tempo de execução. Todos os submenus do menu principal e os itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Um item de menu pode ser designado como o item padrão definindo o <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> propriedade `true`. O item padrão aparece em negrito quando o menu é clicado. O item de menu <xref:System.Windows.Forms.MenuItem.Checked%2A> propriedade está `true` ou `false`e indica se o item de menu é selecionado. O item de menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> propriedade personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `true`, um botão de opção é exibida ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `false`, uma marca de seleção aparece ao lado do item.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [Visão geral do controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)

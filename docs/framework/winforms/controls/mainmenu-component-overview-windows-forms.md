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
ms.openlocfilehash: 6c2c33c8c03751e87d71e65523b82d92b18f31c4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709857"
---
# <a name="mainmenu-component-overview-windows-forms"></a>Visão geral do componente MainMenu (Windows Forms)
> [!IMPORTANT]
>  Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade para o <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, os controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 Os formulários do Windows <xref:System.Windows.Forms.MainMenu> componente exibe um menu no tempo de execução. Todos os submenus do menu principal e itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Um item de menu pode ser designado como o item padrão definindo a <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> propriedade para `true`. O item padrão aparece em negrito quando o menu é clicado. O item de menu <xref:System.Windows.Forms.MenuItem.Checked%2A> propriedade está `true` ou `false`e indica se o item de menu é selecionado. O item de menu <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> propriedade personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> é definido como `true`, um botão de opção é exibida ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> está definido como `false`, uma marca de seleção aparece ao lado do item.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)

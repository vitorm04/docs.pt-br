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
# <a name="mainmenu-component-overview-windows-forms"></a>Visão geral do componente MainMenu (Windows Forms)
> [!IMPORTANT]
> Embora <xref:System.Windows.Forms.MenuStrip> e <xref:System.Windows.Forms.ContextMenuStrip> substituam e adicionem funcionalidade aos controles <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> de versões anteriores, <xref:System.Windows.Forms.MainMenu> e <xref:System.Windows.Forms.ContextMenu> são mantidos para a compatibilidade com versões anteriores e o uso futuro, se você escolher.  
  
 O componente Windows Forms <xref:System.Windows.Forms.MainMenu> exibe um menu em tempo de execução. Todos os submenus do menu principal e itens individuais são <xref:System.Windows.Forms.MenuItem> objetos.  
  
## <a name="key-properties"></a>Propriedades da chave  
 Um item de menu pode ser designado como o item padrão definindo a propriedade <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> como `true`. O item padrão é exibido em negrito quando o menu é clicado. A propriedade <xref:System.Windows.Forms.MenuItem.Checked%2A> do item de menu é `true` ou `false`e indica se o item de menu está selecionado. A propriedade <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> do item de menu personaliza a aparência do item selecionado: se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> for definido como `true`, um botão de opção aparecerá ao lado do item; se <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> for definido como `false`, uma marca de seleção aparecerá ao lado do item.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)

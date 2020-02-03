---
title: Visão geral do controle MenuStrip
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734472"
---
# <a name="menustrip-control-overview-windows-forms"></a>Visão geral do controle MenuStrip (Windows Forms)
Os menus expõem funcionalidades para os usuários, mantendo os comandos que são agrupados por um tema comum.  
  
 O controle de <xref:System.Windows.Forms.MenuStrip> foi introduzido na versão 2,0 do .NET Framework. Com o controle <xref:System.Windows.Forms.MenuStrip>, você pode facilmente criar menus como aqueles encontrados no Microsoft Office.  
  
 O controle <xref:System.Windows.Forms.MenuStrip> dá suporte à interface de vários documentos (MDI) e à mesclagem de menus, a dicas de ferramentas e ao estouro. Você pode melhorar a usabilidade e a legibilidade dos seus menus adicionando teclas de acesso, teclas de atalho, marcas de seleção, imagens e barras separadoras.  
  
 O controle de <xref:System.Windows.Forms.MenuStrip> substitui e adiciona funcionalidade ao controle de <xref:System.Windows.Forms.MainMenu>; no entanto, o controle de <xref:System.Windows.Forms.MainMenu> é retido para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Maneiras de usar o controle MenuStrip  
 Use o controle de <xref:System.Windows.Forms.MenuStrip> para:  
  
- Crie facilmente menus personalizados e comumente usados que dão suporte a recursos avançados de interface do usuário e layout, tais como ordenação e alinhamento de texto e imagem, operações do tipo "arrastar e soltar", MDI, estouro e modos alternativos de acessar os comandos de menu.  
  
- Suporte à aparência e comportamento típicos do sistema operacional.  
  
- Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.  
  
 A tabela a seguir mostra algumas propriedades particularmente importantes de <xref:System.Windows.Forms.MenuStrip> e classes associadas.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtém ou define o <xref:System.Windows.Forms.ToolStripMenuItem> usado para exibir uma lista de formulários filho MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtém ou define como os menus filho são mescladas com os menus pai em aplicativos MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtém ou define a posição de um item mesclado dentro de um menu em aplicativos MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtém ou define um valor que indica se o formulário é um contêiner para formulários MDI filho.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtém ou define um valor que indica se as dicas de ferramenta são mostradas para o <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtém ou define um valor que indica se o <xref:System.Windows.Forms.MenuStrip> dá suporte à funcionalidade de estouro.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtém ou define as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtém ou define um valor que indica se as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem> são exibidas ao lado do <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 A tabela a seguir mostra as classes importantes do <xref:System.Windows.Forms.MenuStrip> Companion.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Representa uma opção selecionável exibida em um <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Representa um menu de atalho.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Representa um controle que permite ao usuário selecionar um único item de uma lista que é exibida quando o usuário clica em um <xref:System.Windows.Forms.ToolStripDropDownButton> ou em um item de menu de nível superior.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fornece a funcionalidade básica para controles derivados de <xref:System.Windows.Forms.ToolStripItem> que exibem itens suspensos quando clicados.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>

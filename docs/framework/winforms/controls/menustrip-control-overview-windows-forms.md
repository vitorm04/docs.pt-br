---
title: Visão geral do controle MenuStrip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 41688dce0e645b643d7a10a5cf330f1f3a5f9cc8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653704"
---
# <a name="menustrip-control-overview-windows-forms"></a>Visão geral do controle MenuStrip (Windows Forms)
Os menus expõem funcionalidades para os usuários, mantendo os comandos que são agrupados por um tema comum.  
  
 O <xref:System.Windows.Forms.MenuStrip> controle há de novo nesta versão do Visual Studio e o .NET Framework. Com o controle, você pode criar facilmente menus como os encontrados no Microsoft Office.  
  
 O <xref:System.Windows.Forms.MenuStrip> controle é compatível com a interface de documentos múltiplos (MDI) e mesclagem de menu, dicas de ferramenta e estouro. Você pode melhorar a usabilidade e a legibilidade dos seus menus adicionando teclas de acesso, teclas de atalho, marcas de seleção, imagens e barras separadoras.  
  
 O <xref:System.Windows.Forms.MenuStrip> controle substitui e adiciona funcionalidade para o <xref:System.Windows.Forms.MainMenu> controle; no entanto, o <xref:System.Windows.Forms.MainMenu> controle é mantido para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Maneiras de usar o controle MenuStrip  
 Use o <xref:System.Windows.Forms.MenuStrip> o controle para:  
  
-   Crie facilmente menus personalizados e comumente usados que dão suporte a recursos avançados de interface do usuário e layout, tais como ordenação e alinhamento de texto e imagem, operações do tipo "arrastar e soltar", MDI, estouro e modos alternativos de acessar os comandos de menu.  
  
-   Suporte à aparência e comportamento típicos do sistema operacional.  
  
-   Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.  
  
 A tabela a seguir mostra algumas propriedades especialmente importantes de <xref:System.Windows.Forms.MenuStrip> e associados a classes.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtém ou define o <xref:System.Windows.Forms.ToolStripMenuItem> que é usado para exibir uma lista dos formulários filho MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtém ou define como os menus filho são mescladas com os menus pai em aplicativos MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtém ou define a posição de um item mesclado dentro de um menu em aplicativos MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtém ou define um valor que indica se o formulário é um contêiner para formulários MDI filho.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtém ou define um valor que indica se as dicas de ferramenta serão mostradas para o <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtém ou define um valor que indica se o <xref:System.Windows.Forms.MenuStrip> dá suporte à funcionalidade de estouro.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtém ou define as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtém ou define um valor que indica se as teclas de atalho associadas ao <xref:System.Windows.Forms.ToolStripMenuItem> são exibidas ao lado do <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 A tabela a seguir mostra a importante <xref:System.Windows.Forms.MenuStrip> classe complementares.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Representa uma opção selecionável exibida em um <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Representa um menu de atalho.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Representa um controle que permite que o usuário selecionar um único item em uma lista que é exibida quando o usuário clica em um <xref:System.Windows.Forms.ToolStripDropDownButton> ou um item de menu de nível superior.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fornece a funcionalidade básica para controles derivados de <xref:System.Windows.Forms.ToolStripItem> que exibem itens de lista suspensa quando clicados.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>

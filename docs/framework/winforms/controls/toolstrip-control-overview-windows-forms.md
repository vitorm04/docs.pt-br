---
title: Visão geral do controle ToolStrip (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 3927f180e738541f2f2f8af6d03d281f6a601167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542042"
---
# <a name="toolstrip-control-overview-windows-forms"></a>Visão geral do controle ToolStrip (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolStrip> controle e suas classes associadas fornecem uma estrutura comum para a combinação de elementos da interface do usuário em menus, barras de ferramentas e barras de status. <xref:System.Windows.Forms.ToolStrip> controles de oferecem uma experiência avançada de tempo de design que inclui a ativação no local e editar, layout personalizado e rafting, que é a capacidade de compartilhar espaço horizontal ou vertical das barras de ferramentas.  
  
 Embora <xref:System.Windows.Forms.ToolStrip> substitui e adiciona a funcionalidade para o controle nas versões anteriores, <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e o uso futuro, se desejado.  
  
## <a name="features-of-the-toolstrip-controls"></a>Recursos dos controles ToolStrip  
 Use o <xref:System.Windows.Forms.ToolStrip> controlar para:  
  
-   Apresente uma interface do usuário comum entre contêineres.  
  
-   Criar facilmente personalizado, comumente usadas barras de ferramentas que dão suporte avançado de recursos de layout e interface de usuário, como botões de encaixe, rafting, com texto, imagens, botões suspensos e controles, estouro botões e reordenação de tempo de execução de <xref:System.Windows.Forms.ToolStrip> itens.  
  
-   Dê suporte a reordenação de item de tempo de execução e estouro. O recurso de estouro move itens para um menu suspenso quando não há espaço suficiente para exibi-los em um <xref:System.Windows.Forms.ToolStrip>.  
  
-   Dê suporte à aparência e ao comportamento típicos do sistema operacional por meio de um modelo comum de renderização.  
  
-   Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.  
  
-   Arraste itens de um <xref:System.Windows.Forms.ToolStrip> para outro ou em um <xref:System.Windows.Forms.ToolStrip>.  
  
-   Criar editores de tipo de interface de usuário e controles de lista suspensa com layouts avançados em um <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Use o <xref:System.Windows.Forms.ToolStripControlHost> classe para usar outros controles em um <xref:System.Windows.Forms.ToolStrip> e obter <xref:System.Windows.Forms.ToolStrip> funcionalidade para eles.  
  
 Você pode estender a funcionalidade e modificar a aparência e comportamento usando o <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, e <xref:System.Windows.Forms.ToolStripManager> juntamente com o <xref:System.Windows.Forms.ToolStripRenderMode> e <xref:System.Windows.Forms.ToolStripManagerRenderMode> enumerações.  
  
 O <xref:System.Windows.Forms.ToolStrip> controle é altamente configurável e extensível, e fornece muitas propriedades, métodos e eventos para personalizar a aparência e comportamento. Abaixo estão alguns membros importantes:  
  
### <a name="important-toolstrip-members"></a>Membros importantes do ToolStrip  
  
|Nome|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Obtém ou define a margem do contêiner pai de um <xref:System.Windows.Forms.ToolStrip> está encaixado.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Obtém ou define um valor que indica se a operação do tipo "arrastar e soltar" e a reordenação de itens são manipulados pela classe <xref:System.Windows.Forms.ToolStrip> de forma privada.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Obtém ou define um valor que indica como o <xref:System.Windows.Forms.ToolStrip> apresenta seus itens.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Obtém ou define se um <xref:System.Windows.Forms.ToolStripItem> está associada a <xref:System.Windows.Forms.ToolStrip> ou <xref:System.Windows.Forms.ToolStripOverflowButton> ou podem flutuar entre os dois.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Obtém um valor que indica se um <xref:System.Windows.Forms.ToolStripItem> exibe outros itens na lista suspensa lista quando o <xref:System.Windows.Forms.ToolStripItem> é clicado.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Obtém o <xref:System.Windows.Forms.ToolStripItem> que é o botão de estouro para um <xref:System.Windows.Forms.ToolStrip> com o estouro habilitado.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Obtém ou define um <xref:System.Windows.Forms.ToolStripRenderer> usadas para personalizar a aparência e comportamento (e aparência) de um <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Obtém ou define os estilos de pintura a serem aplicados ao <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Gerado quando o <xref:System.Windows.Forms.ToolStrip.Renderer%2A> alterações de propriedade.|  
  
 O <xref:System.Windows.Forms.ToolStrip> flexibilidade do controle é obtida com o uso de um número de classes complementar. Abaixo estão algumas das mais importantes:  
  
### <a name="important-toolstrip-companion-classes"></a>Classes complementares importantes do ToolStrip  
  
|Nome|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.MainMenu> classe.|  
|<xref:System.Windows.Forms.StatusStrip>|Substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> classe.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.ContextMenu> classe.|  
|<xref:System.Windows.Forms.ToolStripItem>|Classe abstrata base que gerencia eventos e o layout para todos os elementos que um <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, ou <xref:System.Windows.Forms.ToolStripDropDown> pode conter.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Fornece um contêiner com um painel em cada lado do formulário em que os controles podem ser organizados de várias maneiras.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Manipula a funcionalidade de pintura para objetos <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Fornece a aparência no estilo do Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Controla a renderização e o reposicionamento de <xref:System.Windows.Forms.ToolStrip> e a mesclagem de objetos <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu> e <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Especifica o estilo de pintura (personalizada, Windows XP ou o Microsoft Office Professional) aplicado a vários <xref:System.Windows.Forms.ToolStrip> objetos contidos em um formulário.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Especifica o estilo de pintura (personalizada, Windows XP ou o Microsoft Office Professional) aplicado a um <xref:System.Windows.Forms.ToolStrip> objeto contido em um formulário.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hospeda outros controles que não sejam especificamente <xref:System.Windows.Forms.ToolStrip> controles mas para a qual você deseja <xref:System.Windows.Forms.ToolStrip> funcionalidade.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Especifica se um <xref:System.Windows.Forms.ToolStripItem> é a ser dispostos na principal <xref:System.Windows.Forms.ToolStrip>, no estouro <xref:System.Windows.Forms.ToolStrip>, ou nenhum deles.|  
  
 Para obter mais informações, consulte [Resumo da tecnologia de ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) e [Arquitetura de controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>

---
title: Visão geral do controle ToolStrip
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741068"
---
# <a name="toolstrip-control-overview-windows-forms"></a>Visão geral do controle ToolStrip (Windows Forms)
O controle de <xref:System.Windows.Forms.ToolStrip> Windows Forms e suas classes associadas fornecem uma estrutura comum para combinar elementos de interface do usuário em barras de ferramentas, barras de status e menus. os controles de <xref:System.Windows.Forms.ToolStrip> oferecem uma rica experiência em tempo de design que inclui ativação in-loco e edição, layout personalizado e rafting, que é a capacidade das barras de ferramentas compartilharem espaço horizontal ou vertical.  
  
 Embora <xref:System.Windows.Forms.ToolStrip> substitua e adicione funcionalidade ao controle em versões anteriores, <xref:System.Windows.Forms.ToolBar> é retido para compatibilidade com versões anteriores e uso futuro, se desejado.  
  
## <a name="features-of-the-toolstrip-controls"></a>Recursos dos controles ToolStrip  
 Use o controle de <xref:System.Windows.Forms.ToolStrip> para:  
  
- Apresente uma interface do usuário comum entre contêineres.  
  
- Crie barras de ferramentas facilmente personalizadas e comumente empregadas que dão suporte a recursos avançados de interface do usuário e layout, como encaixe, rafting, botões com texto e imagens, botões suspensos e controles, botões de estouro e reordenação de tempo de execução de <xref:System.Windows.Forms.ToolStrip> itens.  
  
- Dê suporte a reordenação de item de tempo de execução e estouro. O recurso de estouro move itens para um menu suspenso quando não há espaço suficiente para exibi-los em um <xref:System.Windows.Forms.ToolStrip>.  
  
- Dê suporte à aparência e ao comportamento típicos do sistema operacional por meio de um modelo comum de renderização.  
  
- Manipule eventos de forma consistente em todos os contêineres e os itens contidos da mesma forma que você manipula eventos para outros controles.  
  
- Arraste itens de um <xref:System.Windows.Forms.ToolStrip> para outro ou dentro de um <xref:System.Windows.Forms.ToolStrip>.  
  
- Criar controles suspensos e editores de tipo de interface do usuário com layouts avançados em um <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Use a classe <xref:System.Windows.Forms.ToolStripControlHost> para usar outros controles em um <xref:System.Windows.Forms.ToolStrip> e obter <xref:System.Windows.Forms.ToolStrip> funcionalidade para eles.  
  
 Você pode estender a funcionalidade e modificar a aparência e o comportamento usando o <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>e <xref:System.Windows.Forms.ToolStripManager> juntamente com as enumerações de <xref:System.Windows.Forms.ToolStripRenderMode> e <xref:System.Windows.Forms.ToolStripManagerRenderMode>.  
  
 O controle de <xref:System.Windows.Forms.ToolStrip> é altamente configurável e extensível e fornece muitas propriedades, métodos e eventos para personalizar a aparência e o comportamento. Abaixo estão alguns membros importantes:  
  
### <a name="important-toolstrip-members"></a>Membros importantes do ToolStrip  
  
|Name|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Obtém ou define a qual borda do contêiner pai um <xref:System.Windows.Forms.ToolStrip> está encaixado.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Obtém ou define um valor que indica se a operação do tipo "arrastar e soltar" e a reordenação de itens são manipulados pela classe <xref:System.Windows.Forms.ToolStrip> de forma privada.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Obtém ou define um valor que indica como o <xref:System.Windows.Forms.ToolStrip> cria seus itens.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Obtém ou define se um <xref:System.Windows.Forms.ToolStripItem> está anexado ao <xref:System.Windows.Forms.ToolStrip> ou <xref:System.Windows.Forms.ToolStripOverflowButton> ou pode flutuar entre os dois.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Obtém um valor que indica se um <xref:System.Windows.Forms.ToolStripItem> exibe outros itens em uma lista suspensa quando o <xref:System.Windows.Forms.ToolStripItem> é clicado.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Obtém o <xref:System.Windows.Forms.ToolStripItem> que é o botão de estouro para um <xref:System.Windows.Forms.ToolStrip> com o estouro habilitado.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Obtém ou define um <xref:System.Windows.Forms.ToolStripRenderer> usado para personalizar a aparência e o comportamento (aparência e sensação) de um <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Obtém ou define os estilos de pintura a serem aplicados ao <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Gerado quando a propriedade <xref:System.Windows.Forms.ToolStrip.Renderer%2A> é alterada.|  
  
 A flexibilidade do controle de <xref:System.Windows.Forms.ToolStrip> é obtida com o uso de várias classes complementares. Abaixo estão algumas das mais importantes:  
  
### <a name="important-toolstrip-companion-classes"></a>Classes complementares importantes do ToolStrip  
  
|Name|Descrição|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Substitui e adiciona funcionalidade à classe <xref:System.Windows.Forms.MainMenu>.|  
|<xref:System.Windows.Forms.StatusStrip>|Substitui e adiciona funcionalidade à classe <xref:System.Windows.Forms.StatusBar>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Substitui e adiciona funcionalidade à classe <xref:System.Windows.Forms.ContextMenu>.|  
|<xref:System.Windows.Forms.ToolStripItem>|Classe base abstrata que gerencia eventos e layout para todos os elementos que um <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>ou <xref:System.Windows.Forms.ToolStripDropDown> pode conter.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Fornece um contêiner com um painel em cada lado do formulário em que os controles podem ser organizados de várias maneiras.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Manipula a funcionalidade de pintura para objetos <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Fornece a aparência no estilo do Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Controla a renderização e o reposicionamento de <xref:System.Windows.Forms.ToolStrip> e a mesclagem de objetos <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu> e <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Especifica o estilo de pintura (personalizado, Windows XP ou Microsoft Office Professional) aplicado a vários objetos <xref:System.Windows.Forms.ToolStrip> contidos em um formulário.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Especifica o estilo de pintura (personalizado, Windows XP ou Microsoft Office Professional) aplicado a um objeto <xref:System.Windows.Forms.ToolStrip> contido em um formulário.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Hospeda outros controles que não são especificamente <xref:System.Windows.Forms.ToolStrip> controles, mas para os quais você deseja <xref:System.Windows.Forms.ToolStrip> funcionalidade.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Especifica se um <xref:System.Windows.Forms.ToolStripItem> deve ser disposto no <xref:System.Windows.Forms.ToolStrip>principal, no <xref:System.Windows.Forms.ToolStrip>de estouro ou nenhum deles.|  
  
 Para obter mais informações, consulte [Resumo da tecnologia de ToolStrip](toolstrip-technology-summary.md) e [Arquitetura de controle ToolStrip](toolstrip-control-architecture.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>

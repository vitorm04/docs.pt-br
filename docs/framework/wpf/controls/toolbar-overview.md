---
title: Visão geral de ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 711d55e46fb548787976a1f966c9fbf6dc7f12d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105320"
---
# <a name="toolbar-overview"></a>Visão geral de ToolBar
<xref:System.Windows.Controls.ToolBar> os controles são contêineres para um grupo de comandos ou controles que geralmente são relacionados em sua função. Um <xref:System.Windows.Controls.ToolBar> geralmente contém botões que invocam comandos.  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>Controle ToolBar  
 O <xref:System.Windows.Controls.ToolBar> controle recebe seu nome da organização de semelhante a barra de botões ou outros controles em uma única linha ou coluna. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> os controles fornecem um mecanismo de estouro que coloca os itens que não cabem naturalmente em uma restrição de tamanho <xref:System.Windows.Controls.ToolBar> em uma área de estouro especial. Além disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> controles normalmente são usados com relacionado <xref:System.Windows.Controls.ToolBarTray> controle, que fornece comportamento especial de layout, bem como suporte para iniciada pelo usuário dimensionamento e disposição de barras de ferramentas.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Especificando a posição das ToolBars em uma ToolBarTray  
 Use o <xref:System.Windows.Controls.ToolBar.Band%2A> e <xref:System.Windows.Controls.ToolBar.BandIndex%2A> propriedades para posicionar o <xref:System.Windows.Controls.ToolBar> no <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> indica a posição na qual o <xref:System.Windows.Controls.ToolBar> é colocado dentro de seu pai <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> indica a ordem na qual o <xref:System.Windows.Controls.ToolBar> é colocada em sua faixa. A exemplo a seguir mostra como usa essa propriedade para posicionar <xref:System.Windows.Controls.ToolBar> controles dentro de um <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>ToolBars com itens de estouro  
 Muitas vezes <xref:System.Windows.Controls.ToolBar> controles contêm mais itens do que se adaptam ao tamanho da barra de ferramentas. Quando isso acontece, o <xref:System.Windows.Controls.ToolBar> exibe um botão de estouro. Para ver os itens de estouro, um usuário clica no botão de estouro e os itens são mostrados em uma janela pop-up abaixo o <xref:System.Windows.Controls.ToolBar>. A gráfico a seguir mostra um <xref:System.Windows.Controls.ToolBar> com itens de estouro:  
  
 ![Captura de tela que mostra uma barra de ferramentas com itens de estouro.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Você pode especificar quando um item em uma barra de ferramentas é colocado no painel de estouro definindo a <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> anexado à propriedade <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, ou <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. O exemplo a seguir especifica que os últimos quatro botões na barra de ferramentas sempre devem estar no painel de estouro.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 O <xref:System.Windows.Controls.ToolBar> usa um <xref:System.Windows.Controls.Primitives.ToolBarPanel> e uma <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> em seu <xref:System.Windows.Controls.ControlTemplate>.  O <xref:System.Windows.Controls.Primitives.ToolBarPanel> é responsável pelo layout dos itens na barra de ferramentas.  O <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> é responsável pelo layout dos itens que não se ajustarem a <xref:System.Windows.Controls.ToolBar>. Para obter um exemplo de uma <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ToolBar>, consulte  
  
 [Estilos e modelos de ToolBar](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Moldar os controles em um ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Exemplo da galeria de controles de WPF](https://go.microsoft.com/fwlink/?LinkID=160053)

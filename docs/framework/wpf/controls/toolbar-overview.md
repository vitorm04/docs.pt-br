---
title: Visão geral de ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186612"
---
# <a name="toolbar-overview"></a>Visão geral de ToolBar
<xref:System.Windows.Controls.ToolBar>os controles são recipientes para um grupo de comandos ou controles que são tipicamente relacionados em sua função. Um <xref:System.Windows.Controls.ToolBar> geralmente contém botões que invocam comandos.  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>Controle ToolBar  
 O <xref:System.Windows.Controls.ToolBar> controle leva seu nome a partir do arranjo semelhante à barra de botões ou outros controles em uma única linha ou coluna. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> os controles fornecem um mecanismo de transbordamento que coloca todos os itens <xref:System.Windows.Controls.ToolBar> que não se encaixam naturalmente dentro de uma área de transbordamento especial. Além [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> disso, os controles geralmente <xref:System.Windows.Controls.ToolBarTray> são usados com o controle relacionado, que fornece comportamento de layout especial, bem como suporte para dimensionamento e organização de barras de ferramentas iniciadas pelo usuário.  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Especificando a posição das ToolBars em uma ToolBarTray  
 Use <xref:System.Windows.Controls.ToolBar.Band%2A> as <xref:System.Windows.Controls.ToolBar.BandIndex%2A> propriedades e <xref:System.Windows.Controls.ToolBar> para <xref:System.Windows.Controls.ToolBarTray>posicionar o no . <xref:System.Windows.Controls.ToolBar.Band%2A>indica a posição <xref:System.Windows.Controls.ToolBar> em que o <xref:System.Windows.Controls.ToolBarTray>é colocado dentro de seu pai . <xref:System.Windows.Controls.ToolBar.BandIndex%2A>indica a ordem <xref:System.Windows.Controls.ToolBar> em que o é colocado dentro de sua banda. O exemplo a seguir mostra <xref:System.Windows.Controls.ToolBar> como usar <xref:System.Windows.Controls.ToolBarTray>esta propriedade para colocar controles dentro de um .  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>ToolBars com itens de estouro  
 Muitas <xref:System.Windows.Controls.ToolBar> vezes os controles contêm mais itens do que podem caber no tamanho da barra de ferramentas. Quando isso acontece, o <xref:System.Windows.Controls.ToolBar> exibir um botão de estouro. Para ver os itens de estouro, o usuário clica no botão de estouro e <xref:System.Windows.Controls.ToolBar>os itens são mostrados em uma janela pop-up abaixo da . O gráfico a <xref:System.Windows.Controls.ToolBar> seguir mostra um com itens de estouro:  
  
 ![Captura de tela que mostra uma barra de ferramentas com itens de transbordamento.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Você pode especificar quando um item em uma barra <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> de ferramentas <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>é <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>colocado <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>no painel de estouro definindo a propriedade anexada para , ou . O exemplo a seguir especifica que os últimos quatro botões na barra de ferramentas sempre devem estar no painel de estouro.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 O <xref:System.Windows.Controls.ToolBar> uso <xref:System.Windows.Controls.Primitives.ToolBarPanel> a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> e <xref:System.Windows.Controls.ControlTemplate>a em seu .  O <xref:System.Windows.Controls.Primitives.ToolBarPanel> é responsável pelo layout dos itens na barra de ferramentas.  O <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> é responsável pelo layout dos itens que não <xref:System.Windows.Controls.ToolBar>se encaixam no . Para um exemplo <xref:System.Windows.Controls.ControlTemplate> de <xref:System.Windows.Controls.ToolBar>a para um , ver  
  
 [Estilos e modelos da barra de ferramentas](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Moldar os controles em um ToolBar](how-to-style-controls-on-a-toolbar.md)
- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)

---
title: "Visão geral de painéis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f89ea3308d0e6cffc3ed50809f0e87e7ba854ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="panels-overview"></a>Visão geral de painéis
<xref:System.Windows.Controls.Panel>elementos são componentes que controlam o processamento de elementos, seu tamanho e dimensões, sua posição e a disposição de conteúdo filho. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] oferece inúmeras predefinidos <xref:System.Windows.Controls.Panel> elementos, bem como a capacidade de construir personalizado <xref:System.Windows.Controls.Panel> elementos.  
  
 Este tópico contém as seções a seguir.  
  
-   [A classe do painel](#Panels_view_from_10000_feet)  
  
-   [Membros comuns do elemento de painel](#Panels_declared_members)  
  
-   [Elementos de painel derivados](#Panels_derived_elements)  
  
-   [Painéis de interface do usuário](#Panels_main_UI_elements)  
  
-   [Elementos de painel aninhados](#Panels_nested_panel_elements)  
  
-   [Elementos de painel personalizados](#Panels_custom_panel_elements)  
  
-   [Suporte à localização/globalização](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>   
## <a name="the-panel-class"></a>A classe do painel  
 <xref:System.Windows.Controls.Panel>é a classe base para dar suporte a todos os elementos que fornecem o layout em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Derivado <xref:System.Windows.Controls.Panel> elementos são usados para posicionar e organizar os elementos na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e código.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui um conjunto abrangente de implementações de painel derivadas que possibilita vários layouts complexos. Essas classes derivadas expõem propriedades e métodos que permitem a maioria dos cenários padrão de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Os desenvolvedores que não conseguem encontrar um comportamento de organização filho que atenda às suas necessidades pode criar novos layouts, substituindo o <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> e <xref:System.Windows.FrameworkElement.MeasureOverride%2A> métodos. Para obter mais informações sobre comportamentos de layout personalizados, consulte [Elementos de painel personalizados](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>   
## <a name="panel-common-members"></a>Membros comuns do painel  
 Todos os <xref:System.Windows.Controls.Panel> elementos oferecem suporte a base de dados de dimensionamento e posicionamento propriedades definidas por <xref:System.Windows.FrameworkElement>, incluindo <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, e <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Para obter informações adicionais sobre o posicionamento propriedades definidas por <xref:System.Windows.FrameworkElement>, consulte [alinhamento, margens e visão geral do preenchimento](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md).  
  
 <xref:System.Windows.Controls.Panel>expõe as propriedades adicionais que são de importância fundamental na compreensão e uso de layout. O <xref:System.Windows.Controls.Panel.Background%2A> propriedade é usada para preencher a área entre os limites de um elemento derivado do painel com um <xref:System.Windows.Media.Brush>. <xref:System.Windows.Controls.Panel.Children%2A>representa a coleção de elementos filho que o <xref:System.Windows.Controls.Panel> é composto. <xref:System.Windows.Controls.Panel.InternalChildren%2A>representa o conteúdo do <xref:System.Windows.Controls.Panel.Children%2A> coleção mais esses membros gerados por associação de dados. Ambos consistem em uma <xref:System.Windows.Controls.UIElementCollection> de elementos filho hospedados dentro do pai <xref:System.Windows.Controls.Panel>.  
  
 Painel também expõe um <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> anexado a propriedade que pode ser usada para alcançar a ordem em camadas em um derivado <xref:System.Windows.Controls.Panel>. Membros de um painel <xref:System.Windows.Controls.Panel.Children%2A> coleção com uma maior <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> valor exibido na frente com menos <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> valor. Isso é particularmente útil para painéis, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.Grid> que permitem que os filhos compartilhar o mesmo espaço de coordenada.  
  
 <xref:System.Windows.Controls.Panel>também define o <xref:System.Windows.Controls.Panel.OnRender%2A> método, que pode ser usado para substituir o comportamento de apresentação de padrão de um <xref:System.Windows.Controls.Panel>.  
  
#### <a name="attached-properties"></a>Propriedades anexadas  
 Elementos do painel derivados fazem amplo uso de propriedades anexadas. Uma propriedade anexada é uma forma especializada de propriedade de dependência que não tem o “wrapper” de propriedade [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] convencional. As propriedades anexadas têm uma sintaxe especializada em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], que pode ser vista em vários dos exemplos a seguir.  
  
 Uma das finalidades de uma propriedade anexada é permitir que os elementos filho armazenem valores exclusivos de uma propriedade que, na verdade, é definida por um elemento pai. Uma aplicação dessa funcionalidade é fazer com que os elementos filho informem o pai como desejam ser apresentados na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], o que é extremamente útil para o layout do aplicativo. Para obter mais informações, consulte [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>   
## <a name="derived-panel-elements"></a>Elementos de painel derivados  
 Muitos objetos derivam <xref:System.Windows.Controls.Panel>, mas nem todos eles são destinados para uso como provedores de layout de raiz. Há seis classes de painel definido (<xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, e <xref:System.Windows.Controls.WrapPanel>) que são projetados especificamente para criação de aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Cada elemento de painel encapsula sua própria funcionalidade especial, como visto na tabela a seguir.  
  
|Nome de elementos|Painel de interface do usuário?|Descrição|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Sim|Define uma área na qual é possível posicionar explicitamente elementos filhos usando coordenadas relativas ao <xref:System.Windows.Controls.Canvas> área.|  
|<xref:System.Windows.Controls.DockPanel>|Sim|Define uma área dentro da qual você pode organizar elementos filho horizontal ou verticalmente, uns em relação aos outros.|  
|<xref:System.Windows.Controls.Grid>|Sim|Define uma área de grade flexível que consiste em colunas e linhas. Elementos filho de um <xref:System.Windows.Controls.Grid> pode ser posicionada usando precisamente o <xref:System.Windows.FrameworkElement.Margin%2A> propriedade.|  
|<xref:System.Windows.Controls.StackPanel>|Sim|Organiza elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Não|Manipula o layout dos botões da guia em um <xref:System.Windows.Controls.TabControl>.|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Não|Organiza o conteúdo em um <xref:System.Windows.Controls.ToolBar> controle.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Não|<xref:System.Windows.Controls.Primitives.UniformGrid>é usado para organizar filhos em uma grade com todos os tamanhos de célula igual.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Não|Fornece uma classe base para painéis que podem “virtualizar” sua coleção filho.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Sim|Organiza e virtualiza o conteúdo em uma única linha que é orientada horizontal ou verticalmente.|  
|<xref:System.Windows.Controls.WrapPanel>|Sim|<xref:System.Windows.Controls.WrapPanel>Posiciona elementos filho em ordem sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa de conteúdo. Classificação subsequente acontece sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da <xref:System.Windows.Controls.WrapPanel.Orientation%2A> propriedade.|  
  
<a name="Panels_main_UI_elements"></a>   
## <a name="user-interface-panels"></a>Painéis de interface do usuário  
 Há seis classes de painel disponíveis no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que são otimizados para dar suporte a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] cenários: <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>, e <xref:System.Windows.Controls.WrapPanel>. Esses elementos de painel são fáceis de usar, versáteis e extensíveis o suficiente para a maioria dos aplicativos.  
  
 Cada derivado <xref:System.Windows.Controls.Panel> elemento trata as restrições de dimensionamento de forma diferente. Noções básicas sobre como um <xref:System.Windows.Controls.Panel> identificadores restrições no sentido horizontal ou vertical podem tornar layout mais previsível.  
  
|**Nome do Painel**|**Dimensão x**|**Dimensão y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Restrito ao conteúdo|Restrito ao conteúdo|  
|<xref:System.Windows.Controls.DockPanel>|Restrito|Restrito|  
|<xref:System.Windows.Controls.StackPanel>(Orientação vertical)|Restrito|Restrito ao conteúdo|  
|<xref:System.Windows.Controls.StackPanel>(Orientação horizontal)|Restrito ao conteúdo|Restrito|  
|<xref:System.Windows.Controls.Grid>|Restrito|Restrita, exceto em casos onde <xref:System.Windows.GridUnitType.Auto> se aplicam a linhas e colunas|  
|<xref:System.Windows.Controls.WrapPanel>|Restrito ao conteúdo|Restrito ao conteúdo|  
  
 Encontre abaixo descrições mais detalhadas e exemplos de uso de cada um desses elementos.  
  
<a name="Panels_overview_Canvas_subsection"></a>   
### <a name="canvas"></a>Tela  
 O <xref:System.Windows.Controls.Canvas> elemento habilita o posicionamento de conteúdo de acordo com absoluto *x -* e *y -*coordenadas. Os elementos podem ser desenhados em um local exclusivo; ou, se os elementos ocupam as mesmas coordenadas, a ordem em que aparecem na marcação determina a ordem na qual os elementos são desenhados.  
  
 <xref:System.Windows.Controls.Canvas>fornece o suporte de layout mais flexível de qualquer <xref:System.Windows.Controls.Panel>. Propriedades de altura e largura são usadas para definir a área da tela, e elementos dentro recebem absolutas coordenadas relativas à área do pai <xref:System.Windows.Controls.Canvas>. Propriedades, quatro anexadas <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> e <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>, permitir que o controle refinado de posicionamento de objeto dentro de um <xref:System.Windows.Controls.Canvas>, permitindo que o desenvolvedor posicionar e organizar os elementos com precisão na tela.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds em uma tela  
 <xref:System.Windows.Controls.Canvas>pode posicionar elementos filho em qualquer posição na tela, até mesmo em coordenadas que estão fora de seu próprio definido <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A>. Além disso, <xref:System.Windows.Controls.Canvas> não é afetado pelo tamanho de seus filhos. Como resultado, é possível para um elemento filho overdraw outros elementos fora do retângulo delimitador do pai <xref:System.Windows.Controls.Canvas>. O comportamento padrão de um <xref:System.Windows.Controls.Canvas> é permitir que os filhos a ser desenhada fora dos limites do pai <xref:System.Windows.Controls.Canvas>. Se esse comportamento é desejável, o <xref:System.Windows.UIElement.ClipToBounds%2A> propriedade pode ser definida como `true`. Isso faz com que <xref:System.Windows.Controls.Canvas> para recortar para seu próprio tamanho. <xref:System.Windows.Controls.Canvas>é o elemento de layout somente que permite que os filhos a ser desenhada fora dos seus limites.  
  
 Esse comportamento é ilustrado de forma gráfica na [Amostra de comparação de propriedades de largura](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
#### <a name="defining-and-using-a-canvas"></a>Definindo e usando uma tela  
 Um <xref:System.Windows.Controls.Canvas> pode ser instanciado usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou código. O exemplo a seguir demonstra como usar <xref:System.Windows.Controls.Canvas> para posicionar conteúdo absolutamente. Esse código produz três quadrados de 100 pixels. O primeiro quadrado é vermelho e sua posição superior esquerda (*X, Y*) é especificada como (0, 0). O segundo quadrado é verde e sua posição superior esquerda é (100, 100), logo abaixo e à direita do primeiro quadrado. O terceiro quadrado é azul e sua posição superior esquerda é (50, 50), abrangendo o quadrante inferior direito do primeiro quadrado e o quadrante superior esquerdo do segundo. Como o terceiro quadrado é disposto por último, ele parece estar sobre os outros dois quadrados – ou seja, as partes sobrepostas assumem a cor da terceira caixa.  
  
 [!code-csharp[CanvasOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento Canvas típico.](../../../../docs/framework/wpf/controls/media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>   
### <a name="dockpanel"></a>DockPanel  
 O <xref:System.Windows.Controls.DockPanel> elemento usa o <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriedade anexada definido em elementos de conteúdo filho para posicionar o conteúdo ao longo das bordas de um contêiner. Quando <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> é definido como <xref:System.Windows.Controls.Dock.Top> ou <xref:System.Windows.Controls.Dock.Bottom>, posiciona os elementos filho acima ou abaixo do outro. Quando <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> é definido como <xref:System.Windows.Controls.Dock.Left> ou <xref:System.Windows.Controls.Dock.Right>, posiciona os elementos filho para a esquerda ou direita do outro. O <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriedade determina a posição do elemento final adicionado como um filho de um <xref:System.Windows.Controls.DockPanel>.  
  
 Você pode usar <xref:System.Windows.Controls.DockPanel> para a posição de um grupo de controles relacionados, como um conjunto de botões. Como alternativa, é possível usá-lo para criar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] com “painéis”, semelhante àquela encontrada no [!INCLUDE[TLA#tla_outlook](../../../../includes/tlasharptla-outlook-md.md)].  
  
#### <a name="sizing-to-content"></a>Dimensionando para o conteúdo  
 Se seu <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades não forem especificadas, <xref:System.Windows.Controls.DockPanel> tamanhos para seu conteúdo. O tamanho pode aumentar ou diminuir para acomodar o tamanho de seus elementos filho. No entanto, quando essas propriedades são especificadas e não existe mais espaço para o próximo elemento filho especificado, <xref:System.Windows.Controls.DockPanel> não exibirá esse elemento filho ou elementos filho subsequentes e não medidas elementos filho subsequentes.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Por padrão, o último filho de um <xref:System.Windows.Controls.DockPanel> elemento "preencherá" demais, espaço não alocado. Se esse comportamento não for desejado, defina o <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriedade `false`.  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definindo e usando um DockPanel  
 O exemplo a seguir demonstra como particionar o espaço usando um <xref:System.Windows.Controls.DockPanel>. Cinco <xref:System.Windows.Controls.Border> elementos são adicionados como filhos de um pai <xref:System.Windows.Controls.DockPanel>. Cada uma usa outra propriedade de posicionamento de um <xref:System.Windows.Controls.DockPanel> ao espaço da partição. O elemento final “preenche” o espaço restante não alocado.  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um cenário de DockPanel típico.](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>   
### <a name="grid"></a>Grade  
 O <xref:System.Windows.Controls.Grid> elemento mescla a funcionalidade de um controle de dados tabulares e de posicionamento absoluto. Um <xref:System.Windows.Controls.Grid> permite facilmente os elementos de estilo e de posição. <xref:System.Windows.Controls.Grid>permite que você defina a linha flexível e agrupamentos de colunas e ainda fornece um mecanismo para compartilhar informações de dimensionamento entre vários <xref:System.Windows.Controls.Grid> elementos.  
  
#### <a name="how-is-grid-different-from-table"></a>Qual a diferença entre uma grade e uma tabela?  
 <xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> compartilham funcionalidade comum, mas cada um é mais adequada para cenários diferentes. Um <xref:System.Windows.Documents.Table> foi projetado para uso em conteúdo de fluxo (consulte [visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md) para obter mais informações sobre o conteúdo de fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro de um <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Table> dá suporte ao fluxo de conteúdo comportamentos como paginação, refluxo de coluna e seleção de conteúdo enquanto um <xref:System.Windows.Controls.Grid> não. Um <xref:System.Windows.Controls.Grid> por outro lado, é melhor utilizado fora de um <xref:System.Windows.Documents.FlowDocument> por muitas razões incluindo <xref:System.Windows.Controls.Grid> adiciona elementos com base em um índice de linha e coluna, <xref:System.Windows.Documents.Table> não. O <xref:System.Windows.Controls.Grid> elemento permite que o conteúdo filho, permitindo que mais de um elemento exista em uma única "célula." em camadas <xref:System.Windows.Documents.Table>não dá suporte a camadas. Elementos filho de um <xref:System.Windows.Controls.Grid> pode ser posicionado absolutamente relativas à área de seus limites de "célula". <xref:System.Windows.Documents.Table>não oferece suporte a esse recurso. Por fim, um <xref:System.Windows.Controls.Grid> é leve do que um <xref:System.Windows.Documents.Table>.  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Comportamento de dimensionamento de colunas e linhas  
 Colunas e linhas definidas em um <xref:System.Windows.Controls.Grid> pode tirar proveito do <xref:System.Windows.GridUnitType.Star> dimensionamento para distribuir o espaço restante proporcionalmente. Quando <xref:System.Windows.GridUnitType.Star> é selecionado como a altura ou largura de uma linha ou coluna, que a coluna ou linha recebe uma proporção ponderada de espaço restante disponível. Isso é, em oposição à <xref:System.Windows.GridUnitType.Auto>, que distribui espaço uniformemente com base no tamanho do conteúdo dentro de uma coluna ou linha. Esse valor é expresso como `*` ou `2*` ao usar o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. No primeiro caso, a linha ou a coluna receberia uma vez o espaço disponível, no segundo caso, duas vezes e assim por diante. Combinando essa técnica para distribuir proporcionalmente espaço com uma <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> valor `Stretch` é possível para o espaço de layout de partição em porcentagem do espaço de tela. <xref:System.Windows.Controls.Grid>é o painel de layout somente que pode distribuir espaço dessa maneira.  
  
#### <a name="defining-and-using-a-grid"></a>Definindo e usando uma grade  
 O exemplo a seguir demonstra como compilar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] semelhante àquela encontrada na caixa de diálogo Executar disponíveis no menu Iniciar do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento Grid típico.](../../../../docs/framework/wpf/controls/media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>   
### <a name="stackpanel"></a>StackPanel  
 Um <xref:System.Windows.Controls.StackPanel> permite que você "pilha" elementos em uma direção atribuído. A direção padrão da pilha é vertical. O <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade pode ser usada para controlar o fluxo de conteúdo.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Embora <xref:System.Windows.Controls.DockPanel> pode também "pilha" elementos filho, <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Controls.StackPanel> não produzem resultados análogos em alguns cenários de uso. Por exemplo, a ordem dos elementos filho pode afetar seu tamanho em um <xref:System.Windows.Controls.DockPanel> , mas não em um <xref:System.Windows.Controls.StackPanel>. Isso ocorre porque <xref:System.Windows.Controls.StackPanel> medidas na direção de empilhamento em <xref:System.Double.PositiveInfinity>, enquanto <xref:System.Windows.Controls.DockPanel> mede somente o tamanho disponível.  
  
 O exemplo a seguir demonstra essa diferença básica.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 A diferença no comportamento de renderização pode ser vista nesta imagem.  
  
 ![Captura de tela: StackPanel vs. Captura de tela de DockPanel](../../../../docs/framework/wpf/controls/media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definindo e usando um StackPanel  
 O exemplo a seguir demonstra como usar um <xref:System.Windows.Controls.StackPanel> para criar um conjunto de botões posicionado verticalmente. Para obter o posicionamento horizontal, defina o <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento StackPanel típico.](../../../../docs/framework/wpf/controls/media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>   
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também fornece uma variação de <xref:System.Windows.Controls.StackPanel> elemento que automaticamente "virtualiza" conteúdo filho de associação de dados. Nesse contexto, a palavra virtualizar refere-se a uma técnica pela qual um subconjunto de elementos é gerado de um grande número de itens de dados com base em quais itens estão visíveis na tela. É intensivo, tanto em termos de memória quanto de processador, gerar um grande número de elementos de interface do usuário quando apenas alguns podem estar na tela em um determinado momento. <xref:System.Windows.Controls.VirtualizingStackPanel>(por meio da funcionalidade fornecida pelo <xref:System.Windows.Controls.VirtualizingPanel>) calcula itens visíveis e funciona com o <xref:System.Windows.Controls.ItemContainerGenerator> de um <xref:System.Windows.Controls.ItemsControl> (como <xref:System.Windows.Controls.ListBox> ou <xref:System.Windows.Controls.ListView>) apenas para criar elementos de itens visíveis.  
  
 O <xref:System.Windows.Controls.VirtualizingStackPanel> elemento é automaticamente definido como os itens de host para controles, como o <xref:System.Windows.Controls.ListBox>. Ao hospedar um dado associado a coleção, conteúdo é automaticamente virtualizado, desde que o conteúdo está dentro dos limites de um <xref:System.Windows.Controls.ScrollViewer>. Isso melhora o desempenho consideravelmente ao hospedar vários itens filho.  
  
 A marcação a seguir demonstra como usar um <xref:System.Windows.Controls.VirtualizingStackPanel> como um host de itens. O <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty%2A?displayProperty=nameWithType> propriedade anexada deve ser definida como `true` (padrão) para virtualização ocorra.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>   
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>é usado para posicionar elementos filho em ordem sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha quando atingir o limite de seu contêiner pai. O conteúdo pode tem uma orientação horizontal ou vertical. <xref:System.Windows.Controls.WrapPanel>é útil para transferir simples [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] cenários. Também pode ser usado para aplicar um dimensionamento uniforme a todos os seus elementos filho.  
  
 O exemplo a seguir demonstra como criar um <xref:System.Windows.Controls.WrapPanel> exibir <xref:System.Windows.Controls.Button> controles que encapsulam quando eles atingirem a borda do contêiner.  
  
 [!code-cpp[WrapPanel_Intro#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento WrapPanel típico.](../../../../docs/framework/wpf/controls/media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>   
## <a name="nested-panel-elements"></a>Elementos de painel aninhados  
 <xref:System.Windows.Controls.Panel>elementos podem ser aninhados dentro do outro para produzir layouts complexos. Isso pode ser muito útil em situações onde um <xref:System.Windows.Controls.Panel> é ideal para uma parte de um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], mas poderá não atender às necessidades de uma parte diferente de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Não há nenhum limite prático para a quantidade de aninhamento à qual o aplicativo pode dar suporte; no entanto, de modo geral, é melhor limitar o aplicativo a usar somente os painéis que são realmente necessários para o layout desejado. Em muitos casos, um <xref:System.Windows.Controls.Grid> elemento pode ser usado em vez de painéis aninhados devido a sua flexibilidade como um contêiner de layout. Isso pode aumentar o desempenho do aplicativo mantendo os elementos desnecessários fora da árvore.  
  
 O exemplo a seguir demonstra como criar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que se aproveita de aninhadas <xref:System.Windows.Controls.Panel> elementos para alcançar um layout específico. Nesse caso específico, um <xref:System.Windows.Controls.DockPanel> elemento é usado para fornecer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] estrutura e aninhados <xref:System.Windows.Controls.StackPanel> elementos, um <xref:System.Windows.Controls.Grid>e um <xref:System.Windows.Controls.Canvas> são usados para posicionar elementos filhos precisamente dentro do pai <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-csharp[Nested_Panels#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Uma interface do usuário que aproveita os painéis aninhados.](../../../../docs/framework/wpf/controls/media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>   
## <a name="custom-panel-elements"></a>Elementos de painel personalizados  
 Enquanto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fornece um conjunto de controles de layout flexível de layout personalizado comportamentos também podem ser obtidos por meio da substituição de <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> e <xref:System.Windows.FrameworkElement.MeasureOverride%2A> métodos. O dimensionamento e o posicionamento personalizados podem ser feitos com a definição de novos comportamentos de posicionamento nesses métodos de substituição.  
  
 Da mesma forma, o comportamentos de layout personalizado com base em classes derivadas (como <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.Grid>) podem ser definidas por meio da substituição seus <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> e <xref:System.Windows.FrameworkElement.MeasureOverride%2A> métodos.  
  
 A marcação a seguir demonstra como criar um personalizado <xref:System.Windows.Controls.Panel> elemento. Essa nova <xref:System.Windows.Controls.Panel>, definida como `PlotPanel`, oferece suporte ao posicionamento dos elementos filho com o uso de embutido *x -* e *y -*coordenadas. Neste exemplo, um <xref:System.Windows.Shapes.Rectangle> (não mostrado) do elemento é posicionado no ponto de plotagem 50 (*x*) e 50 (*y*).  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Para exibir uma implementação mais complexa de painel personalizado, consulte [Criar uma amostra de painel de encapsulamento com conteúdo personalizado](http://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>   
## <a name="localizationglobalization-support"></a>Suporte à localização/globalização  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a vários recursos que ajudam na criação de uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localizável.  
  
 Suportam nativo a todos os elementos do painel de <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade, que pode ser usada para dinamicamente novamente fluxo de conteúdo com base nas configurações de idioma ou localidade do usuário. Para obter mais informações, consulte <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 O <xref:System.Windows.Window.SizeToContent%2A> propriedade fornece um mecanismo que permite que os desenvolvedores de aplicativos prever as necessidades de localizado [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Usando o <xref:System.Windows.SizeToContent.WidthAndHeight> valor dessa propriedade, um pai <xref:System.Windows.Window> sempre tamanhos dinamicamente para ajustar o conteúdo e não é restrito por restrições de altura ou largura artificiais.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>, e <xref:System.Windows.Controls.StackPanel> são todas as boas opções para localizável [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. <xref:System.Windows.Controls.Canvas>é não é uma boa opção, no entanto, porque ele posiciona conteúdo absolutamente, tornando difícil localizar.  
  
 Para obter mais informações sobre como criar aplicativos do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]s localizáveis, consulte a [Visão geral do uso de layout automático](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Exemplo de galeria de layout do WPF](http://go.microsoft.com/fwlink/?LinkID=160054)  
 [Layout](../../../../docs/framework/wpf/advanced/layout.md)  
 [Exemplo da galeria de controles de WPF](http://go.microsoft.com/fwlink/?LinkID=160053)  
 [Visão geral de alinhamento, margens e preenchimento](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Criar um exemplo de painel de disposição de conteúdo personalizado](http://go.microsoft.com/fwlink/?LinkID=159979)  
 [Visão geral das propriedades anexadas](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [Visão geral do uso de layout automático](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [Layout e design](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)

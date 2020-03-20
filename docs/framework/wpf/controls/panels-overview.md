---
title: Visão geral de painéis
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7810bfbf4f5bedf51e0797a4b9017f589e0b0a8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187587"
---
# <a name="panels-overview"></a>Visão geral de painéis
<xref:System.Windows.Controls.Panel>elementos são componentes que controlam a renderização dos elementos — seu tamanho e dimensões, sua posição e o arranjo de seu conteúdo filho. O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma série <xref:System.Windows.Controls.Panel> de elementos predefinidos, bem como a capacidade de construir elementos personalizados. <xref:System.Windows.Controls.Panel>  
  
 Este tópico inclui as seções a seguir.  
  
- [A classe do painel](#Panels_view_from_10000_feet)  
  
- [Membros comuns do elemento de painel](#Panels_declared_members)  
  
- [Elementos de painel derivados](#Panels_derived_elements)  
  
- [Painéis de interface do usuário](#Panels_main_UI_elements)  
  
- [Elementos de painel aninhados](#Panels_nested_panel_elements)  
  
- [Elementos de painel personalizados](#Panels_custom_panel_elements)  
  
- [Suporte à localização/globalização](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>A classe do painel  
 <xref:System.Windows.Controls.Panel>é a classe base para todos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]os elementos que fornecem suporte ao layout em . Elementos <xref:System.Windows.Controls.Panel> derivados são usados [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para posicionar e organizar elementos dentro e código.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui um conjunto abrangente de implementações de painel derivadas que possibilita vários layouts complexos. Essas classes derivadas expõem propriedades e métodos que permitem a maioria dos cenários padrão de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Desenvolvedores que não conseguem encontrar um comportamento de arranjo infantil que atenda às suas necessidades podem criar novos layouts substituindo os <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos e. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> Para obter mais informações sobre comportamentos de layout personalizados, consulte [Elementos de painel personalizados](#Panels_custom_panel_elements).  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Membros comuns do painel  
 Todos <xref:System.Windows.Controls.Panel> os elementos suportam as <xref:System.Windows.FrameworkElement>propriedades <xref:System.Windows.FrameworkElement.Height%2A>de <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>dimensionamento e posicionamento de base definidas por , incluindo , , <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, , <xref:System.Windows.FrameworkElement.Margin%2A>e <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Para obter informações adicionais <xref:System.Windows.FrameworkElement>sobre as propriedades de posicionamento definidas por , consulte ['Alinhamento, Margens e Visão geral de preenchimento'.](../advanced/alignment-margins-and-padding-overview.md)  
  
 <xref:System.Windows.Controls.Panel>expõe propriedades adicionais que são de importância crítica na compreensão e uso do layout. A <xref:System.Windows.Controls.Panel.Background%2A> propriedade é usada para preencher a área entre os <xref:System.Windows.Media.Brush>limites de um elemento de painel derivado com um . <xref:System.Windows.Controls.Panel.Children%2A>representa a coleção infantil de <xref:System.Windows.Controls.Panel> elementos que o é composto. <xref:System.Windows.Controls.Panel.InternalChildren%2A>representa o conteúdo <xref:System.Windows.Controls.Panel.Children%2A> da coleção mais os membros gerados pela vinculação de dados. Ambos consistem <xref:System.Windows.Controls.UIElementCollection> em um de elementos infantis hospedados dentro do pai <xref:System.Windows.Controls.Panel>.  
  
 O painel também <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> expõe uma propriedade anexada que pode ser <xref:System.Windows.Controls.Panel>usada para alcançar a ordem em camadas em um derivado . Membros da coleção <xref:System.Windows.Controls.Panel.Children%2A> de um <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> painel com um valor mais <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> alto aparecem na frente daqueles com um valor mais baixo. Isso é particularmente útil <xref:System.Windows.Controls.Canvas> para <xref:System.Windows.Controls.Grid> painéis como e que permitem que as crianças compartilhem o mesmo espaço de coordenadas.  
  
 <xref:System.Windows.Controls.Panel>também define <xref:System.Windows.Controls.Panel.OnRender%2A> o método, que pode ser usado para <xref:System.Windows.Controls.Panel>substituir o comportamento de apresentação padrão de um .  
  
#### <a name="attached-properties"></a>Propriedades anexadas  
 Elementos do painel derivados fazem amplo uso de propriedades anexadas. Uma propriedade anexada é uma forma especializada de propriedade de dependência que não tem o "wrapper" de propriedade de tempo de execução comum convencional (CLR). As propriedades anexadas têm uma sintaxe especializada em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], que pode ser vista em vários dos exemplos a seguir.  
  
 Uma das finalidades de uma propriedade anexada é permitir que os elementos filho armazenem valores exclusivos de uma propriedade que, na verdade, é definida por um elemento pai. Uma aplicação dessa funcionalidade é fazer com que os elementos filho informem o pai como desejam ser apresentados na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], o que é extremamente útil para o layout do aplicativo. Para obter mais informações, consulte [Visão geral das propriedades anexadas](../advanced/attached-properties-overview.md).  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>Elementos de painel derivados  
 Muitos objetos <xref:System.Windows.Controls.Panel>derivam, mas nem todos eles são destinados a serem usados como provedores de layout raiz. Existem seis classes<xref:System.Windows.Controls.Canvas>de <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>painéis definidas <xref:System.Windows.Controls.StackPanel>( , , , , <xref:System.Windows.Controls.VirtualizingStackPanel>e <xref:System.Windows.Controls.WrapPanel>) que são projetadas especificamente para criar aplicação [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Cada elemento de painel encapsula sua própria funcionalidade especial, como visto na tabela a seguir.  
  
|Nome do elemento|Painel de interface do usuário?|Descrição|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Sim|Define uma área dentro da qual você pode posicionar explicitamente <xref:System.Windows.Controls.Canvas> elementos infantis por coordenadas em relação à área.|  
|<xref:System.Windows.Controls.DockPanel>|Sim|Define uma área dentro da qual você pode organizar elementos filho horizontal ou verticalmente, uns em relação aos outros.|  
|<xref:System.Windows.Controls.Grid>|Sim|Define uma área de grade flexível que consiste em colunas e linhas. Elementos infantis <xref:System.Windows.Controls.Grid> de um pode <xref:System.Windows.FrameworkElement.Margin%2A> ser posicionado precisamente usando a propriedade.|  
|<xref:System.Windows.Controls.StackPanel>|Sim|Organiza elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|Não|Lida com o layout dos <xref:System.Windows.Controls.TabControl>botões de guia em um .|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Não|Organiza o conteúdo <xref:System.Windows.Controls.ToolBar> dentro de um controle.|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|Não|<xref:System.Windows.Controls.Primitives.UniformGrid>é usado para organizar crianças em uma grade com todos os tamanhos de células iguais.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Não|Fornece uma classe base para painéis que podem “virtualizar” sua coleção filho.|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|Sim|Organiza e virtualiza o conteúdo em uma única linha que é orientada horizontal ou verticalmente.|  
|<xref:System.Windows.Controls.WrapPanel>|Sim|<xref:System.Windows.Controls.WrapPanel>posiciona elementos filho na posição seqüencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa de contenção. A encomenda subseqüente acontece sequencialmente de cima para baixo <xref:System.Windows.Controls.WrapPanel.Orientation%2A> ou da direita para a esquerda, dependendo do valor da propriedade.|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>Painéis de interface do usuário  
 Há seis classes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] painéis disponíveis [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que <xref:System.Windows.Controls.Canvas>são <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid>otimizadas para apoiar cenários: , , , <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.VirtualizingStackPanel>e <xref:System.Windows.Controls.WrapPanel>. Esses elementos de painel são fáceis de usar, versáteis e extensíveis o suficiente para a maioria dos aplicativos.  
  
 Cada elemento <xref:System.Windows.Controls.Panel> derivado trata as restrições de dimensionamento de forma diferente. Entender como <xref:System.Windows.Controls.Panel> um lida com restrições na direção horizontal ou vertical pode tornar o layout mais previsível.  
  
|**Nome do painel**|**Dimensão x**|**Dimensão y**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|Restrito ao conteúdo|Restrito ao conteúdo|  
|<xref:System.Windows.Controls.DockPanel>|Restrito|Restrito|  
|<xref:System.Windows.Controls.StackPanel>(Orientação Vertical)|Restrito|Restrito ao conteúdo|  
|<xref:System.Windows.Controls.StackPanel>(Orientação Horizontal)|Restrito ao conteúdo|Restrito|  
|<xref:System.Windows.Controls.Grid>|Restrito|Constrangido, <xref:System.Windows.GridUnitType.Auto> exceto nos casos em que se aplicam a linhas e colunas|  
|<xref:System.Windows.Controls.WrapPanel>|Restrito ao conteúdo|Restrito ao conteúdo|  
  
 Encontre abaixo descrições mais detalhadas e exemplos de uso de cada um desses elementos.  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>Tela  
 O <xref:System.Windows.Controls.Canvas> elemento permite o posicionamento do conteúdo de acordo com as coordenadas *absolutas x* e *y.* Os elementos podem ser desenhados em um local exclusivo; ou, se os elementos ocupam as mesmas coordenadas, a ordem em que aparecem na marcação determina a ordem na qual os elementos são desenhados.  
  
 <xref:System.Windows.Controls.Canvas>fornece o suporte de <xref:System.Windows.Controls.Panel>layout mais flexível de qualquer . As propriedades de altura e largura são usadas para definir a área da tela, e <xref:System.Windows.Controls.Canvas>os elementos dentro são atribuídos coordenadas absolutas em relação à área do pai . Quatro propriedades <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType>anexadas, <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType>e permitem um controle fino <xref:System.Windows.Controls.Canvas>da colocação do objeto dentro de um, permitindo que o desenvolvedor posicione e organize elementos precisamente na tela.  
  
#### <a name="cliptobounds-within-a-canvas"></a>ClipToBounds em uma tela  
 <xref:System.Windows.Controls.Canvas>pode posicionar elementos infantis em qualquer posição na tela, mesmo <xref:System.Windows.FrameworkElement.Height%2A> em <xref:System.Windows.FrameworkElement.Width%2A>coordenadas que estão fora de sua própria definição e . Além disso, <xref:System.Windows.Controls.Canvas> não é afetado pelo tamanho de seus filhos. Como resultado, é possível que um elemento filho sobretire outros elementos fora <xref:System.Windows.Controls.Canvas>do retângulo delimitador do pai . O comportamento padrão <xref:System.Windows.Controls.Canvas> de a é permitir que as crianças sejam desenhadas fora dos limites dos pais <xref:System.Windows.Controls.Canvas>. Se esse comportamento for <xref:System.Windows.UIElement.ClipToBounds%2A> indesejável, a `true`propriedade pode ser definida como . Isso <xref:System.Windows.Controls.Canvas> faz com que o clipe seja do seu próprio tamanho. <xref:System.Windows.Controls.Canvas>é o único elemento de layout que permite que as crianças sejam desenhadas fora de seus limites.  
  
 Esse comportamento é ilustrado de forma gráfica na [Amostra de comparação de propriedades de largura](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).  
  
#### <a name="defining-and-using-a-canvas"></a>Definindo e usando uma tela  
 A <xref:System.Windows.Controls.Canvas> pode ser instanciado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] simplesmente usando ou código. O exemplo a seguir <xref:System.Windows.Controls.Canvas> demonstra como usar para posicionar absolutamente o conteúdo. Esse código produz três quadrados de 100 pixels. O primeiro quadrado é vermelho e sua posição superior esquerda (*X, Y*) é especificada como (0, 0). O segundo quadrado é verde e sua posição superior esquerda é (100, 100), logo abaixo e à direita do primeiro quadrado. O terceiro quadrado é azul e sua posição superior esquerda é (50, 50), abrangendo o quadrante inferior direito do primeiro quadrado e o quadrante superior esquerdo do segundo. Como o terceiro quadrado é disposto por último, ele parece estar sobre os outros dois quadrados – ou seja, as partes sobrepostas assumem a cor da terceira caixa.  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento típico do Canvas.](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 O <xref:System.Windows.Controls.DockPanel> elemento <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> usa a propriedade anexada como definido em elementos de conteúdo infantil para posicionar o conteúdo ao longo das bordas de um recipiente. Quando <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> é <xref:System.Windows.Controls.Dock.Top> definido <xref:System.Windows.Controls.Dock.Bottom>ou , posiciona elementos infantis acima ou abaixo do outro. Quando <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> é <xref:System.Windows.Controls.Dock.Left> definido <xref:System.Windows.Controls.Dock.Right>ou , posiciona elementos infantis à esquerda ou à direita uns dos outros. A <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriedade determina a posição do elemento final <xref:System.Windows.Controls.DockPanel>adicionado como filho de um .  
  
 Você pode <xref:System.Windows.Controls.DockPanel> usar para posicionar um grupo de controles relacionados, como um conjunto de botões. Alternativamente, você pode usá-lo para [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]criar um "paned", semelhante ao encontrado no Microsoft Outlook.  
  
#### <a name="sizing-to-content"></a>Dimensionando para o conteúdo  
 Se <xref:System.Windows.FrameworkElement.Height%2A> suas <xref:System.Windows.FrameworkElement.Width%2A> propriedades não forem especificadas, <xref:System.Windows.Controls.DockPanel> tamanhos para o seu conteúdo. O tamanho pode aumentar ou diminuir para acomodar o tamanho de seus elementos filho. No entanto, quando essas propriedades são especificadas e não há <xref:System.Windows.Controls.DockPanel> mais espaço para o próximo elemento filho especificado, não exibe esse elemento filho ou elementos subsequentes da criança e não mede elementos subsequentes da criança.  
  
#### <a name="lastchildfill"></a>LastChildFill  
 Por padrão, o último <xref:System.Windows.Controls.DockPanel> filho de um elemento "preencherá" o espaço restante e não alocado. Se esse comportamento não for <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> desejado, `false`defina a propriedade para .  
  
#### <a name="defining-and-using-a-dockpanel"></a>Definindo e usando um DockPanel  
 O exemplo a seguir demonstra <xref:System.Windows.Controls.DockPanel>como particionar o espaço usando um . Cinco <xref:System.Windows.Controls.Border> elementos são adicionados <xref:System.Windows.Controls.DockPanel>como filhos de um pai . Cada um usa uma <xref:System.Windows.Controls.DockPanel> propriedade de posicionamento diferente de um espaço de partição. O elemento final “preenche” o espaço restante não alocado.  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um cenário típico do DockPanel.](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Grade  
 O <xref:System.Windows.Controls.Grid> elemento mescla a funcionalidade de um posicionamento absoluto e controle de dados tabular. A <xref:System.Windows.Controls.Grid> permite que você posicione e estilize facilmente elementos. <xref:System.Windows.Controls.Grid>permite definir agrupamentos flexíveis de linhas e colunas e até <xref:System.Windows.Controls.Grid> mesmo fornece um mecanismo para compartilhar informações de dimensionamento entre múltiplos elementos.  
  
#### <a name="how-is-grid-different-from-table"></a>Qual a diferença entre uma grade e uma tabela?  
 <xref:System.Windows.Documents.Table>e <xref:System.Windows.Controls.Grid> compartilhar alguma funcionalidade comum, mas cada uma é mais adequada para diferentes cenários. A <xref:System.Windows.Documents.Table> foi projetado para uso dentro do conteúdo de fluxo (consulte [Visão geral do documento de fluxo](../advanced/flow-document-overview.md) para obter mais informações sobre o conteúdo do fluxo). As grades são melhor utilizadas em formulários (basicamente em qualquer lugar fora do conteúdo de fluxo). Dentro <xref:System.Windows.Documents.FlowDocument>de <xref:System.Windows.Documents.Table> um , suporta comportamentos de conteúdo de fluxo, como <xref:System.Windows.Controls.Grid> paginação, refluxo de coluna e seleção de conteúdo enquanto um não faz. A <xref:System.Windows.Controls.Grid> por outro lado é melhor <xref:System.Windows.Documents.FlowDocument> usado fora <xref:System.Windows.Controls.Grid> de um por muitas razões, incluindo adicionar elementos baseados em uma linha e índice de coluna, <xref:System.Windows.Documents.Table> não. O <xref:System.Windows.Controls.Grid> elemento permite camadas de conteúdo infantil, permitindo que mais de um elemento exista dentro de uma única "célula". <xref:System.Windows.Documents.Table>não suporta camadas. Elementos infantis <xref:System.Windows.Controls.Grid> de a podem ser absolutamente posicionados em relação à área de seus limites "célula". <xref:System.Windows.Documents.Table>não suporta esse recurso. Finalmente, <xref:System.Windows.Controls.Grid> um é mais <xref:System.Windows.Documents.Table>leve do que um .  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>Comportamento de dimensionamento de colunas e linhas  
 Colunas e linhas definidas dentro <xref:System.Windows.Controls.Grid> <xref:System.Windows.GridUnitType.Star> de um podem aproveitar o dimensionamento para distribuir o espaço restante proporcionalmente. Quando <xref:System.Windows.GridUnitType.Star> é selecionada como altura ou largura de uma linha ou coluna, essa coluna ou linha recebe uma proporção ponderada de espaço disponível restante. Isso contrasta <xref:System.Windows.GridUnitType.Auto>com , que distribuirá espaço uniformemente com base no tamanho do conteúdo dentro de uma coluna ou linha. Esse valor é expresso como `*` ou `2*` ao usar o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. No primeiro caso, a linha ou a coluna receberia uma vez o espaço disponível, no segundo caso, duas vezes e assim por diante. Ao combinar essa técnica para distribuir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> proporcionalmente o espaço com um valor <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> dele é possível dividir o espaço do `Stretch` layout por porcentagem do espaço da tela. <xref:System.Windows.Controls.Grid>é o único painel de layout que pode distribuir espaço desta maneira.  
  
#### <a name="defining-and-using-a-grid"></a>Definindo e usando uma grade  
 O exemplo a seguir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] demonstra como construir um semelhante ao encontrado na caixa de diálogo Executar disponível no menu Iniciar do Windows.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um típico Elemento grade.](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 A <xref:System.Windows.Controls.StackPanel> permite que você "empilhe" elementos em uma direção atribuída. A direção padrão da pilha é vertical. A <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade pode ser usada para controlar o fluxo de conteúdo.  
  
#### <a name="stackpanel-vs-dockpanel"></a>StackPanel vs. DockPanel  
 Embora <xref:System.Windows.Controls.DockPanel> também possa "empilhar" elementos infantis, <xref:System.Windows.Controls.DockPanel> e <xref:System.Windows.Controls.StackPanel> não produzir resultados análogos em alguns cenários de uso. Por exemplo, a ordem dos elementos <xref:System.Windows.Controls.DockPanel> da criança <xref:System.Windows.Controls.StackPanel>pode afetar seu tamanho em um, mas não em um . Isso ocorre <xref:System.Windows.Controls.StackPanel> porque as medidas na <xref:System.Double.PositiveInfinity>direção <xref:System.Windows.Controls.DockPanel> do empilhamento em , enquanto que mede apenas o tamanho disponível.  
  
 O exemplo a seguir demonstra essa diferença básica.  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 A diferença no comportamento de renderização pode ser vista nesta imagem.  
  
 ![Captura de tela: StackPanel vs. DockPanel screenshot](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>Definindo e usando um StackPanel  
 O exemplo a seguir <xref:System.Windows.Controls.StackPanel> demonstra como usar um para criar um conjunto de botões posicionados verticalmente. Para posicionamento horizontal, <xref:System.Windows.Controls.StackPanel.Orientation%2A> defina a propriedade como <xref:System.Windows.Controls.Orientation.Horizontal>.  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento típico stackpanel.](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]também fornece uma <xref:System.Windows.Controls.StackPanel> variação do elemento que automaticamente "virtualiza" o conteúdo infantil vinculado a dados. Nesse contexto, a palavra virtualizar refere-se a uma técnica pela qual um subconjunto de elementos é gerado de um grande número de itens de dados com base em quais itens estão visíveis na tela. É intensivo, tanto em termos de memória quanto de processador, gerar um grande número de elementos de interface do usuário quando apenas alguns podem estar na tela em um determinado momento. <xref:System.Windows.Controls.VirtualizingStackPanel>(através da funcionalidade <xref:System.Windows.Controls.VirtualizingPanel>fornecida por ) calcula itens <xref:System.Windows.Controls.ItemContainerGenerator> visíveis <xref:System.Windows.Controls.ItemsControl> e <xref:System.Windows.Controls.ListBox> trabalha <xref:System.Windows.Controls.ListView>com o de um (como ou ) para criar apenas elementos para itens visíveis.  
  
 O <xref:System.Windows.Controls.VirtualizingStackPanel> elemento é automaticamente definido como o host de <xref:System.Windows.Controls.ListBox>itens para controles como o . Ao hospedar uma coleta vinculada a dados, o conteúdo é virtualmente virtualizado, desde que o conteúdo esteja dentro dos limites de um <xref:System.Windows.Controls.ScrollViewer>. Isso melhora o desempenho consideravelmente ao hospedar vários itens filho.  
  
 A marcação a seguir <xref:System.Windows.Controls.VirtualizingStackPanel> demonstra como usar um host de itens. A <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType> propriedade anexada deve `true` ser definida como (padrão) para que a virtualização ocorra.  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>é usado para posicionar elementos da criança em posição seqüencial da esquerda para a direita, quebrando o conteúdo para a próxima linha quando atinge a borda de seu recipiente pai. O conteúdo pode tem uma orientação horizontal ou vertical. <xref:System.Windows.Controls.WrapPanel>é útil para [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] cenários simples de fluxo. Também pode ser usado para aplicar um dimensionamento uniforme a todos os seus elementos filho.  
  
 O exemplo a seguir <xref:System.Windows.Controls.WrapPanel> demonstra <xref:System.Windows.Controls.Button> como criar controles para exibir que envolvem quando chegam à borda do recipiente.  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Um elemento wrappanel típico.](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>Elementos de painel aninhados  
 <xref:System.Windows.Controls.Panel>elementos podem ser aninhados entre si, a fim de produzir layouts complexos. Isso pode ser muito útil <xref:System.Windows.Controls.Panel> em situações em [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]que se é ideal para uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]porção de um, mas pode não atender às necessidades de uma porção diferente do .  
  
 Não há nenhum limite prático para a quantidade de aninhamento à qual o aplicativo pode dar suporte; no entanto, de modo geral, é melhor limitar o aplicativo a usar somente os painéis que são realmente necessários para o layout desejado. Em muitos casos, um <xref:System.Windows.Controls.Grid> elemento pode ser usado em vez de painéis aninhados devido à sua flexibilidade como um recipiente de layout. Isso pode aumentar o desempenho do aplicativo mantendo os elementos desnecessários fora da árvore.  
  
 O exemplo a seguir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] demonstra como criar <xref:System.Windows.Controls.Panel> um que aproveite elementos aninhados para alcançar um layout específico. Neste caso específico, <xref:System.Windows.Controls.DockPanel> um elemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é usado para <xref:System.Windows.Controls.StackPanel> fornecer <xref:System.Windows.Controls.Grid>estrutura, <xref:System.Windows.Controls.Canvas> e elementos aninhados, <xref:System.Windows.Controls.DockPanel>a , e a são usados para posicionar elementos da criança precisamente dentro do pai .  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 O aplicativo compilado produz uma nova [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] parecida com a mostrada a seguir.  
  
 ![Uma ui que se aproveita de painéis aninhados.](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>Elementos de painel personalizados  
 Embora [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] forneça uma matriz de controles de layout flexíveis, comportamentos <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> de <xref:System.Windows.FrameworkElement.MeasureOverride%2A> layout personalizados também podem ser alcançados substituindo os métodos e métodos. O dimensionamento e o posicionamento personalizados podem ser feitos com a definição de novos comportamentos de posicionamento nesses métodos de substituição.  
  
 Da mesma forma, comportamentos de layout personalizados <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid>baseados em classes derivadas (como ou ) podem ser definidos substituindo seus <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos e <xref:System.Windows.FrameworkElement.MeasureOverride%2A> métodos.  
  
 A marcação a seguir demonstra <xref:System.Windows.Controls.Panel> como criar um elemento personalizado. Este <xref:System.Windows.Controls.Panel>novo , `PlotPanel`definido como , apoia o posicionamento de elementos infantis através do uso de coordenadas *x* e *y* codificadas. Neste exemplo, <xref:System.Windows.Shapes.Rectangle> um elemento (não mostrado) é posicionado no ponto de enredo 50 *(x),* e 50 *(y).*  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 Para exibir uma implementação mais complexa de painel personalizado, consulte [Criar uma amostra de painel de encapsulamento com conteúdo personalizado](https://go.microsoft.com/fwlink/?LinkID=159979).  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>Suporte à localização/globalização  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dá suporte a vários recursos que ajudam na criação de uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] localizável.  
  
 Todos os elementos <xref:System.Windows.FrameworkElement.FlowDirection%2A> do painel suportam nativamente a propriedade, que pode ser usada para refluir dinamicamente o conteúdo com base nas configurações de localização ou idioma de um usuário. Para obter mais informações, consulte <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 A <xref:System.Windows.Window.SizeToContent%2A> propriedade fornece um mecanismo que permite aos desenvolvedores de aplicativos antecipar as necessidades dos localizados. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Usando <xref:System.Windows.SizeToContent.WidthAndHeight> o valor desta propriedade, um pai <xref:System.Windows.Window> sempre dimensiona dinamicamente para se encaixar no conteúdo e não é limitado por restrições artificiais de altura ou largura.  
  
 <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Grid>e <xref:System.Windows.Controls.StackPanel> são todas boas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]escolhas para localizáveis. <xref:System.Windows.Controls.Canvas>não é uma boa escolha, no entanto, porque posiciona o conteúdo absolutamente, dificultando a localização.  
  
 Para obter informações [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adicionais sobre a criação de aplicativos com interfaces de usuário (UIs) localizadas, consulte a visão geral do [layout automático de uso](../advanced/use-automatic-layout-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Exemplo de galeria de layout do WPF](https://go.microsoft.com/fwlink/?LinkID=160054)
- [Layout](../advanced/layout.md)
- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Visão geral de alinhamento, margens e preenchimento](../advanced/alignment-margins-and-padding-overview.md)
- [Criar uma amostra de painel de encapsulamento com conteúdo personalizado](https://go.microsoft.com/fwlink/?LinkID=159979)
- [Visão geral das propriedades anexadas](../advanced/attached-properties-overview.md)
- [Visão geral do uso de layout automático](../advanced/use-automatic-layout-overview.md)
- [Layout e design](../advanced/optimizing-performance-layout-and-design.md)

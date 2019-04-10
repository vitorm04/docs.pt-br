---
title: Layout
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 7fc69ff0434a26dc196d24395bbd1e2f441008de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231117"
---
# <a name="layout"></a>Layout
Este tópico descreve o sistema de layout do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Entender como e quando ocorrem os cálculos de layout é essencial para a criação de interfaces do usuário no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Esse tópico contém as seguintes seções:  
  
-   [Caixas delimitadoras de elementos](#LayoutSystem_BoundingBox)  
  
-   [O sistema de layout](#LayoutSystem_Overview)  
  
-   [Medindo e organizando filhos](#LayoutSystem_Measure_Arrange)  
  
-   [Elementos de painel e comportamentos de layout personalizados](#LayoutSystem_PanelsCustom)  
  
-   [Considerações sobre desempenho de layout](#LayoutSystem_Performance)  
  
-   [Renderização subpixel e arredondamento de layout](#LayoutSystem_LayoutRounding)  
  
-   [Novidades](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Caixas delimitadoras de elementos  
 Ao pensar sobre layout no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], é importante compreender a caixa delimitadora que circunda todos os elementos. Cada <xref:System.Windows.FrameworkElement> consumido no layout de sistema pode ser pensado como um retângulo que é encaixado no layout. O <xref:System.Windows.Controls.Primitives.LayoutInformation> classe retorna os limites de alocação de layout de um elemento ou slot. O tamanho do retângulo é determinado pelo cálculo do espaço disponível na tela, o tamanho de quaisquer restrições, propriedades específicas de layout (como margem e preenchimento) e o comportamento individual do pai <xref:System.Windows.Controls.Panel> elemento. O processamento de dados, o sistema de layout é capaz de calcular a posição de todos os filhos de um determinado <xref:System.Windows.Controls.Panel>. É importante lembrar que as características de dimensionamento definidas no elemento pai, como um <xref:System.Windows.Controls.Border>, afetam seus filhos.  
  
 A ilustração a seguir mostra um layout simples.  
  
 ![Captura de tela que mostra uma grade típica, sem caixa delimitadora sobreposta.](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 Este layout pode ser alcançado usando o seguinte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Uma única <xref:System.Windows.Controls.TextBlock> elemento é hospedado dentro de um <xref:System.Windows.Controls.Grid>. Enquanto o texto preenche apenas o canto superior esquerdo da primeira coluna, o espaço alocado para o <xref:System.Windows.Controls.TextBlock> é muito maior. A caixa delimitadora de qualquer <xref:System.Windows.FrameworkElement> podem ser recuperados usando o <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> método. A ilustração a seguir mostra a caixa delimitadora para o <xref:System.Windows.Controls.TextBlock> elemento.  
  
 ![Captura de tela que mostra a caixa delimitadora do TextBlock agora está visível.](./media/layout/visible-textblock-bounding-box.png)  
  
 Conforme mostrado pelo retângulo amarelo, o espaço alocado para o <xref:System.Windows.Controls.TextBlock> elemento é muito maior do que parece. Como outros elementos são adicionados para o <xref:System.Windows.Controls.Grid>, essa alocação pode reduzir ou expandir, dependendo do tipo e tamanho dos elementos que são adicionados.  
  
 O slot de layout a <xref:System.Windows.Controls.TextBlock> é convertida em uma <xref:System.Windows.Shapes.Path> usando o <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> método. Essa técnica pode ser útil para exibir a caixa delimitadora de um elemento.  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>O sistema de layout  
 Em sua forma mais simples, o layout é um sistema recursivo que leva um elemento a ser dimensionado, posicionado e desenhado. Mais especificamente, o layout descreve o processo de medir e organizar os membros de um <xref:System.Windows.Controls.Panel> do elemento <xref:System.Windows.Controls.Panel.Children%2A> coleção. O layout é um processo intensivo. Quanto maior o <xref:System.Windows.Controls.Panel.Children%2A> coleção, maior o número de cálculos que devem ser feitas. Complexidade também pode ser introduzida com base no comportamento de layout definido pelo <xref:System.Windows.Controls.Panel> elemento que possui a coleção. Relativamente simples <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas>, pode ter um desempenho significativamente melhor do que mais complexo <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Grid>.  
  
 Cada vez que um filho <xref:System.Windows.UIElement> muda de posição, ele tem o potencial de disparar uma nova passagem pelo sistema de layout. Portanto, é importante compreender os eventos que podem invocar o sistema de layout, pois invocações desnecessárias podem levar a desempenho ruim do aplicativo. O exemplo a seguir descreve o processo que ocorre quando o sistema de layout é invocado.  
  
1.  Um filho <xref:System.Windows.UIElement> começa o processo de layout primeiro tendo suas propriedades principais medidas.  
  
2.  As propriedades definidas em de dimensionamento <xref:System.Windows.FrameworkElement> são avaliadas, como <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, e <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>-lógica específica é aplicado, como <xref:System.Windows.Controls.Dock> direção ou empilhamento <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  O conteúdo é organizado depois que todos os filhos são medidos.  
  
5.  O <xref:System.Windows.Controls.Panel.Children%2A> coleção é desenhada na tela.  
  
6.  O processo é chamado novamente se adicionais <xref:System.Windows.Controls.Panel.Children%2A> são adicionados à coleção, um <xref:System.Windows.FrameworkElement.LayoutTransform%2A> é aplicado, ou o <xref:System.Windows.UIElement.UpdateLayout%2A> método é chamado.  
  
 Esse processo e como ele é invocado são definidos em mais detalhes nas seções a seguir.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Medindo e organizando filhos  
 O sistema de layout completa duas passagens para cada membro do <xref:System.Windows.Controls.Panel.Children%2A> coleta, uma passagem de medição e uma passagem de organização. Cada criança <xref:System.Windows.Controls.Panel> fornece sua própria <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos para alcançar o seu próprio comportamento específico de layout.  
  
 Durante a passagem de medida, cada membro do <xref:System.Windows.Controls.Panel.Children%2A> coleção é avaliada. O processo começa com uma chamada para o <xref:System.Windows.UIElement.Measure%2A> método. Esse método é chamado dentro da implementação do pai <xref:System.Windows.Controls.Panel> elemento e não precisa ser chamado explicitamente para o layout ocorra.  
  
 Propriedades de tamanho em primeiro lugar, nativo do <xref:System.Windows.UIElement> são avaliadas, como <xref:System.Windows.UIElement.Clip%2A> e <xref:System.Windows.UIElement.Visibility%2A>. Isso gera um valor chamado `constraintSize` que é passado para <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Em segundo lugar, as propriedades de estrutura definido em <xref:System.Windows.FrameworkElement> são processados, que afeta o valor de `constraintSize`. Essas propriedades geralmente descrevem as características de dimensionamento de subjacente <xref:System.Windows.UIElement>, como seu <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, e <xref:System.Windows.FrameworkElement.Style%2A>. Cada uma dessas propriedades pode alterar o espaço necessário para exibir o elemento. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> é então chamado com `constraintSize` como um parâmetro.  
  
> [!NOTE]
>  Há uma diferença entre as propriedades de <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A> e <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Por exemplo, o <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriedade é um valor calculado com base nas outras entradas de altura e o sistema de layout. O valor é definido pelo sistema de layout em si, com base em uma passagem de renderização e pode, portanto, ficar um pouco diferente do valor de conjunto de propriedades, tais como <xref:System.Windows.FrameworkElement.Height%2A>, que são a base das alterações de entrada.  
>   
>  Porque <xref:System.Windows.FrameworkElement.ActualHeight%2A> é um valor calculado, você deve estar ciente que podem haver várias mudanças ou alterações incrementais a ele como resultado de várias operações pelo sistema de layout. O sistema de layout pode estar calculando o espaço de medição necessário para elementos filhos, as restrições do elemento pai e assim por diante.  
  
 O objetivo final da passagem de medição é para o filho determinar seu <xref:System.Windows.UIElement.DesiredSize%2A>, que ocorre durante o <xref:System.Windows.FrameworkElement.MeasureCore%2A> chamar. O <xref:System.Windows.UIElement.DesiredSize%2A> valor é armazenado por <xref:System.Windows.UIElement.Measure%2A> para uso durante a passagem de organização de conteúdo.  
  
 A passagem de organização começa com uma chamada para o <xref:System.Windows.UIElement.Arrange%2A> método. Durante a passagem de organização, o pai <xref:System.Windows.Controls.Panel> elemento gera um retângulo que representa os limites do filho. Esse valor é passado para o <xref:System.Windows.FrameworkElement.ArrangeCore%2A> método para processamento.  
  
 O <xref:System.Windows.FrameworkElement.ArrangeCore%2A> método avalia o <xref:System.Windows.UIElement.DesiredSize%2A> do filho e avalia as margens adicionais que podem afetar o tamanho do elemento renderizado. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> gera uma `arrangeSize`, que é passado para o <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> método o <xref:System.Windows.Controls.Panel> como um parâmetro. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> gera o `finalSize` do filho. Por fim, o <xref:System.Windows.FrameworkElement.ArrangeCore%2A> método faz uma avaliação final das propriedades de deslocamento, como margem e alinhamento e coloca o filho em seu slot de layout. O filho não precisa preencher o espaço inteiro alocado (e geralmente não faz isso). Controle, em seguida, é retornado para o pai <xref:System.Windows.Controls.Panel> e o processo de layout é concluído.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Elementos de painel e comportamentos de layout personalizados  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui um grupo de elementos que derivam de <xref:System.Windows.Controls.Panel>. Eles <xref:System.Windows.Controls.Panel> elementos permitem vários layouts complexos. Por exemplo, Empilhando elementos pode ser facilmente obtido usando o <xref:System.Windows.Controls.StackPanel> elemento, embora layouts fluxo mais complexos e livres sejam possíveis usando um <xref:System.Windows.Controls.Canvas>.  
  
 A tabela a seguir resume o layout disponível <xref:System.Windows.Controls.Panel> elementos.  
  
|Nome do painel|Descrição|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Define uma área na qual você pode posicionar explicitamente elementos filho usando coordenadas relativas ao <xref:System.Windows.Controls.Canvas> área.|  
|<xref:System.Windows.Controls.DockPanel>|Define uma área dentro da qual você pode organizar elementos filho horizontal ou verticalmente, uns em relação aos outros.|  
|<xref:System.Windows.Controls.Grid>|Define uma área de grade flexível que consiste em colunas e linhas.|  
|<xref:System.Windows.Controls.StackPanel>|Organiza elementos filho em uma única linha que pode ser orientada horizontal ou verticalmente.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Fornece uma estrutura para os elementos <xref:System.Windows.Controls.Panel> que virtualizam os respectivos dados filho. Esta é uma classe abstrata.|  
|<xref:System.Windows.Controls.WrapPanel>|Coloca os elementos filho na posição sequencial da esquerda para a direita, quebrando o conteúdo para a próxima linha na borda da caixa delimitadora. A ordenação posterior ocorre sequencialmente de cima para baixo ou da direita para a esquerda, dependendo do valor da <xref:System.Windows.Controls.WrapPanel.Orientation%2A> propriedade.|  
  
 Para aplicativos que exigem um layout que não é possível usando qualquer um dos predefinida <xref:System.Windows.Controls.Panel> elementos, comportamentos de layout personalizados podem ser obtidos ao herdando <xref:System.Windows.Controls.Panel> e substituindo o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos. Para obter um exemplo, consulte [Custom Radial Panel Sample](https://go.microsoft.com/fwlink/?LinkID=159982) (Amostra de painel radial personalizado).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Considerações sobre desempenho de layout  
 O layout é um processo recursivo. Cada elemento filho em um <xref:System.Windows.Controls.Panel.Children%2A> coleção é processada durante cada chamada do sistema de layout. Como resultado, disparar o sistema de layout deve ser evitado quando não for necessário. As considerações a seguir podem ajudá-lo a melhorar o desempenho.  
  
-   Esteja ciente de quais alterações de valor da propriedade forçarão uma atualização recursiva realizada pelo sistema de layout.  
  
     As propriedades de dependência cujos valores podem fazer com que o sistema de layout seja inicializado são marcadas com sinalizadores públicos. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> e <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> fornecem dicas úteis sobre qual propriedade alterações de valor forçará uma recursiva atualizar pelo sistema de layout. Em geral, qualquer propriedade que pode afetar o tamanho da caixa delimitadora de um elemento deve ter um <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> o sinalizador será definido como true. Para obter mais informações, consulte [Visão geral sobre propriedades de dependência](dependency-properties-overview.md).  
  
-   Quando possível, use uma <xref:System.Windows.UIElement.RenderTransform%2A> em vez de um <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     Um <xref:System.Windows.FrameworkElement.LayoutTransform%2A> pode ser uma maneira muito útil para afetar o conteúdo de um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. No entanto, se o efeito da transformação não precisa afetar a posição dos outros elementos, é melhor usar um <xref:System.Windows.UIElement.RenderTransform%2A> em vez disso, porque <xref:System.Windows.UIElement.RenderTransform%2A> não invoca o sistema de layout. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> aplica sua transformação e força uma atualização recursiva de layout para levar em conta a nova posição do elemento afetado.  
  
-   Evite chamadas desnecessárias a <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     O <xref:System.Windows.UIElement.UpdateLayout%2A> método força uma atualização recursiva de layout e não é necessário com frequência. A menos que você tenha certeza de que uma atualização completa é necessária, confie no sistema de layout para chamar esse método para você.  
  
-   Ao trabalhar com um grande <xref:System.Windows.Controls.Panel.Children%2A> coleta, considere o uso de um <xref:System.Windows.Controls.VirtualizingStackPanel> em vez de uma expressão <xref:System.Windows.Controls.StackPanel>.  
  
     Virtualizando a coleção de filhos, o <xref:System.Windows.Controls.VirtualizingStackPanel> mantém apenas os objetos na memória que estão dentro do visor do pai. Como resultado, o desempenho é significativamente melhorado na maioria dos cenários.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Renderização subpixel e arredondamento de layout  
 O sistema gráfico do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa unidades independentes de dispositivo para habilitar a independência entre resolução e dispositivo. Cada pixel independente de dispositivo pode ser dimensionado automaticamente com o sistema [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] configuração. Isso fornece aos aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uma colocação em escala apropriada para diferentes configurações de [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] e faz com que o aplicativo reconheça o [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] automaticamente.  
  
 No entanto, essa independência de [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] pode criar uma renderização de borda irregular devido à suavização. Esses artefatos, geralmente vistos como bordas desfocadas ou semitransparentes, podem ocorrer quando o local de uma borda está no meio de um pixel de dispositivo, em vez de entre os pixels de dispositivo. O sistema de layout fornece uma maneira de compensar isso com o arredondamento de layout. O arredondamento de layout ocorre quando o sistema de layout arredonda valores de pixel não integrais durante a passagem de layout.  
  
 O arredondamento de layout é desabilitado por padrão. Para habilitar o arredondamento de layout, defina as <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> propriedade para `true` em qualquer <xref:System.Windows.FrameworkElement>. Como essa é uma propriedade de dependência, o valor será propagado para todos os filhos na árvore visual. Para habilitar o layout de arredondamento para toda a interface do usuário, defina <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> para `true` no contêiner raiz. Para ver um exemplo, consulte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Novidades  
 Entender como os elementos são medidos e organizados é o primeiro passo para entender o layout. Para obter mais informações sobre como as disponíveis <xref:System.Windows.Controls.Panel> elementos, consulte [visão geral de painéis](../controls/panels-overview.md). Para compreender melhor as várias propriedades de posicionamento que podem afetar o layout, consulte [Visão geral de alinhamento, margens e preenchimento](alignment-margins-and-padding-overview.md). Para obter um exemplo de um personalizado <xref:System.Windows.Controls.Panel> elemento, consulte [Custom Panel Sample Radial](https://go.microsoft.com/fwlink/?LinkID=159982). Quando você estiver pronto para juntar tudo em um aplicativo leve, consulte [passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Visão geral de painéis](../controls/panels-overview.md)
- [Visão geral de alinhamento, margens e preenchimento](alignment-margins-and-padding-overview.md)
- [Layout e design](optimizing-performance-layout-and-design.md)

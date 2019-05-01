---
title: Visão geral de alinhamento, margens e preenchimento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: 58af8848a6b8a5e4ded453831f5a7ef985548492
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032195"
---
# <a name="alignment-margins-and-padding-overview"></a>Visão geral de alinhamento, margens e preenchimento
O <xref:System.Windows.FrameworkElement> classe expõe várias propriedades que são usadas para posicionar elementos filho precisamente. Este tópico discute quatro das propriedades mais importantes: <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. É importante entender os efeitos dessas propriedades, pois eles fornecem a base para controlar a posição dos elementos em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>Introdução ao posicionamento de elementos  
 Há diversas formas de posicionar elementos usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. No entanto, alcançar um layout ideal vai além de simplesmente escolher o direito de <xref:System.Windows.Controls.Panel> elemento. Controle fino do posicionamento requer uma compreensão do <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedades.  
  
 A ilustração a seguir mostra um cenário de layout que utiliza diversas propriedades de posicionamento.  
  
 ![Exemplo de propriedades de posicionamento do WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 À primeira vista, o <xref:System.Windows.Controls.Button> elementos nesta ilustração parecem estar posicionados aleatoriamente. No entanto, suas posições são precisamente controladas usando uma combinação de preenchimentos, margens e alinhamentos.  
  
 O exemplo a seguir descreve como criar o layout na ilustração anterior. Um <xref:System.Windows.Controls.Border> encapsula o elemento pai <xref:System.Windows.Controls.StackPanel>, com um <xref:System.Windows.Controls.Border.Padding%2A> valor de 15 pixels independentes de dispositivo. Isso conta para o estreito <xref:System.Windows.Media.Brushes.LightBlue%2A> banda que circunda o filho <xref:System.Windows.Controls.StackPanel>. Elementos filho do <xref:System.Windows.Controls.StackPanel> são usados para ilustrar cada uma das várias propriedades de posicionamento detalhadas neste tópico. Três <xref:System.Windows.Controls.Button> elementos são usados para demonstrar a ambos os <xref:System.Windows.FrameworkElement.Margin%2A> e <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedades.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 O diagrama a seguir fornece uma exibição em primeiro plano de várias propriedades de posicionamento que são usadas no exemplo anterior. As seções seguintes neste tópico descrevem mais detalhadamente como usar cada propriedade de posicionamento.  
  
 ![Posicionamento de propriedades com chamada de tela&#45;outs](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>Compreendendo as propriedades de alinhamento  
 O <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedades que descrevem como um elemento filho deve ser posicionado no espaço de layout alocado do elemento pai. Ao usar essas propriedades juntas, você pode posicionar elementos filho com precisão. Por exemplo, os elementos filho de um <xref:System.Windows.Controls.DockPanel> pode especificar quatro alinhamentos horizontais diferentes: <xref:System.Windows.HorizontalAlignment.Left>, <xref:System.Windows.HorizontalAlignment.Right>, ou <xref:System.Windows.HorizontalAlignment.Center>, ou como <xref:System.Windows.HorizontalAlignment.Stretch> para preencher o espaço disponível. Valores semelhantes estão disponíveis para o posicionamento vertical.  
  
> [!NOTE]
>  Definidas explicitamente <xref:System.Windows.FrameworkElement.Height%2A> e <xref:System.Windows.FrameworkElement.Width%2A> propriedades em um elemento têm precedência sobre o <xref:System.Windows.HorizontalAlignment.Stretch> valor da propriedade. Tentativa de definir <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>e um <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor de `Stretch` resulta no `Stretch` de solicitação que está sendo ignorado.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>Propriedade HorizontalAlignment  
 O <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade declara as características de alinhamento horizontal para aplicar aos elementos filho. A tabela a seguir mostra cada um dos possíveis valores da <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementos filhos são alinhados à esquerda do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementos filho são alinhados ao centro do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementos filho são alinhados à direita do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Padrão)|Os elementos filho são redimensionados para preencher o espaço de layout alocado do elemento pai. Explícito <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> prevalecem os valores.|  
  
 O exemplo a seguir mostra como aplicar a <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade para <xref:System.Windows.Controls.Button> elementos. Cada valor de atributo é mostrado para melhor ilustrar os diversos comportamentos de renderização.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 O código anterior resulta num layout semelhante à imagem a seguir. Os efeitos de posicionamento de cada <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valor são visíveis na ilustração.  
  
 ![Exemplo de HorizontalAlignment](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>Propriedade VerticalAlignment  
 O <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade descreve as características de alinhamento vertical para aplicar aos elementos filho. A tabela a seguir mostra cada um dos possíveis valores para o <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementos filho são alinhados no topo do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementos filho são alinhados ao centro do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementos filho são alinhados na parte inferior do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Padrão)|Os elementos filho são redimensionados para preencher o espaço de layout alocado do elemento pai. Explícito <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> prevalecem os valores.|  
  
 O exemplo a seguir mostra como aplicar a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade para <xref:System.Windows.Controls.Button> elementos. Cada valor de atributo é mostrado para melhor ilustrar os diversos comportamentos de renderização. Para fins deste exemplo, um <xref:System.Windows.Controls.Grid> elemento com linhas de grade visíveis é utilizado como o pai, para melhor ilustrar o comportamento de layout de cada valor de propriedade.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 O código anterior resulta num layout semelhante à imagem a seguir. Os efeitos de posicionamento de cada <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> valor são visíveis na ilustração.  
  
 ![Exemplo da propriedade VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>Entendendo as propriedades de margem  
 O <xref:System.Windows.FrameworkElement.Margin%2A> propriedade descreve a distância entre um elemento e seus filhos ou pares. <xref:System.Windows.FrameworkElement.Margin%2A> valores podem ser uniformes, utilizando sintaxe como `Margin="20"`. Com essa sintaxe, um uniforme <xref:System.Windows.FrameworkElement.Margin%2A> do dispositivo de 20 pixels independentes de seriam aplicadas ao elemento. <xref:System.Windows.FrameworkElement.Margin%2A> valores também podem tomar a forma de quatro valores distintos, cada valor descrevendo uma margem distinta para aplicar à esquerda, superior, direita e inferior (nessa ordem), como `Margin="0,10,5,25"`. Uso adequado do <xref:System.Windows.FrameworkElement.Margin%2A> propriedade permite que um controle muito fino da posição de renderização de um elemento e a posição de renderização de seus elementos vizinhos e filhos.  
  
> [!NOTE]
>  Uma margem diferente de zero aplica espaço fora do elemento <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A>.  
  
 O exemplo a seguir mostra como aplicar margens uniformes em torno de um grupo de <xref:System.Windows.Controls.Button> elementos. O <xref:System.Windows.Controls.Button> elementos são espaçados uniformemente com uma margem de dez pixels em cada direção.  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 Em muitos casos, uma margem uniforme não é apropriada. Nesses casos, o espaçamento não uniforme pode ser aplicado. O exemplo a seguir mostra como aplicar espaçamento de margens não uniformes a elementos filho. As margens são descritas nesta ordem: à esquerda, na parte superior, à direita, na parte inferior.  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Entendendo a propriedade de preenchimento  
 Preenchimento é semelhante ao <xref:System.Windows.FrameworkElement.Margin%2A> na maioria dos aspectos. A propriedade de preenchimento é exposta em apenas em algumas classes, principalmente como uma conveniência: <xref:System.Windows.Documents.Block>, <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Control>, e <xref:System.Windows.Controls.TextBlock> são exemplos de classes que expõem uma propriedade de preenchimento. O <xref:System.Windows.Controls.Border.Padding%2A> propriedade aumenta o tamanho efetivo de um elemento filho especificado <xref:System.Windows.Thickness> valor.  
  
 O exemplo a seguir mostra como aplicar <xref:System.Windows.Controls.Border.Padding%2A> a um pai <xref:System.Windows.Controls.Border> elemento.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Usando alinhamento, margens e preenchimento em um aplicativo  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, <xref:System.Windows.Controls.Border.Padding%2A>, e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> fornecem o controle de posicionamento necessário para criar um complexo [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Você pode usar os efeitos de cada propriedade para alterar o posicionamento do elemento filho, permitindo a flexibilidade na criação de aplicativos dinâmicos e experiências de usuário.  
  
 O exemplo a seguir demonstra cada um dos conceitos detalhados neste tópico. Criando a infraestrutura encontrada no primeiro exemplo neste tópico, este exemplo adiciona uma <xref:System.Windows.Controls.Grid> elemento como um filho de <xref:System.Windows.Controls.Border> no primeiro exemplo. <xref:System.Windows.Controls.Border.Padding%2A> é aplicado ao pai <xref:System.Windows.Controls.Border> elemento. O <xref:System.Windows.Controls.Grid> é usado para particionar espaço entre três filho <xref:System.Windows.Controls.StackPanel> elementos. <xref:System.Windows.Controls.Button> elementos são novamente usados para mostrar os diversos efeitos de <xref:System.Windows.FrameworkElement.Margin%2A> e <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>. <xref:System.Windows.Controls.TextBlock> os elementos são adicionados a cada <xref:System.Windows.Controls.ColumnDefinition> para definir melhor as várias propriedades aplicadas para o <xref:System.Windows.Controls.Button> elementos em cada coluna.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Quando compilado, o aplicativo anterior produz um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que parece com a ilustração a seguir. Os efeitos de vários valores de propriedade são evidentes no espaçamento entre os elementos, e valores de propriedade significativos para elementos em cada coluna são exibidos em <xref:System.Windows.Controls.TextBlock> elementos.  
  
 ![Várias propriedades de posicionamento em um aplicativo](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>Novidades  
 Propriedades de posicionamento definidas pela <xref:System.Windows.FrameworkElement> classe permitem um controle fino do posicionamento de elementos dentro do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos. Agora você tem várias técnicas que pode usar para melhor posicionar elementos usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Recursos adicionais estão disponíveis e explicam o layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mais detalhadamente. O [visão geral de painéis](../controls/panels-overview.md) tópico contém mais detalhes sobre os vários <xref:System.Windows.Controls.Panel> elementos. O tópico [passo a passo: Meu primeiro aplicativo da área de trabalho do WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) apresenta técnicas avançadas que usam elementos de layout para posicionar componentes e associar suas ações a fontes de dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Visão geral de painéis](../controls/panels-overview.md)
- [Layout](layout.md)
- [Exemplo de galeria de layout do WPF](https://go.microsoft.com/fwlink/?LinkID=160054)

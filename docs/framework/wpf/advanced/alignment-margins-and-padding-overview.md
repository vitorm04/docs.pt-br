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
ms.openlocfilehash: bec2d9cd224febb650e2de67bb7406365d075963
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145469"
---
# <a name="alignment-margins-and-padding-overview"></a>Visão geral de alinhamento, margens e preenchimento
A <xref:System.Windows.FrameworkElement> classe expõe várias propriedades que são usadas para posicionar com precisão elementos infantis. Este tópico discute quatro das propriedades <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>mais <xref:System.Windows.Controls.Border.Padding%2A>importantes: , e <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>. É importante entender os efeitos dessas propriedades, pois eles fornecem a base para controlar a posição dos elementos em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>Introdução ao posicionamento de elementos  
 Há diversas formas de posicionar elementos usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. No entanto, alcançar o layout <xref:System.Windows.Controls.Panel> ideal vai além de simplesmente escolher o elemento certo. O bom controle do posicionamento <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A>requer <xref:System.Windows.Controls.Border.Padding%2A>uma <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> compreensão das propriedades e propriedades.  
  
 A ilustração a seguir mostra um cenário de layout que utiliza diversas propriedades de posicionamento.  
  
 ![Amostra de propriedades de posicionamento do WPF](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 À primeira vista, os <xref:System.Windows.Controls.Button> elementos nesta ilustração podem parecer ser colocados aleatoriamente. No entanto, suas posições são precisamente controladas usando uma combinação de preenchimentos, margens e alinhamentos.  
  
 O exemplo a seguir descreve como criar o layout na ilustração anterior. Um <xref:System.Windows.Controls.Border> elemento encapsula um <xref:System.Windows.Controls.StackPanel>pai, <xref:System.Windows.Controls.Border.Padding%2A> com um valor de 15 pixels independentes do dispositivo. Isso explica a <xref:System.Windows.Media.Brushes.LightBlue%2A> faixa estreita que <xref:System.Windows.Controls.StackPanel>cerca a criança. Os elementos <xref:System.Windows.Controls.StackPanel> infantis do são usados para ilustrar cada uma das várias propriedades de posicionamento que são detalhadas neste tópico. Três <xref:System.Windows.Controls.Button> elementos são usados <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> para demonstrar as propriedades e as <xref:System.Windows.FrameworkElement.Margin%2A> propriedades.  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 O diagrama a seguir fornece uma exibição em primeiro plano de várias propriedades de posicionamento que são usadas no exemplo anterior. As seções seguintes neste tópico descrevem mais detalhadamente como usar cada propriedade de posicionamento.  
  
 ![Propriedades de posicionamento com saídas de chamada de tela&#45;](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>Compreendendo as propriedades de alinhamento  
 As <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedades descrevem como um elemento filho deve ser posicionado dentro do espaço de layout alocado de um elemento pai. Ao usar essas propriedades juntas, você pode posicionar elementos filho com precisão. Por exemplo, elementos <xref:System.Windows.Controls.DockPanel> infantis de um podem <xref:System.Windows.HorizontalAlignment.Left> <xref:System.Windows.HorizontalAlignment.Right>especificar <xref:System.Windows.HorizontalAlignment.Center>quatro <xref:System.Windows.HorizontalAlignment.Stretch> alinhamentos horizontais diferentes: , ou , para preencher o espaço disponível. Valores semelhantes estão disponíveis para o posicionamento vertical.  
  
> [!NOTE]
> Explicitamente definidos <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> e propriedades em um elemento <xref:System.Windows.HorizontalAlignment.Stretch> têm precedência sobre o valor da propriedade. <xref:System.Windows.FrameworkElement.Height%2A>Tentando definir , <xref:System.Windows.FrameworkElement.Width%2A>e <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> um `Stretch` valor de `Stretch` resultados no pedido sendo ignorado.  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>Propriedade HorizontalAlignment  
 A <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade declara as características de alinhamento horizontal para aplicar aos elementos da criança. A tabela a seguir mostra cada <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> um dos valores possíveis da propriedade.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|Elementos filhos são alinhados à esquerda do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Center>|Elementos filho são alinhados ao centro do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Right>|Elementos filho são alinhados à direita do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.HorizontalAlignment.Stretch> (Padrão)|Os elementos filho são redimensionados para preencher o espaço de layout alocado do elemento pai. Valores explícitos <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> precedinos.|  
  
 O exemplo a seguir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> mostra <xref:System.Windows.Controls.Button> como aplicar a propriedade aos elementos. Cada valor de atributo é mostrado para melhor ilustrar os diversos comportamentos de renderização.  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 O código anterior resulta num layout semelhante à imagem a seguir. Os efeitos de <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> posicionamento de cada valor são visíveis na ilustração.  
  
 ![Amostra de alinhamento horizontal](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>Propriedade VerticalAlignment  
 A <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> propriedade descreve as características de alinhamento vertical para aplicar aos elementos da criança. A tabela a seguir mostra cada <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> um dos valores possíveis para a propriedade.  
  
|Membro|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|Elementos filho são alinhados no topo do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Center>|Elementos filho são alinhados ao centro do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Bottom>|Elementos filho são alinhados na parte inferior do espaço de layout alocado do elemento pai.|  
|<xref:System.Windows.VerticalAlignment.Stretch> (Padrão)|Os elementos filho são redimensionados para preencher o espaço de layout alocado do elemento pai. Valores explícitos <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> precedinos.|  
  
 O exemplo a seguir <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> mostra <xref:System.Windows.Controls.Button> como aplicar a propriedade aos elementos. Cada valor de atributo é mostrado para melhor ilustrar os diversos comportamentos de renderização. Para efeitos desta amostra, um <xref:System.Windows.Controls.Grid> elemento com linhas de grade visíveis é usado como pai, para ilustrar melhor o comportamento de layout de cada valor de propriedade.  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 O código anterior resulta num layout semelhante à imagem a seguir. Os efeitos de <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> posicionamento de cada valor são visíveis na ilustração.  
  
 ![Amostra de propriedade VerticalAlignment](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>Entendendo as propriedades de margem  
 A <xref:System.Windows.FrameworkElement.Margin%2A> propriedade descreve a distância entre um elemento e seu filho ou pares. <xref:System.Windows.FrameworkElement.Margin%2A>valores podem ser uniformes, `Margin="20"`usando sintaxe como . Com esta sintaxe, um uniforme <xref:System.Windows.FrameworkElement.Margin%2A> de 20 pixels independentes do dispositivo seria aplicado ao elemento. <xref:System.Windows.FrameworkElement.Margin%2A>os valores também podem assumir a forma de quatro valores distintos, cada valor descrevendo uma margem `Margin="0,10,5,25"`distinta para aplicar à esquerda, superior, direita e inferior (nessa ordem), como . O uso <xref:System.Windows.FrameworkElement.Margin%2A> adequado da propriedade permite um controle muito fino da posição de renderização de um elemento e da posição de renderização de seus elementos vizinhos e crianças.  
  
> [!NOTE]
> Uma margem não-zero aplica espaço fora <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A>do elemento e .  
  
 O exemplo a seguir mostra como aplicar <xref:System.Windows.Controls.Button> margens uniformes em torno de um grupo de elementos. Os <xref:System.Windows.Controls.Button> elementos são espaçados uniformemente com um buffer de margem de dez pixels em cada direção.  
  
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
 O preenchimento é <xref:System.Windows.FrameworkElement.Margin%2A> semelhante à maioria dos aspectos. A propriedade Desacolchoado é exposta apenas em <xref:System.Windows.Documents.Block>algumas <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Control>classes, <xref:System.Windows.Controls.TextBlock> principalmente como uma conveniência: , , e são amostras de classes que expõem uma propriedade de preenchimento. A <xref:System.Windows.Controls.Border.Padding%2A> propriedade aumenta o tamanho efetivo de um <xref:System.Windows.Thickness> elemento filho pelo valor especificado.  
  
 O exemplo a seguir <xref:System.Windows.Controls.Border.Padding%2A> mostra <xref:System.Windows.Controls.Border> como aplicar a um elemento pai.  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>Usando alinhamento, margens e preenchimento em um aplicativo  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> e fornecer o controle de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]posicionamento necessário para criar um complexo . Você pode usar os efeitos de cada propriedade para alterar o posicionamento do elemento filho, permitindo a flexibilidade na criação de aplicativos dinâmicos e experiências de usuário.  
  
 O exemplo a seguir demonstra cada um dos conceitos detalhados neste tópico. Com base na infra-estrutura encontrada na primeira amostra <xref:System.Windows.Controls.Grid> deste tópico, <xref:System.Windows.Controls.Border> este exemplo adiciona um elemento como filho da primeira amostra. <xref:System.Windows.Controls.Border.Padding%2A>é aplicado ao <xref:System.Windows.Controls.Border> elemento pai. O <xref:System.Windows.Controls.Grid> é usado para dividir <xref:System.Windows.Controls.StackPanel> o espaço entre três elementos infantis. <xref:System.Windows.Controls.Button>elementos são novamente usados <xref:System.Windows.FrameworkElement.Margin%2A> para <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>mostrar os vários efeitos de e . <xref:System.Windows.Controls.TextBlock>elementos são <xref:System.Windows.Controls.ColumnDefinition> adicionados a cada um para <xref:System.Windows.Controls.Button> definir melhor as várias propriedades aplicadas aos elementos em cada coluna.  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 Quando compilado, o aplicativo anterior produz um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que parece com a ilustração a seguir. Os efeitos dos diversos valores de propriedade são evidentes no espaçamento entre <xref:System.Windows.Controls.TextBlock> elementos, e valores de propriedade significativos para elementos em cada coluna são mostrados dentro dos elementos.  
  
 ![Várias propriedades de posicionamento em uma aplicação](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>E agora?  
 As propriedades de <xref:System.Windows.FrameworkElement> posicionamento definidas pela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe permitem um controle fino da colocação do elemento dentro das aplicações. Agora você tem várias técnicas que pode usar para melhor posicionar elementos usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Recursos adicionais estão disponíveis e explicam o layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mais detalhadamente. O tópico [Visão geral dos painéis](../controls/panels-overview.md) contém mais detalhes sobre os vários <xref:System.Windows.Controls.Panel> elementos. O tópico [Passo a Passo: Meu primeiro aplicativo de desktop WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md) introduz técnicas avançadas que usam elementos de layout para posicionar componentes e vincular suas ações a fontes de dados.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [Visão geral de painéis](../controls/panels-overview.md)
- [Layout](layout.md)
- [Exemplo de galeria de layout do WPF](https://go.microsoft.com/fwlink/?LinkID=160054)

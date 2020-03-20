---
title: Visão geral do expansor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187117"
---
# <a name="expander-overview"></a>Visão geral do expansor
Um <xref:System.Windows.Controls.Expander> controle fornece uma maneira de fornecer conteúdo em uma área expansível que se assemelha a uma janela e inclui um cabeçalho.  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>Criando um expansor simples  
 O exemplo a seguir mostra <xref:System.Windows.Controls.Expander> como criar um controle simples. Este exemplo <xref:System.Windows.Controls.Expander> cria um que se parece com a ilustração anterior.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 O <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e <xref:System.Windows.Controls.Expander> de um também pode <xref:System.Windows.Controls.RadioButton> conter <xref:System.Windows.Controls.Image> conteúdo complexo, como e objetos.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Definindo a direção da área de conteúdo de expansão  
 Você pode definir a <xref:System.Windows.Controls.Expander> área de conteúdo de um<xref:System.Windows.Controls.ExpandDirection.Down>controle <xref:System.Windows.Controls.ExpandDirection.Up> <xref:System.Windows.Controls.ExpandDirection.Left>para <xref:System.Windows.Controls.ExpandDirection.Right>expandir em uma das quatro direções ( , , ou ) usando a <xref:System.Windows.Controls.ExpandDirection> propriedade. Quando a área de conteúdo <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> é colapsada, apenas o botão alternar e o botão de alternância aparecerão. Um <xref:System.Windows.Controls.Button> controle que exibe uma seta direcional é usado como um botão de alternar para expandir ou colapsar a área de conteúdo. Quando expandido, <xref:System.Windows.Controls.Expander> ele tenta exibir todo o seu conteúdo em uma área semelhante a uma janela.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Controlando o tamanho de um expansor em um painel  
 Se <xref:System.Windows.Controls.Expander> um controle estiver dentro de <xref:System.Windows.Controls.Panel>um controle <xref:System.Windows.Controls.StackPanel>de layout <xref:System.Windows.FrameworkElement.Height%2A> que <xref:System.Windows.Controls.Expander> herde, como, não especifique um sobre quando a <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriedade está definida ou <xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.Controls.ExpandDirection.Up>. Da mesma forma, <xref:System.Windows.FrameworkElement.Width%2A> não <xref:System.Windows.Controls.Expander> especifique um sobre quando a <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriedade é definida para <xref:System.Windows.Controls.ExpandDirection.Left> ou <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Quando você define uma <xref:System.Windows.Controls.Expander> dimensão de tamanho em um controle na <xref:System.Windows.Controls.Expander> direção em que o conteúdo expandido é exibido, assume o controle da área que é usada pelo conteúdo e exibe uma borda ao seu redor. A borda é mostrada mesmo quando o conteúdo está recolhido. Para definir o tamanho da área de conteúdo expandida, <xref:System.Windows.Controls.Expander>defina as dimensões de tamanho <xref:System.Windows.Controls.ScrollViewer> no conteúdo do , ou se você quiser capacidade de rolagem, no que inclui o conteúdo.  
  
 Quando <xref:System.Windows.Controls.Expander> um controle é o <xref:System.Windows.Controls.DockPanel> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] último elemento <xref:System.Windows.Controls.Expander> em a , define automaticamente <xref:System.Windows.Controls.DockPanel>as dimensões para igualar a área restante do . Para evitar esse comportamento <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> padrão, <xref:System.Windows.Controls.DockPanel> defina `false`a propriedade no <xref:System.Windows.Controls.Expander> objeto para , <xref:System.Windows.Controls.DockPanel>ou certifique-se de que não é o último elemento em um .  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>Criando conteúdo rolável  
 Se o conteúdo for muito grande para o tamanho da área <xref:System.Windows.Controls.Expander> de <xref:System.Windows.Controls.ScrollViewer> conteúdo, você pode envolver o conteúdo de um em a, a fim de fornecer conteúdo rolável. O <xref:System.Windows.Controls.Expander> controle não fornece automaticamente capacidade de rolagem. A ilustração <xref:System.Windows.Controls.Expander> a seguir <xref:System.Windows.Controls.ScrollViewer> mostra um controle que contém um controle.  
  
 **Expansor em um ScrollViewer**  
  
 ![Captura de tela que mostra um expansor com ScrollBar.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Quando você <xref:System.Windows.Controls.Expander> coloca um <xref:System.Windows.Controls.ScrollViewer>controle <xref:System.Windows.Controls.ScrollViewer> em um , defina a <xref:System.Windows.Controls.Expander> propriedade de dimensão <xref:System.Windows.Controls.Expander> que corresponde à direção em que o conteúdo abre para o tamanho da área de conteúdo. Por exemplo, se <xref:System.Windows.Controls.Expander.ExpandDirection%2A> você definir <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.ExpandDirection.Down> a propriedade no para (a área <xref:System.Windows.Controls.ScrollViewer> de conteúdo abre), defina a <xref:System.Windows.FrameworkElement.Height%2A> propriedade no controle para a altura necessária para a área de conteúdo. Se você definir a dimensão de <xref:System.Windows.Controls.ScrollViewer> altura no conteúdo em si, não reconhece essa configuração e, portanto, não fornece conteúdo rolável.  
  
 O exemplo a seguir <xref:System.Windows.Controls.Expander> mostra como criar um controle <xref:System.Windows.Controls.ScrollViewer> que tenha conteúdo complexo e que contenha um controle. Este exemplo <xref:System.Windows.Controls.Expander> cria uma ilustração no início desta seção.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>Usando as propriedades de alinhamento  
 Você pode alinhar o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> conteúdo definindo as propriedades e as propriedades no <xref:System.Windows.Controls.Expander> controle. Quando você define essas propriedades, o alinhamento se aplica ao cabeçalho e também ao conteúdo expandido.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Tópicos de como fazer](expander-how-to-topics.md)

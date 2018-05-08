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
ms.openlocfilehash: abcc7c48c602aee742959b39bb5244563eaf4d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="expander-overview"></a>Visão geral do expansor
Um <xref:System.Windows.Controls.Expander> controle fornece uma maneira de fornecer o conteúdo em uma área expansível que lembra uma janela e inclui um cabeçalho.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Criando um expansor simples  
 O exemplo a seguir mostra como criar um simples <xref:System.Windows.Controls.Expander> controle. Este exemplo cria um <xref:System.Windows.Controls.Expander> parece ilustração anterior.  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 O <xref:System.Windows.Controls.ContentControl.Content%2A> e <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> de um <xref:System.Windows.Controls.Expander> também pode conter conteúdo complexo, como <xref:System.Windows.Controls.RadioButton> e <xref:System.Windows.Controls.Image> objetos.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Definindo a direção da área de conteúdo de expansão  
 Você pode definir a área de conteúdo de um <xref:System.Windows.Controls.Expander> controle para expandir em uma das quatro direções (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, ou <xref:System.Windows.Controls.ExpandDirection.Right>) usando o <xref:System.Windows.Controls.ExpandDirection> propriedade. Quando a área de conteúdo estiver recolhida, apenas o <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e o botão de alternância é exibida. Um <xref:System.Windows.Controls.Button> controle que exibe uma seta direcional é usado como um botão de alternância para expandir ou recolher a área de conteúdo. Quando expandido, o <xref:System.Windows.Controls.Expander> tenta exibir todo o conteúdo em uma área como de janela.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Controlando o tamanho de um expansor em um painel  
 Se um <xref:System.Windows.Controls.Expander> controle está dentro de um controle de layout que herda de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.StackPanel>, não especifique um <xref:System.Windows.FrameworkElement.Height%2A> no <xref:System.Windows.Controls.Expander> quando o <xref:System.Windows.Controls.Expander.ExpandDirection%2A> está definida como <xref:System.Windows.Controls.ExpandDirection.Down> ou <xref:System.Windows.Controls.ExpandDirection.Up>. Da mesma forma, não especifique um <xref:System.Windows.FrameworkElement.Width%2A> no <xref:System.Windows.Controls.Expander> quando o <xref:System.Windows.Controls.Expander.ExpandDirection%2A> está definida como <xref:System.Windows.Controls.ExpandDirection.Left> ou <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Quando você definir um tamanho de dimensão em um <xref:System.Windows.Controls.Expander> controle na direção que o conteúdo expandido é exibido, o <xref:System.Windows.Controls.Expander> assume o controle da área que é usada pelo conteúdo e exibirá uma borda ao redor dele. A borda é mostrada mesmo quando o conteúdo está recolhido. Para definir o tamanho da área de conteúdo expandido, defina dimensões de tamanho do conteúdo do <xref:System.Windows.Controls.Expander>, ou se você quiser rolagem recurso, no <xref:System.Windows.Controls.ScrollViewer> que inclui o conteúdo.  
  
 Quando um <xref:System.Windows.Controls.Expander> controle é o último elemento em um <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] define automaticamente o <xref:System.Windows.Controls.Expander> dimensões para igualar a área restante do <xref:System.Windows.Controls.DockPanel>. Para evitar esse comportamento padrão, defina o <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriedade o <xref:System.Windows.Controls.DockPanel> do objeto para `false`, ou certifique-se de que o <xref:System.Windows.Controls.Expander> não é o último elemento em um <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Criando conteúdo rolável  
 Se o conteúdo for muito grande para o tamanho da área de conteúdo, você pode encapsular o conteúdo de um <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> para fornecer conteúdo rolável. O <xref:System.Windows.Controls.Expander> controle não oferece automaticamente a capacidade de rolagem. A ilustração a seguir mostra um <xref:System.Windows.Controls.Expander> controle que contém um <xref:System.Windows.Controls.ScrollViewer> controle.  
  
 **Expansor em um ScrollViewer**  
  
 ![Expansor com ScrollBar](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Quando você coloca um <xref:System.Windows.Controls.Expander> controlar um <xref:System.Windows.Controls.ScrollViewer>, defina o <xref:System.Windows.Controls.ScrollViewer> dimensão propriedade que corresponda à direção na qual o <xref:System.Windows.Controls.Expander> conteúdo é aberto para o tamanho do <xref:System.Windows.Controls.Expander> área de conteúdo. Por exemplo, se você definir o <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriedade no <xref:System.Windows.Controls.Expander> para <xref:System.Windows.Controls.ExpandDirection.Down> (a área de conteúdo é aberto para baixo), definir o <xref:System.Windows.FrameworkElement.Height%2A> propriedade no <xref:System.Windows.Controls.ScrollViewer> controle à altura necessária para a área de conteúdo. Se você, em vez disso, defina a altura do conteúdo propriamente dito, <xref:System.Windows.Controls.ScrollViewer> não reconhece essa configuração e, portanto, não fornece conteúdo rolável.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Expander> controle que tem conteúdo complexo e que contém um <xref:System.Windows.Controls.ScrollViewer> controle. Este exemplo cria um <xref:System.Windows.Controls.Expander> que é como a ilustração no início desta seção.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Usando as propriedades de alinhamento  
 Você pode alinhar o conteúdo definindo a <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> e <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriedades de <xref:System.Windows.Controls.Expander> controle. Quando você define essas propriedades, o alinhamento se aplica ao cabeçalho e também ao conteúdo expandido.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)

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
ms.openlocfilehash: ddf6ee550e0eb6af5af44d032e85ecd5b735b951
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054920"
---
# <a name="expander-overview"></a>Visão geral do expansor
Um <xref:System.Windows.Controls.Expander> controle fornece uma maneira de fornecer o conteúdo em uma área expansível que lembra uma janela e inclui um cabeçalho.  

<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Criando um expansor simples  
 O exemplo a seguir mostra como criar um simples <xref:System.Windows.Controls.Expander> controle. Este exemplo cria um <xref:System.Windows.Controls.Expander> que se parece com a ilustração anterior.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 O <xref:System.Windows.Controls.ContentControl.Content%2A> e <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> de uma <xref:System.Windows.Controls.Expander> também podem conter conteúdo complexo, como <xref:System.Windows.Controls.RadioButton> e <xref:System.Windows.Controls.Image> objetos.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Definindo a direção da área de conteúdo de expansão  
 Você pode definir a área de conteúdo de um <xref:System.Windows.Controls.Expander> controle para expandir em uma das quatro direções (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, ou <xref:System.Windows.Controls.ExpandDirection.Right>) usando o <xref:System.Windows.Controls.ExpandDirection> propriedade. Quando a área de conteúdo estiver recolhida, apenas o <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> e seu botão de alternância aparecem. Um <xref:System.Windows.Controls.Button> controle que exibe uma seta direcional é usado como um botão de alternância para expandir ou recolher a área de conteúdo. Quando expandido, o <xref:System.Windows.Controls.Expander> tenta exibir todo o seu conteúdo em uma área tipo janela.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Controlando o tamanho de um expansor em um painel  
 Se um <xref:System.Windows.Controls.Expander> controle está dentro de um controle de layout que herda de <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.StackPanel>, não especificar um <xref:System.Windows.FrameworkElement.Height%2A> no <xref:System.Windows.Controls.Expander> quando o <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriedade é definida como <xref:System.Windows.Controls.ExpandDirection.Down> ou <xref:System.Windows.Controls.ExpandDirection.Up>. Da mesma forma, não especifique um <xref:System.Windows.FrameworkElement.Width%2A> sobre o <xref:System.Windows.Controls.Expander> quando o <xref:System.Windows.Controls.Expander.ExpandDirection%2A> estiver definida como <xref:System.Windows.Controls.ExpandDirection.Left> ou <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Quando você definir um tamanho de dimensão em um <xref:System.Windows.Controls.Expander> controle na direção que o conteúdo expandido é exibido, o <xref:System.Windows.Controls.Expander> assume o controle da área que é usada pelo conteúdo e exibe uma borda ao redor dele. A borda é mostrada mesmo quando o conteúdo está recolhido. Para definir o tamanho da área de conteúdo expandido, defina dimensões de tamanho no conteúdo do <xref:System.Windows.Controls.Expander>, ou se você quiser a capacidade, de rolagem no <xref:System.Windows.Controls.ScrollViewer> que inclui o conteúdo.  
  
 Quando um <xref:System.Windows.Controls.Expander> controle é o último elemento em um <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] define automaticamente o <xref:System.Windows.Controls.Expander> dimensões para igualar a área restante do <xref:System.Windows.Controls.DockPanel>. Para evitar esse comportamento padrão, defina as <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriedade no <xref:System.Windows.Controls.DockPanel> do objeto para `false`, ou certifique-se de que o <xref:System.Windows.Controls.Expander> não é o último elemento em um <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Criando conteúdo rolável  
 Se o conteúdo for muito grande para o tamanho da área de conteúdo, você pode dispor o conteúdo de um <xref:System.Windows.Controls.Expander> em um <xref:System.Windows.Controls.ScrollViewer> para fornecer conteúdo rolável. O <xref:System.Windows.Controls.Expander> controle não fornece automaticamente a capacidade de rolagem. A ilustração a seguir mostra uma <xref:System.Windows.Controls.Expander> controle que contém um <xref:System.Windows.Controls.ScrollViewer> controle.  
  
 **Expansor em um ScrollViewer**  
  
 ![Captura de tela que mostra um expansor com ScrollBar.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Quando você coloca um <xref:System.Windows.Controls.Expander> controlar em uma <xref:System.Windows.Controls.ScrollViewer>, defina o <xref:System.Windows.Controls.ScrollViewer> dimensão propriedade que corresponde à direção na qual o <xref:System.Windows.Controls.Expander> conteúdo é aberto para o tamanho do <xref:System.Windows.Controls.Expander> de área de conteúdo. Por exemplo, se você definir a <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriedade no <xref:System.Windows.Controls.Expander> para <xref:System.Windows.Controls.ExpandDirection.Down> (a área de conteúdo é aberto para baixo), definir a <xref:System.Windows.FrameworkElement.Height%2A> propriedade no <xref:System.Windows.Controls.ScrollViewer> controle para a altura necessária para a área de conteúdo. Se você definir em vez disso, a dimensão de altura no próprio conteúdo, <xref:System.Windows.Controls.ScrollViewer> não reconhece essa configuração e, portanto, não fornece conteúdo rolável.  
  
 O exemplo a seguir mostra como criar uma <xref:System.Windows.Controls.Expander> controle que tem conteúdo complexo e que contém um <xref:System.Windows.Controls.ScrollViewer> controle. Este exemplo cria um <xref:System.Windows.Controls.Expander> que é como a ilustração no início desta seção.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Usando as propriedades de alinhamento  
 Você pode alinhar o conteúdo, definindo o <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> e <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriedades no <xref:System.Windows.Controls.Expander> controle. Quando você define essas propriedades, o alinhamento se aplica ao cabeçalho e também ao conteúdo expandido.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Tópicos de instruções](expander-how-to-topics.md)

---
title: Visão geral de ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181948"
---
# <a name="tooltip-overview"></a>Visão geral de ToolTip
Uma dica de ferramenta é uma pequena janela pop-up que aparece quando um <xref:System.Windows.Controls.Button>usuário pausa o ponteiro do mouse sobre um elemento, como mais de um . Este tópico apresenta a dica de ferramenta e discute como criar e personalizar o conteúdo da dica de ferramenta.  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>O que é uma dica de ferramenta?  
 Quando um usuário move o ponteiro do mouse sobre um elemento que tem uma dica de ferramenta, aparecerá uma janela com conteúdo da dica de ferramenta (por exemplo, conteúdo de texto que descreve a função de um controle) por um período especificado. Se o usuário mover o ponteiro do mouse para fora do controle, a janela desaparecerá, pois o conteúdo da dica de ferramenta não poderá receber foco.  
  
 O conteúdo de uma dica de ferramenta pode conter uma ou mais linhas de texto, imagens, formas ou outros conteúdos visuais. Você define uma dica de ferramenta para um controle definindo uma das seguintes propriedades para o conteúdo da dica de ferramenta.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Qual propriedade você usa depende se o controle que define <xref:System.Windows.FrameworkContentElement> a <xref:System.Windows.FrameworkElement> dica de ferramenta herda da classe ou da classe.  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>Criando uma ToolTip  
 O exemplo a seguir mostra como criar <xref:System.Windows.FrameworkElement.ToolTip%2A> uma dica <xref:System.Windows.Controls.Button> de ferramenta simples definindo a propriedade para um controle em uma seqüência de texto.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Você também pode definir uma <xref:System.Windows.Controls.ToolTip> dica de ferramenta como um objeto. O exemplo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a seguir <xref:System.Windows.Controls.ToolTip> usa para especificar <xref:System.Windows.Controls.TextBox> um objeto como a dica de ferramenta de um elemento. Observe que o exemplo <xref:System.Windows.Controls.ToolTip> especifica <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> o definindo a propriedade.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 O exemplo a seguir <xref:System.Windows.Controls.ToolTip> usa código para gerar um objeto. O exemplo <xref:System.Windows.Controls.ToolTip> cria`tt`um ( ) <xref:System.Windows.Controls.Button>e associa-o a um .  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Você também pode criar conteúdo de dica <xref:System.Windows.Controls.ToolTip> de ferramenta que não é definido como um <xref:System.Windows.Controls.DockPanel>objeto, envolvendo o conteúdo da dica de ferramenta em um elemento de layout, como um . O exemplo a seguir <xref:System.Windows.FrameworkElement.ToolTip%2A> mostra como <xref:System.Windows.Controls.TextBox> definir a propriedade de <xref:System.Windows.Controls.DockPanel> um conteúdo que está incluído em um controle.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Usando as propriedades das classes ToolTip e ToolTipService  
 Você pode personalizar o conteúdo da dica de ferramenta definindo propriedades visuais e aplicando estilos. Se você definir o conteúdo <xref:System.Windows.Controls.ToolTip> da dica de ferramenta como <xref:System.Windows.Controls.ToolTip> um objeto, você pode definir as propriedades visuais do objeto. Caso contrário, você deve definir propriedades <xref:System.Windows.Controls.ToolTipService> anexadas equivalentes na classe.  
  
 Para obter um exemplo de como definir propriedades para especificar <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> posição do conteúdo da dica de ferramenta usando as propriedades e, consulte [Posicionar uma Dica de Ferramenta](how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>Definindo o estilo de uma ToolTip  
 Você pode <xref:System.Windows.Controls.ToolTip> estilizar a <xref:System.Windows.Style>definindo um costume . O exemplo a <xref:System.Windows.Style> seguir `Simple` define um chamado que <xref:System.Windows.Controls.ToolTip> mostra como compensar a <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>colocação do e alterar sua aparência definindo o , e <xref:System.Windows.Controls.Control.FontSize%2A> <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Usando as propriedades Intervalo de Tempo de ToolTipService  
 A <xref:System.Windows.Controls.ToolTipService> classe fornece as seguintes propriedades para <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>você <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>definir <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>os tempos de exibição da dica de ferramenta: , e .  
  
 Use <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> as <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriedades e para especificar um <xref:System.Windows.Controls.ToolTip> atraso, normalmente breve, <xref:System.Windows.Controls.ToolTip> antes de aparecer e também para especificar quanto tempo um permanece visível. Para obter mais informações, consulte [Como adiar a exibição de uma ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).  
  
 A <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade determina se as dicas de ferramentas para diferentes controles aparecem sem um atraso inicial quando você move o ponteiro do mouse rapidamente entre eles. Para obter mais <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> informações sobre a propriedade, consulte [Use o EntreMostrarDelay Property](how-to-use-the-betweenshowdelay-property.md).  
  
 O exemplo a seguir mostra como definir essas propriedades para uma dica de ferramenta.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Tópicos de como fazer](tooltip-how-to-topics.md)

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
ms.openlocfilehash: a11dcfc9030944365adda3656a8895912b0ef0d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399202"
---
# <a name="tooltip-overview"></a>Visão geral de ToolTip
Uma dica de ferramenta é uma pequena janela pop-up que aparece quando um usuário pausa o ponteiro do mouse sobre um elemento, como por um <xref:System.Windows.Controls.Button>. Este tópico apresenta a dica de ferramenta e discute como criar e personalizar o conteúdo da dica de ferramenta.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>O que é uma dica de ferramenta?  
 Quando um usuário move o ponteiro do mouse sobre um elemento que tem uma dica de ferramenta, aparecerá uma janela com conteúdo da dica de ferramenta (por exemplo, conteúdo de texto que descreve a função de um controle) por um período especificado. Se o usuário mover o ponteiro do mouse para fora do controle, a janela desaparecerá, pois o conteúdo da dica de ferramenta não poderá receber foco.  
  
 O conteúdo de uma dica de ferramenta pode conter uma ou mais linhas de texto, imagens, formas ou outros conteúdos visuais. Você define uma dica de ferramenta para um controle definindo uma das seguintes propriedades para o conteúdo da dica de ferramenta.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Propriedade que você usa depende se o controle que define a dica de ferramenta herda de <xref:System.Windows.FrameworkContentElement> ou <xref:System.Windows.FrameworkElement> classe.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Criando uma ToolTip  
 O exemplo a seguir mostra como criar uma dica de ferramenta simple, definindo o <xref:System.Windows.FrameworkElement.ToolTip%2A> propriedade para um <xref:System.Windows.Controls.Button> controle para uma cadeia de caracteres de texto.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Você também pode definir uma dica de ferramenta como um <xref:System.Windows.Controls.ToolTip> objeto. O exemplo a seguir usa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para especificar um <xref:System.Windows.Controls.ToolTip> objeto como a dica de ferramenta de um <xref:System.Windows.Controls.TextBox> elemento. Observe que o exemplo especifica o <xref:System.Windows.Controls.ToolTip> definindo o <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> propriedade.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 O exemplo a seguir usa o código para gerar um <xref:System.Windows.Controls.ToolTip> objeto. O exemplo cria um <xref:System.Windows.Controls.ToolTip> (`tt`) e o associa com um <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Você também pode criar o conteúdo da dica de ferramenta que não está definido como um <xref:System.Windows.Controls.ToolTip> objeto colocando o conteúdo da dica de ferramenta em um elemento de layout, como um <xref:System.Windows.Controls.DockPanel>. O exemplo a seguir mostra como definir a <xref:System.Windows.FrameworkElement.ToolTip%2A> propriedade de um <xref:System.Windows.Controls.TextBox> para o conteúdo que é colocado entre um <xref:System.Windows.Controls.DockPanel> controle.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Usando as propriedades das classes ToolTip e ToolTipService  
 Você pode personalizar o conteúdo da dica de ferramenta definindo propriedades visuais e aplicando estilos. Se você definir a dica de ferramenta com conteúdo como um <xref:System.Windows.Controls.ToolTip> do objeto, você pode definir as propriedades visuais do <xref:System.Windows.Controls.ToolTip> objeto. Caso contrário, você deve definir propriedades anexadas equivalentes no <xref:System.Windows.Controls.ToolTipService> classe.  
  
 Para obter um exemplo de como definir propriedades para especificar a posição do conteúdo da dica de ferramenta usando o <xref:System.Windows.Controls.ToolTip> e <xref:System.Windows.Controls.ToolTipService> propriedades, consulte [posicionar um ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Definindo o estilo de uma ToolTip  
 Você pode estilizar um <xref:System.Windows.Controls.ToolTip> definindo um personalizado <xref:System.Windows.Style>. O exemplo a seguir define uma <xref:System.Windows.Style> chamado `Simple` que mostra como deslocar o posicionamento do <xref:System.Windows.Controls.ToolTip> e alterar sua aparência, definindo o <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, e <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Usando as propriedades Intervalo de Tempo de ToolTipService  
 O <xref:System.Windows.Controls.ToolTipService> classe fornece as seguintes propriedades para definir a dica de ferramenta exibem tempos: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, e <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Use o <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> e <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriedades para especificar um atraso, normalmente breve, antes uma <xref:System.Windows.Controls.ToolTip> aparece e também para especificar por quanto tempo um <xref:System.Windows.Controls.ToolTip> permanece visível. Para obter mais informações, consulte [Como adiar a exibição de uma ToolTip](https://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 O <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade determina se as dicas de ferramentas para controles diferentes aparecem sem um atraso inicial quando você move o ponteiro do mouse rapidamente entre eles. Para obter mais informações sobre o <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriedade, consulte [usar a propriedade BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 O exemplo a seguir mostra como definir essas propriedades para uma dica de ferramenta.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)

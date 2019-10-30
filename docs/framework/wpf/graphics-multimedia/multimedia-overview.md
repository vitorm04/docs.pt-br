---
title: Visão geral de multimídia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039799"
---
# <a name="multimedia-overview"></a>Visão geral de multimídia
Recursos de multimídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permitem a integração de áudio e vídeo em seus aplicativos para aprimorar a experiência do usuário. Este tópico apresenta os recursos de multimídia do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>API de mídia  
 As classes <xref:System.Windows.Controls.MediaElement> e <xref:System.Windows.Media.MediaPlayer> são usadas para apresentar conteúdo de áudio ou vídeo. Essas classes podem ser controladas interativamente ou por um relógio. Essas classes podem ser usadas no controle do Microsoft Windows Media Player 10 para reprodução de mídia. A classe que você usa, dependendo do cenário.  
  
 <xref:System.Windows.Controls.MediaElement> é uma <xref:System.Windows.UIElement> que é suportada pelo [layout](../advanced/layout.md) e pode ser consumida como o conteúdo de muitos controles. Também é útil em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], assim como código. <xref:System.Windows.Media.MediaPlayer>, por outro lado, foi projetado para objetos de <xref:System.Windows.Media.Drawing> e falta de suporte a layout. A mídia carregada usando uma <xref:System.Windows.Media.MediaPlayer> só pode ser apresentada usando uma <xref:System.Windows.Media.VideoDrawing> ou interagindo diretamente com uma <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> não pode ser usada em XAML.  
  
 Para obter mais informações sobre objetos de desenho e contexto de desenho, consulte [visão geral de objetos de desenho](drawing-objects-overview.md).  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modos de reprodução de mídia  
  
> [!NOTE]
> Tanto <xref:System.Windows.Controls.MediaElement> quanto <xref:System.Windows.Media.MediaPlayer> têm Membros semelhantes. Os links nesta seção referem-se aos membros da classe <xref:System.Windows.Controls.MediaElement>. A menos que indicado especificamente, os membros vinculados ao na classe <xref:System.Windows.Controls.MediaElement> também podem ser encontrados na classe <xref:System.Windows.Media.MediaPlayer>.  
  
 Para entender a reprodução de mídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a compreensão dos diferentes modos em que a mídia pode ser executada é necessária. Tanto <xref:System.Windows.Controls.MediaElement> quanto <xref:System.Windows.Media.MediaPlayer> podem ser usados em dois modos de mídia diferentes, modo independente e modo de relógio. O modo de mídia é determinado pela propriedade <xref:System.Windows.Controls.MediaElement.Clock%2A>. Quando <xref:System.Windows.Controls.MediaElement.Clock%2A> é `null`, o objeto de mídia está no modo independente. Quando o <xref:System.Windows.Controls.MediaElement.Clock%2A> é não nulo, o objeto de mídia está no modo de relógio. Por padrão, os objetos de mídia estão no modo independente.  
  
### <a name="independent-mode"></a>Modo independente  
 No modo independente, o conteúdo de mídia conduz a reprodução de mídia. Modo independente permite as seguintes opções:  
  
- Os <xref:System.Uri> da mídia podem ser especificados diretamente.  
  
- Reprodução de mídia pode ser controlada diretamente.  
  
- As propriedades <xref:System.Windows.Controls.MediaElement.Position%2A> e <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> da mídia podem ser modificadas.  
  
 A mídia é carregada definindo a propriedade <xref:System.Windows.Controls.MediaElement.Source%2A> do objeto de <xref:System.Windows.Controls.MediaElement> ou chamando o método <xref:System.Windows.Media.MediaPlayer.Open%2A> do objeto de <xref:System.Windows.Media.MediaPlayer>.  
  
 Para controlar a reprodução de mídia no modo independente, métodos de controle do objeto de mídia podem ser usados. Os métodos de controle disponíveis são <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>e <xref:System.Windows.Controls.MediaElement.Stop%2A>. Por <xref:System.Windows.Controls.MediaElement>, o controle interativo usando esses métodos só estará disponível quando a <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> estiver definida como <xref:System.Windows.Controls.MediaState.Manual>. Esses métodos não estão disponíveis quando o objeto de mídia está no modo relógio.  
  
 Consulte [Controlar um MediaElement (executar, pausar, parar, volume e velocidade)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) para obter um exemplo de modo independente.  
  
### <a name="clock-mode"></a>Modo relógio  
 No modo de relógio, um <xref:System.Windows.Media.MediaTimeline> unidade de reprodução de mídia. O modo relógio tem as seguintes características:  
  
- A <xref:System.Uri> da mídia é definida indiretamente por meio de um <xref:System.Windows.Media.MediaTimeline>.  
  
- Reprodução de mídia pode ser controlada pelo relógio. Métodos de controle do objeto de mídia não podem ser usados.  
  
- A mídia é carregada definindo a propriedade <xref:System.Windows.Media.MediaTimeline.Source%2A> de um <xref:System.Windows.Media.MediaTimeline> objeto, criando o relógio na linha do tempo e atribuindo o relógio ao objeto de mídia. A mídia também é carregada dessa maneira quando um <xref:System.Windows.Media.MediaTimeline> dentro de um <xref:System.Windows.Media.Animation.Storyboard> tem como alvo uma <xref:System.Windows.Controls.MediaElement>.  
  
 Para controlar a reprodução de mídia no modo de relógio, os métodos de controle de <xref:System.Windows.Media.Animation.ClockController> devem ser usados. Uma <xref:System.Windows.Media.Animation.ClockController> é obtida da propriedade <xref:System.Windows.Media.Animation.ClockController> do <xref:System.Windows.Media.MediaClock>. Se você tentar usar os métodos de controle de um <xref:System.Windows.Controls.MediaElement> ou <xref:System.Windows.Media.MediaPlayer> objeto no modo de relógio, uma <xref:System.InvalidOperationException> será lançada.  
  
 Consulte a [Visão geral da Animação](animation-overview.md) para obter mais informações sobre linhas do tempo e relógios.  
  
 Consulte [controlar um MediaElement usando um Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md) para obter um exemplo de modo relógio.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 Adicionar mídia a um aplicativo é tão simples quanto adicionar um controle de <xref:System.Windows.Controls.MediaElement> à [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo e fornecer uma <xref:System.Uri> à mídia que você deseja incluir. Todos os tipos de mídia com suporte no Microsoft Windows Media Player 10 têm suporte no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O exemplo a seguir mostra um uso simples do <xref:System.Windows.Controls.MediaElement> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Neste exemplo, mídia será executada automaticamente assim que ele é carregada. Depois que a mídia tenha terminado sua execução, a mídia é fechada e todos os recursos de mídia são liberados (incluindo a memória de vídeo). Esse é o comportamento padrão do objeto <xref:System.Windows.Controls.MediaElement> e é controlado pelas propriedades <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  
  
### <a name="controlling-a-mediaelement"></a>Controlar um MediaElement  
 As propriedades <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> controlam o comportamento do <xref:System.Windows.Controls.MediaElement> quando <xref:System.Windows.FrameworkElement.IsLoaded%2A> é `true` ou `false`, respectivamente. O <xref:System.Windows.Controls.MediaState> as propriedades são definidas para afetar o comportamento de reprodução de mídia. Por exemplo, o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> padrão é <xref:System.Windows.Controls.MediaState.Play> e o <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> padrão é <xref:System.Windows.Controls.MediaState.Close>. Isso significa que assim que o <xref:System.Windows.Controls.MediaElement> for carregado e o prelance estiver concluído, a mídia começará a ser reproduzida. Após a conclusão da reprodução, mídia é fechada e todos os recursos de mídia são liberados.  
  
 As propriedades <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> não são a única maneira de controlar a reprodução de mídia. No modo de relógio, o relógio pode controlar a <xref:System.Windows.Controls.MediaElement> e os métodos de controle interativos têm controle quando o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> lida com essa competição para controle, avaliando as seguintes prioridades.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> Em vigor quando a mídia for descarregada. Isso garante que todos os recursos de mídia sejam liberados por padrão, mesmo quando um <xref:System.Windows.Media.MediaClock> estiver associado à <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock> Em vigor quando a mídia tem um <xref:System.Windows.Controls.MediaElement.Clock%2A>. Se a mídia for descarregada, o <xref:System.Windows.Media.MediaClock> entrará em vigor, contanto que o <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> seja <xref:System.Windows.Controls.MediaState.Manual>. O modo de relógio sempre substitui o comportamento carregado do <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> Em vigor quando a mídia for carregada.  
  
4. Métodos de controle interativo. Em vigor quando <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> for <xref:System.Windows.Controls.MediaState.Manual>. Os métodos de controle disponíveis são <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>e <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Exibir um MediaElement  
 Para exibir um <xref:System.Windows.Controls.MediaElement> ele deve ter conteúdo para renderizar e terá seu <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriedades definidas como zero até que o conteúdo seja carregado. Para conteúdo de somente áudio, essas propriedades serão sempre zero. Para conteúdo de vídeo, depois que o evento de <xref:System.Windows.Controls.MediaElement.MediaOpened> tiver sido gerado na <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A> relatará o tamanho da mídia carregada. Isso significa que, até que a mídia seja carregada, a <xref:System.Windows.Controls.MediaElement> não ocupará nenhum espaço físico na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], a menos que as propriedades <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> estejam definidas.  
  
 Definir as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> fará com que a mídia seja ampliada para preencher a área fornecida para o <xref:System.Windows.Controls.MediaElement>. Para preservar a taxa de proporção original da mídia, a propriedade <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> deve ser definida, mas não ambas. Definir as propriedades <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> fará com que a mídia apresente um tamanho de elemento fixo que pode não ser desejável.  
  
 Para evitar ter um elemento de tamanho fixo, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode executar pré-rolagem da mídia. Isso é feito definindo o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> como <xref:System.Windows.Controls.MediaState.Play> ou <xref:System.Windows.Controls.MediaState.Pause>. Em um estado de <xref:System.Windows.Controls.MediaState.Pause>, a mídia será prevertida e apresentará o primeiro quadro. Em um estado <xref:System.Windows.Controls.MediaState.Play>, a mídia será prevertida e começará a ser reproduzida.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Onde a classe <xref:System.Windows.Controls.MediaElement> é um elemento de estrutura, a classe <xref:System.Windows.Media.MediaPlayer> é projetada para ser usada em objetos <xref:System.Windows.Media.Drawing>. Os objetos de desenho são usados quando você pode sacrificar os recursos de nível de estrutura para obter benefícios de desempenho ou quando você precisa de <xref:System.Windows.Freezable> recursos. <xref:System.Windows.Media.MediaPlayer> permite que você aproveite esses recursos enquanto fornece conteúdo de mídia em seus aplicativos. Assim como <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> pode ser usado em modo independente ou de relógio, mas não tem os Estados descarregados e carregados do objeto <xref:System.Windows.Controls.MediaElement>. Isso reduz a complexidade do controle de reprodução da <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Controlando o Media Player  
 Como <xref:System.Windows.Media.MediaPlayer> é sem monitoração de estado, há apenas duas maneiras de controlar a reprodução de mídia.  
  
1. Métodos de controle interativo. Em vigor quando estiver no modo independente (`null`Propriedade<xref:System.Windows.Media.MediaPlayer.Clock%2A>).  
  
2. <xref:System.Windows.Media.MediaClock> Em vigor quando a mídia tem um <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Exibindo um MediaPlayer  
 Tecnicamente, uma <xref:System.Windows.Media.MediaPlayer> não pode ser exibida porque não tem nenhuma representação física. No entanto, ele pode ser usado para apresentar mídia em um <xref:System.Windows.Media.Drawing> usando a classe <xref:System.Windows.Media.VideoDrawing>. O exemplo a seguir demonstra o uso de um <xref:System.Windows.Media.VideoDrawing> para exibir a mídia.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Consulte a [visão geral de objetos de desenho](drawing-objects-overview.md) para obter mais informações sobre objetos de <xref:System.Windows.Media.Drawing>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingGroup>
- [Layout](../advanced/layout.md)
- [Tópicos explicativos](audio-and-video-how-to-topics.md)

---
title: Visão geral de multimídia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181879"
---
# <a name="multimedia-overview"></a>Visão geral de multimídia
Recursos de multimídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permitem a integração de áudio e vídeo em seus aplicativos para aprimorar a experiência do usuário. Este tópico apresenta os recursos de multimídia do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>
## <a name="media-api"></a>API de mídia  
 As <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> aulas são usadas para apresentar conteúdo de áudio ou vídeo. Essas classes podem ser controladas interativamente ou por um relógio. Essas classes podem ser usados no controle do Microsoft Windows Media Player 10 para reprodução de mídia. A classe que você usa, dependendo do cenário.  
  
 <xref:System.Windows.Controls.MediaElement>é <xref:System.Windows.UIElement> um que é suportado pelo [Layout](../advanced/layout.md) e pode ser consumido como o conteúdo de muitos controles. Também é útil em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], assim como código. <xref:System.Windows.Media.MediaPlayer>, por outro lado, <xref:System.Windows.Media.Drawing> é projetado para objetos e não tem suporte de layout. A mídia carregada <xref:System.Windows.Media.MediaPlayer> usando um só <xref:System.Windows.Media.VideoDrawing> pode ser apresentada <xref:System.Windows.Media.DrawingContext>usando uma ou interagindo diretamente com um . <xref:System.Windows.Media.MediaPlayer>não pode ser usado em XAML.  
  
 Para obter mais informações sobre objetos de desenho e contexto de desenho, consulte [visão geral de objetos de desenho](drawing-objects-overview.md).  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>Modos de reprodução de mídia  
  
> [!NOTE]
> Ambos <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> e têm membros semelhantes. Os links nesta seção <xref:System.Windows.Controls.MediaElement> referem-se aos membros da classe. A menos que especificamente notado, membros ligados <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> à classe também podem ser encontrados na classe.  
  
 Para entender a reprodução de mídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a compreensão dos diferentes modos em que a mídia pode ser executada é necessária. Ambos <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> podem ser usados em dois modos de mídia diferentes, modo independente e modo relógio. O modo de mídia <xref:System.Windows.Controls.MediaElement.Clock%2A> é determinado pela propriedade. Quando <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`é , o objeto de mídia está no modo independente. Quando <xref:System.Windows.Controls.MediaElement.Clock%2A> o objeto não é nulo, o objeto de mídia está no modo relógio. Por padrão, os objetos de mídia estão no modo independente.  
  
### <a name="independent-mode"></a>Modo independente  
 No modo independente, o conteúdo de mídia conduz a reprodução de mídia. Modo independente permite as seguintes opções:  
  
- Os meios de <xref:System.Uri> comunicação podem ser especificados diretamente.  
  
- Reprodução de mídia pode ser controlada diretamente.  
  
- Os meios de <xref:System.Windows.Controls.MediaElement.Position%2A> comunicação e <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriedades podem ser modificados.  
  
 A mídia é carregada <xref:System.Windows.Controls.MediaElement> definindo <xref:System.Windows.Controls.MediaElement.Source%2A> a propriedade do <xref:System.Windows.Media.MediaPlayer> objeto <xref:System.Windows.Media.MediaPlayer.Open%2A> ou chamando o método do objeto.  
  
 Para controlar a reprodução de mídia no modo independente, métodos de controle do objeto de mídia podem ser usados. Os métodos de <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>controle <xref:System.Windows.Controls.MediaElement.Close%2A>disponíveis <xref:System.Windows.Controls.MediaElement.Stop%2A>são, e . Para, <xref:System.Windows.Controls.MediaElement>o controle interativo usando esses <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> métodos <xref:System.Windows.Controls.MediaState.Manual>só está disponível quando o conjunto é definido para . Esses métodos não estão disponíveis quando o objeto de mídia está no modo relógio.  
  
 Consulte [Controlar um MediaElement (executar, pausar, parar, volume e velocidade)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) para obter um exemplo de modo independente.  
  
### <a name="clock-mode"></a>Modo relógio  
 No modo relógio, uma <xref:System.Windows.Media.MediaTimeline> reprodução de mídia impulsiona. O modo relógio tem as seguintes características:  
  
- A mídia <xref:System.Uri> é indiretamente <xref:System.Windows.Media.MediaTimeline>definida através de um .  
  
- Reprodução de mídia pode ser controlada pelo relógio. Métodos de controle do objeto de mídia não podem ser usados.  
  
- A mídia é carregada <xref:System.Windows.Media.MediaTimeline> definindo <xref:System.Windows.Media.MediaTimeline.Source%2A> a propriedade de um objeto, criando o relógio a partir da linha do tempo e atribuindo o relógio ao objeto de mídia. A mídia também é carregada <xref:System.Windows.Media.MediaTimeline> desta <xref:System.Windows.Media.Animation.Storyboard> forma <xref:System.Windows.Controls.MediaElement>quando um dentro de um alvo a .  
  
 Para controlar a reprodução da <xref:System.Windows.Media.Animation.ClockController> mídia no modo relógio, os métodos de controle devem ser usados. A <xref:System.Windows.Media.Animation.ClockController> é obtido <xref:System.Windows.Media.Animation.ClockController> a partir <xref:System.Windows.Media.MediaClock>da propriedade do . Se você tentar usar os métodos <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> de controle de um <xref:System.InvalidOperationException> ou objeto enquanto estiver no modo relógio, um será jogado.  
  
 Consulte a [Visão geral da Animação](animation-overview.md) para obter mais informações sobre linhas do tempo e relógios.  
  
 Consulte [controlar um MediaElement usando um Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md) para obter um exemplo de modo relógio.  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>Classe MediaElement  
 Adicionar mídia a um aplicativo é <xref:System.Windows.Controls.MediaElement> tão [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] simples quanto adicionar <xref:System.Uri> um controle ao aplicativo e fornecer um para a mídia que você deseja incluir. Todos os tipos de mídia suportados pelo Microsoft [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Windows Media Player 10 são suportados em . O exemplo a seguir mostra <xref:System.Windows.Controls.MediaElement> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]um simples uso do in .  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Neste exemplo, mídia será executada automaticamente assim que ele é carregada. Depois que a mídia tenha terminado sua execução, a mídia é fechada e todos os recursos de mídia são liberados (incluindo a memória de vídeo). Este é o comportamento <xref:System.Windows.Controls.MediaElement> padrão do objeto <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> e é controlado pelas propriedades e.  
  
### <a name="controlling-a-mediaelement"></a>Controlar um MediaElement  
 As <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriedades controlam o <xref:System.Windows.Controls.MediaElement> comportamento <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` do `false`quando é ou, respectivamente. As <xref:System.Windows.Controls.MediaState> propriedades são definidas para afetar o comportamento de reprodução de mídia. Por exemplo, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> o <xref:System.Windows.Controls.MediaState.Play> padrão <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Close>e o padrão é . Isso significa que assim <xref:System.Windows.Controls.MediaElement> que o pré-roll é carregado e o pré-roll é concluído, a mídia começa a jogar. Após a conclusão da reprodução, mídia é fechada e todos os recursos de mídia são liberados.  
  
 As <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriedades e as propriedades não são a única maneira de controlar a reprodução de mídia. No modo relógio, o <xref:System.Windows.Controls.MediaElement> relógio pode controlar os métodos <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>de controle interativos e os métodos de controle interativos têm controle quando o é . <xref:System.Windows.Controls.MediaElement>lida com essa competição de controle avaliando as seguintes prioridades.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Em vigor quando a mídia for descarregada. Isso garante que todos os recursos de mídia <xref:System.Windows.Media.MediaClock> sejam liberados por padrão, mesmo quando um está associado ao <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock>. No lugar quando <xref:System.Windows.Controls.MediaElement.Clock%2A>a mídia tem um . Se a mídia for <xref:System.Windows.Media.MediaClock> descarregada, a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>vontade entrará em vigor enquanto for. O modo relógio sempre substitui o <xref:System.Windows.Controls.MediaElement>comportamento carregado do .  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Em vigor quando a mídia for carregada.  
  
4. Métodos de controle interativo. No lugar <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>quando é . Os métodos de <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>controle <xref:System.Windows.Controls.MediaElement.Close%2A>disponíveis <xref:System.Windows.Controls.MediaElement.Stop%2A>são, e .  
  
### <a name="displaying-a-mediaelement"></a>Exibir um MediaElement  
 Para exibir <xref:System.Windows.Controls.MediaElement> um, ele deve ter conteúdo <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> para renderizar e terá suas propriedades definidas como zero até que o conteúdo seja carregado. Para conteúdo de somente áudio, essas propriedades serão sempre zero. Para conteúdo em <xref:System.Windows.Controls.MediaElement.MediaOpened> vídeo, uma vez <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> que o evento tenha sido levantado e informará o tamanho da mídia carregada. Isso significa que, até que <xref:System.Windows.Controls.MediaElement> a mídia seja carregada, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] não <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> haverá qualquer espaço físico, a menos que as propriedades estejam definidas.  
  
 A definição <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> tanto das propriedades quanto as propriedades fará com <xref:System.Windows.Controls.MediaElement>que a mídia se estique para preencher a área fornecida para o . Para preservar a proporção original da <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> mídia, ou a propriedade deve ser definida, mas não ambas. A configuração tanto das <xref:System.Windows.FrameworkElement.Width%2A> propriedades quanto <xref:System.Windows.FrameworkElement.Height%2A> as propriedades fará com que a mídia apresente um tamanho de elemento fixo que pode não ser desejável.  
  
 Para evitar ter um elemento de tamanho fixo, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode executar pré-rolagem da mídia. Isso é feito <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> definindo <xref:System.Windows.Controls.MediaState.Play> <xref:System.Windows.Controls.MediaState.Pause>o para ou ou . Em <xref:System.Windows.Controls.MediaState.Pause> um estado, a mídia irá pré-lançar e apresentará o primeiro quadro. Em <xref:System.Windows.Controls.MediaState.Play> um estado, a mídia vai pré-rolar e começar a jogar.  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Quando a <xref:System.Windows.Controls.MediaElement> classe é um <xref:System.Windows.Media.MediaPlayer> elemento-quadro, a <xref:System.Windows.Media.Drawing> classe é projetada para ser usada em objetos. Os objetos de desenho são usados quando você pode <xref:System.Windows.Freezable> sacrificar recursos de nível de estrutura para obter benefícios de desempenho ou quando você precisa de recursos. <xref:System.Windows.Media.MediaPlayer>permite que você aproveite esses recursos enquanto fornece conteúdo de mídia em seus aplicativos. Como <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> , pode ser usado no modo independente <xref:System.Windows.Controls.MediaElement> ou relógio, mas não tem os estados descarregados e carregados do objeto. Isso reduz a complexidade do <xref:System.Windows.Media.MediaPlayer>controle de reprodução do .  
  
### <a name="controlling-mediaplayer"></a>Controlando o Media Player  
 Por <xref:System.Windows.Media.MediaPlayer> ser apátrida, há apenas duas maneiras de controlar a reprodução de mídia.  
  
1. Métodos de controle interativo. No lugar quando em`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> modo independente (propriedade).  
  
2. <xref:System.Windows.Media.MediaClock>. No lugar quando <xref:System.Windows.Media.MediaPlayer.Clock%2A>a mídia tem um .  
  
### <a name="displaying-a-mediaplayer"></a>Exibindo um MediaPlayer  
 Tecnicamente, <xref:System.Windows.Media.MediaPlayer> não pode ser exibido, pois não tem representação física. No entanto, ele pode ser <xref:System.Windows.Media.Drawing> usado <xref:System.Windows.Media.VideoDrawing> para apresentar mídia em um uso da classe. O exemplo a seguir <xref:System.Windows.Media.VideoDrawing> demonstra o uso de uma mídia para exibir.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Consulte a visão geral dos <xref:System.Windows.Media.Drawing> [objetos de desenho](drawing-objects-overview.md) para obter mais informações sobre objetos.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.DrawingGroup>
- [Layout](../advanced/layout.md)
- [Tópicos de como fazer](audio-and-video-how-to-topics.md)

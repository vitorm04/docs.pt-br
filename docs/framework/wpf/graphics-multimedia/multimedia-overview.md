---
title: "Visão geral de multimídia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7097f5bd58573315681c61d0380e58638a4c4fb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="multimedia-overview"></a>Visão geral de multimídia
Recursos de multimídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permitem a integração de áudio e vídeo em seus aplicativos para aprimorar a experiência do usuário. Este tópico apresenta os recursos de multimídia do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>API de mídia  
 O <xref:System.Windows.Controls.MediaElement> e <xref:System.Windows.Media.MediaPlayer> classes são usadas para apresentar conteúdo de áudio ou vídeo. Essas classes podem ser controladas interativamente ou por um relógio. Essas classes podem ser usadas no controle do [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 para reprodução de mídia. A classe que você usa, dependendo do cenário.  
  
 <xref:System.Windows.Controls.MediaElement>é um <xref:System.Windows.UIElement> que tem suporte a [Layout](../../../../docs/framework/wpf/advanced/layout.md) e pode ser consumido como o conteúdo de vários controles. Também é útil em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], assim como código. <xref:System.Windows.Media.MediaPlayer>, por outro lado, foi projetado para <xref:System.Windows.Media.Drawing> objetos e não tem suporte de layout. Mídia carregada usando um <xref:System.Windows.Media.MediaPlayer> só podem ser exibidas usando um <xref:System.Windows.Media.VideoDrawing> ou interagindo diretamente com um <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>não pode ser usado em XAML.  
  
 Para obter mais informações sobre objetos de desenho e contexto de desenho, consulte [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modos de reprodução de mídia  
  
> [!NOTE]
>  Ambos <xref:System.Windows.Controls.MediaElement> e <xref:System.Windows.Media.MediaPlayer> têm membros semelhantes. Os links nesta seção se referem a <xref:System.Windows.Controls.MediaElement> membros de classe. A menos que especificamente observado, os membros vinculados no <xref:System.Windows.Controls.MediaElement> classe também pode ser encontrada no <xref:System.Windows.Media.MediaPlayer> classe.  
  
 Para entender a reprodução de mídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a compreensão dos diferentes modos em que a mídia pode ser executada é necessária. Ambos <xref:System.Windows.Controls.MediaElement> e <xref:System.Windows.Media.MediaPlayer> podem ser usados em dois modos de mídia diferentes, o modo independente e o modo de relógio. O modo de mídia é determinado pelo <xref:System.Windows.Controls.MediaElement.Clock%2A> propriedade. Quando <xref:System.Windows.Controls.MediaElement.Clock%2A> é `null`, o objeto de mídia está em modo independente. Quando o <xref:System.Windows.Controls.MediaElement.Clock%2A> é não nulo, o objeto de mídia está em modo de relógio. Por padrão, os objetos de mídia estão no modo independente.  
  
### <a name="independent-mode"></a>Modo independente  
 No modo independente, o conteúdo de mídia conduz a reprodução de mídia. Modo independente permite as seguintes opções:  
  
-   Da mídia <xref:System.Uri> pode ser especificada diretamente.  
  
-   Reprodução de mídia pode ser controlada diretamente.  
  
-   Da mídia <xref:System.Windows.Controls.MediaElement.Position%2A> e <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriedades podem ser modificadas.  
  
 Mídia é carregada ou definindo o <xref:System.Windows.Controls.MediaElement> do objeto <xref:System.Windows.Controls.MediaElement.Source%2A> propriedade ou chamando o <xref:System.Windows.Media.MediaPlayer> do objeto <xref:System.Windows.Media.MediaPlayer.Open%2A> método.  
  
 Para controlar a reprodução de mídia no modo independente, métodos de controle do objeto de mídia podem ser usados. Os métodos de controle disponíveis são <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, e <xref:System.Windows.Controls.MediaElement.Stop%2A>. Para <xref:System.Windows.Controls.MediaElement>, usando esses métodos de controle interativo está disponível apenas quando o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é definido como <xref:System.Windows.Controls.MediaState.Manual>. Esses métodos não estão disponíveis quando o objeto de mídia está no modo relógio.  
  
 Consulte [Controlar um MediaElement (executar, pausar, parar, volume e velocidade)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) para obter um exemplo de modo independente.  
  
### <a name="clock-mode"></a>Modo relógio  
 No modo de relógio, um <xref:System.Windows.Media.MediaTimeline> reprodução de mídia de unidades. O modo relógio tem as seguintes características:  
  
-   Da mídia <xref:System.Uri> está definida indiretamente por meio de um <xref:System.Windows.Media.MediaTimeline>.  
  
-   Reprodução de mídia pode ser controlada pelo relógio. Métodos de controle do objeto de mídia não podem ser usados.  
  
-   Mídia é carregada, definindo um <xref:System.Windows.Media.MediaTimeline> do objeto <xref:System.Windows.Media.MediaTimeline.Source%2A> propriedade, criando o relógio da linha do tempo e atribuindo o relógio para o objeto de mídia. Mídia também é carregada dessa maneira quando um <xref:System.Windows.Media.MediaTimeline> dentro de um <xref:System.Windows.Media.Animation.Storyboard> destinos um <xref:System.Windows.Controls.MediaElement>.  
  
 Para controlar a reprodução de mídia no modo de relógio, o <xref:System.Windows.Media.Animation.ClockController> métodos de controle devem ser usados. Um <xref:System.Windows.Media.Animation.ClockController> é obtida a <xref:System.Windows.Media.Animation.ClockController> propriedade o <xref:System.Windows.Media.MediaClock>. Se você tentar usar os métodos de controle de um <xref:System.Windows.Controls.MediaElement> ou <xref:System.Windows.Media.MediaPlayer> do objeto no modo de relógio, um <xref:System.InvalidOperationException> será lançada.  
  
 Consulte a [Visão geral da Animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) para obter mais informações sobre linhas do tempo e relógios.  
  
 Consulte [controlar um MediaElement usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md) para obter um exemplo de modo relógio.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 Adicionando a mídia para um aplicativo é tão simple quanto adicionando um <xref:System.Windows.Controls.MediaElement> o controle para o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplicativo e fornecendo um <xref:System.Uri> na mídia que você deseja incluir. Todos os tipos de mídia com suporte ao [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 têm suporte em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O exemplo a seguir mostra um uso simple do <xref:System.Windows.Controls.MediaElement> em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Neste exemplo, mídia será executada automaticamente assim que ele é carregada. Depois que a mídia tenha terminado sua execução, a mídia é fechada e todos os recursos de mídia são liberados (incluindo a memória de vídeo). Esse é o comportamento padrão da <xref:System.Windows.Controls.MediaElement> do objeto e é controlado pelo <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriedades.  
  
### <a name="controlling-a-mediaelement"></a>Controlar um MediaElement  
 O <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriedades controlam o comportamento de <xref:System.Windows.Controls.MediaElement> quando <xref:System.Windows.FrameworkElement.IsLoaded%2A> é `true` ou `false`, respectivamente. O <xref:System.Windows.Controls.MediaState> as propriedades são definidas para afetar o comportamento de reprodução de mídia. Por exemplo, o padrão <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Play> e o padrão <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Close>. Isso significa que, assim como o <xref:System.Windows.Controls.MediaElement> é carregado e o pré-avanço for concluída, a mídia começa a ser executada. Após a conclusão da reprodução, mídia é fechada e todos os recursos de mídia são liberados.  
  
 O <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> propriedades não são a única maneira de controlar a reprodução de mídia. No modo de relógio, o relógio pode controlar o <xref:System.Windows.Controls.MediaElement> e os métodos de controle interativo tiver o controle quando o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>manipula essa competição por controle avaliando as prioridades a seguir.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Em vigor quando a mídia for descarregada. Isso garante que todos os recursos de mídia são liberados por padrão, mesmo quando um <xref:System.Windows.Media.MediaClock> está associado a <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. Em vigor quando a mídia tem um <xref:System.Windows.Controls.MediaElement.Clock%2A>. Se a mídia é descarregada, o <xref:System.Windows.Media.MediaClock> entrará em vigor, contanto que o <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Manual>. Modo de relógio sempre substitui o comportamento de carregado do <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Em vigor quando a mídia for carregada.  
  
4.  Métodos de controle interativo. Coloca quando <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Manual>. Os métodos de controle disponíveis são <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, e <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Exibir um MediaElement  
 Para exibir um <xref:System.Windows.Controls.MediaElement> deve ter conteúdo para processar e ele terá seu <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A> propriedades definidas como zero até que o conteúdo é carregado. Para conteúdo de somente áudio, essas propriedades serão sempre zero. Para conteúdo de vídeo, uma vez a <xref:System.Windows.Controls.MediaElement.MediaOpened> evento foi gerado o <xref:System.Windows.FrameworkElement.ActualWidth%2A> e <xref:System.Windows.FrameworkElement.ActualHeight%2A> relatará o tamanho da mídia carregada. Isso significa que, até que a mídia é carregada, o <xref:System.Windows.Controls.MediaElement> não entrará em qualquer espaço físico no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , a menos que o <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> propriedades são definidas.  
  
 Configurar ambos o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades fará com que a mídia a ser esticada para preencher a área fornecida para o <xref:System.Windows.Controls.MediaElement>. Para preservar a taxa de proporção original da mídia, ou o <xref:System.Windows.FrameworkElement.Width%2A> ou <xref:System.Windows.FrameworkElement.Height%2A> propriedade deve ser definido, mas não ambos. Configurar ambos o <xref:System.Windows.FrameworkElement.Width%2A> e <xref:System.Windows.FrameworkElement.Height%2A> propriedades fará com que a mídia presente em um tamanho fixo de elemento que pode não ser desejável.  
  
 Para evitar ter um elemento de tamanho fixo, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode executar pré-rolagem da mídia. Isso é feito definindo o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> como <xref:System.Windows.Controls.MediaState.Play> ou <xref:System.Windows.Controls.MediaState.Pause>. Em um <xref:System.Windows.Controls.MediaState.Pause> de estado, a mídia será pré-rolar e apresentará o primeiro quadro. Em um <xref:System.Windows.Controls.MediaState.Play> de estado, a mídia será pré-rolar e começa a ser executado.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Enquanto o <xref:System.Windows.Controls.MediaElement> classe é um elemento de estrutura, o <xref:System.Windows.Media.MediaPlayer> classe foi projetada para ser usado em <xref:System.Windows.Media.Drawing> objetos. Objetos de desenho são usados quando você puder sacrificar características de nível de framework para obter benefícios de desempenho ou quando você precisar <xref:System.Windows.Freezable> recursos. <xref:System.Windows.Media.MediaPlayer>permite que você tire proveito desses recursos ao fornecimento de conteúdo de mídia em seus aplicativos. Como <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> podem ser usados em independentes ou de relógio modo mas não não tem o <xref:System.Windows.Controls.MediaElement> objeto descarregado e carregados estados. Isso reduz a complexidade do controle de reprodução do <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Controlando o Media Player  
 Porque <xref:System.Windows.Media.MediaPlayer> é sem monitoração de estado, há apenas duas maneiras para controlar a reprodução de mídia.  
  
1.  Métodos de controle interativo. Em vigor quando no modo independente (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> propriedade).  
  
2.  <xref:System.Windows.Media.MediaClock>. Em vigor quando a mídia tem um <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Exibindo um MediaPlayer  
 Tecnicamente, um <xref:System.Windows.Media.MediaPlayer> não pode ser exibida porque não tem nenhuma representação física. No entanto, ele pode ser usado para apresentar a mídia em um <xref:System.Windows.Media.Drawing> usando o <xref:System.Windows.Media.VideoDrawing> classe. O exemplo a seguir demonstra o uso de um <xref:System.Windows.Media.VideoDrawing> para exibir a mídia.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Consulte o [visão geral de objetos de desenho](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) para obter mais informações sobre <xref:System.Windows.Media.Drawing> objetos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.DrawingGroup>  
 [Layout](../../../../docs/framework/wpf/advanced/layout.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)

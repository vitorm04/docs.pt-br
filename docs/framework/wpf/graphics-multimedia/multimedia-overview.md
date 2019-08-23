---
title: Visão geral de multimídia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929615"
---
# <a name="multimedia-overview"></a>Visão geral de multimídia
Recursos de multimídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permitem a integração de áudio e vídeo em seus aplicativos para aprimorar a experiência do usuário. Este tópico apresenta os recursos de multimídia do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>API de mídia  
 As <xref:System.Windows.Controls.MediaElement> classes <xref:System.Windows.Media.MediaPlayer> e são usadas para apresentar conteúdo de áudio ou vídeo. Essas classes podem ser controladas interativamente ou por um relógio. Essas classes podem ser usadas no controle do [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 para reprodução de mídia. A classe que você usa, dependendo do cenário.  
  
 <xref:System.Windows.Controls.MediaElement>é um <xref:System.Windows.UIElement> que tem suporte no [layout](../advanced/layout.md) e pode ser consumido como o conteúdo de muitos controles. Também é útil em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], assim como código. <xref:System.Windows.Media.MediaPlayer>, por outro lado, foi projetado para objetos <xref:System.Windows.Media.Drawing> e falta de suporte a layout. A mídia carregada usando <xref:System.Windows.Media.MediaPlayer> um só pode ser apresentada usando <xref:System.Windows.Media.VideoDrawing> um ou diretamente interagindo com um <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>Não pode ser usado em XAML.  
  
 Para obter mais informações sobre objetos de desenho e contexto de desenho, consulte [visão geral de objetos de desenho](drawing-objects-overview.md).  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Modos de reprodução de mídia  
  
> [!NOTE]
> Ambos <xref:System.Windows.Controls.MediaElement> e<xref:System.Windows.Media.MediaPlayer> têm Membros semelhantes. Os links nesta seção referem-se <xref:System.Windows.Controls.MediaElement> aos membros da classe. A menos que indicado especificamente, os membros vinculados à <xref:System.Windows.Controls.MediaElement> classe também podem ser encontrados <xref:System.Windows.Media.MediaPlayer> na classe.  
  
 Para entender a reprodução de mídia no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a compreensão dos diferentes modos em que a mídia pode ser executada é necessária. Ambos <xref:System.Windows.Controls.MediaElement> e<xref:System.Windows.Media.MediaPlayer> podem ser usados em dois modos de mídia diferentes, modo independente e modo de relógio. O modo de mídia é determinado pela <xref:System.Windows.Controls.MediaElement.Clock%2A> propriedade. Quando <xref:System.Windows.Controls.MediaElement.Clock%2A> é`null`, o objeto de mídia está no modo independente. Quando o <xref:System.Windows.Controls.MediaElement.Clock%2A> é não nulo, o objeto de mídia está no modo de relógio. Por padrão, os objetos de mídia estão no modo independente.  
  
### <a name="independent-mode"></a>Modo independente  
 No modo independente, o conteúdo de mídia conduz a reprodução de mídia. Modo independente permite as seguintes opções:  
  
- A mídia <xref:System.Uri> pode ser especificada diretamente.  
  
- Reprodução de mídia pode ser controlada diretamente.  
  
- As mídias <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>eas propriedades podem ser modificadas. <xref:System.Windows.Controls.MediaElement.Position%2A>  
  
 A mídia é <xref:System.Windows.Controls.MediaElement> carregada definindo a propriedade do <xref:System.Windows.Controls.MediaElement.Source%2A> objeto ou chamando o <xref:System.Windows.Media.MediaPlayer> método do <xref:System.Windows.Media.MediaPlayer.Open%2A> objeto.  
  
 Para controlar a reprodução de mídia no modo independente, métodos de controle do objeto de mídia podem ser usados. Os métodos de controle disponíveis <xref:System.Windows.Controls.MediaElement.Play%2A>são <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>,, e <xref:System.Windows.Controls.MediaElement.Stop%2A>. Para <xref:System.Windows.Controls.MediaElement>, o controle interativo usando esses métodos só está disponível quando <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> o é definido <xref:System.Windows.Controls.MediaState.Manual>como. Esses métodos não estão disponíveis quando o objeto de mídia está no modo relógio.  
  
 Consulte [Controlar um MediaElement (executar, pausar, parar, volume e velocidade)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) para obter um exemplo de modo independente.  
  
### <a name="clock-mode"></a>Modo relógio  
 No modo de relógio, <xref:System.Windows.Media.MediaTimeline> uma reprodução de mídia de unidades. O modo relógio tem as seguintes características:  
  
- A mídia <xref:System.Windows.Media.MediaTimeline>é definida indiretamente por meio de um. <xref:System.Uri>  
  
- Reprodução de mídia pode ser controlada pelo relógio. Métodos de controle do objeto de mídia não podem ser usados.  
  
- A mídia é carregada definindo a <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline.Source%2A> propriedade de um objeto, criando o relógio na linha do tempo e atribuindo o relógio ao objeto de mídia. A mídia também é carregada dessa maneira quando <xref:System.Windows.Media.MediaTimeline> um dentro <xref:System.Windows.Media.Animation.Storyboard> de um <xref:System.Windows.Controls.MediaElement>destino é um.  
  
 Para controlar a reprodução de mídia no modo de <xref:System.Windows.Media.Animation.ClockController> relógio, os métodos de controle devem ser usados. Um <xref:System.Windows.Media.Animation.ClockController> é obtido <xref:System.Windows.Media.Animation.ClockController> da Propriedade do <xref:System.Windows.Media.MediaClock>. Se você tentar usar os métodos de controle de um <xref:System.Windows.Controls.MediaElement> objeto ou <xref:System.Windows.Media.MediaPlayer> no modo de relógio, um <xref:System.InvalidOperationException> será gerado.  
  
 Consulte a [Visão geral da Animação](animation-overview.md) para obter mais informações sobre linhas do tempo e relógios.  
  
 Consulte [controlar um MediaElement usando um Storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md) para obter um exemplo de modo relógio.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Classe MediaElement  
 Adicionar mídia a um aplicativo é tão simples quanto adicionar um <xref:System.Windows.Controls.MediaElement> controle [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ao do aplicativo e fornecer um <xref:System.Uri> para a mídia que você deseja incluir. Todos os tipos de mídia com suporte ao [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 têm suporte em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. O exemplo a seguir mostra um uso simples do <xref:System.Windows.Controls.MediaElement> no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 Neste exemplo, mídia será executada automaticamente assim que ele é carregada. Depois que a mídia tenha terminado sua execução, a mídia é fechada e todos os recursos de mídia são liberados (incluindo a memória de vídeo). Esse é o comportamento padrão do <xref:System.Windows.Controls.MediaElement> objeto e é controlado <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> pelas propriedades e <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> .  
  
### <a name="controlling-a-mediaelement"></a>Controlar um MediaElement  
 As <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedades <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> e <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` controlam o comportamento do `false`quando é ou, respectivamente. <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaState> As propriedades são definidas para afetar o comportamento de reprodução de mídia. Por exemplo, o padrão <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Play> e o padrão <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> é <xref:System.Windows.Controls.MediaState.Close>. Isso significa que, assim que o <xref:System.Windows.Controls.MediaElement> for carregado e o prelance estiver concluído, a mídia começará a ser reproduzida. Após a conclusão da reprodução, mídia é fechada e todos os recursos de mídia são liberados.  
  
 As <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedades <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> e não são a única maneira de controlar a reprodução de mídia. No modo de relógio, o relógio pode controlar <xref:System.Windows.Controls.MediaElement> o e os métodos de controle interativos <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> têm <xref:System.Windows.Controls.MediaState.Manual>controle quando o é. <xref:System.Windows.Controls.MediaElement>lida com essa competição para controle, avaliando as seguintes prioridades.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. Em vigor quando a mídia for descarregada. Isso garante que todos os recursos de mídia sejam liberados por padrão, <xref:System.Windows.Media.MediaClock> mesmo quando um estiver <xref:System.Windows.Controls.MediaElement>associado ao.  
  
2. <xref:System.Windows.Media.MediaClock>. Em vigor quando a mídia tiver <xref:System.Windows.Controls.MediaElement.Clock%2A>um. Se a mídia for descarregada, o <xref:System.Windows.Media.MediaClock> terá efeito, desde <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> que seja. <xref:System.Windows.Controls.MediaState.Manual> O modo de relógio sempre substitui o comportamento carregado <xref:System.Windows.Controls.MediaElement>do.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. Em vigor quando a mídia for carregada.  
  
4. Métodos de controle interativo. Em vigor quando <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> for <xref:System.Windows.Controls.MediaState.Manual>. Os métodos de controle disponíveis <xref:System.Windows.Controls.MediaElement.Play%2A>são <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>,, e <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Exibir um MediaElement  
 Para exibir um <xref:System.Windows.Controls.MediaElement> , ele deve ter conteúdo para renderizar e terá suas <xref:System.Windows.FrameworkElement.ActualWidth%2A> propriedades <xref:System.Windows.FrameworkElement.ActualHeight%2A> e definidas como zero até que o conteúdo seja carregado. Para conteúdo de somente áudio, essas propriedades serão sempre zero. Para conteúdo de vídeo, depois <xref:System.Windows.Controls.MediaElement.MediaOpened> que o evento tiver sido <xref:System.Windows.FrameworkElement.ActualWidth%2A> acionado, o e <xref:System.Windows.FrameworkElement.ActualHeight%2A> o relatarão o tamanho da mídia carregada. Isso significa que, até que a mídia seja <xref:System.Windows.Controls.MediaElement> carregada, o não ocupará nenhum espaço físico [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] no, <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> menos que as propriedades ou sejam definidas.  
  
 Definir as <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> fará com que a mídia seja ampliada para preencher a área fornecida para <xref:System.Windows.Controls.MediaElement>o. Para preservar a taxa de proporção original da mídia, a <xref:System.Windows.FrameworkElement.Width%2A> propriedade <xref:System.Windows.FrameworkElement.Height%2A> ou deve ser definida, mas não ambas. Definir as <xref:System.Windows.FrameworkElement.Width%2A> Propriedades e <xref:System.Windows.FrameworkElement.Height%2A> fará com que a mídia apresente em um tamanho de elemento fixo que pode não ser desejável.  
  
 Para evitar ter um elemento de tamanho fixo, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pode executar pré-rolagem da mídia. Isso é feito definindo o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> como ou <xref:System.Windows.Controls.MediaState.Pause>. Em um <xref:System.Windows.Controls.MediaState.Pause> estado, a mídia será prevertida e apresentará o primeiro quadro. Em um <xref:System.Windows.Controls.MediaState.Play> estado, a mídia será prevertida e começará a ser reproduzida.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Classe MediaPlayer  
 Onde a <xref:System.Windows.Controls.MediaElement> classe é um elemento de estrutura, a <xref:System.Windows.Media.MediaPlayer> classe é projetada para ser usada em <xref:System.Windows.Media.Drawing> objetos. Os objetos de desenho são usados quando você pode sacrificar os recursos de nível de estrutura para obter benefícios <xref:System.Windows.Freezable> de desempenho ou quando você precisa de recursos. <xref:System.Windows.Media.MediaPlayer>permite que você aproveite esses recursos enquanto fornece conteúdo de mídia em seus aplicativos. Like <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Controls.MediaElement> , <xref:System.Windows.Media.MediaPlayer> pode ser usado em modo independente ou de relógio, mas não tem os Estados descarregados e carregados do objeto. Isso reduz a complexidade do controle de reprodução <xref:System.Windows.Media.MediaPlayer>do.  
  
### <a name="controlling-mediaplayer"></a>Controlando o Media Player  
 Como <xref:System.Windows.Media.MediaPlayer> o é sem monitoração de estado, há apenas duas maneiras de controlar a reprodução de mídia.  
  
1. Métodos de controle interativo. Em vigor quando estiver no modo independente`null` (<xref:System.Windows.Media.MediaPlayer.Clock%2A> Propriedade).  
  
2. <xref:System.Windows.Media.MediaClock>. Em vigor quando a mídia tiver <xref:System.Windows.Media.MediaPlayer.Clock%2A>um.  
  
### <a name="displaying-a-mediaplayer"></a>Exibindo um MediaPlayer  
 Tecnicamente, um <xref:System.Windows.Media.MediaPlayer> não pode ser exibido porque não tem nenhuma representação física. No entanto, ele pode ser usado para apresentar a <xref:System.Windows.Media.Drawing> mídia em <xref:System.Windows.Media.VideoDrawing> um usando a classe. O exemplo a seguir demonstra o uso de <xref:System.Windows.Media.VideoDrawing> um para exibir a mídia.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Consulte a [visão geral de objetos de desenho](drawing-objects-overview.md) para <xref:System.Windows.Media.Drawing> obter mais informações sobre objetos.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingGroup>
- [Layout](../advanced/layout.md)
- [Tópicos de instruções](audio-and-video-how-to-topics.md)

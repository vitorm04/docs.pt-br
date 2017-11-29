---
title: Como controlar um MediaElement usando um storyboard
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2341d2814e5bd42c652865c76d115defcc5b15b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Como controlar um MediaElement usando um storyboard
Este exemplo mostra como controlar um <xref:System.Windows.Controls.MediaElement> usando um <xref:System.Windows.Media.MediaTimeline> em um <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Exemplo  
 Quando você usa um <xref:System.Windows.Media.MediaTimeline> em uma <xref:System.Windows.Media.Animation.Storyboard> para controlar o tempo de um <xref:System.Windows.Controls.MediaElement>, a funcionalidade é idêntica à funcionalidade de outros <xref:System.Windows.Media.Animation.Timeline> objetos, como animações. Por exemplo, um <xref:System.Windows.Media.MediaTimeline> usa <xref:System.Windows.Media.Animation.Timeline> propriedades como o <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade para especificar quando iniciar um <xref:System.Windows.Controls.MediaElement> (Iniciar a reprodução de mídia). Ele também usa o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade para especificar quanto tempo o <xref:System.Windows.Controls.MediaElement> está ativa (duração da reprodução de mídia). Para obter mais informações sobre como usar <xref:System.Windows.Media.Animation.Timeline> objetos com um <xref:System.Windows.Media.Animation.Storyboard>, consulte [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Este exemplo mostra como criar um reprodutor de mídia simples que usa um <xref:System.Windows.Media.MediaTimeline> para controlar a reprodução. O player de mídia inclui botões de reprodução, retomada, reinício e parada. O player também tem um <xref:System.Windows.Controls.Slider> controle que atua como uma barra de progresso.  
  
 O exemplo a seguir cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para o player de mídia.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 O exemplo a seguir cria a funcionalidade para a barra de progresso.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)

---
title: Como executar mídia com animações
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 21c9b35828dca03c05def11cff22f1f1e33d45cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-media-with-animations"></a>Como executar mídia com animações
Este exemplo mostra como reproduzir mídia e animações ao mesmo tempo usando o <xref:System.Windows.Media.MediaTimeline> e <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes no mesmo <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Exemplo  
 Você pode usar um ou mais <xref:System.Windows.Media.MediaTimeline> objetos em um <xref:System.Windows.Media.Animation.Storyboard> junto com outros <xref:System.Windows.Media.Animation.Timeline> objetos, como animações.  
  
 O exemplo a seguir define o <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> propriedade o <xref:System.Windows.Media.Animation.Storyboard> para um valor de `Slip`, que especifica que a animação não progride até que o andamento de mídia (vídeo neste exemplo). Essa funcionalidade pode ser necessária se a reprodução de mídia é atrasada devido ao tempo de carregamento.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)

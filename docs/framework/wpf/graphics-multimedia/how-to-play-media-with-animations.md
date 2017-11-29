---
title: "Como executar mídia com animações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 [Tópicos explicativos](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Visão geral de storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)

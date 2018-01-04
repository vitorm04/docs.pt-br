---
title: Como controlar um MediaElement (executar, pausar, parar, volume e velocidade)
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
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57b140391526c5b2a0e73a8bab2355ae445b395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Como controlar um MediaElement (executar, pausar, parar, volume e velocidade)
O exemplo a seguir mostra como controlar a reprodução de mídia usando um <xref:System.Windows.Controls.MediaElement>. O exemplo cria um player de mídia simples que permite reproduzir, pausar, parar, retroceder e avançar a mídia, bem como ajustar a taxa de velocidade e o volume.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria a interface do usuário.  
  
> [!NOTE]
>  O <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedade <xref:System.Windows.Controls.MediaElement> deve ser definido como `Manual` para poder interativamente parar, pausar e reproduzir a mídia.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir implementa a funcionalidade dos controles de interface do usuário de exemplo. O <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, e <xref:System.Windows.Controls.MediaElement.Stop%2A> métodos são usados para respectivamente executar, pausar e parar a mídia. Alterando o <xref:System.Windows.Controls.MediaElement.Position%2A> propriedade o <xref:System.Windows.Controls.MediaElement> permite que você ignore em torno de mídia. Por fim, o <xref:System.Windows.Controls.MediaElement.Volume%2A> e <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> propriedades são usadas para ajustar a velocidade de reprodução e volume de mídia.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Controlar um MediaElement usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md)

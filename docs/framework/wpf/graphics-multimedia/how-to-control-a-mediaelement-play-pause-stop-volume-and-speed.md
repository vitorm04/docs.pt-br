---
title: 'Como: Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930156"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>Como: Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)
O exemplo a seguir mostra como controlar a reprodução de mídia usando <xref:System.Windows.Controls.MediaElement>um. O exemplo cria um player de mídia simples que permite reproduzir, pausar, parar, retroceder e avançar a mídia, bem como ajustar a taxa de velocidade e o volume.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria a interface do usuário.  
  
> [!NOTE]
> A <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> propriedade de <xref:System.Windows.Controls.MediaElement> deve ser definida como `Manual` para poder parar, pausar e reproduzir a mídia interativamente.  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir implementa a funcionalidade dos controles de interface do usuário de exemplo. Os <xref:System.Windows.Controls.MediaElement.Play%2A>métodos <xref:System.Windows.Controls.MediaElement.Pause%2A>, e<xref:System.Windows.Controls.MediaElement.Stop%2A> são usados para reproduzir, pausar e parar a mídia respectivamente. Alterar a <xref:System.Windows.Controls.MediaElement.Position%2A> propriedade <xref:System.Windows.Controls.MediaElement> do permite que você pule na mídia. Por fim, <xref:System.Windows.Controls.MediaElement.Volume%2A> as <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> Propriedades e são usadas para ajustar o volume e a velocidade de reprodução da mídia.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Controlar um MediaElement usando um storyboard](how-to-control-a-mediaelement-by-using-a-storyboard.md)

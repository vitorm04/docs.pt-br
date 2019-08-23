---
title: 'Como: Executar mídia usando um VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956963"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Como: Executar mídia usando um VideoDrawing
Para reproduzir um arquivo de áudio ou de vídeo, use <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer>um. Há duas maneiras de carregar e reproduzir mídia. A <xref:System.Windows.Media.MediaPlayer> primeira é usar um e um <xref:System.Windows.Media.VideoDrawing> por si só, e a segunda maneira é criar seu próprio <xref:System.Windows.Media.MediaTimeline> para uso com o e <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>o.  
  
> [!NOTE]
> Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer> um para reproduzir um arquivo de vídeo uma vez.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Para obter controle de tempo adicional sobre a mídia, use <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> os <xref:System.Windows.Media.VideoDrawing> objetos e. O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> os <xref:System.Windows.Media.VideoDrawing> objetos e para reproduzir um vídeo repetidamente.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Observe que <xref:System.Windows.Media.MediaTimeline>, ao usar um, você usa o interativo <xref:System.Windows.Media.Animation.ClockController> retornado <xref:System.Windows.Media.MediaClock> da <xref:System.Windows.Media.Animation.Clock.Controller%2A> Propriedade do para controlar a reprodução de mídia em vez dos métodos interativos <xref:System.Windows.Media.MediaPlayer>do.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.VideoDrawing>
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)

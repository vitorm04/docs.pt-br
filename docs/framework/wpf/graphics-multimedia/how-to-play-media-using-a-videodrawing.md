---
title: 'Como: Executar mídia usando um VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 186c9ae8167dafd09f029418c1d23f81f7a9e906
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203607"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>Como: Executar mídia usando um VideoDrawing
Para reproduzir um arquivo de áudio ou vídeo, você deve usar um <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer>. Há duas maneiras de carregar e reproduzir mídia. A primeira é usar um <xref:System.Windows.Media.MediaPlayer> e uma <xref:System.Windows.Media.VideoDrawing> por si só e a segunda maneira é criar seu próprio <xref:System.Windows.Media.MediaTimeline> para usar com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing>.  
  
> [!NOTE]
>  Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem. Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer> para reproduzir um arquivo de vídeo uma vez.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Para obter controle adicional sobre a mídia de tempo, use uma <xref:System.Windows.Media.MediaTimeline> com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing> objetos. O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma <xref:System.Windows.Media.MediaTimeline> com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing> objetos para reproduzir um vídeo repetidamente.  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 Observe que, quando você usa um <xref:System.Windows.Media.MediaTimeline>, você usar o interactive <xref:System.Windows.Media.Animation.ClockController> retornados da <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade do <xref:System.Windows.Media.MediaClock> para controlar a reprodução de mídia em vez dos métodos interativos do <xref:System.Windows.Media.MediaPlayer>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.VideoDrawing>
- [Visão geral dos objetos de desenho](drawing-objects-overview.md)

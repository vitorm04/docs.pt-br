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
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="35893-102">Como: Executar mídia usando um VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="35893-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="35893-103">Para reproduzir um arquivo de áudio ou de vídeo, use <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer>um.</span><span class="sxs-lookup"><span data-stu-id="35893-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="35893-104">Há duas maneiras de carregar e reproduzir mídia.</span><span class="sxs-lookup"><span data-stu-id="35893-104">There are two ways to load and play media.</span></span> <span data-ttu-id="35893-105">A <xref:System.Windows.Media.MediaPlayer> primeira é usar um e um <xref:System.Windows.Media.VideoDrawing> por si só, e a segunda maneira é criar seu próprio <xref:System.Windows.Media.MediaTimeline> para uso com o e <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>o.</span><span class="sxs-lookup"><span data-stu-id="35893-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35893-106">Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem.</span><span class="sxs-lookup"><span data-stu-id="35893-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="35893-107">Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.</span><span class="sxs-lookup"><span data-stu-id="35893-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35893-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35893-108">Example</span></span>  
 <span data-ttu-id="35893-109">O exemplo a seguir usa <xref:System.Windows.Media.VideoDrawing> um e <xref:System.Windows.Media.MediaPlayer> um para reproduzir um arquivo de vídeo uma vez.</span><span class="sxs-lookup"><span data-stu-id="35893-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="35893-110">Para obter controle de tempo adicional sobre a mídia, use <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> os <xref:System.Windows.Media.VideoDrawing> objetos e.</span><span class="sxs-lookup"><span data-stu-id="35893-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="35893-111">O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetido.</span><span class="sxs-lookup"><span data-stu-id="35893-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35893-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35893-112">Example</span></span>  
 <span data-ttu-id="35893-113">O exemplo a seguir usa <xref:System.Windows.Media.MediaTimeline> um com <xref:System.Windows.Media.MediaPlayer> os <xref:System.Windows.Media.VideoDrawing> objetos e para reproduzir um vídeo repetidamente.</span><span class="sxs-lookup"><span data-stu-id="35893-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="35893-114">Observe que <xref:System.Windows.Media.MediaTimeline>, ao usar um, você usa o interativo <xref:System.Windows.Media.Animation.ClockController> retornado <xref:System.Windows.Media.MediaClock> da <xref:System.Windows.Media.Animation.Clock.Controller%2A> Propriedade do para controlar a reprodução de mídia em vez dos métodos interativos <xref:System.Windows.Media.MediaPlayer>do.</span><span class="sxs-lookup"><span data-stu-id="35893-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35893-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35893-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="35893-116">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="35893-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)

---
title: 'Como: Executar mídia usando um VideoDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 186c9ae8167dafd09f029418c1d23f81f7a9e906
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926057"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="054b2-102">Como: Executar mídia usando um VideoDrawing</span><span class="sxs-lookup"><span data-stu-id="054b2-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="054b2-103">Para reproduzir um arquivo de áudio ou vídeo, você deve usar um <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="054b2-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="054b2-104">Há duas maneiras de carregar e reproduzir mídia.</span><span class="sxs-lookup"><span data-stu-id="054b2-104">There are two ways to load and play media.</span></span> <span data-ttu-id="054b2-105">A primeira é usar um <xref:System.Windows.Media.MediaPlayer> e uma <xref:System.Windows.Media.VideoDrawing> por si só e a segunda maneira é criar seu próprio <xref:System.Windows.Media.MediaTimeline> para usar com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="054b2-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="054b2-106">Ao distribuir mídia com seu aplicativo, você não pode usar um arquivo de mídia como um recurso do projeto, como faria com uma imagem.</span><span class="sxs-lookup"><span data-stu-id="054b2-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="054b2-107">Em seu arquivo de projeto, em vez disso, você deve definir o tipo de mídia como `Content` e defina `CopyToOutputDirectory` para `PreserveNewest` ou `Always`.</span><span class="sxs-lookup"><span data-stu-id="054b2-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="054b2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="054b2-108">Example</span></span>  
 <span data-ttu-id="054b2-109">O exemplo a seguir usa uma <xref:System.Windows.Media.VideoDrawing> e um <xref:System.Windows.Media.MediaPlayer> para reproduzir um arquivo de vídeo uma vez.</span><span class="sxs-lookup"><span data-stu-id="054b2-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="054b2-110">Para obter controle adicional sobre a mídia de tempo, use uma <xref:System.Windows.Media.MediaTimeline> com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing> objetos.</span><span class="sxs-lookup"><span data-stu-id="054b2-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="054b2-111">O <xref:System.Windows.Media.MediaTimeline> permite que você especifique se o vídeo deve ser repetida.</span><span class="sxs-lookup"><span data-stu-id="054b2-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="054b2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="054b2-112">Example</span></span>  
 <span data-ttu-id="054b2-113">O exemplo a seguir usa uma <xref:System.Windows.Media.MediaTimeline> com o <xref:System.Windows.Media.MediaPlayer> e <xref:System.Windows.Media.VideoDrawing> objetos para reproduzir um vídeo repetidamente.</span><span class="sxs-lookup"><span data-stu-id="054b2-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="054b2-114">Observe que, quando você usa um <xref:System.Windows.Media.MediaTimeline>, você usar o interactive <xref:System.Windows.Media.Animation.ClockController> retornados da <xref:System.Windows.Media.Animation.Clock.Controller%2A> propriedade do <xref:System.Windows.Media.MediaClock> para controlar a reprodução de mídia em vez dos métodos interativos do <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="054b2-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054b2-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="054b2-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="054b2-116">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="054b2-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)

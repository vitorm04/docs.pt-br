---
title: 'Como: Controlar um MediaElement usando um Storyboard'
ms.date: 03/30/2017
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
ms.openlocfilehash: ae785e11b1da0f2c408b24021ad46ab071419378
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100308"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="f83cb-102">Como: Controlar um MediaElement usando um Storyboard</span><span class="sxs-lookup"><span data-stu-id="f83cb-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="f83cb-103">Este exemplo mostra como controlar um <xref:System.Windows.Controls.MediaElement> usando um <xref:System.Windows.Media.MediaTimeline> em um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="f83cb-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f83cb-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f83cb-104">Example</span></span>  
 <span data-ttu-id="f83cb-105">Quando você usa um <xref:System.Windows.Media.MediaTimeline> em um <xref:System.Windows.Media.Animation.Storyboard> para controlar a duração de uma <xref:System.Windows.Controls.MediaElement>, a funcionalidade é idêntica à funcionalidade de outros <xref:System.Windows.Media.Animation.Timeline> objetos, como animações.</span><span class="sxs-lookup"><span data-stu-id="f83cb-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="f83cb-106">Por exemplo, uma <xref:System.Windows.Media.MediaTimeline> usa <xref:System.Windows.Media.Animation.Timeline> propriedades como o <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade para especificar quando iniciar um <xref:System.Windows.Controls.MediaElement> (Iniciar a reprodução de mídia).</span><span class="sxs-lookup"><span data-stu-id="f83cb-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="f83cb-107">Ele também usa o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade para especificar quanto tempo o <xref:System.Windows.Controls.MediaElement> está ativo (duração da reprodução de mídia).</span><span class="sxs-lookup"><span data-stu-id="f83cb-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="f83cb-108">Para obter mais informações sobre como usar <xref:System.Windows.Media.Animation.Timeline> objetos com um <xref:System.Windows.Media.Animation.Storyboard>, consulte [visão geral de Storyboards](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f83cb-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="f83cb-109">Este exemplo mostra como criar um player de mídia simples que usa um <xref:System.Windows.Media.MediaTimeline> para controlar a reprodução.</span><span class="sxs-lookup"><span data-stu-id="f83cb-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="f83cb-110">O player de mídia inclui botões de reprodução, retomada, reinício e parada.</span><span class="sxs-lookup"><span data-stu-id="f83cb-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="f83cb-111">O reprodutor também tem um <xref:System.Windows.Controls.Slider> controle que atua como uma barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="f83cb-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="f83cb-112">O exemplo a seguir cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para o player de mídia.</span><span class="sxs-lookup"><span data-stu-id="f83cb-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="f83cb-113">O exemplo a seguir cria a funcionalidade para a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="f83cb-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f83cb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f83cb-114">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="f83cb-115">Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)</span><span class="sxs-lookup"><span data-stu-id="f83cb-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="f83cb-116">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="f83cb-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="f83cb-117">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="f83cb-117">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="f83cb-118">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="f83cb-118">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="f83cb-119">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f83cb-119">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="f83cb-120">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="f83cb-120">Graphics and Multimedia</span></span>](index.md)

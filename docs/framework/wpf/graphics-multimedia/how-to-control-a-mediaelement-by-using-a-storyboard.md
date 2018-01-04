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
ms.workload: dotnet
ms.openlocfilehash: f52801ee3704c13ec5213cfc54b6392baa97e245
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="95f64-102">Como controlar um MediaElement usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="95f64-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="95f64-103">Este exemplo mostra como controlar um <xref:System.Windows.Controls.MediaElement> usando um <xref:System.Windows.Media.MediaTimeline> em um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="95f64-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95f64-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95f64-104">Example</span></span>  
 <span data-ttu-id="95f64-105">Quando você usa um <xref:System.Windows.Media.MediaTimeline> em uma <xref:System.Windows.Media.Animation.Storyboard> para controlar o tempo de um <xref:System.Windows.Controls.MediaElement>, a funcionalidade é idêntica à funcionalidade de outros <xref:System.Windows.Media.Animation.Timeline> objetos, como animações.</span><span class="sxs-lookup"><span data-stu-id="95f64-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="95f64-106">Por exemplo, um <xref:System.Windows.Media.MediaTimeline> usa <xref:System.Windows.Media.Animation.Timeline> propriedades como o <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> propriedade para especificar quando iniciar um <xref:System.Windows.Controls.MediaElement> (Iniciar a reprodução de mídia).</span><span class="sxs-lookup"><span data-stu-id="95f64-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="95f64-107">Ele também usa o <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade para especificar quanto tempo o <xref:System.Windows.Controls.MediaElement> está ativa (duração da reprodução de mídia).</span><span class="sxs-lookup"><span data-stu-id="95f64-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="95f64-108">Para obter mais informações sobre como usar <xref:System.Windows.Media.Animation.Timeline> objetos com um <xref:System.Windows.Media.Animation.Storyboard>, consulte [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95f64-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="95f64-109">Este exemplo mostra como criar um reprodutor de mídia simples que usa um <xref:System.Windows.Media.MediaTimeline> para controlar a reprodução.</span><span class="sxs-lookup"><span data-stu-id="95f64-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="95f64-110">O player de mídia inclui botões de reprodução, retomada, reinício e parada.</span><span class="sxs-lookup"><span data-stu-id="95f64-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="95f64-111">O player também tem um <xref:System.Windows.Controls.Slider> controle que atua como uma barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="95f64-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="95f64-112">O exemplo a seguir cria o [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para o player de mídia.</span><span class="sxs-lookup"><span data-stu-id="95f64-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="95f64-113">O exemplo a seguir cria a funcionalidade para a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="95f64-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="95f64-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95f64-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="95f64-115">Controlar um MediaElement (reproduzir, pausar, parar, volume e velocidade)</span><span class="sxs-lookup"><span data-stu-id="95f64-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="95f64-116">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="95f64-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="95f64-117">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="95f64-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="95f64-118">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="95f64-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="95f64-119">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="95f64-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="95f64-120">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="95f64-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)

---
title: 'Como: Reproduzir mídia com animações'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 200f9d62c67a02088fe5a5789cdb41a04837d430
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921661"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="6ad1c-102">Como: Reproduzir mídia com animações</span><span class="sxs-lookup"><span data-stu-id="6ad1c-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="6ad1c-103">Este exemplo mostra como reproduzir mídia e animações ao mesmo tempo usando o <xref:System.Windows.Media.MediaTimeline> e <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes no mesmo <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="6ad1c-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ad1c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ad1c-104">Example</span></span>  
 <span data-ttu-id="6ad1c-105">Você pode usar um ou mais <xref:System.Windows.Media.MediaTimeline> objetos em um <xref:System.Windows.Media.Animation.Storyboard> junto com outros <xref:System.Windows.Media.Animation.Timeline> objetos, como animações.</span><span class="sxs-lookup"><span data-stu-id="6ad1c-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="6ad1c-106">O exemplo a seguir define o <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> propriedade do <xref:System.Windows.Media.Animation.Storyboard> com um valor de `Slip`, que especifica que a animação progride até que o andamento da mídia (vídeo, neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="6ad1c-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="6ad1c-107">Essa funcionalidade pode ser necessário se a reprodução de mídia está atrasada devido ao tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="6ad1c-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6ad1c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ad1c-108">See also</span></span>

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [<span data-ttu-id="6ad1c-109">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="6ad1c-109">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="6ad1c-110">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="6ad1c-110">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="6ad1c-111">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="6ad1c-111">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6ad1c-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="6ad1c-112">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="6ad1c-113">Elementos gráficos e multimídia</span><span class="sxs-lookup"><span data-stu-id="6ad1c-113">Graphics and Multimedia</span></span>](index.md)

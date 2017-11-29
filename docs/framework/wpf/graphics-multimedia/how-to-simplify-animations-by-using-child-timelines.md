---
title: "Como simplificar animações usando linhas do tempo filho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daa4caac0046293e8b86a773bfffd46cf30e835b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="35943-102">Como simplificar animações usando linhas do tempo filho</span><span class="sxs-lookup"><span data-stu-id="35943-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="35943-103">Este exemplo mostra como simplificar animações usando filho <xref:System.Windows.Media.Animation.ParallelTimeline> objetos.</span><span class="sxs-lookup"><span data-stu-id="35943-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="35943-104">Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de <xref:System.Windows.Media.Animation.Timeline> que fornece informações de direcionamento para o cronogramas que ele contém.</span><span class="sxs-lookup"><span data-stu-id="35943-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="35943-105">Use um <xref:System.Windows.Media.Animation.Storyboard> para fornecer informações, incluindo informações de objeto e propriedade de direcionamento da linha do tempo.</span><span class="sxs-lookup"><span data-stu-id="35943-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="35943-106">Para começar uma animação, use um ou mais <xref:System.Windows.Media.Animation.ParallelTimeline> objetos como elementos aninhados filhos de um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="35943-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="35943-107">Essas <xref:System.Windows.Media.Animation.ParallelTimeline> objetos podem conter outras animações e portanto, podem melhor encapsular as sequências de tempo em animações complexas.</span><span class="sxs-lookup"><span data-stu-id="35943-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="35943-108">Por exemplo, se são animar uma <xref:System.Windows.Controls.TextBlock> e várias formas da mesma <xref:System.Windows.Media.Animation.Storyboard>, você pode separar as animações a <xref:System.Windows.Controls.TextBlock> e formas, colocando cada uma em um separado <xref:System.Windows.Media.Animation.ParallelTimeline>.</span><span class="sxs-lookup"><span data-stu-id="35943-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="35943-109">Como cada <xref:System.Windows.Media.Animation.ParallelTimeline> tem seu próprio <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> e todos os elementos filho do <xref:System.Windows.Media.Animation.ParallelTimeline> começar em relação a esse <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, temporização é melhor encapsulada.</span><span class="sxs-lookup"><span data-stu-id="35943-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="35943-110">O exemplo a seguir anima dois pedaços de texto (<xref:System.Windows.Controls.TextBlock> objetos) de dentro do mesmo <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="35943-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="35943-111">Um <xref:System.Windows.Media.Animation.ParallelTimeline> encapsula as animações de um do <xref:System.Windows.Controls.TextBlock> objetos.</span><span class="sxs-lookup"><span data-stu-id="35943-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="35943-112">**Observação de desempenho:** Embora você possa aninhar <xref:System.Windows.Media.Animation.Storyboard> cronogramas, <xref:System.Windows.Media.Animation.ParallelTimeline>s são mais adequadas para aninhamento, pois requerem menos sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="35943-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="35943-113">(O <xref:System.Windows.Media.Animation.Storyboard> classe herda o <xref:System.Windows.Media.Animation.ParallelTimeline> classe.)</span><span class="sxs-lookup"><span data-stu-id="35943-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="35943-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35943-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="35943-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35943-115">See Also</span></span>  
 [<span data-ttu-id="35943-116">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="35943-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="35943-117">Especificar HandoffBehavior entre animações de storyboard</span><span class="sxs-lookup"><span data-stu-id="35943-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)

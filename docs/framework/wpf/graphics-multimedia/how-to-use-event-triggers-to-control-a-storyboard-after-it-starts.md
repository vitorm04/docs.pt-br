---
title: "Como usar gatilhos de evento para controlar um storyboard depois de ter começado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9e096969713cc4b9c42261b238691d51cb49d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="82660-102">Como usar gatilhos de evento para controlar um storyboard depois de ter começado</span><span class="sxs-lookup"><span data-stu-id="82660-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="82660-103">Este exemplo mostra como controlar um <xref:System.Windows.Media.Animation.Storyboard> após ele ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="82660-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="82660-104">Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, que distribui as animações aos objetos e propriedades que ele anima e, em seguida, inicia o storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="82660-105">Se você fornecer <xref:System.Windows.Media.Animation.BeginStoryboard> especificando um nome de seu <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriedade, você torná-lo um storyboard controlável.</span><span class="sxs-lookup"><span data-stu-id="82660-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="82660-106">Você pode então controlar interativamente o storyboard depois que ele for iniciado.</span><span class="sxs-lookup"><span data-stu-id="82660-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="82660-107">Use as seguintes ações de storyboard em conjunto com <xref:System.Windows.EventTrigger> objetos para controlar um storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="82660-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="82660-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.</span><span class="sxs-lookup"><span data-stu-id="82660-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="82660-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="82660-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final do período de preenchimento, se ele tiver um.</span><span class="sxs-lookup"><span data-stu-id="82660-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="82660-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="82660-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>Remove o storyboard, liberando recursos.</span><span class="sxs-lookup"><span data-stu-id="82660-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82660-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82660-114">Example</span></span>  
 <span data-ttu-id="82660-115">No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.</span><span class="sxs-lookup"><span data-stu-id="82660-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="82660-116">**Observação:** para ver um exemplo de como controlar um storyboard usando um código, consulte [Controlar um Storyboard depois de ter começado usando os método interativos](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="82660-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="82660-117">Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="82660-117">For additional examples, see the [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82660-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82660-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="82660-119">Controlar um storyboard depois de ter começado usando os métodos interativos</span><span class="sxs-lookup"><span data-stu-id="82660-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="82660-120">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="82660-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="82660-121">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="82660-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)

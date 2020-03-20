---
title: Como usar gatilhos de evento para controlar um storyboard depois de ter começado
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186711"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="95265-102">Como usar gatilhos de evento para controlar um storyboard depois de ter começado</span><span class="sxs-lookup"><span data-stu-id="95265-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="95265-103">Este exemplo mostra como <xref:System.Windows.Media.Animation.Storyboard> controlar um depois de iniciado.</span><span class="sxs-lookup"><span data-stu-id="95265-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="95265-104">Para iniciar <xref:System.Windows.Media.Animation.Storyboard> um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]usando <xref:System.Windows.Media.Animation.BeginStoryboard>, use , que distribui as animações para os objetos e propriedades que eles animam e, em seguida, inicia o storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="95265-105">Se você <xref:System.Windows.Media.Animation.BeginStoryboard> der um <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> nome especificando sua propriedade, você o torna um storyboard controlável.</span><span class="sxs-lookup"><span data-stu-id="95265-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="95265-106">Você pode então controlar interativamente o storyboard depois que ele for iniciado.</span><span class="sxs-lookup"><span data-stu-id="95265-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="95265-107">Use as seguintes ações <xref:System.Windows.EventTrigger> de storyboard juntamente com objetos para controlar um storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="95265-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="95265-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.</span><span class="sxs-lookup"><span data-stu-id="95265-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="95265-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Muda a velocidade do storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="95265-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Adianta um storyboard até o final do seu período de preenchimento, se tiver um.</span><span class="sxs-lookup"><span data-stu-id="95265-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="95265-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Pare o storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="95265-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard, liberando recursos.</span><span class="sxs-lookup"><span data-stu-id="95265-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="95265-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95265-114">Example</span></span>

<span data-ttu-id="95265-115">No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.</span><span class="sxs-lookup"><span data-stu-id="95265-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="95265-116">Para ver um exemplo de controle de um storyboard usando código, consulte [Controle um Storyboard depois que ele começar a usar seus métodos interativos](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="95265-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="95265-117">Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="95265-117">For additional examples, see the [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

## <a name="see-also"></a><span data-ttu-id="95265-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="95265-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="95265-119">Controlar um Storyboard depois de ter começado usando os métodos interativos</span><span class="sxs-lookup"><span data-stu-id="95265-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="95265-120">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="95265-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="95265-121">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="95265-121">Storyboards Overview</span></span>](storyboards-overview.md)

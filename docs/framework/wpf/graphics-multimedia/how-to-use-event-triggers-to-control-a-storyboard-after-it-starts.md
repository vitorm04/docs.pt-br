---
title: 'Como: Usar gatilhos de evento para controlar um Storyboard depois de ter começado'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855855"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="b5f74-102">Como: Usar gatilhos de evento para controlar um Storyboard depois de ter começado</span><span class="sxs-lookup"><span data-stu-id="b5f74-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="b5f74-103">Este exemplo mostra como controlar um <xref:System.Windows.Media.Animation.Storyboard> depois que ele é iniciado.</span><span class="sxs-lookup"><span data-stu-id="b5f74-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="b5f74-104">Para iniciar um <xref:System.Windows.Media.Animation.Storyboard> usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]o, use <xref:System.Windows.Media.Animation.BeginStoryboard>o, que distribui as animações para os objetos e as propriedades que eles animam e, em seguida, inicia o storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="b5f74-105">Se você der <xref:System.Windows.Media.Animation.BeginStoryboard> um nome especificando sua <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> Propriedade, você o tornará um storyboard controlável.</span><span class="sxs-lookup"><span data-stu-id="b5f74-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="b5f74-106">Você pode então controlar interativamente o storyboard depois que ele for iniciado.</span><span class="sxs-lookup"><span data-stu-id="b5f74-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="b5f74-107">Use as seguintes ações de storyboard junto <xref:System.Windows.EventTrigger> com objetos para controlar um Storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="b5f74-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pausa o storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="b5f74-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Retoma um storyboard pausado.</span><span class="sxs-lookup"><span data-stu-id="b5f74-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="b5f74-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Altera a velocidade do storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="b5f74-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avança um storyboard até o final de seu período de preenchimento, se ele tiver um.</span><span class="sxs-lookup"><span data-stu-id="b5f74-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="b5f74-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Para o storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="b5f74-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Remove o storyboard, liberando recursos.</span><span class="sxs-lookup"><span data-stu-id="b5f74-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="b5f74-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5f74-114">Example</span></span>

<span data-ttu-id="b5f74-115">No exemplo a seguir, usa ações de storyboard controlável para controlar interativamente um storyboard.</span><span class="sxs-lookup"><span data-stu-id="b5f74-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="b5f74-116">Para ver um exemplo de controle de um storyboard usando código, consulte [controlar um storyboard depois que ele começar a usar seus métodos interativos](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="b5f74-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="b5f74-117">Para obter exemplos adicionais, consulte a [Galeria de exemplos de animação](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="b5f74-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f74-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f74-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="b5f74-119">Controlar um storyboard depois de ter começado usando os métodos interativos</span><span class="sxs-lookup"><span data-stu-id="b5f74-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="b5f74-120">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="b5f74-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b5f74-121">Visão geral de storyboards</span><span class="sxs-lookup"><span data-stu-id="b5f74-121">Storyboards Overview</span></span>](storyboards-overview.md)

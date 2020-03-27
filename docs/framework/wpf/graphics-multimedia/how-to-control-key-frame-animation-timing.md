---
title: Como controlar o tempo de animação do quadro-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344728"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="5e5e7-102">Como controlar o tempo de animação do quadro-chave</span><span class="sxs-lookup"><span data-stu-id="5e5e7-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="5e5e7-103">Este exemplo mostra como controlar o intervalo de quadros chave em uma animação de quadro chave.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="5e5e7-104">Como outras animações, as animações de quadro-chave têm uma <xref:System.Windows.Media.Animation.Timeline.Duration%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="5e5e7-105">Além de especificar a duração de uma animação, é necessário especificar qual parte da duração é atribuída a cada um de seus quadros chave.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="5e5e7-106">Para alocar a hora, <xref:System.Windows.Media.Animation.KeyTime> você especifica um para cada quadro de tecla na animação.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="5e5e7-107">O <xref:System.Windows.Media.Animation.KeyTime> para cada quadro de tecla especifica quando um quadro-chave termina (não especifica o tempo que um quadro-chave reproduz).</span><span class="sxs-lookup"><span data-stu-id="5e5e7-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="5e5e7-108">Você pode <xref:System.Windows.Media.Animation.KeyTime> especificar <xref:System.TimeSpan> um como um valor, <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> como uma porcentagem, ou como o ou valor especial.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="5e5e7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e5e7-109">Example</span></span>

<span data-ttu-id="5e5e7-110">O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> seguir usa um para animar um retângulo através da tela.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="5e5e7-111">Os tempos-chave dos quadros-chave são definidos com <xref:System.TimeSpan> valores.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="5e5e7-112">A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="5e5e7-113">![Os valores-chave são alcançados em 3, 4 e 10 segundos](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="5e5e7-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="5e5e7-114">O exemplo a seguir mostra uma animação que é idêntica, exceto que os tempos da chave os quadros chave são especificados com valores de percentual.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="5e5e7-115">A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="5e5e7-116">![Os valores-chave são alcançados em 3, 4 e 10 segundos](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="5e5e7-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="5e5e7-117">O próximo <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> exemplo usa valores de tempo-chave.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="5e5e7-118">A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="5e5e7-119">![Os valores-chave são alcançados em 3.3,6.6 e 9,9 segundos](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="5e5e7-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="5e5e7-120">O exemplo <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> final usa valores de tempo-chave.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="5e5e7-121">A ilustração a seguir mostra quando o valor de cada quadro chave é alcançado.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="5e5e7-122">![Os valores-chave são alcançados em 0, 5 e 10 segundos](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="5e5e7-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="5e5e7-123">Para simplificar, as versões de código neste exemplo usam animações locais, não storyboards, porque uma única animação está sendo aplicada a uma única propriedade, mas os exemplos podem ser modificados para utilizar storyboards.</span><span class="sxs-lookup"><span data-stu-id="5e5e7-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="5e5e7-124">Para ver um exemplo que mostra como declarar um storyboard no código, consulte [Animar uma propriedade usando um Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="5e5e7-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="5e5e7-125">Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="5e5e7-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="5e5e7-126">Para obter mais informações sobre animações de quadro chave, consulte a [Visão geral de animações de quadro chave](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5e5e7-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e5e7-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e5e7-127">See also</span></span>

- [<span data-ttu-id="5e5e7-128">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="5e5e7-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="5e5e7-129">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="5e5e7-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="5e5e7-130">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="5e5e7-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)

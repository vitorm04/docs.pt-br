---
title: 'Como: Adicionar um valor de saída da animação a um valor inicial de animação'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102603"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="182ce-102">Como: Adicionar um valor de saída da animação a um valor inicial de animação</span><span class="sxs-lookup"><span data-stu-id="182ce-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="182ce-103">Este exemplo mostra como adicionar um valor de saída da animação a um valor inicial de animação.</span><span class="sxs-lookup"><span data-stu-id="182ce-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="182ce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="182ce-104">Example</span></span>  
 <span data-ttu-id="182ce-105">O <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> propriedade especifica se você deseja que o valor de saída de uma animação seja adicionado como o valor inicial (valor base) de uma propriedade animada.</span><span class="sxs-lookup"><span data-stu-id="182ce-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="182ce-106">Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> com animações mais básicas e a maioria das animações de quadro-chave.</span><span class="sxs-lookup"><span data-stu-id="182ce-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="182ce-107">Para obter mais informações, consulte [Visão geral da animação](animation-overview.md) e [Visão geral de animações de quadro-chave](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="182ce-107">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="182ce-108">O exemplo a seguir mostra o efeito de usar o <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimation> e usando o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="182ce-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="182ce-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="182ce-109">See also</span></span>

- [<span data-ttu-id="182ce-110">Acumular valores de animação durante ciclos de repetição</span><span class="sxs-lookup"><span data-stu-id="182ce-110">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="182ce-111">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="182ce-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="182ce-112">Visão geral das animações de quadro-chave</span><span class="sxs-lookup"><span data-stu-id="182ce-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="182ce-113">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="182ce-113">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)

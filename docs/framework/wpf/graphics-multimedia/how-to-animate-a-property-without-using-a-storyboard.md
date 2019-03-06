---
title: 'Como: Animar uma propriedade sem usar um storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: b76afeb0187065ff07c832363d3a52896aa36822
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371151"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="6fc0d-102">Como: Animar uma propriedade sem usar um storyboard</span><span class="sxs-lookup"><span data-stu-id="6fc0d-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="6fc0d-103">Este exemplo mostra uma maneira de aplicar uma animação a uma propriedade sem usar um <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6fc0d-104">Essa funcionalidade não está disponível no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6fc0d-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="6fc0d-105">Para obter informações sobre como animar uma propriedade em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], veja [Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="6fc0d-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="6fc0d-106">Para aplicar um animação local a uma propriedade, use o <xref:System.Windows.UIElement.BeginAnimation%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="6fc0d-107">Esse método usa dois parâmetros: um <xref:System.Windows.DependencyProperty> que especifica a propriedade a ser animada e a animação a ser aplicado a essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc0d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fc0d-108">Example</span></span>  
 <span data-ttu-id="6fc0d-109">O exemplo a seguir mostra como animar a cor de plano de fundo e a largura de um <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="6fc0d-110">Uma variedade de classes de animação no <xref:System.Windows.Media.Animation> namespace existe para diferentes tipos de propriedades de animação.</span><span class="sxs-lookup"><span data-stu-id="6fc0d-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="6fc0d-111">Para obter mais informações sobre propriedades de animação, consulte [Visão geral da animação](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6fc0d-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="6fc0d-112">Para obter mais informações sobre propriedades de dependência (o tipo de propriedades mostradas neste exemplo) e suas funcionalidades, veja [Visão geral das propriedades de dependência](../advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6fc0d-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="6fc0d-113">Há outras maneiras de animar sem usar <xref:System.Windows.Media.Animation.Storyboard> objetos; para obter mais informações, consulte [visão geral das técnicas de animação de propriedade](property-animation-techniques-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6fc0d-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc0d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fc0d-114">See also</span></span>
- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="6fc0d-115">Visão geral das técnicas de animação da propriedade</span><span class="sxs-lookup"><span data-stu-id="6fc0d-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="6fc0d-116">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="6fc0d-116">Animation Overview</span></span>](animation-overview.md)

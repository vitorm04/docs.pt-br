---
title: Funções de easing
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186495"
---
# <a name="easing-functions"></a><span data-ttu-id="1130f-102">Funções de easing</span><span class="sxs-lookup"><span data-stu-id="1130f-102">Easing Functions</span></span>
<span data-ttu-id="1130f-103">As funções easing permitem aplicar fórmulas matemáticas personalizadas às suas animações.</span><span class="sxs-lookup"><span data-stu-id="1130f-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="1130f-104">Por exemplo, talvez você queira que um objeto ricocheteie de modo realista ou comporte-se como se estivesse em uma mola.</span><span class="sxs-lookup"><span data-stu-id="1130f-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="1130f-105">Você pode usar o Quadro Chave ou até mesmo as animações De/Para/Por para aproximar esses efeitos, mas isso exigiria uma quantidade significativa de trabalho e a animação seria menos precisa do que usando uma fórmula matemática.</span><span class="sxs-lookup"><span data-stu-id="1130f-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="1130f-106">Além de criar sua própria função <xref:System.Windows.Media.Animation.EasingFunctionBase>de facilitação personalizada herdando, você pode usar uma das várias funções de facilitação fornecidas pelo tempo de execução para criar efeitos comuns.</span><span class="sxs-lookup"><span data-stu-id="1130f-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="1130f-107"><xref:System.Windows.Media.Animation.BackEase>: Retrai o movimento de uma animação ligeiramente antes de começar a animar no caminho indicado.</span><span class="sxs-lookup"><span data-stu-id="1130f-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="1130f-108"><xref:System.Windows.Media.Animation.BounceEase>: Cria um efeito de salto.</span><span class="sxs-lookup"><span data-stu-id="1130f-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="1130f-109"><xref:System.Windows.Media.Animation.CircleEase>: Cria uma animação que acelera e/ou desacelera usando uma função circular.</span><span class="sxs-lookup"><span data-stu-id="1130f-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="1130f-110"><xref:System.Windows.Media.Animation.CubicEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="1130f-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="1130f-111"><xref:System.Windows.Media.Animation.ElasticEase>: Cria uma animação que se assemelha a uma mola oscilando para frente e para trás até que ela venha a descansar.</span><span class="sxs-lookup"><span data-stu-id="1130f-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="1130f-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Cria uma animação que acelera e/ou desacelera usando uma fórmula exponencial.</span><span class="sxs-lookup"><span data-stu-id="1130f-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="1130f-113"><xref:System.Windows.Media.Animation.PowerEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>p</sup> onde p é igual à <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1130f-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="1130f-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="1130f-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="1130f-115"><xref:System.Windows.Media.Animation.QuarticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="1130f-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="1130f-116"><xref:System.Windows.Media.Animation.QuinticEase>: Criar uma animação que acelere e/ou desacelere usando a fórmula *f\*\*(t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="1130f-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="1130f-117"><xref:System.Windows.Media.Animation.SineEase>: Cria uma animação que acelera e/ou desacelera usando uma fórmula seno.</span><span class="sxs-lookup"><span data-stu-id="1130f-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="1130f-118">Para aplicar uma função de facilitação a uma animação, use a `EasingFunction` propriedade da animação para especificar a função de facilitação para aplicar à animação.</span><span class="sxs-lookup"><span data-stu-id="1130f-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="1130f-119">O exemplo a <xref:System.Windows.Media.Animation.BounceEase> seguir aplica <xref:System.Windows.Media.Animation.DoubleAnimation> uma função de facilitação a um para criar um efeito de salto.</span><span class="sxs-lookup"><span data-stu-id="1130f-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="1130f-120">No exemplo anterior, a função de easing foi aplicada a uma animação De/Para/Por.</span><span class="sxs-lookup"><span data-stu-id="1130f-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="1130f-121">Você também pode aplicar essas funções de easing a animações de Quadro-Chave.</span><span class="sxs-lookup"><span data-stu-id="1130f-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="1130f-122">O exemplo a seguir mostra como usar quadros-chave com as funções de easing associadas a eles para criar uma animação de um retângulo que se contrai para cima, desacelera e então expande-se para baixo (como se estivesse caindo) e então ricocheteia até parar.</span><span class="sxs-lookup"><span data-stu-id="1130f-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="1130f-123">Você pode <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> usar a propriedade para alterar como a função de facilitação se comporta, ou seja, alterar a forma como a animação interpola.</span><span class="sxs-lookup"><span data-stu-id="1130f-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="1130f-124">Existem três valores possíveis <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>que você pode dar para:</span><span class="sxs-lookup"><span data-stu-id="1130f-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="1130f-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: A interpolação segue a fórmula matemática associada à função de facilitação.</span><span class="sxs-lookup"><span data-stu-id="1130f-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="1130f-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: A interpolação segue 100% de interpolação menos a saída da fórmula associada à função de facilitação.</span><span class="sxs-lookup"><span data-stu-id="1130f-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="1130f-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolação <xref:System.Windows.Media.Animation.EasingMode.EaseIn> utiliza para a primeira <xref:System.Windows.Media.Animation.EasingMode.EaseOut> metade da animação e para a segunda metade.</span><span class="sxs-lookup"><span data-stu-id="1130f-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="1130f-128">Os gráficos abaixo demonstram <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> os diferentes valores de onde *f*(*x*) representa o progresso da animação e *t* representa o tempo.</span><span class="sxs-lookup"><span data-stu-id="1130f-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="1130f-129">![Gráficos do BackEase EasingMode.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="1130f-130">![Gráficos bounceEase EasingMode.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="1130f-131">![Gráficos do CircleEase EasingMode.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="1130f-132">![Gráficos cubicease easingmode.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="1130f-133">![ElasticEase com gráficos de diferentes modos de facilitação.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="1130f-134">![Gráficos exponentialEase de diferentes modos de facilitação.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="1130f-135">![QuarticEase com gráficos de diferentes modos de facilitação.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="1130f-136">![QuadraticEase com gráficos de diferentes modos de facilitação](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="1130f-137">![QuarticEase com gráficos de diferentes modos de facilitação.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="1130f-138">![QuinticEase com gráficos de diferentes modos de facilitação.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="1130f-139">![SineEase para diferentes valores do EasingMode](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="1130f-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1130f-140">Você pode <xref:System.Windows.Media.Animation.PowerEase> usar para criar <xref:System.Windows.Media.Animation.CubicEase> <xref:System.Windows.Media.Animation.QuadraticEase>o <xref:System.Windows.Media.Animation.QuarticEase>mesmo <xref:System.Windows.Media.Animation.QuinticEase> comportamento <xref:System.Windows.Media.Animation.PowerEase.Power%2A> que , e usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="1130f-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="1130f-141">Por exemplo, se você <xref:System.Windows.Media.Animation.PowerEase> quiser <xref:System.Windows.Media.Animation.CubicEase>usar para <xref:System.Windows.Media.Animation.PowerEase.Power%2A> substituir, especifique um valor de 3.</span><span class="sxs-lookup"><span data-stu-id="1130f-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="1130f-142">Além de usar as funções de facilitação incluídas no tempo de execução, <xref:System.Windows.Media.Animation.EasingFunctionBase>você pode criar suas próprias funções de facilitação personalizadas herdando de .</span><span class="sxs-lookup"><span data-stu-id="1130f-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="1130f-143">O exemplo a seguir demonstra como criar uma função de easing personalizada simples.</span><span class="sxs-lookup"><span data-stu-id="1130f-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="1130f-144">Você pode adicionar sua própria lógica matemática para como a <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> função de facilitação se comporta substituindo o método.</span><span class="sxs-lookup"><span data-stu-id="1130f-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

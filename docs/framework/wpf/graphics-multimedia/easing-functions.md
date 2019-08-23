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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965726"
---
# <a name="easing-functions"></a>Funções de easing
As funções easing permitem aplicar fórmulas matemáticas personalizadas às suas animações. Por exemplo, talvez você queira que um objeto ricocheteie de modo realista ou comporte-se como se estivesse em uma mola. Você pode usar o Quadro Chave ou até mesmo as animações De/Para/Por para aproximar esses efeitos, mas isso exigiria uma quantidade significativa de trabalho e a animação seria menos precisa do que usando uma fórmula matemática.  
  
 Além de criar sua própria função de atenuação personalizada herdando de <xref:System.Windows.Media.Animation.EasingFunctionBase>, você pode usar uma das várias funções de atenuação fornecidas pelo tempo de execução para criar efeitos comuns.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Cancela ligeiramente o movimento de uma animação antes de começar a animar no caminho indicado.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Cria um efeito de saltando.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Cria uma animação que acelera e/ou acelera o uso de uma função circular.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Cria uma animação que se assemelha a uma mola de oscillating de frente até que se torne REST.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Cria uma animação que acelera e/ou acelera o uso de uma fórmula exponencial.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Cria uma animação que acelera e/ou faz a desaceleração usando a fórmula *f*(*t*) = *t*<sup>p</sup> , em que p <xref:System.Windows.Media.Animation.PowerEase.Power%2A> é igual à propriedade.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Crie uma animação que acelere e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Cria uma animação que acelera e/ou acelera o uso de uma fórmula do seno.  
  
 Para aplicar uma função de atenuação a uma animação, `EasingFunction` use a propriedade da animação especifique a função de atenuação a ser aplicada à animação. O exemplo a seguir aplica <xref:System.Windows.Media.Animation.BounceEase> uma função de atenuação a um <xref:System.Windows.Media.Animation.DoubleAnimation> para criar um efeito de saltamento.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 No exemplo anterior, a função de easing foi aplicada a uma animação De/Para/Por. Você também pode aplicar essas funções de easing a animações de Quadro-Chave. O exemplo a seguir mostra como usar quadros-chave com as funções de easing associadas a eles para criar uma animação de um retângulo que se contrai para cima, desacelera e então expande-se para baixo (como se estivesse caindo) e então ricocheteia até parar.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Você pode usar a <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriedade para alterar a forma como a função de atenuação se comporta, ou seja, alterar a forma como a animação interpola. Há três valores possíveis que você pode fornecer para <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: A interpolação segue a fórmula matemática associada à função de easing.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolação segue 100% de interpolação menos a saída da fórmula associada à função de easing.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Usa interpolação <xref:System.Windows.Media.Animation.EasingMode.EaseIn> para a primeira metade da animação e <xref:System.Windows.Media.Animation.EasingMode.EaseOut> para a segunda metade.  
  
 Os grafos a seguir demonstram os diferentes <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> valores de onde *f*(*x*) representam o progresso da animação e *t* representa o tempo.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Grafos de EasingMode BackEase.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Grafos de EasingMode BounceEase.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Grafos de EasingMode CircleEase.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Grafos de EasingMode CubicEase.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase com grafos de diferentes easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![ExponentialEase com grafos de diferentes easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase com grafos de diferentes easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase com grafos de diferentes easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase com grafos de diferentes easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase com grafos de diferentes easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase para diferentes valores de EasingMode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Você pode usar <xref:System.Windows.Media.Animation.PowerEase> para criar o mesmo comportamento que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>e <xref:System.Windows.Media.Animation.QuinticEase> usando a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade. Por exemplo, se você quiser usar <xref:System.Windows.Media.Animation.PowerEase> para substituir por <xref:System.Windows.Media.Animation.CubicEase>, especifique um <xref:System.Windows.Media.Animation.PowerEase.Power%2A> valor de 3.  
  
 Além de usar as funções de atenuação incluídas no tempo de execução, você pode criar suas próprias funções de atenuação personalizadas herdando <xref:System.Windows.Media.Animation.EasingFunctionBase>de. O exemplo a seguir demonstra como criar uma função de easing personalizada simples. Você pode adicionar sua própria lógica matemática para saber como a função de atenuação se comporta substituindo o <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> método.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

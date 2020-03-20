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
# <a name="easing-functions"></a>Funções de easing
As funções easing permitem aplicar fórmulas matemáticas personalizadas às suas animações. Por exemplo, talvez você queira que um objeto ricocheteie de modo realista ou comporte-se como se estivesse em uma mola. Você pode usar o Quadro Chave ou até mesmo as animações De/Para/Por para aproximar esses efeitos, mas isso exigiria uma quantidade significativa de trabalho e a animação seria menos precisa do que usando uma fórmula matemática.  
  
 Além de criar sua própria função <xref:System.Windows.Media.Animation.EasingFunctionBase>de facilitação personalizada herdando, você pode usar uma das várias funções de facilitação fornecidas pelo tempo de execução para criar efeitos comuns.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Retrai o movimento de uma animação ligeiramente antes de começar a animar no caminho indicado.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Cria um efeito de salto.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Cria uma animação que acelera e/ou desacelera usando uma função circular.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Cria uma animação que se assemelha a uma mola oscilando para frente e para trás até que ela venha a descansar.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Cria uma animação que acelera e/ou desacelera usando uma fórmula exponencial.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>p</sup> onde p é igual à <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Cria uma animação que acelera e/ou desacelera usando a fórmula *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Criar uma animação que acelere e/ou desacelere usando a fórmula *f**(t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Cria uma animação que acelera e/ou desacelera usando uma fórmula seno.  
  
 Para aplicar uma função de facilitação a uma animação, use a `EasingFunction` propriedade da animação para especificar a função de facilitação para aplicar à animação. O exemplo a <xref:System.Windows.Media.Animation.BounceEase> seguir aplica <xref:System.Windows.Media.Animation.DoubleAnimation> uma função de facilitação a um para criar um efeito de salto.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 No exemplo anterior, a função de easing foi aplicada a uma animação De/Para/Por. Você também pode aplicar essas funções de easing a animações de Quadro-Chave. O exemplo a seguir mostra como usar quadros-chave com as funções de easing associadas a eles para criar uma animação de um retângulo que se contrai para cima, desacelera e então expande-se para baixo (como se estivesse caindo) e então ricocheteia até parar.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Você pode <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> usar a propriedade para alterar como a função de facilitação se comporta, ou seja, alterar a forma como a animação interpola. Existem três valores possíveis <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>que você pode dar para:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: A interpolação segue a fórmula matemática associada à função de facilitação.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: A interpolação segue 100% de interpolação menos a saída da fórmula associada à função de facilitação.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolação <xref:System.Windows.Media.Animation.EasingMode.EaseIn> utiliza para a primeira <xref:System.Windows.Media.Animation.EasingMode.EaseOut> metade da animação e para a segunda metade.  
  
 Os gráficos abaixo demonstram <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> os diferentes valores de onde *f*(*x*) representa o progresso da animação e *t* representa o tempo.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Gráficos do BackEase EasingMode.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Gráficos bounceEase EasingMode.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Gráficos do CircleEase EasingMode.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Gráficos cubicease easingmode.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase com gráficos de diferentes modos de facilitação.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Gráficos exponentialEase de diferentes modos de facilitação.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase com gráficos de diferentes modos de facilitação.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase com gráficos de diferentes modos de facilitação](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase com gráficos de diferentes modos de facilitação.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase com gráficos de diferentes modos de facilitação.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase para diferentes valores do EasingMode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Você pode <xref:System.Windows.Media.Animation.PowerEase> usar para criar <xref:System.Windows.Media.Animation.CubicEase> <xref:System.Windows.Media.Animation.QuadraticEase>o <xref:System.Windows.Media.Animation.QuarticEase>mesmo <xref:System.Windows.Media.Animation.QuinticEase> comportamento <xref:System.Windows.Media.Animation.PowerEase.Power%2A> que , e usando a propriedade. Por exemplo, se você <xref:System.Windows.Media.Animation.PowerEase> quiser <xref:System.Windows.Media.Animation.CubicEase>usar para <xref:System.Windows.Media.Animation.PowerEase.Power%2A> substituir, especifique um valor de 3.  
  
 Além de usar as funções de facilitação incluídas no tempo de execução, <xref:System.Windows.Media.Animation.EasingFunctionBase>você pode criar suas próprias funções de facilitação personalizadas herdando de . O exemplo a seguir demonstra como criar uma função de easing personalizada simples. Você pode adicionar sua própria lógica matemática para como a <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> função de facilitação se comporta substituindo o método.
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

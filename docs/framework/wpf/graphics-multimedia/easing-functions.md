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
ms.openlocfilehash: 038d9423ddae6f16165ed0618beab8391c462ac9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461703"
---
# <a name="easing-functions"></a>Funções de easing
As funções easing permitem aplicar fórmulas matemáticas personalizadas às suas animações. Por exemplo, talvez você queira que um objeto ricocheteie de modo realista ou comporte-se como se estivesse em uma mola. Você pode usar o Quadro Chave ou até mesmo as animações De/Para/Por para aproximar esses efeitos, mas isso exigiria uma quantidade significativa de trabalho e a animação seria menos precisa do que usando uma fórmula matemática.  
  
 Além de criar sua própria função de easing personalizada herdando de <xref:System.Windows.Media.Animation.EasingFunctionBase>, você pode usar uma das várias funções de easing fornecidas pelo tempo de execução para criar efeitos comuns.  
  
-   <xref:System.Windows.Media.Animation.BackEase>: Retrai o movimento de uma animação um pouco antes de começar a ser animada no caminho indicado.  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: Cria um efeito de devolução.  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: Cria uma animação que acelera e/ou desacelerada usando uma função circular.  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: Cria uma animação que acelera e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>3</sup>.  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: Cria uma animação que se parece com uma mola oscilando para parar e para trás até que se trata de rest.  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: Cria uma animação que acelera e/ou desacelerada usando uma fórmula exponencial.  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: Cria uma animação que acelera e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>p</sup> onde p é igual ao <xref:System.Windows.Media.Animation.PowerEase.Power%2A>propriedade.  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: Cria uma animação que acelera e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>2</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: Cria uma animação que acelera e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>4</sup>.  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: Criar uma animação que acelera e/ou desacelerada usando a fórmula *f*(*t*) = *t*<sup>5</sup>.  
  
-   <xref:System.Windows.Media.Animation.SineEase>: Cria uma animação que acelera e/ou desacelerada usando uma fórmula de seno.  
  
 Para aplicar uma função de easing a uma animação, use o `EasingFunction` propriedade da animação especificar a função de easing para aplicar a animação. O exemplo a seguir aplica uma <xref:System.Windows.Media.Animation.BounceEase> função de easing um <xref:System.Windows.Media.Animation.DoubleAnimation> para criar um efeito de devolução.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 No exemplo anterior, a função de easing foi aplicada a uma animação De/Para/Por. Você também pode aplicar essas funções de easing a animações de Quadro-Chave. O exemplo a seguir mostra como usar quadros-chave com as funções de easing associadas a eles para criar uma animação de um retângulo que se contrai para cima, desacelera e então expande-se para baixo (como se estivesse caindo) e então ricocheteia até parar.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Você pode usar o <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> alteração de propriedade para alterar como a função de easing se comporta, ou seja, como a animação interpola. Há três valores possíveis, você pode fornecer para <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: A interpolação segue a fórmula matemática associada com a função de easing.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: A interpolação segue 100% de interpolação menos a saída da fórmula associada à função de easing.  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolação usa <xref:System.Windows.Media.Animation.EasingMode.EaseIn> na primeira metade da animação e <xref:System.Windows.Media.Animation.EasingMode.EaseOut> na segunda metade.  
  
 Os gráficos a seguir demonstram os diferentes valores de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> onde *f*(*x*) representa o progresso da animação e *t* representa o tempo.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Grafos de EasingMode BackEase.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Grafos de EasingMode BounceEase.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Grafos de EasingMode CircleEase.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Grafos de EasingMode CubicEase.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![ExponentialEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase com grafos de diferentes easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase com grafos de diferentes easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase para diferentes valores de EasingMode](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  Você pode usar <xref:System.Windows.Media.Animation.PowerEase> para criar o mesmo comportamento <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, e <xref:System.Windows.Media.Animation.QuinticEase> usando o <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriedade. Por exemplo, se você quiser usar <xref:System.Windows.Media.Animation.PowerEase> para substituir <xref:System.Windows.Media.Animation.CubicEase>, especifique um <xref:System.Windows.Media.Animation.PowerEase.Power%2A> valor 3.  
  
 Além de usar as funções de easing incluídas no tempo de execução, você pode criar suas próprias funções de easing personalizadas herdando de <xref:System.Windows.Media.Animation.EasingFunctionBase>. O exemplo a seguir demonstra como criar uma função de easing personalizada simples. Você pode adicionar sua própria lógica matemática como a função de easing se comporta substituindo o <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> método.   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]

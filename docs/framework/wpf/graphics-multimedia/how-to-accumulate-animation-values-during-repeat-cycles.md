---
title: "Como acumular valores de animação durante ciclos de repetição"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a91856cdfcf1ca7ae87e8e571306170feecb7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Como acumular valores de animação durante ciclos de repetição
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade para acumular valores de animação entre ciclos de repetição.  
  
## <a name="example"></a>Exemplo  
 Use o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade acumular valores de base de uma animação entre ciclos de repetição. Por exemplo, se você definir uma animação para repetir 9 vezes (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") e você definir a propriedade para animar entre 10 e 15 (de = 10 para = 15), a propriedade anima de 10 a 15 durante o primeiro ciclo, de 15 a 20 durante o segundo ciclo , de 20 a 25 durante o ciclo de terceiro e assim por diante. Portanto, cada ciclo de animação usa o valor final de animação do ciclo de animação anterior como seu valor de base.  
  
 Você pode usar a propriedade `IsCumulative` com animações mais básicas e a maioria das animações de quadro-chave. Para obter mais informações, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) e [Visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra esse comportamento, animando a largura de quatro retângulos. O Exemplo:  
  
-   Anima o primeiro retângulo com <xref:System.Windows.Media.Animation.DoubleAnimation> e define o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade `true`.  
  
-   Anima o segundo retângulo com <xref:System.Windows.Media.Animation.DoubleAnimation> e define o <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> propriedade para o valor padrão de `false`.  
  
-   Anima o terceiro retângulo com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> e define o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriedade `true`.  
  
-   Anima o último retângulo com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> e define o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> propriedade `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Adicionar um valor de saída da animação a um valor inicial de animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [Repetir uma animação](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)

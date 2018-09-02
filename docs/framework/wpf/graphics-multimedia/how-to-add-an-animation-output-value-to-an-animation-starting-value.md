---
title: Como adicionar um valor de saída da animação a um valor inicial de animação
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: bae7bf57507e3345c92cbbaf24491d86772425a4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407045"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Como adicionar um valor de saída da animação a um valor inicial de animação
Este exemplo mostra como adicionar um valor de saída da animação a um valor inicial de animação.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> propriedade especifica se você deseja que o valor de saída de uma animação seja adicionado como o valor inicial (valor base) de uma propriedade animada. Você pode usar a propriedade <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> com animações mais básicas e a maioria das animações de quadro-chave. Para obter mais informações, consulte [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) e [Visão geral de animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 O exemplo a seguir mostra o efeito de usar o <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimation> e usando o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> propriedade com <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Acumular valores de animação durante ciclos de repetição](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animação e tempo](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)

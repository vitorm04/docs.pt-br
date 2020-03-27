---
title: Como animar cor usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344745"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Como animar cor usando quadros-chave
Este exemplo mostra como <xref:System.Windows.Media.SolidColorBrush.Color%2A> animar <xref:System.Windows.Media.SolidColorBrush> a de a usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.SolidColorBrush.Color%2A> a classe <xref:System.Windows.Media.SolidColorBrush>para animar a propriedade de um . Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante os dois primeiros segundos, <xref:System.Windows.Media.Animation.LinearColorKeyFrame> usa uma instância da classe para mudar gradualmente a cor de verde para vermelho. Quadros de <xref:System.Windows.Media.Animation.LinearColorKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.  
  
2. Durante o final do segundo seguinte, usa <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> uma instância da classe para mudar rapidamente a cor de vermelho para amarelo. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> como criar mudanças bruscas entre valores, ou seja, a mudança de cor nesta parte da animação ocorre rapidamente e não é sutil.  
  
3. Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineColorKeyFrame> usa uma instância da classe para mudar a cor novamente — desta vez de amarelo de volta para verde. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineColorKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade. Neste exemplo, a alteração na cor começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

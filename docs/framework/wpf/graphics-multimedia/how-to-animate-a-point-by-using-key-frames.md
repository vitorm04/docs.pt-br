---
title: Como animar um ponto usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344875"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Como animar um ponto usando quadros-chave
Este exemplo mostra como <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> usar a <xref:System.Windows.Point>classe para animar um .  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move uma elipse ao longo de um caminho triangular. O exemplo <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> usa a classe <xref:System.Windows.Media.EllipseGeometry.Center%2A> para <xref:System.Windows.Media.EllipseGeometry>animar a propriedade de um . Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante a primeira metade do segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearPointKeyFrame> classe para mover a elipse ao longo de um caminho a uma taxa constante de sua posição inicial. Quadros de <xref:System.Windows.Media.Animation.LinearPointKeyFrame> tecla lineares como criar uma interpolação linear suave entre valores.  
  
2. Durante o final da próxima metade do <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> segundo, usa uma instância da classe para de repente mover a elipse ao longo do caminho para a próxima posição. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> como criar saltos repentinos entre os valores.  
  
3. Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplinePointKeyFrame> usa uma instância da classe para mover a elipse de volta à sua posição inicial. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplinePointKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade. Neste exemplo, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Para obter consistência com outros exemplos de animação, <xref:System.Windows.Media.Animation.Storyboard> as versões de código deste exemplo usam um objeto para aplicar o <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. No entanto, ao aplicar uma única animação em <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> código, é <xref:System.Windows.Media.Animation.Storyboard>mais simples usar o método em vez de usar um . Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

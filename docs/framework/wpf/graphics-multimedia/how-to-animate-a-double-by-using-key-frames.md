---
title: Como animar um duplo usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344925"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Como animar um duplo usando quadros-chave
Este exemplo mostra como animar o valor de <xref:System.Double> uma propriedade que leva a usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move um retângulo por uma tela. O exemplo <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> usa a classe <xref:System.Windows.Media.TranslateTransform.X%2A> para <xref:System.Windows.Media.TranslateTransform> animar a <xref:System.Windows.Shapes.Rectangle>propriedade de um aplicado a um . Essa animação, que se repete indefinidamente, usa três quadros chave da seguinte maneira:  
  
1. Durante os primeiros três segundos, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> usa uma instância da classe para mover o retângulo ao longo de um caminho a uma taxa constante de sua posição inicial para a posição de 500. Quadros de <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.  
  
2. No final do quarto segundo, usa <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> uma instância da classe para de repente mover o retângulo para a próxima posição. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> como criar saltos repentinos entre os valores. Neste exemplo, o retângulo está na posição inicial e, de repente, aparece na posição 500.  
  
3. Nos dois segundos finais, usa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> uma instância da classe para mover o retângulo de volta para sua posição inicial. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> entre valores de acordo com o valor da propriedade. Neste exemplo, o retângulo começa a se mover lentamente e acelera exponencialmente em direção ao final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
 Para obter consistência com outros exemplos de animação, <xref:System.Windows.Media.Animation.Storyboard> as versões de código deste exemplo usam um objeto para aplicar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternativamente, ao aplicar uma única animação em código, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> é mais <xref:System.Windows.Media.Animation.Storyboard>simples usar o método em vez de usar um . Por exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

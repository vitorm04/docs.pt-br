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
ms.openlocfilehash: 4adeb858ab1b69ef1b00f7bf3b6868dbcbbc4154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557427"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Como animar um duplo usando quadros-chave
Este exemplo mostra como animar o valor de uma propriedade que utiliza um <xref:System.Double> usando quadros chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move um retângulo por uma tela. O exemplo usa o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.TranslateTransform.X%2A> propriedade de um <xref:System.Windows.Media.TranslateTransform> aplicado a um <xref:System.Windows.Shapes.Rectangle>. Essa animação, que se repete indefinidamente, usa três quadros chave da seguinte maneira:  
  
1.  Durante os primeiros três segundos, usa uma instância do <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> classe para mover o retângulo ao longo de um caminho a uma taxa constante de sua posição inicial até a posição 500. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> criam uma transição linear suave entre valores.  
  
2.  No final do quarto segundo, usa uma instância do <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> classe repentinamente mover o retângulo para a próxima posição. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> criar saltos repentinos entre valores. Neste exemplo, o retângulo está na posição inicial e, de repente, aparece na posição 500.  
  
3.  Os últimos dois segundos, usa uma instância do <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> classe para mover o retângulo de volta para sua posição inicial. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> criar uma transição de variável entre valores de acordo com o valor de <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> propriedade. Neste exemplo, o retângulo começa a se mover lentamente e acelera exponencialmente em direção ao final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Para manter a consistência com outros exemplos de animação, as versões de código deste exemplo usam um <xref:System.Windows.Media.Animation.Storyboard> objeto ao qual aplicar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Como alternativa, ao aplicar uma única animação no código, é mais simples usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método em vez de usar um <xref:System.Windows.Media.Animation.Storyboard>. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

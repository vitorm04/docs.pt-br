---
title: Como animar uma geometria de retângulo usando quadros-chave
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344688"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Como animar uma geometria de retângulo usando quadros-chave
Este exemplo mostra como <xref:System.Windows.Media.RectangleGeometry.Rect%2A> animar a <xref:System.Windows.Media.RectangleGeometry> propriedade de a usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.RectangleGeometry.Rect%2A> a classe <xref:System.Windows.Media.RectangleGeometry>para animar a propriedade de um . Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante os dois primeiros segundos, <xref:System.Windows.Media.Animation.LinearRectKeyFrame> usa uma instância da classe para animar uma mudança gradual na posição, largura e altura de um retângulo. Quadros de <xref:System.Windows.Media.Animation.LinearRectKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.  
  
2. Durante o final do segundo seguinte, usa <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> uma instância da classe para diminuir repentinamente a altura do retângulo. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> como criar mudanças bruscas entre os valores, ou seja, a diminuição da altura ocorre rapidamente e não é sutil.  
  
3. Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineRectKeyFrame> usa uma instância da classe para alterar o retângulo de volta ao seu tamanho e posição originais. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineRectKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade. Neste exemplo, a alteração começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

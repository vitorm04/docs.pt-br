---
title: 'Como: Animar uma geometria de retângulo usando quadros principais'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010092"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Como: Animar uma geometria de retângulo usando quadros principais
Este exemplo mostra como animar a <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry> usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry>. Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante os primeiros dois segundos, usa uma instância da <xref:System.Windows.Media.Animation.LinearRectKeyFrame> classe para animar uma alteração gradual na posição, largura e altura de um retângulo. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearRectKeyFrame> criam uma transição linear suave entre valores.  
  
2. Durante o final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> classe para diminuir repentinamente a altura do retângulo. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> criam alterações repentinas entre valores, ou seja, a redução de altura ocorre rapidamente e não é sutil.  
  
3. Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineRectKeyFrame> classe para alterar o retângulo de volta para seu tamanho e posição originais. Como quadros-chave spline <xref:System.Windows.Media.Animation.SplineRectKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> propriedade. Neste exemplo, a alteração começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

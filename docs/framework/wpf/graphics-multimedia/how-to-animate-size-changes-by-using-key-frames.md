---
title: Como animar alterações de tamanho usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344643"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Como animar alterações de tamanho usando quadros-chave
Esse exemplo demonstra como animar alterações de tamanho usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.ArcSegment.Size%2A> a classe <xref:System.Windows.Media.ArcSegment>para animar a propriedade de um . Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante a primeira metade da animação, usa <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> uma instância da classe para aumentar gradualmente o tamanho do arco. Quadros de <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> chaves lineares como criar uma transição linear suave entre os valores.  
  
2. No final da próxima metade do segundo, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> usa uma instância da classe para aumentar repentinamente o tamanho do arco. Quadros-chave discretos <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> como criar saltos repentinos entre os valores, ou seja, as mudanças de tamanho ocorrem de repente e não são sutis.  
  
3. Nos dois segundos finais, usa <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> uma instância da classe para aumentar o tamanho do arco. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> criar uma transição variável <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> entre valores de acordo com os valores da propriedade. Neste exemplo, o tamanho do arco aumenta lentamente no início e aumenta exponencialmente até o final do segmento de tempo.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

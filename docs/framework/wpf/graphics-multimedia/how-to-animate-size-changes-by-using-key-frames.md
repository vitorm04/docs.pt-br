---
title: Como animar alterações de tamanho usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 69845d1d75f81042bbeb20ee6b1015f5c2f53b81
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43803747"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Como animar alterações de tamanho usando quadros-chave
Esse exemplo demonstra como animar alterações de tamanho usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.ArcSegment.Size%2A> propriedade de um <xref:System.Windows.Media.ArcSegment>. Essa animação usa três quadros-chave da seguinte maneira:  
  
1.  Durante o primeiro meio segundo da animação, usa uma instância da <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> classe para aumentar gradualmente o tamanho do arco. Quadros-chave lineares como <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> criam uma transição linear suave entre valores.  
  
2.  No final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> classe, de repente, aumentar o tamanho do arco. Quadros chave discretos como <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> criam saltos repentinos entre valores, ou seja, as alterações de tamanho ocorrem repentinamente e não são sutis.  
  
3.  Sobre os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> classe para aumentar o tamanho do arco. Como quadros-chave spline <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> propriedade. Neste exemplo, o tamanho do arco aumenta lentamente no início e aumenta exponencialmente até o final do segmento de tempo.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

---
title: Como animar a espessura de uma borda usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344699"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Como animar a espessura de uma borda usando quadros-chave
Este exemplo mostra como <xref:System.Windows.Controls.Control.BorderThickness%2A> animar a <xref:System.Windows.Controls.Border>propriedade de um .  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Controls.Control.BorderThickness%2A> a classe <xref:System.Windows.Controls.Border>para animar a propriedade de um . Essa animação usa três quadros-chave da seguinte maneira:  
  
1. Durante a primeira metade do segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> classe para aumentar gradualmente a espessura da borda. O exemplo <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> é usar para criar um aumento linear suave entre os valores.  
  
2. No final da próxima metade do segundo, <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> usa uma instância da classe para aumentar repentinamente a espessura da borda. Quadros-chave discretos como os <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> derivados criam saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.  
  
3. Durante os dois segundos finais, <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> usa uma instância da classe para diminuir a espessura da borda. Quadros-chave spline como <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> os derivados criam uma transição <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> variável entre valores de acordo com os valores da propriedade. Neste quadro-chave, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)
- [Animar um valor de BorderThickness](../controls/how-to-animate-a-borderthickness-value.md)

---
title: Como animar uma matriz usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344917"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Como animar uma matriz usando quadros-chave
Este exemplo mostra como <xref:System.Windows.Media.MatrixTransform.Matrix%2A> animar a <xref:System.Windows.Media.MatrixTransform> propriedade de a usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> seguir usa <xref:System.Windows.Media.MatrixTransform.Matrix%2A> a classe <xref:System.Windows.Media.MatrixTransform>para animar a propriedade de um . O exemplo <xref:System.Windows.Media.MatrixTransform> usa o objeto para transformar <xref:System.Windows.Controls.Button>a aparência e a posição de um .  
  
 Esta animação <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> usa a classe para criar dois quadros-chave e faz o seguinte com eles:  
  
1. Anima o primeiro <xref:System.Windows.Media.Matrix> durante os primeiros 0,2 segundos. O exemplo <xref:System.Windows.Media.Matrix.M11%2A> altera <xref:System.Windows.Media.Matrix.M12%2A> as <xref:System.Windows.Media.Matrix>propriedades do . Essa alteração faz com que o botão se alongue e fique achatado. O exemplo também <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> altera as propriedades e propriedades para que o botão mude de posição.  
  
2. Anima o segundo <xref:System.Windows.Media.Matrix> em 1,0 segundos. O botão muda para outra posição enquanto o botão não é mais distorcido ou alongado.  
  
3. Repete a animação indefinidamente.  
  
> [!NOTE]
> Quadros-chave que <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> derivam do objeto criam saltos repentinos entre os valores, ou seja, o movimento da animação é jerky.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

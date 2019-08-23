---
title: 'Como: Animar uma matriz usando quadros principais'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963033"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Como: Animar uma matriz usando quadros principais
Este exemplo mostra como animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform> usando quadros-chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> a classe para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade <xref:System.Windows.Media.MatrixTransform>de um. O exemplo usa o <xref:System.Windows.Media.MatrixTransform> objeto para transformar a aparência e a posição de <xref:System.Windows.Controls.Button>um.  
  
 Essa animação usa a <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> classe para criar dois quadros-chave e faz o seguinte com eles:  
  
1. Anima o primeiro <xref:System.Windows.Media.Matrix> durante os primeiros 0,2 segundos. O exemplo altera as <xref:System.Windows.Media.Matrix.M11%2A> propriedades <xref:System.Windows.Media.Matrix.M12%2A> e do <xref:System.Windows.Media.Matrix>. Essa alteração faz com que o botão se alongue e fique achatado. O exemplo também altera as <xref:System.Windows.Media.Matrix.OffsetX%2A> propriedades <xref:System.Windows.Media.Matrix.OffsetY%2A> e para que o botão mude de posição.  
  
2. Anima o segundo <xref:System.Windows.Media.Matrix> em 1,0 segundos. O botão muda para outra posição enquanto o botão não é mais distorcido ou alongado.  
  
3. Repete a animação indefinidamente.  
  
> [!NOTE]
> Os quadros-chave que derivam do <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objeto criam saltos repentinos entre valores, ou seja, a movimentação da animação é Jerky.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Visão geral das animações de quadro-chave](key-frame-animations-overview.md)
- [Tópicos explicativos sobre quadros-chave](key-frame-animation-how-to-topics.md)

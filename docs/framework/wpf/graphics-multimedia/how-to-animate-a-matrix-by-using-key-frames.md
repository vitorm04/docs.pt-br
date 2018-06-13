---
title: Como animar uma matriz usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: edb7074dffab23810872f4347f5339270af86bd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557011"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Como animar uma matriz usando quadros-chave
Este exemplo mostra como animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform> usando quadros chave.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform>. O exemplo usa o <xref:System.Windows.Media.MatrixTransform> objeto para transformar a aparência e a posição de um <xref:System.Windows.Controls.Button>.  
  
 Esta animação usa o <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> de classe para criar dois quadros-chave e faz o seguinte com eles:  
  
1.  Anima a primeira <xref:System.Windows.Media.Matrix> durante os primeiros 0,2 segundos. O exemplo altera o <xref:System.Windows.Media.Matrix.M11%2A> e <xref:System.Windows.Media.Matrix.M12%2A> propriedades da <xref:System.Windows.Media.Matrix>. Essa alteração faz com que o botão se alongue e fique achatado. O exemplo também altera o <xref:System.Windows.Media.Matrix.OffsetX%2A> e <xref:System.Windows.Media.Matrix.OffsetY%2A> propriedades para que o botão muda de posição.  
  
2.  Anima a segunda <xref:System.Windows.Media.Matrix> em 1,0 segundo. O botão muda para outra posição enquanto o botão não é mais distorcido ou alongado.  
  
3.  Repete a animação indefinidamente.  
  
> [!NOTE]
>  Chave de quadro que deriva de <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> objeto criam saltos repentinos entre valores, ou seja, a movimentação da animação é uma.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)

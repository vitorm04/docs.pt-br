---
title: Como animar uma matriz usando quadros-chave
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c67b5c8e179485083a40aa8a196fbee3e0fc24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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

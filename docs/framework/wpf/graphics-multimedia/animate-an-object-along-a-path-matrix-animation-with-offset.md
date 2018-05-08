---
title: Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 77daf4efb913f2bc2606247178b6a6c4add29bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> valores de classe para animar um objeto ao longo de um caminho e fazer com que essa animação acumule seu deslocamento enquanto ela se repete.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto para animar a <xref:System.Windows.Media.MatrixTransform.Matrix%2A> propriedade de um <xref:System.Windows.Media.MatrixTransform> aplicado a um botão. Como resultado, um botão se move ao longo de um caminho curvo.  
  
 Além disso, o exemplo define o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriedade `true`, que faz com que o deslocamento da matriz animada se acumule a medida que a animação se repete. Como o deslocamento é acumulado, o botão se move para mais longe na tela quando a animação se repete, em vez de recomeçar da posição inicial.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Observe que, embora o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> propriedade faz com que os valores de deslocamento se acumulem entre repetições, ele não os valores de rotação acumular. Para fazer com que os valores de rotação acumular, defina a animação <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> e <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> propriedades `true`.  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028). Para obter um exemplo mostrando como animar uma <xref:System.Windows.Media.Matrix> ao longo de um caminho sem acúmulo de deslocamento, consulte [animar um objeto ao longo de um caminho (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

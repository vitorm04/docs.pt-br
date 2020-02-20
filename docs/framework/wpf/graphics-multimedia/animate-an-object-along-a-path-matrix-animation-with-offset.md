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
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453098"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a>Como animar um objeto ao longo de um caminho (animação de matriz com acúmulo de deslocamento)
Este exemplo mostra como usar a classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar um objeto ao longo de um caminho e fazer com que essa animação acumule seus valores de deslocamento à medida que ele se repetir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o objeto <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar a propriedade <xref:System.Windows.Media.MatrixTransform.Matrix%2A> de um <xref:System.Windows.Media.MatrixTransform> aplicado a um botão. Como resultado, um botão se move ao longo de um caminho curvo.  
  
 Além disso, o exemplo define a propriedade <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> como `true`, o que faz com que o deslocamento da matriz animada seja acumulado à medida que a animação se repete. Como o deslocamento é acumulado, o botão se move para mais longe na tela quando a animação se repete, em vez de recomeçar da posição inicial.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 Observe que, embora a propriedade <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> faça com que os valores de deslocamento sejam acumulados em repetições, isso não faz com que os valores de rotação sejam acumulados. Para tornar os valores de rotação acumulados, defina as propriedades <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> da animação e <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> como `true`.  
  
 Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Para obter um exemplo que mostra como animar um valor de <xref:System.Windows.Media.Matrix> ao longo de um caminho sem acumulação de deslocamento, consulte [animar um objeto ao longo de um caminho (animação de matriz)](how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)

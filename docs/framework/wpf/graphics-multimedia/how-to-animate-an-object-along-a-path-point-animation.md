---
title: Como animar um objeto ao longo de um caminho (animação de ponto)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452890"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Como animar um objeto ao longo de um caminho (animação de ponto)
Este exemplo mostra como usar um objeto <xref:System.Windows.Media.Animation.PointAnimationUsingPath> para animar uma <xref:System.Windows.Point> ao longo de um caminho curvo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move um <xref:System.Windows.Media.EllipseGeometry> ao longo de um caminho definido por um <xref:System.Windows.Media.PathGeometry>. A propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A> da geometria de elipse, que usa um valor de <xref:System.Windows.Point>, especifica sua posição; para mover a geometria da elipse, você anima sua propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A>. O exemplo usa um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> para animar a propriedade <xref:System.Windows.Media.EllipseGeometry.Center%2A> do objeto <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
 A versão de código do exemplo anterior usou um <xref:System.Windows.Media.Animation.Storyboard> para animar o <xref:System.Windows.Media.EllipseGeometry>, embora apenas uma animação tenha sido aplicada. Uma <xref:System.Windows.Media.Animation.Storyboard> geralmente é a maneira mais fácil de aplicar várias animações, pois essas animações podem ser controladas pela mesma <xref:System.Windows.Media.Animation.Storyboard>. No entanto, uma maneira mais fácil de aplicar uma única animação a uma propriedade ao usar o código é usar o método <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Confira também

- [Exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)

---
title: Como animar um objeto ao longo de um caminho (animação dupla)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: ebe24f060a342633a93b778d5e8030173970029c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a>Como animar um objeto ao longo de um caminho (animação dupla)
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> classe para mover um objeto ao longo de um caminho definido por uma <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa duas <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico:  
  
-   A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.X%2A> do <xref:System.Windows.Media.TranslateTransform> aplicada ao retângulo. Isto faz o retângulo mover horizontalmente ao longo do caminho.  
  
-   A segunda <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima a <xref:System.Windows.Media.TranslateTransform.Y%2A> do <xref:System.Windows.Media.TranslateTransform> aplicada ao retângulo. Isto faz o retângulo mover verticalmente ao longo do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Outra maneira de mover um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> objeto. Para obter um exemplo, consulte [animar um objeto ao longo de um caminho (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

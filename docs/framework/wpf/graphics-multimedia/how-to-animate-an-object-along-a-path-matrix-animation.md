---
title: Como animar um objeto ao longo de um caminho (animação de matriz)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452903"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Como animar um objeto ao longo de um caminho (animação de matriz)
Este exemplo mostra como usar a classe <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> para animar um objeto ao longo de um caminho que é definido por um <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima um objeto ao longo de um caminho fazendo o seguinte:  
  
- Aplica um <xref:System.Windows.Media.MatrixTransform> ao objeto para movê-lo.  
  
- Define o caminho usando um <xref:System.Windows.Media.PathGeometry>.  
  
- Cria um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e o usa para animar a propriedade <xref:System.Windows.Media.Matrix> da <xref:System.Windows.Media.MatrixTransform>. O <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> usa o <xref:System.Windows.Media.PathGeometry> e o usa para gerar valores de <xref:System.Windows.Media.Matrix>.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Para obter o exemplo completo, consulte [exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations). Para obter mais informações sobre caminhos geométricos, consulte a [visão geral da geometria](geometry-overview.md).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)

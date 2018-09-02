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
ms.openlocfilehash: d6dc79cd7a15aef2a4168fffb293c5e1f33cde08
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416614"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Como animar um objeto ao longo de um caminho (animação de ponto)
Este exemplo mostra como usar um <xref:System.Windows.Media.Animation.PointAnimationUsingPath> objeto para animar um <xref:System.Windows.Point> ao longo de um caminho curvo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move uma <xref:System.Windows.Media.EllipseGeometry> ao longo de um caminho definido por uma <xref:System.Windows.Media.PathGeometry>. A geometria elipse <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade, que usa um <xref:System.Windows.Point> valor, especifica sua posição; para mover a geometria da elipse, você animar sua <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade. O exemplo usa uma <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animar o <xref:System.Windows.Media.EllipseGeometry> do objeto <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028).  
  
 A versão de código do exemplo anterior usada um <xref:System.Windows.Media.Animation.Storyboard> animar o <xref:System.Windows.Media.EllipseGeometry>, mesmo que apenas uma animação foi aplicada. Um <xref:System.Windows.Media.Animation.Storyboard> geralmente é a maneira mais fácil para aplicar várias animações, pois essas animações podem ser controladas pelo mesmo <xref:System.Windows.Media.Animation.Storyboard>. No entanto, uma maneira fácil de aplicar uma única animação a uma propriedade ao usar o código é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método. Para obter um exemplo, consulte [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de animação de caminho](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

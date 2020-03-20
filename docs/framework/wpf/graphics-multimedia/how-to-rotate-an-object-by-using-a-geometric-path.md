---
title: Como girar um objeto usando um caminho geométrico
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186872"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Como girar um objeto usando um caminho geométrico
Este exemplo mostra como girar (pivô) um objeto ao <xref:System.Windows.Media.PathGeometry> longo de um caminho geométrico que é definido por um objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> seguir usa três objetos para mover um retângulo ao longo de um caminho geométrico.  
  
- O <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> primeiro anima <xref:System.Windows.Media.RotateTransform> um que é aplicado ao retângulo. A animação gera valores de ângulos. Isso faz o retângulo girar ao longo dos contornos do caminho.  
  
- Os outros dois objetos <xref:System.Windows.Media.TranslateTransform.Y%2A> animam <xref:System.Windows.Media.TranslateTransform> os <xref:System.Windows.Media.TranslateTransform.X%2A> valores de um que é aplicado ao retângulo. Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Outra maneira de girar um objeto usando um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> caminho geométrico é usar um objeto e definir sua <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade para `true`. Para obter mais informações e um exemplo, consulte ["Gire um objeto usando um caminho geométrico" (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Para obter a amostra completa, consulte [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da animação](animation-overview.md)
- [Exemplo de animação de caminho](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [Tópicos explicativos de animação do caminho](path-animation-how-to-topics.md)

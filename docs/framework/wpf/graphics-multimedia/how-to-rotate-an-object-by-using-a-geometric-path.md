---
title: "Como girar um objeto usando um caminho geométrico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e4963d174f889ac51087356b042bc5b06990593
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a>Como girar um objeto usando um caminho geométrico
Este exemplo mostra como girar um objeto ao longo de um caminho geométrico que é definido por um <xref:System.Windows.Media.PathGeometry> objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa três <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objetos para mover um retângulo ao longo de um caminho geométrico.  
  
-   A primeira <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> anima um <xref:System.Windows.Media.RotateTransform> que é aplicada ao retângulo. A animação gera valores de ângulos. Isso faz o retângulo girar ao longo dos contornos do caminho.  
  
-   Os dois objetos animam a <xref:System.Windows.Media.TranslateTransform.X%2A> e <xref:System.Windows.Media.TranslateTransform.Y%2A> valores de um <xref:System.Windows.Media.TranslateTransform> que é aplicada ao retângulo. Eles fazem o retângulo ser mover horizontal e verticalmente ao longo do caminho.  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 Outra maneira de girar um objeto usando um caminho geométrico é usar um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> do objeto e defina seu <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> propriedade `true`. Para obter mais informações e um exemplo, consulte [girar um objeto usando um caminho Geométrico (animação de matriz)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

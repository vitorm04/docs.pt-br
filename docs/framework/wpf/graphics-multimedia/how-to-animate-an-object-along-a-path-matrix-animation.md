---
title: "Como animar um objeto ao longo de um caminho (animação de matriz)"
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
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb1bbe43c7e1797d5943bf3da6b4aca22a11c3a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a>Como animar um objeto ao longo de um caminho (animação de matriz)
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> classe para animar um objeto ao longo de um caminho que é definido por um <xref:System.Windows.Media.PathGeometry>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima um objeto ao longo de um caminho, fazendo o seguinte:  
  
-   Aplica-se um <xref:System.Windows.Media.MatrixTransform> ao objeto para movê-lo.  
  
-   Define o caminho usando um <xref:System.Windows.Media.PathGeometry>.  
  
-   Cria um <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> e o utiliza para animar a <xref:System.Windows.Media.Matrix> propriedade o <xref:System.Windows.Media.MatrixTransform>. O <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> leva o <xref:System.Windows.Media.PathGeometry> e o utiliza para gerar <xref:System.Windows.Media.Matrix> valores.  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 Para o exemplo completo, consulte [exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028). Para obter mais informações sobre caminhos geométricos, consulte o [visão geral de geometria](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Exemplo de animação de caminho](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Tópicos explicativos de animação do caminho](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)

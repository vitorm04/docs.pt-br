---
title: Como animar a posição de um objeto usando PointAnimation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 326b71c10ad608e2481673e1c4a8cbc9ecbdc0dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559151"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a>Como animar a posição de um objeto usando PointAnimation
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.PointAnimation> classe para animar um objeto ao longo de um <xref:System.Windows.Shapes.Path>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir move uma elipse ao longo de um <xref:System.Windows.Shapes.Path> de um ponto na tela para outra. O exemplo anima a posição de um <xref:System.Windows.Media.EllipseGeometry> usando <xref:System.Windows.Media.Animation.PointAnimation> para animar a <xref:System.Windows.Media.EllipseGeometry.Center%2A> propriedade.  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [Animação e temporização](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)

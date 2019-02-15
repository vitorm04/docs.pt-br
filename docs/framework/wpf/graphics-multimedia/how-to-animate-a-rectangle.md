---
title: 'Como: Animar um retângulo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], rectangles
- rectangles [WPF], animating
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
ms.openlocfilehash: dbff015bdc5f9ce56d2c366e0d348429efb7f4b5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305149"
---
# <a name="how-to-animate-a-rectangle"></a>Como: Animar um retângulo
Este exemplo mostra como animar alterações de tamanho e posição de um retângulo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma instância das <xref:System.Windows.Media.Animation.RectAnimation> classe animar o <xref:System.Windows.Media.RectangleGeometry.Rect%2A> propriedade de um <xref:System.Windows.Media.RectangleGeometry>, que anima as alterações para o tamanho e posição do retângulo.  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Media.Animation.RectAnimation>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.RectangleGeometry>
- [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Elementos gráficos e multimídia](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [Tópicos explicativos de elementos gráficos](graphics-how-to-topics.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)

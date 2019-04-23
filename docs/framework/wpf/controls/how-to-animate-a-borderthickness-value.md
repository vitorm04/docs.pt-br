---
title: 'Como: Animar um valor de BorderThickness'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 10e177d1f6d6add4638ce14af900e75d7e363890
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150729"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Como: Animar um valor de BorderThickness
Este exemplo mostra como animar alterações para a espessura de uma borda usando o <xref:System.Windows.Media.Animation.ThicknessAnimation> classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir anima a espessura de uma borda usando <xref:System.Windows.Media.Animation.ThicknessAnimation>. O exemplo usa o <xref:System.Windows.Controls.Border.BorderThickness%2A> propriedade de <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Visão geral da animação](../graphics-multimedia/animation-overview.md)
- [Tópicos explicativos de animação e tempo](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animar a espessura de uma borda usando quadros principais](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)

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
ms.openlocfilehash: 4f38895f58e1a41a8a66b31a116e94f5b02492f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368932"
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

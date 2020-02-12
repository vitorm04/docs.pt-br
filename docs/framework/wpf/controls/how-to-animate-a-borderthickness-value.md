---
title: Como animar um valor de BorderThickness
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124657"
---
# <a name="how-to-animate-a-borderthickness-value"></a>Como animar um valor de BorderThickness
Este exemplo mostra como animar as alterações na espessura de uma borda usando a classe <xref:System.Windows.Media.Animation.ThicknessAnimation>.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo a seguir anima a espessura de uma borda usando <xref:System.Windows.Media.Animation.ThicknessAnimation>. O exemplo usa a propriedade <xref:System.Windows.Controls.Border.BorderThickness%2A> de <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 Para obter o exemplo completo, consulte [Galeria de exemplo de animação](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [Visão geral da animação](../graphics-multimedia/animation-overview.md)
- [Tópicos explicativos de animação e tempo](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [Animar a espessura de uma borda usando quadros principais](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)

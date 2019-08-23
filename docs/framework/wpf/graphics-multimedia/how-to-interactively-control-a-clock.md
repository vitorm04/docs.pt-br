---
title: 'Como: Controlar interativamente um relógio'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951343"
---
# <a name="how-to-interactively-control-a-clock"></a>Como: Controlar interativamente um relógio
A <xref:System.Windows.Media.Animation.Clock> propriedade de <xref:System.Windows.Media.Animation.ClockController> um objeto permite que você inicie, pause, retome, busque, avance o relógio para seu período de preenchimento interativamente e pare o relógio. Somente o relógio raiz de uma árvore de tempo pode ser controlado interativamente.  
  
> [!NOTE]
> Há outras maneiras de controlar interativamente animações que não exigem que você trabalhe diretamente com relógios: você também pode usar storyboards. Os storyboards têm suporte tanto na marcação quanto no código. Para obter um exemplo, consulte [animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md) ou a [visão geral da animação](animation-overview.md).  
  
 No exemplo a seguir, vários botões são usados para controlar interativamente um relógio de animação.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Consulte também

- [Animar uma propriedade usando um storyboard](how-to-animate-a-property-by-using-a-storyboard.md)
- [Visão geral da animação](animation-overview.md)

---
title: Como controlar interativamente um relógio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 63e72c48afd9b72a6b334ccdc234d08cef7288f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-interactively-control-a-clock"></a>Como controlar interativamente um relógio
Um <xref:System.Windows.Media.Animation.Clock> do objeto <xref:System.Windows.Media.Animation.ClockController> propriedade permite que você interativamente Iniciar, pausar, retomar, busca, Avançar o relógio para completar seu período e parar o relógio. Somente o relógio raiz de uma árvore de tempo pode ser controlado interativamente.  
  
> [!NOTE]
>  Existem outras maneiras de controlar animações que não exigem que você trabalhe diretamente com relógios: você também pode usar Storyboards. Storyboards são suportados na marcação e código. Para obter um exemplo, consulte [animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ou [visão geral de animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 No exemplo a seguir, vários botões são usados para controlar interativamente um relógio de animação.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Consulte também  
 [Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)

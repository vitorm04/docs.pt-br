---
title: Como animar uma propriedade usando um AnimationClock
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: b8c64586d0dc5dc2e565fe4cb002e0f9cd4109af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Como animar uma propriedade usando um AnimationClock
Este exemplo mostra como usar <xref:System.Windows.Media.Animation.Clock> objetos para animar uma propriedade.  
  
 Existem três maneiras de animar uma propriedade de dependência:  
  
-   Criar um <xref:System.Windows.Media.Animation.AnimationTimeline> e associá-la com essa propriedade usando um <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Usar o objeto <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método para aplicar uma única <xref:System.Windows.Media.Animation.AnimationTimeline> para uma propriedade de destino.  
  
-   Criar um <xref:System.Windows.Media.Animation.AnimationClock> de um <xref:System.Windows.Media.Animation.AnimationTimeline> e aplicá-la a uma propriedade.  
  
 <xref:System.Windows.Media.Animation.Storyboard> objetos e o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> método permitem que você animar propriedades sem criar e distribuir relógios diretamente (para obter exemplos, consulte [animar uma propriedade usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) e [animar uma propriedade sem Usando um Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); relógios são criados e distribuídos para você automaticamente.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Media.Animation.AnimationClock> e aplicá-la a duas propriedades semelhantes.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Para obter um exemplo mostrando como controlar interativamente um <xref:System.Windows.Media.Animation.Clock> depois de iniciada, consulte [controle interativamente um relógio](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Consulte também  
 [Animar uma propriedade usando um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animar uma propriedade sem usar um storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [Visão geral das técnicas de animação da propriedade](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)

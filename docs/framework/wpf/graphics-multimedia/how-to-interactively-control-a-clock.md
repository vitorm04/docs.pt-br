---
title: "Como controlar interativamente um relógio"
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
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: debe65ef1587171dc2f324a19da4b43e7274c438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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

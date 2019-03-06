---
title: 'Como: Alterar a velocidade de um relógio sem alterar a velocidade da linha do tempo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 19e6874b9b472cb4a5f716677f99af03f2b73b10
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358269"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a>Como: Alterar a velocidade de um relógio sem alterar a velocidade da linha do tempo
Um <xref:System.Windows.Media.Animation.ClockController> do objeto <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> propriedade permite que você alterar a velocidade de uma <xref:System.Windows.Media.Animation.Clock> sem alterar o <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> o relógio <xref:System.Windows.Media.Animation.Timeline>. No exemplo a seguir, uma <xref:System.Windows.Media.Animation.ClockController> é usado para modificar interativamente o <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> de um relógio. O <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> evento e o relógio <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> propriedade são usados para exibir a velocidade do relógio atual global cada vez que seu interativo <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> é alterado.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]

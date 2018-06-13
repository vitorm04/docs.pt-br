---
title: Como alterar a velocidade de um relógio sem alterar a velocidade da linha do tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 126d260fbd59c1c35d8f56be6aa7dabe7688fa32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556608"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="c3f03-102">Como alterar a velocidade de um relógio sem alterar a velocidade da linha do tempo</span><span class="sxs-lookup"><span data-stu-id="c3f03-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="c3f03-103">Um <xref:System.Windows.Media.Animation.ClockController> do objeto <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> propriedade permite que você altere a velocidade de um <xref:System.Windows.Media.Animation.Clock> sem alterar o <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> do relógio do <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="c3f03-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="c3f03-104">No exemplo a seguir, uma <xref:System.Windows.Media.Animation.ClockController> é usado para modificar interativamente o <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> de um relógio.</span><span class="sxs-lookup"><span data-stu-id="c3f03-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="c3f03-105">O <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> evento e o relógio <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> propriedade são usados para exibir a velocidade de global atual do relógio sempre que seu interativo <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> é alterado.</span><span class="sxs-lookup"><span data-stu-id="c3f03-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3f03-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3f03-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]

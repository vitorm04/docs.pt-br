---
title: Como especificar se uma linha do tempo é revertida automaticamente
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="1b59b-102">Como especificar se uma linha do tempo é revertida automaticamente</span><span class="sxs-lookup"><span data-stu-id="1b59b-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="1b59b-103">Uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade determina se ele executa em ordem inversa após ele concluir uma interação direta.</span><span class="sxs-lookup"><span data-stu-id="1b59b-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="1b59b-104">O exemplo a seguir mostra várias animações com duração e valores de destino idênticos, mas com diferentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="1b59b-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="1b59b-105">Para demonstrar como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade se comporta com diferentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configurações, algumas animações são definidas para repetir.</span><span class="sxs-lookup"><span data-stu-id="1b59b-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="1b59b-106">A última animação mostra como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade funciona em cronogramas aninhados.</span><span class="sxs-lookup"><span data-stu-id="1b59b-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b59b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1b59b-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]

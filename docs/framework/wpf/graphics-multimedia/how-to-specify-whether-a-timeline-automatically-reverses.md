---
title: 'Como: Especificar se uma linha do tempo é revertida automaticamente'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024658"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="293fe-102">Como: Especificar se uma linha do tempo é revertida automaticamente</span><span class="sxs-lookup"><span data-stu-id="293fe-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="293fe-103">Uma linha do tempo <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade determina se ele executa em ordem inversa após ele concluir uma iteração.</span><span class="sxs-lookup"><span data-stu-id="293fe-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="293fe-104">O exemplo a seguir mostra várias animações com duração e valores de destino idênticos, mas com diferentes <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> configurações.</span><span class="sxs-lookup"><span data-stu-id="293fe-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="293fe-105">Para demonstrar como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade comporta-se com diferentes <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> configurações, algumas animações são definidas para repetir.</span><span class="sxs-lookup"><span data-stu-id="293fe-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="293fe-106">A última animação mostra como o <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> propriedade funciona em cronogramas aninhados.</span><span class="sxs-lookup"><span data-stu-id="293fe-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="293fe-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="293fe-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]

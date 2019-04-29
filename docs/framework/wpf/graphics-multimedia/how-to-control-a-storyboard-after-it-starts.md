---
title: 'Como: Controlar um Storyboard depois de ter começado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762131"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="7b302-102">Como: Controlar um Storyboard depois de ter começado</span><span class="sxs-lookup"><span data-stu-id="7b302-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="7b302-103">Este exemplo mostra como usar código para controlar um <xref:System.Windows.Media.Animation.Storyboard> depois que ele foi iniciado.</span><span class="sxs-lookup"><span data-stu-id="7b302-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="7b302-104">Para controlar um storyboard no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> e <xref:System.Windows.TriggerAction> objetos; por exemplo, consulte [usar gatilhos de evento para controlar um Storyboard depois de ter começado](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="7b302-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="7b302-105">Para iniciar um storyboard, use seu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método, que distribui as animações do storyboard às propriedades que elas animam e inicia o storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b302-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="7b302-106">Para tornar um storyboard controlável, você deve usar o <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método e especifique **verdadeiro** como o segundo parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7b302-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="7b302-107">Em seguida, use os métodos interativos do storyboard para pausar, retomar, procurar, parar, acelerar ou retardar o storyboard ou avançar para seu período de preenchimento.</span><span class="sxs-lookup"><span data-stu-id="7b302-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="7b302-108">A seguir temos uma lista de métodos interativos de storyboard:</span><span class="sxs-lookup"><span data-stu-id="7b302-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
- <span data-ttu-id="7b302-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pausa o storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b302-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
- <span data-ttu-id="7b302-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Retoma um storyboard em pausa.</span><span class="sxs-lookup"><span data-stu-id="7b302-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
- <span data-ttu-id="7b302-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Define a velocidade interativa do storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b302-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
- <span data-ttu-id="7b302-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Busca o storyboard no local especificado.</span><span class="sxs-lookup"><span data-stu-id="7b302-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
- <span data-ttu-id="7b302-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Busca o storyboard para o local especificado.</span><span class="sxs-lookup"><span data-stu-id="7b302-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="7b302-114">Ao contrário de <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> método, essa operação é processado antes da próxima escala.</span><span class="sxs-lookup"><span data-stu-id="7b302-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
- <span data-ttu-id="7b302-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Avança o storyboard para seu período de preenchimento, se ele tiver um.</span><span class="sxs-lookup"><span data-stu-id="7b302-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
- <span data-ttu-id="7b302-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Interrompe o storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b302-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="7b302-117">No exemplo a seguir, diversos métodos de storyboard são usados para controlar de forma interativa um storyboard.</span><span class="sxs-lookup"><span data-stu-id="7b302-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="7b302-118">**Observação:** Para ver um exemplo de como controlar um storyboard usando gatilhos com [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consulte [usar gatilhos de evento para controlar um Storyboard depois de ter começado](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="7b302-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b302-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b302-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7b302-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b302-120">See also</span></span>

- [<span data-ttu-id="7b302-121">Usar gatilhos de evento para controlar um storyboard depois de ter começado</span><span class="sxs-lookup"><span data-stu-id="7b302-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)

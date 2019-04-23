---
title: 'Como: Especificar HandoffBehavior entre animações de Storyboard'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083875"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="2f9eb-102">Como: Especificar HandoffBehavior entre animações de Storyboard</span><span class="sxs-lookup"><span data-stu-id="2f9eb-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="2f9eb-103">Este exemplo mostra como especificar o comportamento de entrega entre animações de storyboard.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="2f9eb-104">O <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> propriedade de <xref:System.Windows.Media.Animation.BeginStoryboard> Especifica como novas animações interagem com quaisquer outras existentes já aplicadas a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f9eb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2f9eb-105">Example</span></span>  
 <span data-ttu-id="2f9eb-106">O exemplo a seguir cria dois botões que aumentam quando o cursor do mouse passa sobre eles e ficam menores quando o cursor se afasta.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="2f9eb-107">Se você passar o mouse sobre um botão e depois remover rapidamente o cursor, a segunda animação será aplicada antes da conclusão da primeira.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="2f9eb-108">Quando duas animações se sobrepõem assim que você pode ver a diferença entre o <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> valores de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> e <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="2f9eb-109">Um valor de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combina as animações sobrepostas causando uma transição mais suave entre animações enquanto um valor de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> faz com que a nova animação substitua imediatamente a animação sobreposta anterior.</span><span class="sxs-lookup"><span data-stu-id="2f9eb-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2f9eb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f9eb-110">See also</span></span>

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="2f9eb-111">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="2f9eb-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2f9eb-112">Tópicos explicativos de animação e tempo</span><span class="sxs-lookup"><span data-stu-id="2f9eb-112">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)

---
title: 'Como: Especificar HandoffBehavior entre animações de Storyboard'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651032"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Como: Especificar HandoffBehavior entre animações de Storyboard
Este exemplo mostra como especificar o comportamento de entrega entre animações de storyboard. O <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> propriedade de <xref:System.Windows.Media.Animation.BeginStoryboard> Especifica como novas animações interagem com quaisquer outras existentes já aplicadas a uma propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois botões que aumentam quando o cursor do mouse passa sobre eles e ficam menores quando o cursor se afasta. Se você passar o mouse sobre um botão e depois remover rapidamente o cursor, a segunda animação será aplicada antes da conclusão da primeira. Quando duas animações se sobrepõem assim que você pode ver a diferença entre o <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> valores de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> e <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Um valor de <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combina as animações sobrepostas causando uma transição mais suave entre animações enquanto um valor de <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> faz com que a nova animação substitua imediatamente a animação sobreposta anterior.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [Visão geral da animação](animation-overview.md)
- [Tópicos explicativos de animação e tempo](animation-and-timing-how-to-topics.md)

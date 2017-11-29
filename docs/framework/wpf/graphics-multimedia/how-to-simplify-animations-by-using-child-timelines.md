---
title: "Como simplificar animações usando linhas do tempo filho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daa4caac0046293e8b86a773bfffd46cf30e835b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Como simplificar animações usando linhas do tempo filho
Este exemplo mostra como simplificar animações usando filho <xref:System.Windows.Media.Animation.ParallelTimeline> objetos. Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de <xref:System.Windows.Media.Animation.Timeline> que fornece informações de direcionamento para o cronogramas que ele contém. Use um <xref:System.Windows.Media.Animation.Storyboard> para fornecer informações, incluindo informações de objeto e propriedade de direcionamento da linha do tempo.  
  
 Para começar uma animação, use um ou mais <xref:System.Windows.Media.Animation.ParallelTimeline> objetos como elementos aninhados filhos de um <xref:System.Windows.Media.Animation.Storyboard>. Essas <xref:System.Windows.Media.Animation.ParallelTimeline> objetos podem conter outras animações e portanto, podem melhor encapsular as sequências de tempo em animações complexas. Por exemplo, se são animar uma <xref:System.Windows.Controls.TextBlock> e várias formas da mesma <xref:System.Windows.Media.Animation.Storyboard>, você pode separar as animações a <xref:System.Windows.Controls.TextBlock> e formas, colocando cada uma em um separado <xref:System.Windows.Media.Animation.ParallelTimeline>. Como cada <xref:System.Windows.Media.Animation.ParallelTimeline> tem seu próprio <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> e todos os elementos filho do <xref:System.Windows.Media.Animation.ParallelTimeline> começar em relação a esse <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, temporização é melhor encapsulada.  
  
 O exemplo a seguir anima dois pedaços de texto (<xref:System.Windows.Controls.TextBlock> objetos) de dentro do mesmo <xref:System.Windows.Media.Animation.Storyboard>. Um <xref:System.Windows.Media.Animation.ParallelTimeline> encapsula as animações de um do <xref:System.Windows.Controls.TextBlock> objetos.  
  
 **Observação de desempenho:** Embora você possa aninhar <xref:System.Windows.Media.Animation.Storyboard> cronogramas, <xref:System.Windows.Media.Animation.ParallelTimeline>s são mais adequadas para aninhamento, pois requerem menos sobrecarga. (O <xref:System.Windows.Media.Animation.Storyboard> classe herda o <xref:System.Windows.Media.Animation.ParallelTimeline> classe.)  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Especificar HandoffBehavior entre animações de storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)

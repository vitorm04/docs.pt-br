---
title: 'Como: Simplificar animações usando linhas do tempo filho'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 933ba2dff86b99bddd8d8f75bafcd94833b2e066
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370352"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Como: Simplificar animações usando linhas do tempo filho
Este exemplo mostra como simplificar animações usando filho <xref:System.Windows.Media.Animation.ParallelTimeline> objetos. Um <xref:System.Windows.Media.Animation.Storyboard> é um tipo de <xref:System.Windows.Media.Animation.Timeline> que fornece informações de direcionamento para as linhas do tempo que ele contém. Use um <xref:System.Windows.Media.Animation.Storyboard> para fornecer informações, incluindo informações de propriedade e o objeto de direcionamento de linha do tempo.  
  
 Para começar uma animação, use um ou mais <xref:System.Windows.Media.Animation.ParallelTimeline> objetos como elementos filho aninhados de um <xref:System.Windows.Media.Animation.Storyboard>. Eles <xref:System.Windows.Media.Animation.ParallelTimeline> objetos podem conter outras animações e portanto, podem melhor encapsular as sequências de tempo em animações complexas. Por exemplo, se você estiver animando um <xref:System.Windows.Controls.TextBlock> e várias formas no mesmo <xref:System.Windows.Media.Animation.Storyboard>, você pode separar as animações para o <xref:System.Windows.Controls.TextBlock> e das formas, colocando cada uma em um separado <xref:System.Windows.Media.Animation.ParallelTimeline>. Porque cada <xref:System.Windows.Media.Animation.ParallelTimeline> tem seu próprio <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> e todos os elementos filho a <xref:System.Windows.Media.Animation.ParallelTimeline> começam em relação a isso <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, medição de tempo é mais bem encapsulada.  
  
 O exemplo a seguir anima dois pedaços de texto (<xref:System.Windows.Controls.TextBlock> objetos) de dentro do mesmo <xref:System.Windows.Media.Animation.Storyboard>. Um <xref:System.Windows.Media.Animation.ParallelTimeline> encapsula as animações de um do <xref:System.Windows.Controls.TextBlock> objetos.  
  
 **Observação de desempenho:** Embora você possa aninhar <xref:System.Windows.Media.Animation.Storyboard> cronogramas dentro uns aos outros, <xref:System.Windows.Media.Animation.ParallelTimeline>s são mais adequadas para aninhar, pois requerem menos sobrecarga. (O <xref:System.Windows.Media.Animation.Storyboard> herda o <xref:System.Windows.Media.Animation.ParallelTimeline> classe.)  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da animação](animation-overview.md)
- [Especificar HandoffBehavior entre animações de storyboard](how-to-specify-handoffbehavior-between-storyboard-animations.md)
